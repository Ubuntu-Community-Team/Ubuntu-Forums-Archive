---
title: "ATI Driver and Radeon 5750"
date: 2010-05-13
forum: Multimedia Software
---

### Post by mattlach on 2010-05-13
Hey all,

I could use some help with this.

I installed Lucid when I had my Nvidia board in the computer.   Yesterday I pulled out the nvidia board and installed my new Radeon 5750.

Hearing that the Open Source driver is the way to go, I first decided to try that.  I edited xorg.conf replacing "nvidia" with "radeon", since this is the module name (right?) but it still doesn't seem to load.  Does anyone have an example of what a properly configured xorg.conf is supposed to look like using the ATI Open Source driver?

I get X up and running in "low graphics mode", but can never get beyond that.  Trying to turn on window effects causes a "searching for drivers" dialogue to appear and then disappear without success.   A quick "glxinfo |grep -i render" indicates that it is indeed in the software mode. I even tried to manually modprobe the radeon module and restart GDM, but still nothing...

At first I thought this was a limitation of the Open Source drivers on 5xxx series boards, but [this page](http://www.x.org/wiki/RadeonProgram) suggests that it should work in "gold" status.

I have since installed FGLX and it is just terribly buggy, so I am hoping to use the Open Source driver.

Can anyone provide any help to get me up and running with the open source driver?  [This guide](https://help.ubuntu.com/community/RadeonDriver) seems obsolete.

---

### Post by vandorjw on 2010-05-13
Hey,

I have the Radeon 5670 in my tower, and it worked perfectly fine using the closed source drivers from ATI.

After it installed, I removed the xorg.conf file and everything worked like a dream, well, not exactly. It seems to only use 8 bit colour until I log in. I am not quite sure why this is, but as soon as I log in it works fine.

I have to admit that it runs Arch Linux, and not Ubuntu, but that shouldn't make to much of a difference.

Have you tried completely removing the xorg.conf file. I believe the Ubuntu team has implemented the most recent version of X in 10.04 , and it no longer needs a configuration file.

---

### Post by mattlach on 2010-05-13
Thank you for your reply.

Yeah, I currently have the latest version of the proprietary driver and it is showing all kinfds of bugs, the most serious of which is to not clear the screen after a Open GL screensaver is used, so you can't see the login dialog box.

It also displays significant tearing in Glitz, and in videos despite the refresh rate being manually set correctly to 60hz and vsync being enabled in both Glitz and amdcccle.

I'm hoping for a better experience witht he open source driver, as it boasts tear free video performance and glitz support on this site: [http://www.x.org/wiki/RadeonProgram](http://www.x.org/wiki/RadeonProgram)

I just can't seem to get it to work...

---

### Post by vandorjw on 2010-05-13
I just noticed...if you are going to specify the driver in the xorg.conf file, use radeonhd , instead of radeon

---

### Post by mattlach on 2010-05-13
> **cc7gir said:**
> I just noticed...if you are going to specify the driver in the xorg.conf file, use radeonhd , instead of radeon

Hmm..   This page on the x11 wiki suggests that RadeonHD only supports R500-R700 boards...  Have you had success with the RadeonHD driver on your board?  I may try it just in case...

According to these pages the [Radeon driver](http://www.x.org/wiki/RadeonFeature) has more mature support for Evergreen (5xxx boards) than the [RadeonHD driver](http://www.x.org/wiki/radeonhd%3Afeature) does...   In fact, the RadeonHD driver lists everything on Evergreen as "to do"...

---

### Post by vandorjw on 2010-05-13
I never tried the opensource drivers.

However, I just check the supported hardware list and the 5750 is not supported with the radeonHD driver just yet.
[http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README](http://cgit.freedesktop.org/xorg/driver/xf86-video-radeonhd/plain/README)
So I do not know if it is worth trying?

Just out of curiosity, did you try without providing a configuration file?

---

