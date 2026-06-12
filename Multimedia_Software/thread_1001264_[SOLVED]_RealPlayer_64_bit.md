---
title: "[SOLVED] RealPlayer 64 bit?"
date: 2008-12-03
forum: Multimedia Software
---

### Post by thadacto on 2008-12-03
I am running Hardy 8.04 on 64 bit and also Windows XP on the same machine. In XP I run Realplayer 11 with which I can also download from YouTube. But I don't seem to be able to find the version for Linux. Everything I download seems to be the wrong architecture (i.e 32 bit)
Anyone any ideas how to get Real to run on Hardy 64 bit?

---

### Post by Izek on 2008-12-03
There was this:

[http://ubuntuforums.org/showthread.php?t=598355](http://ubuntuforums.org/showthread.php?t=598355)

But it's still 32-bit.

---

### Post by thadacto on 2008-12-03
Yes, I came across another post in the "How to..." forum which said

//////////
Before you can use the 32-bit version of Firefox you must make sure to install the fundamental libraries for 32 bit support under 64 bit native Linux. Open Synaptic Package Manager, search and install all these:

libraries for 32 bit support
Code:
ia32-libs
gsfonts
alsa-oss
lib32gcc1
lib32stdc++6
lib32asound2
lib32ncurses5
lib32z1
libc6-i386
lib32nss-mdns
///////
However, I have firefox working (don't know if it is 32 or 64 bit)
and I am afraid to install all the above files in case somethiong drastic goes wrong - knowing my knowledge of Ububtu and my luck, it will go hay-wire.
Can anyone confirm that these would be OK to install?

---

### Post by Izek on 2008-12-03
Firefox comes with Ubuntu regardless the arch. Whether or not it's x64 or not, I do not know. However, 32 bit plugins like flash WILL run on it, the x64 arch.

You can try installing the dependencies for your plugin and see if your OS crashes or stops working properly. Then you can remove them if they do and submit a bug on launchpad.

---

### Post by thadacto on 2008-12-03
I am exactly trying to avoid a crash. I bought this computer new about 18 months ago, with Ubuntu and XP installed. I have only been connected to the internet for a 10 days and have upgraded from my original Ubuntu to 8.04, about three upgrades I think. I have not got everything running smoothly and quite frankly I am starting to loose patience. XP has never caused me any problems except for viruses which came via internet downloads in cyber cafes.
I know nothing about all this bash code and really am quite lost in it.
I don't want crashes!!!

Eventually tried the Install and RealPlayer works - but it's not as good as the windows version, by any means.

---

