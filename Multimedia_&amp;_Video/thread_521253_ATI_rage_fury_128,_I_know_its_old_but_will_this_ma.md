---
title: "ATI rage fury 128, I know its old but will this make a difference"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by philinux on 2007-08-09
From [https://wiki.ubuntu.com/PowerPCFAQ#head-d6be5f475782e6b1d7c441ad9571a2d83d8cbffa](https://wiki.ubuntu.com/PowerPCFAQ#head-d6be5f475782e6b1d7c441ad9571a2d83d8cbffa)

There are no official ATI nor Nvidia 3D drivers for PPC Linux. Neither company has developed any, nor released hardware specs to create a good open source driver. However, the current open source developed ati driver works well for most ATI chips, and has somewhat stable 3D support.

You do not need to download drivers from nvidia or ati's website. (There aren't any there for PPC Linux.) Currently, PPC Linux uses drivers which are built into the Linux kernel. To make sure the correct driver is enabled, you must edit the file /etc/X11/xorg.conf:

sudo gedit /etc/X11/xorg.conf

And look for the Driver line in the Device section:

Section  "Device"
          Driver   "ati"

For ATI users, make sure that the driver is specified as 'ati' or 'radeon' specifically for Radeon cards. ATI Rage 128 users, make sure that the driver is specified as 'r128'.

My xorg.conf shows driver "ati". I'm not an expert in this stuf so go easy, thanks

---

