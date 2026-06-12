---
title: "b43 driver getting modprobe errors"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by mbender on 2009-05-14
I've been trying to get the b43 drivers working on a Xubuntu 9.04 install with no success.  The drivers install fine, but won't get showing in the Hardware Drivers gui.  I've tried just about every trick and suggestion in the forums with no luck.  The weird thing about the situation is that modprobe throws errors when I run it by b43.  Here's what happens.

:~$ modprobe b43
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

Anyone know what is causing the modprobe error and could that be party of my problem?

---

### Post by Ayuthia on 2009-05-14
The modprobe warning is just pointing out that there is a file in /etc/modprobe.d that does not have the .conf extension.  In this case, it was the oss-compat file.  The warning should not be causing any problems with the b43 module.

I have found that the Hardware Drivers screen does not always reflect the correct information.  The issue that you are having could be caused by a wireless module conflict.  Have you tried the following:
```
sudo modprobe -r b43 ssb wl
sudo modprobe b43
sudo ifconfig wlan0 up
sudo iwlist scan
```

---

