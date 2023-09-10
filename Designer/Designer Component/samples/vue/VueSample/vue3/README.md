# GC.Spread.Sheets.Designer Wrapper for VUE

### `npm install`
The dependencies required to install

### `npm run dev`
Start the dev server

### SpreadJS Designer Vue Wrapper Component Markup
```js
<gc-spread-sheets-designer>
</gc-spread-sheets-designer>
```

**styleInfo prop** Pass styleInfo to the component props to customize the designer's style.
```js
<gc-spread-sheets-designer :styleInfo='styleInfo'>
</gc-spread-sheets-designer>
  export default {
    data: function () {
      return {
        styleInfo: { height: '800px', width: '1200px', border: 'solid red 1px' }
      };
    }
  }
```

**config prop** Pass in the custom **config** to customize the Designer.
```js
<gc-spread-sheets-designer :config='customConfig'>
</gc-spread-sheets-designer>
  export default {
    data: function () {
      return {
        config: config //default config json import from local
      };
    },
    computed: {
        customConfig: function () {
            this.config.ribbon[0].buttonGroups.unshift(
                {
                    "label":"NewDesigner",
                    "thumbnailClass":"welcome",
                    "commandGroup":{
                        "children":[
                            {
                                "direction":"vertical",
                                "commands":[
                                    "Welcome"
                                ]
                            }
                        ]
                    }
                }
            );
            let customCommand = {
                title: "Welcome",
                text: "Welcome",
                iconClass: "ribbon-button-welcome",
                bigButton: "true",
                commandName: "Welcome",
                execute: async (context, propertyName) => {
                    alert('Welcome to new designer.');
                }
            }
            this.config.commandMap = {
                Welcome: customCommand
            }
            return this.config;
        }
    }
  }
```
**spreadOptions prop** Pass spreadOptions to the component props to customize the spread's options.
```js
<gc-spread-sheets-designer :spreadOptions='spreadOptions'>
</gc-spread-sheets-designer>
  export default {
    data: function () {
      return {
        spreadOptions: { sheetCount: 2 }
      };
    }
  }
```
**designerInitialized event** Fired after instantiation.
```js
<gc-spread-sheets-designer @designerInitialized='designerInitialized'>
</gc-spread-sheets-designer>

export default {
    methods: {
      designerInitialized(designer) {
        //this is designer instance
        console.log(designer);
      }
    }
  }
```

**Apply License** You can register the below code in the component.vue file.
```js
//In src/App.vue file
import '@grapecity/spread-sheets-designer-resources-en'
import * as GC from '@grapecity/spread-sheets';
import '@grapecity/spread-sheets-designer';

//Apply License
GC.Spread.Sheets.LicenseKey = 'Your License';
GC.Spread.Sheets.Designer.LicenseKey = 'Your License';
```