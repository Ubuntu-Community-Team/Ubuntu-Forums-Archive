---
title: "Minimal-Ubuntu with wireless"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by durammx on 2009-07-11
Hello to all!
I can't install the minimal ubuntu cd because I have no wire conection!
Have a wireless conection from a HSPA usb stick Huawie E-220, adsl provider Vodafone PT.

Can anyone help?

---

### Post by kerry_s on 2009-07-11
use the alternate installer.

---

### Post by Crafty Kisses on 2009-07-11
I'm not sure what you're asking. Is it because you're in the CLI environment and you're not sure on what commands to run to connect to wireless via the CLI? Well you can search for wireless networks by running:
```
iwlist scan
```
Then you can actually connect to the wireless network by running the following:
```
iwconfig wlan0 essid *youressid*
```

---

### Post by durammx on 2009-07-11
iwlist not found! it seems that wasn't a built-in.

I'm using the shell ash of the cli

alternatives?

---

### Post by ibuclaw on 2009-07-11
You will need to:
```
sudo apt-get install wireless-tools libiw29
```

If you cannot install, you'll have to download them and move them to your minimal ubuntu via another method.

[http://packages.ubuntu.com/jaunty/wireless-tools](http://packages.ubuntu.com/jaunty/wireless-tools)
[http://packages.ubuntu.com/jaunty/libiw29](http://packages.ubuntu.com/jaunty/libiw29)

To install those debs once on your system, cd to the directory, then run:
```
sudo dpkg -i *.deb
```

Regards
Iain

---

### Post by kerry_s on 2009-07-11
it's not that kind of wireless. he needs to use something like wvdial.
[http://en.wikipedia.org/wiki/Huawei_E220](http://en.wikipedia.org/wiki/Huawei_E220)

---

### Post by durammx on 2009-07-11
And I need before the installation. There's no apt on the minimal cd.

How do I put it?

---

### Post by kerry_s on 2009-07-11
the minimal install is really made for a wired connection, so you can install from the internet.
in your situation you should use the alternate installer, it can install a full base install without internet, once you have the base installed you can grab the wvdial.deb install it with dpkg -i , then you can setup your connection, then you can apt-get what ever else you need.

---

