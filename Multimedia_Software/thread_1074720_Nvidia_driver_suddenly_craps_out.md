---
title: "Nvidia driver suddenly craps out?"
date: 2009-02-19
forum: Multimedia Software
---

### Post by clk99 on 2009-02-19
Something gave out on my laptop a while ago so I sent it to the shop for repair.  I got it back about 2 days ago.  I'm running Kubuntu 8.10 and was using the Nvidia beta drivers (180 I think) with my Geforce 8600M graphics card.  I use the proprietary drivers because the open source ones don't play movies smoothly.

Yesterday morning I ran automatic updates since I hadn't since I got my computer back.  I didn't reboot though.  Last night I was watching a movie and about half-way through, it just stopped.  I got up and tried to re-open the file, but it wouldn't open.  I tried to open Dolphin, but it wouldn't.  Konqueror worked.  With no idea what was going on, I decided to reboot.  

Upon reboot I had lost X server.  I switched to NV in xorg.conf and was then able to launch X.  I tried to open the movie again, but there was no sound.  I opened Amarok to test this, and got an error saying somethin like xine couldn't load.  A little research and I found my fix by chmoding "/dev/snd/*" to 777.  I have a hunch that this sound issue is strictly related to the update, but I include it just in case it is of any interest.  

So with sound working, I just need to get back on the nvidia proprietary drivers.  Assuming that the beta drivers simply somehow failed me, I tried switching to 177 (the recommended restricted drivers).  Reboot and still no X. 173: same thing. What happens is it tries to start X, I get some glitchy looking stuff then I see a blank shell screen with a blinking cursor, then more glitchy stuff, then blank shell, and so on.  If I open a new shell (e.g. ctrl alt F1), log in, and type startx, the same happens except it doesn't seemingly repeat forever; eventually I get an error message. Here's my error:
```
Backtrace: 
giving up.
xinit: Connection refused (errno 111): Unable to connect to X server.
xinit: No such process (errno 3): Server error.
```

I also tried reinstalling the beta drivers to no avail.  I think I even may have gotten a "No screens found" error with the 180 beta ones.  

So I'm back on NV right now and still haven't got to see the end of my movie.  My guess is that somehow my computer got stuck last night, and after a reboot some of the recent updates didn't like my running the beta drivers or any proprietary drivers for that matter (just as they screwed with my sound, too).  It'd sure be nice if my video problem is just a permissions problem as it was with sound, but I'm guessing it's not that simple and I'm out of ideas.  I wish I had a list of everything that updated yesterday, but I don't.  

Any help would be MUCH appreciated.  Not only can I not watch movies with NV, but KDE4 seems much more sluggish.

---

### Post by norwoods on 2009-02-19
do you know if you installed a new kernel in the automatic updates?  installing a new kernel can wipe out the nvidia drivers if you installed them the nvidia way.  how did you install the drivers?

---

### Post by clk99 on 2009-02-19
Thanks for the reply.  I can't say for sure if my kernel was updated, but I wouldn't be surprised.  I installed my drivers the nvidia way: with the .sh script from the nvidia website.  

But since receiving this error I've tried reinstalling the drivers multiple ways -- with the nvidia script, with Envy, from the (restricted) "Hardware Drivers" GUI in KDE4.

---

### Post by clk99 on 2009-02-21
Bump.

---

