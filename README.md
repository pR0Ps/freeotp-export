FreeOTP QR Code Exporter
========================

[FreeOTP](https://fedorahosted.org/freeotp/) is a TOTP-compatible authenticator app. It is developed
by RedHat and is open source.

If you would like to move to a different TOTP app, a new phone, or just back up your OTP secrets in
case you lose/break your phone, this app can create QR codes that can be read by other TOTP apps.

This app does all processing locally client side, no data is sent over the network. This can be
verified by looking at the source code (less than 100 lines of JS + the QR code library) or by using
your browser developer tools while running it.

__Although no data leaves your computer, be sure to understand the security implications of backing
up OTP secrets.__

Instructions
------------

Obtain the `tokens.xml` file from the FreeOTP app's stored data.

On rooted devices, this can be done just pulling the file:
```
adb pull /data/data/org.fedorahosted.freeotp/shared_prefs/tokens.xml
```

On a non-rooted device, the file can be recovered by backing up the app and extracting the contents
of the backup file. See [this StackOverflow post](http://stackoverflow.com/a/14686392/369977) for
details.

Once you have the `tokens.xml` file, load it into the app. The QR codes will be displayed below.
You can then either scan the QR codes into a TOTP-compatible app immediately, print them, or save
them. If you choose to store them in any way, make sure to do so safely.

This should work on any modern browser, but has only been tested on Firefox 48 and Chrome 52.

To open the app directly, visit https://rawgit.com/pR0Ps/freeotp-export/master/index.html

Acknowledgements
----------------

- Based on https://github.com/philipsharp/FreeOTPDecoder (Apache license)
- Uses https://github.com/davidshimjs/qrcodejs (MIT license)
- Content served by https://rawgit.com/

License
-------

Apache License, Version 2.0
