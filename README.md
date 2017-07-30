# ionic-location-selector
Ionic plugin - A simple component let you select a location from google place

![alt text](https://raw.githubusercontent.com/ultraxion/ionic-location-selector-example/master/assets/IonicLocationSelectorDemo.gif "Ionic Location Selector")

# Installation

- Extract files from archive
- Copy files into the **src/components** folder _(create this folder if needed)_

# Usage

- Add google maps api library in your **index.html** :

_(Don't forget to add your api key)_
```html
<script src="http://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&libraries=places"></script>
```

- Add the **LocationSelectorModule** in your **app.module.ts** : 

```text
[...]
import { LocationSelectorModule } from '../components/location-selector/location-selector.module'; // <- add this line

@NgModule({
    declarations: [
        MyApp,
        MyPage
    ],
    imports: [
        BrowserModule,
        IonicModule.forRoot(MyApp),
        LocationSelectorModule // <- add this line
    ],
    bootstrap: [IonicApp],
    entryComponents: [
        MyApp,
        MyPage
    ],
    providers: [
        StatusBar,
        SplashScreen,
        {provide: ErrorHandler, useClass: IonicErrorHandler}
    ]
})
export class AppModule {}
```
- Add the selector in your page :
```html
<location-selector-input></location-selector-input>
```

# Configuration
### Global configuration
You can add global configuration using **forRoot()** method at the import: 
- Params available :

    **countries** : _string[]_ // list of countrie code availble for searching location
    
    **inputPlaceholderText** : _string_ // the input placeholder
    
    **inputClearButtonHidden** : _boolean_ // hide the clear button on the input
     
    **modalCloseButtonText** : _string_ // text on the close button from the modal
    
    **modalSearchText** : _string_ // text inside the search bar
    
    **modalTitleText** : _string_ // title of the modal
    
    **modalNoResultText** : _string_ // text shown when no results

_usage exemple:_
```javascript
LocationSelectorModule.forRoot({
    countries: ['us','ca'],
    inputPlaceholderText: 'My location',
    inputClearButtonHidden: false,
    modalCloseButtonText: 'Close',
    modalSearchText: 'Search',
    modalTitleText: 'Select your location',
    modalNoResultText: 'No location found'
})
```

### Attributes

You can also pass some attribute on each selector that override global configuration

- **placeholder** _[ string ]_ default value : 'My location'
- **showClearButton** _[ boolean ]_ default value : true
- **countries** _[ string[] ]_ default value : []

### Events

- **locationSelected($event)**  On location selected, return the full google place object response_
  
### Example
```html
<location-selector-input
        [countries]="['fr']"
        [showClearButton]="false"
        (locationSelected)="onLocationSelected($event)"
        placeholder="J'habite à">
</location-selector-input>
```

