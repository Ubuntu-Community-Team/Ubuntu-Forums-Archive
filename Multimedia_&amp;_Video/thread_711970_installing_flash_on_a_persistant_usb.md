---
title: "installing flash on a persistant usb"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by maulakai on 2008-03-01
Ok, so I've installed ubuntu to my flash memory stick, as per pendrivelinux.com instructions.  got everything working fine.

except macromedia's flash

i visit youtube, which automatically brings up an install prompt.  The install appears to go through fine.  I've already enabled the extra repositories, and according to the package manager, the nonfree version of flash IS installed.

Except that no matter how many times i restart firefox, ubuntu, or reinstall the damn thing, it doesn't work.  I'm constantly prompted to install it, then told that its already installed.

Is there any way to properly install flash on a persistant ubuntu install?

---

### Post by maulakai on 2008-03-01
i'm answering my own question here

[http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

by downloading and installing this deb, flash works fine

I got the link from a post saying the repository .deb failed a hash check

---

### Post by AlPauls on 2008-03-04
I've gone through the install procedure, including the lilo install MBR fix, but still can't get the BIOS to see the USB device as a boot device. The only errors were the symbolic link errors. USB is boot enabled in BIOS but does not appear in the boot priority list What do I need to do?

---

### Post by maulakai on 2008-03-15
try the device on a different pc.   this kind of install can be temperamental and i find my sticks dont work on every pc they should.  the simple solution might be you've gotta use it on another pc

---

