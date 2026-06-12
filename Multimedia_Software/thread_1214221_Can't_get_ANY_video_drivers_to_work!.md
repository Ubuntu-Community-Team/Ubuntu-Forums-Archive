---
title: "Can't get ANY video drivers to work!"
date: 2009-07-15
forum: Multimedia Software
---

### Post by aceole on 2009-07-15
I have a N260GTX-T2D896 OC V2 video card and MSI has no drivers for linux. Nvidia is not helping me eather. when I try to install drivers Manually they only go to 640x480 Max. 
I'm still new at Linux can some one help.
If you write code, put it all there please, I don't know code at all.
Thanks,
ALso ENVY does not support this video card.

Desktop
Running 8.04 Hardy 32bit
MSI N260GTX-T2D896 OC V2

---

### Post by ghostborg on 2009-07-15
I'm no expert but make sure if you just installed your system you go to System:Administration and then launch the Update Manager to make sure your system has all the latest updates prior to installing any card specific video drivers. Then once you do that try System:Administration and launch Hardware Drivers and see if it makes available any video drivers for you.
Also make sure the Software restricted checkbox is selected under System:Administration and Software Sources under the "Ubuntu Software" tab.

It might be helpful to others to know what version of Ubuntu you are running and if it is 32 or 64 bit. If your computer is not a laptop if all else fails install an Nvidia card. Check other peoples opinions.
You can right click on the top menu bar and select from the drop down menu "Add to panel" then select System Monitor which puts an icon on the menu bar with some helpful information. Click on it and a panel will pop up and click on the System tab.

If you get really screwed up there is a recovery? selection from the grub menu which has a box that pops up to help repair you xorg-video. This usually gets you back to a generic video driver that makes your system bootable.


Another useful terminal command to find out what version you are running
is  uname -a  .
Sorry I'm not much help to you but I'm sure someone else will come along.

---

### Post by aceole on 2009-07-15
UBUNTU has only three RESTRICTED DRIVERS for NVIDIA video

 8.04 Hardy Heron
169.12	
96.43.05
71.86.04

By what I've seen this video card (N260GTX-T2D896) needs 185.15. so no there are no restricted drivers in UBUNTU. My system is Updated, and still nothing. my system is a 32bit OS
the Software restricted checkbox is selected under System:Administration and Software Sources under the "Ubuntu Software" tab. My pc is a desktop.
Thanks for trying.

---

### Post by aceole on 2009-07-16
FIXED IT!!!

Yeah!

The needed driver is listed for Ubuntu 9.04. I installed the latest one and it was in the restricted driver list, YEAH

Thanks for you time all!

---

