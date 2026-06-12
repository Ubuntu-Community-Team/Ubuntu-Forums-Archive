---
title: "Digicel modem not registering in network manager"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by dreaminhere on 2011-07-25
I have a digicel modem I'm using here in Papua New Guinea (PNG). The modem says "Edge usb stick DC87-0" and "ZTE". I think it is also the same as a vodofone k2525, but I'm not sure. After reading and trying many things, I have it partially working. Using modeswitch and usbserial, it is now booting up fine with it inserted or it is ok when I insert it and then eject. It is now registering as ttyUSB0 and ttyUSB1 and wvdialconf will configure. However, it is not showing in the network manager and when I try pppd, it says the password is incorrect. There is no user name and password. How can I get it to show in network manager or connect via pppd?

---

### Post by dreaminhere on 2011-07-26
Ok, I'm closer thanks to these two threads. [http://ubuntuforums.org/archive/index.php/t-931872.html](http://ubuntuforums.org/archive/index.php/t-931872.html) and [https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289239](https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/289239). I had to add myself to the dip group :) and change some permissions. It now connects through pppd but disconnects between 4 seconds and 30 seconds. It shows up in the network manager now but doesn't connect through the network manager. What now?

---

