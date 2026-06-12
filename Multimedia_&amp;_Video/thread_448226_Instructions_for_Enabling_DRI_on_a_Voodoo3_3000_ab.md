---
title: "Instructions for Enabling DRI on a Voodoo3 3000 above 1024x768 Resolution"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by cbrinegar on 2007-05-18
Okay, so I am now using my Voodoo3 3000 AGP video card (16 MB of memory) at 1600x1200 with DRI (hardware acceleration) as I wanted. I found that some Ubuntu developers decided to try to protect us from not having enough memory to use fancy textures at this resolution and limited the DRI to lower resolutions. I wanted the DRI at this resolution, because the 2-D acceleration makes my old system much more responsive (PII 400 MHz --- don't laugh).

I'm sure a lot of people don't care, and the people who changed it probably don't want to revert the Ubuntu code. But the power of open source has allowed me to choose what I want for my machine, so that is great. I do think that there must be a more elegant solution to still allow DRI at high resolutions for this card, and I will submit a patch if I come up with something good.

Hope someone finds this useful.  I know I would have.

--------------------

Here is a summary of how I enabled DRI at 1600x1200 under Ubuntu 7.04.

The basic problem comes from a change made to the tdfx_dri.c file:
[http://archive.ubuntu.com/ubuntu/poo...g-driver-tdfx/](http://archive.ubuntu.com/ubuntu/poo...g-driver-tdfx/)

(Note: look in /var/logs/Xorg.0.log to see the error report that disables
DRI. This text is also in the Ubuntu code.)

The development tools were not all installed, so I used the Add Programs
option to add Glade and got most of the development tools (like autoconf).
I searched for the original code and found the Debian sources and a lot of
other things too. It was a bit overwhelming, and the Debian version did
not compile yet.

I found the Sources.gz file for 7.04 and determined the name of the package
that had the tdfx driver in it.

Then I found a post on the Ubuntu forums that gave me information about
how to get source code:
[http://ubuntuforums.org/showthread.php?t=14756](http://ubuntuforums.org/showthread.php?t=14756)

sudo apt-get build-dep xserver-xorg-video-tdfx
sudo apt-get source xserver-xorg-video-tdfx

Then I had all the dependencies and code. The diff file showed the change
that I did not want, so I went into the original Debian code and did the standard
./configure, make, sudo make install.

The files were installed into here though:
/usr/local/lib/xorg/modules/drivers/
tdfx_drv.la
tdfx_drv.so

They needed to be elsewhere, so I put them there:
cd /usr/local/lib/xorg/modules/drivers/
sudo cp *.* /usr/lib/xorg/modules/drivers/

X did not like that, so it restarted but with the new tdfx driver.

DRI is now enabled at the higher resolutions as I desired.

---

