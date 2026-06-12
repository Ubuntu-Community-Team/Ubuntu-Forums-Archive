---
title: "Still can't view files on android phone in Ubuntu"
date: 2013-03-14
forum: Mobile Technology Discussions (CLOSED)
---

### Post by PaulWhipp on 2013-03-14
On my new Galaxy Note II (Android 4.1.1), connecting it to either 10.04 or 12.10; I can see the top level folders but no files.

Unfortunately there is no 'USB utilities' option on the phone so I can't use the fix proposed in [this old thread]("http://ubuntuforums.org/showthread.php?t=1881883") because I can't change the phone's settings. View hidden files has no effect.

Changing the developer USB debugging option also has no effect (although I can use adb at a stretch this way as a very tedious workaround).

This is really annoying. Its a great 'mini-tab'/phone which would almost eliminate the need for a laptop if I could easily work with the files/folders when its connected to a PC. The phone works fine connected to Microsoft Windows but who in their right mind would want to use that?

Does anyone have a workaround or fix for this (preferably one that works in 10.04 up)?

---

### Post by 3rdalbum on 2013-03-14
Install an FTP server on the Note, and have the phone connected to your wifi network. You can connect to FTP using Nautilus.

---

### Post by PaulWhipp on 2013-03-14
Thanks 3rdalbum,

I'll give it a try but it will only be of limited use. There is not always a wifi network available.

---

### Post by wildmanne39 on 2013-03-14
*Thread moved to **Mobile Technology Discussions**.*

---

### Post by 3rdalbum on 2013-03-15
> **PaulWhipp said:**
> Thanks 3rdalbum,

I'll give it a try but it will only be of limited use. There is not always a wifi network available.

I don't know if the Galaxy Note comes with tethering support. If it does, you could try creating the FTP server, then plugging the phone into the computer and turning on tethering on the phone. The computer will use the phone as an internet connection, but it will probably also result in the phone's FTP server being accessible through the USB cable instead of wifi.

There are guides around to make MTP work properly... but I've never got one to work.

Or, the other option is to upgrade to 13.04 a little early as it reportedly has the proper MTP support already, you'll be able to plug the phone in like normal to access it on the computer.

---

### Post by Alekhios on 2013-07-20
At least for me, this problem had an obvious-not-so-obvious solution, although it's been a long time since the start of this thread, it doesn't have a solution, and for future ubuntu noobs as me, my answer might work. When you connect your android 4.0+ to your PC, on your smatphone you should go to the notification bar and click on the usb connection option, by default you'll find that it's enabled for images files transfering (PTP), you have to select the MTP option. If I haven't made myself clear you could take a look at this page [http://www.maketecheasier.com/connect-galaxy-nexus-to-ubuntu/2012/02/15](http://www.maketecheasier.com/connect-galaxy-nexus-to-ubuntu/2012/02/15)

Regards

---

