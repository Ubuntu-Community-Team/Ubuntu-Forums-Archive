---
title: "Ubuntu 9.10 + Firefox 3.5 + Gmail = Segmentation Fault"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by TheBuzzSaw on 2009-10-31
Title says it all.

I have a clean install of Ubuntu 9.10 today. I use Firefox 3.5 for all my web browsing. Whenever I load Gmail up, Firefox goes down with a "Segmentation fault" (determined by running Firefox from the terminal).

I never had any problems in 9.04 under Shiretoko.

I am currently running Xmarks, Adblock Plus, and Adobe Flash 64-bit Alpha.

Ideas? :(

---

### Post by dragupl on 2009-11-01
the same to me :< it started after installation of 64 bit flash plugin so i guess that's the issue, however it would be nice to figure some workarounds out : [

---

### Post by TheBuzzSaw on 2009-11-01
Hmmm... I just noticed that mine stopped. I went to Gmail on accident (it is an engrained daily ritual for me), and after a few minutes, I noticed I was using Firefox to do it, and it had not crashed yet. (I had been using Opera for Gmail only.)

I'll keep an eye out for it. Perhaps I had updated Firefox but not restarted it yet...?

---

### Post by michaelzap on 2009-11-01
This happened to me as well with the 64-bit Flash plugin (the latest from the Adobe site). I finally gave up and removed it and use Synaptic to install the one from the repositories. That one doesn't crash Gmail and generally works except for the annoying unclickable buttons on Flash movies when running Compiz (you have to click outside the movie, roll over where you want to click while holding down the mouse button, and then click on the control that you want to use).

---

### Post by atorch on 2009-11-05
Same issue here (my gmail crashes as soon as gchat loads, if I have 64-bit flash installed).

Is there anyway to install flash, on a 64-bit 9.10, such that (1) all buttons on youtube videos work, even when compiz is running, and (2) gmail doesn't crash?  If so, HOW?

To be clear, the choices I am aware of are:

A - no flash at all; gmail doesn't crash, but... no flash
B - install flash from software center; gmail doesn't crash, but buttons don't work on youtube
C - install 64-bit flash; gmail crashes, but flash works perfectly

---

### Post by bear24rw on 2009-11-05
I have the same exact problem

---

### Post by mission88 on 2009-11-08
I have fixed my Firefox segfault (I had no known Gmail issue). I will say in advance that I had installed Firefox 3.5 as Shiretoko and late last week the Update Manager tried to upgrade Firefox... that was before (and the reason for) my 9.10 upgrade.

During the upgrade Karmic removed the install location from my sources. so I ran the following:

> sudo gedit /etc/apt/sources.list

and then I found the lines referencing

> intrepid-backports main restricted universe multiverse

uncommented them, and changed intrepid to karmic.

I also uncommented the line which read:

> deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

Then I ran update manager and it found updates for Firefox. They fixed whatever issue was causing this.

---

### Post by cmittle on 2009-11-11
I am having problems with my firefox locking up my computer while in Gmail.  I am not able to do a ctrl+alt+backspace (yes i've enabled it and i've tested that it works otherwise).  I also try alt+sysreq r,s,e,i,u,b which blacks the screen but I still have to hard shut down (hold power button).  

How do I find out what "error" is causing this, to see if it is the same as previous posters?

---

### Post by excalq on 2009-11-13
I'm running 9.10 64-bit, with Firefox 3.5.5, and have these same problems.

It seems that the 64-bit flash player (from Adobe Labs, in Alpha), just won't work - it causes Firefox to immediately segfault when a flash video is opened.

I was able to restore sanity by reinstalling the default flashplugin-installer via Synaptic. 

The other issue is that that the standard 32-bit flash player breaks with Compiz. That is, on some sites, like Pandora, flash widgets become unclickable. On other sites, like Youtube, they are ok for me, but I've seen various reports.

To fix that, go to System -> Preferences -> Appearance in Gnome, and set the option on the "Visual Effects" tab to "None", which completely disables compiz.

---

### Post by michaelzap on 2009-11-13
> **excalq said:**
> The other issue is that that the standard 32-bit flash player breaks with Compiz. That is, on some sites, like Pandora, flash widgets become unclickable. On other sites, like Youtube, they are ok for me, but I've seen various reports.

To fix that, go to System -> Preferences -> Appearance in Gnome, and set the option on the "Visual Effects" tab to "None", which completely disables compiz.

Fix that works with Compiz here:
[http://ubuntuforums.org/showpost.php?p=8295058&postcount=18](http://ubuntuforums.org/showpost.php?p=8295058&postcount=18)

---

