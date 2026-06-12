---
title: "Checking and selecting between nVidia and ATI on boot"
date: 2008-11-28
forum: Multimedia Software
---

### Post by Nakor BlueRider on 2008-11-28
This is an odd one, so bear with me.  I've got a working method, but hoping I can improve it a bit.  My Ubuntu 8.10 is installed on a USB drive.  I boot to it off of more than one computer, and find myself sometimes booting off a PC with an nVidia card, and sometimes one with an ATI card.

What I'm looking for is some way to have the drivers for both installed if possible, and then select between them on boot, prior to X loading.  Unfortunately, ATI's require xorg-driver-fglrx and nVidia's require nvidia-glx-177 (or 173), and these two packages conflict and will not install simultaneously.  I fortunately can have all their dependencies installed together though, which saves some time.

For now my solution has been this script, set to run prior to X starting:

```
#!/bin/bash

ADAPTOR=`lspci|grep 'VGA'|cut -d: -f3|awk '{ print $1}'`

rm /etc/X11/xorg.conf

if [ $ADAPTOR = "ATI" ]; then

apt-get install xorg-driver-fglrx fglrx-amdcccle
cp /etc/X11/xorg.conf.ati /etc/X11/xorg.conf

elif [ $ADAPTOR = "nVidia" ]; then

apt-get install nvidia-glx-177
cp /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf

else

cp /etc/X11/xorg.conf.default /etc/X11/xorg.conf

fi
```

As you can see, it installs the right driver, and copies over an xorg.conf that's designed for that driver.  It gets the job done, but the driver install prior to boot does slow things down a bit.  Is there any possible way I could do this without having to install the appropriate driver as part of the boot sequence?

Thanks in advance for any advice!

---

