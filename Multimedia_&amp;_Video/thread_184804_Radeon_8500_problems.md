---
title: "Radeon 8500 problems"
date: 2006-05-30
forum: Multimedia &amp; Video
---

### Post by Amt0571 on 2006-05-30
Hi,

After yesterday's update, as most ATi users I think, I ended up with an fglrx driver that prevented OpenGL and some applications like OpenOffice from working. I uninstalled fglrx and problem solved, altough for some reason, Planetpenguin racer freezed the whole computer after a few seconds.

After today's update, not only is fglrx still not working, but all OpenGL applications (Blender, for example) freeze the computer when I'm using the ATi driver...

Anybody has the same problem or knows about a solution?

Thanks!

---

### Post by Kangaroo on 2006-05-30
I have a Radeon 8500 as well. However, the apps you mention do work for me. 
What isn't working, is the driver itself. I don't have any 3D-Acceleration at all and "fglrxinfo" shows "Mesa". 

Don't know, whether our problems are connected, but i got the driver from the repositories.

---

### Post by Amt0571 on 2006-05-30
I'm also using the fglrx drivers from the repositories, but if I install them I get a lot of graphical errors in the console whenever I run OpenOffice or any 3D app. If I switch to ati ones, I have working OpenGL since things run fine for a few seconds, until everything freezes (except the mouse cursor).

I've tried to do ctrl+alt+backspace, but it does not respond, so I have to do a reset...

By the way, I have an old computer running Xubuntu Dapper with an MX440 and it has given me a lot less problems than the 8500 on Linux... what's the problem with ATi and Linux?


Thanks

---

### Post by phorque on 2006-05-30
There's a [bug report]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/47371") already

---

### Post by rachii on 2006-05-30
i have the same problem and video card....my solution after years of similiar issues stuff like this or the mesa stuff etc..., was to buy a 30 dollar nvidia card.   i think its actually a good upgrade from the 8500 too

---

### Post by Tzimbar on 2007-10-13
Same problem here with Radeon 8500...
If I use open source drivers (not ATI proprietary ones) any OpenGL application gets stuck after a few seconds, completely hanging the entire system, except the mouse which still moves around.
As the video card is old, I cannot install official ATI proprietary drivers because they do not support my kernel version (2.6.20-r15), but they would have worked (as far as I can see from other threads) if I had an older kernel... :confused:

---

