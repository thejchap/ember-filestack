# Ember-filestack

[![npm version](https://badge.fury.io/js/ember-filestack.svg)](http://badge.fury.io/js/ember-filestack)
[![Build Status](https://travis-ci.org/mminkoff/ember-filestack.svg)](https://travis-ci.org/mminkoff/ember-filestack)
[![Ember Observer Score](http://emberobserver.com/badges/ember-filestack.svg)](http://emberobserver.com/addons/ember-filestack)

Provides file picking, storing, and converting funtionality from [Filestack](https://www.filestack.com) using v3+ of their API.

This addon borrows from and builds heavily on [Ember-cli-filepicker](https://github.com/DudaDev/ember-cli-filepicker)

## Installation

* `ember install ember-filestack`

## Usage
* Create your filestack.com key here: https://www.filestack.com/.
* Add your filestack.com key in your config/environment.js
```javascript
//config/environment.js
module.exports = function(environment) {
  var ENV = {
    //...
    filestackKey: '<your-filestack-key>'
  };
  //...
}
```
* Use the filestack.com documentation for options like extensions and services.
* In your template:
```handlebars
{{ember-filestack-picker options=options onSelection='fileSelected' onClose='onClose' onError='onError'}}
```
* You should pass options to determine the behavior of the picker.  Documentation can be found here: https://www.filestack.com/docs/javascript-api/pick-v3.


## Notes
In order to have access to the `filestack` instance you can:
* If `Ember.inject.service` is supported then in your object you can use:
```javascript
export default Ember.Component.extend({
	//injecting the filestack object
	filestack: Ember.inject.service(),

	someFunction: function(){
		// Use the promise in case you are not sure that your component will be initialized after filestack has been loaded
		this.get('filestack.promise').then(function(filestack){
			// do something with filestack
		});

		// OR if you are sure filestack has already been loaded use:
		this.get('filestack.instance')
	}
});
```

## Running

* `ember server`
* Visit your app at http://localhost:4200.

## Running Tests

* `npm test` (Runs `ember try:testall` to test your addon against multiple Ember versions)
* `ember test`
* `ember test --server`

## Building

* `ember build`

For more information on using ember-cli, visit [http://ember-cli.com/](http://ember-cli.com/).
