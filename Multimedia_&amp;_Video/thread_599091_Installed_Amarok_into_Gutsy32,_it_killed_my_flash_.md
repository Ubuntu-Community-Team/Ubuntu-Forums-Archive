---
title: "Installed Amarok into Gutsy32, it killed my flash player sound..."
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by Jim March on 2007-10-31
C title...everything was great until I installed Amarok into Gutsy (standard Ubuntu, Gnome desktop).  Flash player died.

I've tried all kinds of fixes from the forums, nothing doing.  I tried the "reinstall alsa" stunt, and various tricks as outlined at:

[http://ubuntuforums.org/showthread.php?t=590989](http://ubuntuforums.org/showthread.php?t=590989)

[http://ubuntuforums.org/showthread.php?t=265397](http://ubuntuforums.org/showthread.php?t=265397)

[http://ubuntuforums.org/showthread.php?t=199289](http://ubuntuforums.org/showthread.php?t=199289)

...and the like, getting nowhere.  It's clear something about the Amarok setup killed it, probably connected to xine?

I even went so far as to completely nuke the flash player and let Gutsy auto-install a new copy.  Nothing doing.  Sound works in Banshee, Totem, everything else I've tried - looks like it's flash alone got nailed so I'm assuming it's not my sound hardware or core drivers.  Flash fails in both Opera and FireFox.

Any help appreciated...at this point I'd be willing to try switching to Gnash, if that's not similarly cursed?

Jim March

---

### Post by Jim March on 2007-11-01
Update: Gnash is NOT the answer.  It ain't yet ready for prime time.  Bigtime not ready.  Whoa.  Yucko.  Good for reviewing movies at 1/30th time frame by frame with no sound...whoops.  Hope you guys get it right one of these days...

---

### Post by Jim March on 2007-11-01
Well I found the problem, but don't know how to fix it.  

Under Preferences>Sound I find on testing that ESD works but nothing else - alsa, oss and "alc883 analog" all do fail reports:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Resource busy or not available.

Turns out that yes, I have Banshee working in ESD but other things besides flash are puking - mplayer and VirtualBox and God knows what else.  I need to clear ESD out of there but according to Synaptic pulling "esound" pulls basically everything else - gnome, compiz, etc.  Ghaaa.

How do I get alsa and/or oss back?

:(

Jim

---

### Post by Jim March on 2007-11-01
SOLVED.

The culprit was a package available for de-selection in synaptic called "pulseaudio-esound-comp".  Nuke that, all is well.

Dayum, this was an ugly one.  Key thing: don't stick Amarok into Gnome unless you like headaches.

---

