cordova-plugin-magnetometer
====================

![Coin Detector](https://raw.githubusercontent.com/sdesalas/cordova-magnetometer-app/master/design/screenshots/CoinDetector.jpg)

A magnetic field detector plugin ideal for science toolkit or metal detector apps.

The API can be accessed via single call or by placing a listener that fires a callback function repeatedly.

It displays the raw `x`, `y`, and `z` magnetometer values as well as a computed `magnitude` of the magnetic field.

- iOS Support by [Rameez Raja](https://github.com/mrameezraja)
- Android Support by [RedMobile](https://github.com/red-mobile)

See [this page](https://github.com/red-mobile/cordova-magnetometer-app/blob/master/www/index.html) for a basic sample cordova app using this plugin.

For an in-depth article try this article I wrote: [How to Build a Cross-Platform Metal Detector App](http://desalasworks.com/article/how-to-build-a-cross-platform-metal-detector-app-ios-android/)

Installation
------------

<code> cordova plugin add https://github.com/red-mobile/cordova-plugin-magnetometer </code>


Methods
-------
- cordova.plugins.magnetometer.getReading
- cordova.plugins.magnetometer.watchReadings
- cordova.plugins.magnetometer.stop


cordova.plugins.magnetometer.getReading
-------------------------------------------

Gets a single reading from the magenetometer sensor.

<pre>
<code>
  cordova.plugins.magnetometer.getReading(
    function success(reading){
      console.log(JSON.stringify(reading));
      // Output: {x: 23.113, y:-37.245, z:6.172, magnitude: 44.266}
    },
    function error(message){
     console.log(message);
    }
  )
</code>
</pre>

`reading` object properties:
- `x`
- `y`
- `z`
- `magnitude` (calculated total - always positive)
- `timestamp` (Android only)


cordova.plugins.magnetometer.watchReadings
-------------------------------------------

Gets regular magnetometer readings sent by the internal sensor, will fire success callback repeatedly.

<pre>
<code>
  var watchID = cordova.plugins.magnetometer.watchReadings(
    function success(reading){
      console.log(JSON.stringify(reading));
      // Output: {x: 23.113, y:-37.245, z:6.172, magnitude: 44.266}
    },
    function error(message){
     console.log(message);
    }
  )
</code>
</pre>

`reading` object properties:
- `x`
- `y`
- `z`
- `magnitude` (calculated total - always positive)
- `timestamp` (Android only)

cordova.plugins.magnetometer.stop
--------------------------------

Stops getting readings from the magnetometer sensor. Optional watchID parameter.

<pre>
<code>
  cordova.plugins.magnetometer.stop([watchID])
</code>
</pre>

Supported Platforms
-------------------

- iOS
- Android

