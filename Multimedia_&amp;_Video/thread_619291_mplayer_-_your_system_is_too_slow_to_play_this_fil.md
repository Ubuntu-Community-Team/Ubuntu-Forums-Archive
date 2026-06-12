---
title: "mplayer - your system is too slow to play this file"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by leptogenesis on 2007-11-21
I just installed the most recent upgrade of mplayer.  

Before the upgrade, I could play virtually any file with mplayer fine.  Now, whenever I play a file, mplayer prints the message "your system is too SLOW to play this", and the video is jumpy.  Sometimes it's okay when I have the video in a small window but it complains/jumps when I go to full screen.  I suspect that it's not using my graphics card...but I tried all the drivers listed in the mplayer preferences and none worked.  

I know my system IS fast enough to play these files, because they work fine in vlc.  

I'm runnning xubuntu feisty with an ATI radeon x1400 video card, with the fglrx drivers installed.  I've also been starting mplayer from the command line, because the most recent release stopped working by just double-clicking on files.

---

### Post by bingoUV on 2007-11-21
try 
```

mplayer -vo help

```

It will list possible video outputs. Try different outputs like x11, xv, gl etc. and see if some of them work better.

---

### Post by leptogenesis on 2007-11-21
Tried them all...none worked.  Most just didn't initialize; a few opened it but wouldn't full screen.   The only one that did full screen was gl2, and it's the one that gives me the output about being too slow and is jumpy.  

Any other ideas?

---

### Post by Steveway on 2007-11-21
Do you have Compiz and/or XGL running?
Disable that and try again.

---

### Post by leptogenesis on 2007-11-21
> **Steveway said:**
> Do you have Compiz and/or XGL running?

I have no idea...I didn't do anything to intentionally activate them.  How would I find out?  And if I do, how would I disable them?

---

### Post by chalewa on 2007-11-21
> **leptogenesis said:**
> I have no idea...I didn't do anything to intentionally activate them.  How would I find out?  And if I do, how would I disable them?

if you don't recall installing XGL then you probably didn't...the reason that you would probably have it installed is for desktop effects (Compiz/Beryl) which can really screw with video output

---

### Post by leptogenesis on 2007-11-22
Upgraded to gutsy and the problem vanished.  I guess we'll never know what the problem was...

Thanks for the help, everyone.

---

### Post by D. Michael McIntyre on 2007-11-23
> **leptogenesis said:**
> Upgraded to gutsy and the problem vanished.  I guess we'll never know what the problem was...That's amusing.  I just upgraded to Gutsy myself, and I found this thread when I went looking for a solution to the problem I just acquired.

It was working fine on Feisty.

Now I have pretty much the same scenario you outlined with the ATI drivers and this slowness thing.  I tried a double handful of different options, and I don't see a solution yet.

Sigh.

I think the last time I ran into this problem was when I decided to bother with the stupid ATI drivers, and that cured it.  But now I'm using the stupid ATI drivers, and the problem has reared its ugly head again.

Maybe I'll try getting rid of the ATI drivers this time.  :D

---

### Post by leptogenesis on 2007-11-23
I managed to reproduce the problem by going into gutsy's restricted driver's manager and disabling the ATI driver.  So your system needs the ATI driver...although upgrading to gutsy shouldn't have gotten rid of it.  

I've done a few odd things with the ATI drivers in the past.  When I originally installed them on my fresh feisty installation, the debian package didn't work.  I had to go the long way, using the files from the ATI website.  In the process, I blacklisted the original driver - maybe you (or a script) did the same thing?  Take a look at /etc/default/linux-restricted-modules-common and see if DISABLED_MODULES contains the string "fglrx" (fglrx is the name of ATI's driver program).  If it does, remove it.  You may need to reboot the system.  Then try using the restricted drivers manager to enable the ATI drivers.

---

