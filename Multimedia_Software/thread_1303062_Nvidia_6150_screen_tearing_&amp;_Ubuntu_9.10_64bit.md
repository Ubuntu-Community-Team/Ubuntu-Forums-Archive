---
title: "Nvidia 6150 screen tearing &amp; Ubuntu 9.10_64bit"
date: 2009-10-27
forum: Multimedia Software
---

### Post by backwardselvis on 2009-10-27
So I was beating my head against the wall for a while now, wondering why my videos were tearing like crazy during playback (VLC was the primary media player).

After installation, I opened 'Hardware Drivers' application.

System->Administration->Hardware Drivers

I chose to install the (recommended) driver. (As of this writing it is version 185). It will ask you to reboot the system so go ahead and do it.

Once the system reboots, I went into the 'Nvidia X Server Settings' panel and messed with all sorts of settings over the course of a couple days. But nothing worked. Then I found a post that briefly mentioned that the 'Sync to VBlank' options found under the 'Nvidia X Server Settings' wouldn't overide compiz's VBlank settings. So supposedly compiz was causing the screen tearing.

So from here the solution was simple. Go to

System->Preferences->Appearance

And once the window opens, click on the 'Visual Effects' tab. You will notice that 'Normal' is selected. Just select 'None' and that will disable the effects that are causing screen tearing during video playback.

I realize that this isn't the BEST solution. And am open to more ideas, but video playback was the priority for me.

-later

SYSTEM

CPU AMD64 3800
RAM 1GB
MB Asus M2NPV-VM w/ onboard 6150
9.10beta 64bit

---

### Post by Mononofu on 2009-11-05
This does not work for me.

I also have activate "Synch to V-Blank" everywhere in the nVidia driver.

---

### Post by moh0k on 2010-01-04
Thank you so much for this solution! Worked perfectly!

Also, first time to these forums and first time using Ubuntu. Wish me luck!

---

### Post by RabidNelson on 2010-01-18
Yes, this also works perfectly for me, but it is a depressing solution. All of this worked fine for me on 9.04 without disabling compiz. I don't think anyone has been able to find a workaround yet. If anyone finds a solution, please post!

---

### Post by RabidNelson on 2010-01-19
I think I found the perfect solution! In CompizConfig Settings Manager, go to General, then the General tab, then check on "Unredirect Fullscreen Windows". Now I can have compiz enabled and watch videos on my second monitor with no tearing!

If this works for anyone else, let me know. If not, I'll try to help if I can.

---

