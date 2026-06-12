---
title: "Can't connect to network on 9.10"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by dvl300 on 2009-11-17
Well i just booted the live CD and i got a surprise my wireless worked, but it won't connect to my router :(
I have a buffalo wireless n-infiniti(UCG300N) usb adapter,
So i tried ndiswrapper but the config tool for it is missing?
Even unsecured networks will not connect.

---

### Post by dvl300 on 2009-11-18
I recently came up with a solution for wireless problems in 9.10
Follow this quick easy guide by me :)
Download ndiswrapper packages for Ubuntu 9.10 karmic koala, from this .gz archive i have put together download [here](http://www.sendspace.com/file/id9nmh)
Boot Ubuntu 9.10 live cd without your wireless adapter attached and install Ubuntu.
Once installed and your up and running, unpack the .gz file you downloaded earlier :wink: and install all the packages, then run Windows Wireless Drivers, pop in the disc that came with your wireless adapter, copy over the driver files, then restart then in Windows Wireless Drivers, click install new driver and select the windows .inf, then open and install.

Now select your access point and enter your key if needed? and you should be connected :D
Enjoy!
:)

---

