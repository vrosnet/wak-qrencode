wak-qrencode
============

The module includes [qrencode 3.4.4](http://fukuchi.org/works/qrencode/) executable for Mac, Windows x64 and Linux x64.

The executables for Mac are built with @loader_path and for Linux with $ORIGIN, so no need to install qrencode, zlib, or libpng.

Install
-------
The module can be installed in any solution.

* Create a solution level filesystems.js, if you don't already have one, and follow the example.
```
  {
  "name":"Modules",
  "parent":"SOLUTION",
  "path":"Modules",
  "writable":true
  }  
```

That' it!

Example
-------
```
var modulesFolder = FileSystemSync('Modules');
var qrencode = require(modulesFolder.path + 'qrencode');

var desktopPath = FileSystemSync('Desktop').path;

var url = 'http://www.wakanda.org/';

//to create a file on disk
qrencode.qrencode('-o ' + desktopPath + 'test.png' + ' ' + url);

//to create a Buffer/Blob 
qrencode.qrencode('-t PNG -o - ' + ' ' + url).console.stdOut.toBlob('image/png');

//project module (for RPC)
var qr = require('qr');

//returns a data url (see index.html)
qr.encode(url);
```
