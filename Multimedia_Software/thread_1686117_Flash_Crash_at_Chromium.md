---
title: "Flash Crash at Chromium"
date: 2011-02-11
forum: Multimedia Software
---

### Post by rio2000 on 2011-02-11
last 2 or 3 days my flash always crash at Chromium how to fix this?

i use adobe flash player 10.2 r152
ubuntu 10.10
Chromium version 11.0.668.0 (74550) -- using Chromium version 8 flash crash too

---

### Post by garagepoort on 2011-02-11
hello,

I'm having kinda a similar problem. Since the last few days my flashplayer won't work. 
The weird thing is that it doesn't gives an error of some kind but the player just shows a white or black screen depending on the site. The strangest thing is that I can play YouTube videos but they have no sound. I have been installing a lot of stuff from winetricks lately to get a game to work (which eventually it did :p). But maybe it has in some way interfered with my browser flash-plugin in Ubuntu. Or maybe it's just an update that is giving me this trouble. In Firefox the same thing happens. 
It tried reinstalling (--purge) Firefox chrome and the flash-plugin-installer-nonfree.

I don't know if I should make a new thread for this. I thought maybe this could be related too each other.

Thank you in advance :) ,

David

---

### Post by garagepoort on 2011-02-11
ok I searched the forum and found this. [https://addons.mozilla.org/af/firefox/addon/flash-aid/](https://addons.mozilla.org/af/firefox/addon/flash-aid/)

I installed it from firefox and it fixed chrome 2.
Hats off to beew for giving the solution at this thread [http://ubuntuforums.org/showthread.php?t=1685844](http://ubuntuforums.org/showthread.php?t=1685844) :D

Hope this helps you :)

David

---

### Post by rio2000 on 2011-02-11
> **garagepoort said:**
> ok I searched the forum and found this. [https://addons.mozilla.org/af/firefox/addon/flash-aid/](https://addons.mozilla.org/af/firefox/addon/flash-aid/)

I installed it from firefox and it fixed chrome 2.
Hats off to beew for giving the solution at this thread [http://ubuntuforums.org/showthread.php?t=1685844](http://ubuntuforums.org/showthread.php?t=1685844) :D

Hope this helps you :)

David

unfortunely, your solution doesn't for me :(

install firefox add on "Flash-Aid" doesn't fix Chromium flash :(

---

### Post by rio2000 on 2011-02-12
my solution so far is.... install Google Chrome :D

---

### Post by Magick93 on 2011-02-15
Hi

I also have the same problem. As of about 2 days ago the flash player in Chrome crashes EVERY time.

Chrome 9.0.597.94 (73967) Ubuntu 10.10

---

### Post by ankspo71 on 2011-02-16
Nevermind! Flash 10.2 just started crashing in my Chromium 11 too. It was working great for a couple of hours and then nothing.

---

### Post by mpp on 2011-02-18
It's a bug, and your options may be limited for the moment... 
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/716640)

I have encountered it on Ubuntu 10.10 under both 32 and 64 bit systems.

---

### Post by hr.apostolov on 2011-03-01
Hello,

I have the same issue.
I'm using 11.0.672.2 dev of Chrome and I wanted do go with the Chromium (also 11.0.672.2) from now on. But his the Flash plugin (10.2) crashes in every site that has some flash in it. I'm finding no way to solve this, so I will stick with Chrome and hope that the issue will be solved in the next updates. :(

---

### Post by karmila on 2011-03-04
I got this too!

Flash plugin works fine on opera and FF3 or FF4 but crash with chromium.

No fix available yet?

---

### Post by olbj on 2011-03-14
Hello!

There is a work around described in [http://ubuntuforums.org/showthread.php?t=1702764](http://ubuntuforums.org/showthread.php?t=1702764) 

The core idea is to switch of hardware acceleration in the flash-setup.

Regards Olle

---

### Post by blackstar1 on 2011-08-23
Actually yes there is a fix. 

heres the fix [work in terminal]

note:this mostly works with Ubuntu 10.04/10.10 ^^ let me know if it works for you

sudo apt-get install flashplugin-installer=10.1.85.3ubuntu1

then

dpkg -l |egrep -i "chromium|flashp"

:-)

---

