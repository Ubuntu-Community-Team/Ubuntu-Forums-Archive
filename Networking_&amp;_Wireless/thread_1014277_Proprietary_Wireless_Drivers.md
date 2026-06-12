---
title: "Proprietary Wireless Drivers"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by josephst18 on 2008-12-17
I am trying to enable my Broadcom 4306 card. One time, the hardware divers dialogue box came up telling me I could enable fwcutter. I did, since this is what I was trying to do. However, after installing the 188 available updates and rebooting, my wireless card stopped working. I opened up the Hardware Drivers app, and fwcutter was gone. Any help? If I am not able to get this to show up in Hardware Drivers, is there a way to install it manually? If so, I need help with it, since the only thing I can install outside of Add/Remove is a .deb package, which I don't think fwcutter comes in.

---

### Post by Ayuthia on 2008-12-17
The main thing that you need to see is if the firmware files are in /lib/firmware/b43 or /lib/firmware/b43legacy.  If there are files in there, then that is all you need.

I am not for sure which module you are using.  Can you post your lspci -nn info?  Also, can you try going back a kernel version to see if you can get wireless to work?  You can do this by either pressing escape after you reboot so that you can see the GRUB menu or else the menu pops up automatically.  Just select an older kernel version.

Every once in a while, some kernel updates will mess up the modules for some Broadcom cards.  The 4306 rev 03 has been running into problems recently in Intrepid.

If it does not work with a previous kernel version, then it could be that Network Manger might be causing the problem.  If this is the case, please post:
```
lshw -C network
lsmod|grep -e b43 -e ssb
sudo iwlist scan
```

---

