---
title: "Audacity Internal Effects 'MIA'"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by darkstaar on 2008-03-10
I use Audacity quite often. Recently, I inadvertently removed it. No problem. I simply reinstalled it. Now some of the effects are missing, notably '**Change Tempo**' and '**Change Pitch**'.

These two effects in particular are internal effects, not plug-ins.

Just wondering if anyone else has had this problem as well. Version is 1.3.4-B

---

### Post by darkstaar on 2008-03-10
Self-solved.

Got rid of version 1.3.4-B and replaced it with 1.3.3-B. Everything is back to normal.

---

### Post by Pettman on 2008-04-09
Else you can install some aditional plugins and you'll be able to find it under the plugins number # to #.

---

### Post by devnulljp on 2008-04-27
> **darkstaar said:**
> Self-solved.

Got rid of version 1.3.4-B and replaced it with 1.3.3-B. Everything is back to normal.
So, you're no longer relying on apt? Did you just rip it out and install from debs? 
[rant mode]This is one on the main things I use Audacity for, and it's a real pain it's been disabled. I'd just doen an auto update with apt and it's now wasted several hours trying to find a fix.[/rant] 
Thanks for the pointer.

How do we mark particular programs so they aren't upgraded automatically? I can't remember...

---

### Post by dbbolton on 2008-05-05
> **darkstaar said:**
> I use Audacity quite often. Recently, I inadvertently removed it. No problem. I simply reinstalled it. Now some of the effects are missing, notably '**Change Tempo**' and '**Change Pitch**'.

These two effects in particular are internal effects, not plug-ins.

Just wondering if anyone else has had this problem as well. Version is 1.3.4-B
Where did you get version 1.3.3-B ?

---

### Post by luctor on 2008-05-06
This MUST be it why those effects are missing:
Taken from the README.txt from cvs checkout, and also on [http://audacityteam.org/wiki/index.php?title=Known_Issues#Linux_only](http://audacityteam.org/wiki/index.php?title=Known_Issues#Linux_only)

> * Linux (**Debian-derived**) only: Audacity configure script does not detect
    libsoundtouch on the system and so **Change Pitch and Change Tempo**
    effects are disabled. This is a debian bug (#476699), which can be
    worked around by symlinking /usr/lib/pkgconfig/soundtouch-1.0.pc
    to /usr/lib/pkgconfig/libSoundTouch.pc

I've compiled the cvs checkout (1.3.5) and everything seems to work ok except for enabling jack.

---

### Post by dbbolton on 2008-05-06
> **dbbolton said:**
> Where did you get version 1.3.3-B ?
Found it in the gutsy repos:

[http://packages.ubuntu.com/gutsy/audacity](http://packages.ubuntu.com/gutsy/audacity)

---

### Post by QwUo173Hy on 2008-05-08
luctor, I found that message too. Funnily enough (not really!) I don't have that file on my system. I have libsoundtouch1c2 installed. Is there something else I need to install to get this file on my system?

---

