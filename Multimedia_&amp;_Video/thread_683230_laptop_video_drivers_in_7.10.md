---
title: "laptop video drivers in 7.10"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by das88 on 2008-01-30
Hi

I had some install issues with ubuntu due to the default xserver video set up. After a little work (for a super newbie) I've managed to boot into the desktop and now I'm trying to figure out how to install my drivers. I've got an averatec av2260-eh1 laptop with an integrated chrome9 chipset and I'm pretty sure the drivers at this link are what I need to install:

[http://www.viaarena.com/default.aspx?PageID=420&OSID=35&CatID=2830&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=35&CatID=2830&SubCatID=164)

The problem is that I can't just run the program they've written and install the drivers to ubuntu. There are some set up and install instructions with the driver but they are a little confusing and they say to just run the downloaded file from the terminal. When I do that it aborts, saying:

```
cp: cannot create regular file `/usr/X11R6/lib64/modules/drivers': No such file or directory
cp: target `/usr/X11R6/lib64/' is not a directory: No such file or directory
Now start to install VIA/S3G display utility...

Warning, system cannot find the /usr/X11R6/lib/libXv.so.1.0 file.
You can find the package in the installation CD.

Abort, the utility is not installed.
```

My assumption is that this program was written for fedora core 4 and the xorg files are in different locations in ubuntu. Is that correct? How would I install this driver in ubuntu 7.10? I have another video question - assuming that I can get this driver installed, the documentation says that it supports 1024x768 and 1280x1024 resolutions (and others) at various refresh rates but I'm running a laptop LCD with a native resolution of 1280x768. I understand that I might be able to edit the X11 config files directly and force a 1280x768 resolution but how would I determine the refresh rate and horizontal sync? Averatec is completely useless in terms of hardware support/specifications and I can't find this information online. Any suggestions?

EDIT:
I fixed this problem by changing the amount of on-board video memory in my bios. It was defaulted to 64mb and I changed it to 128mb, reset xserver to use the default vesa driver and everything works great now! When I set up xserver (via sudo dpkg-reconfigure xserver-xorg from the shell) I used all the default settings until I got to the monitor set up. It doesn't auto-detect my monitor, so I selected my preferred resolution when asked and used the "advanced" option in the next question. From the advanced settings I told it to use the full refresh range (30-150 or something like that) and the full horizontal refresh range (50-160 or something similar), then I selected 24 bit color and it was finished.

---

