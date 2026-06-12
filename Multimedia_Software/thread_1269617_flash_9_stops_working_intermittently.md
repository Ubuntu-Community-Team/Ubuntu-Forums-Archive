---
title: "flash 9 stops working intermittently"
date: 2009-09-18
forum: Multimedia Software
---

### Post by v1nsai on 2009-09-18
I've had this problem on both Debian and Ubuntu, this seems to be a problem with the flash 9 plugin in the repos.  The problem can be fixed by restarting, so it's only an inconvenience but I'd still like to fix it.

 I tried the instructions _[here]("http://ubuntuforums.org/showthread.php?t=772490")_ for installing flash player 10 (I'm using Hardy 64-bit) but it didn't work and the instructions said not to try anything else but to post some info and blah blah I don't even know if flash 10 will have the same problem so I stopped.

Has anyone had this problem and fixed it by upgrading to 10?  Or know anything I could try to make 9 work?  Thanks :-D

---

### Post by ozzman2 on 2009-09-26
I've got the same intermittent problem (using Ubuntu 8.04 64bit).

I just get a white box in leu of video - but the sound still comes through.  Sometimes reloading the page a couple times resolves it, other times I have to restart Firefox.

If anybody has an answer to this, I'd love to hear it too.
Thanks

---

### Post by v1nsai on 2009-10-13
Maybe it's a 64-bit issue?  Both Debian and Ubuntu that I used were 64 bit.  It's annoying, but easily solved.  If you force quit firefox it will restore your session, even if you only had one tab open, it only takes a second.

---

### Post by v1nsai on 2009-11-06
I'm also having problems with flash ads growing to huge sizes and taking up the whole screen, and when I right-click or click on something that causes a menu to come up (like in facebook) if it's near a flash window instead of covering the window the flash window will cover my menu -_-

I've been trying to get gnash to work, I don't like having to click to make swfdec work.  I've installed mozilla-plugin-gnash but I still don't see anything for gnash.  Does gnash work any better than the nonfree plugin and could someone suggest why this might not be working for me?

---

### Post by v1nsai on 2009-11-18
Bumping, have tried using the 32-bit flash 10 plugin also.  Firefox saw it under 'Plugins' but it didn't actually run any videos.  Still can't get Gnash to work and I'm still having problems with the Flash 9 plugin.

Would really appreciate some help this has been going on for a long time and I haven't been able to get anything to work

---

### Post by v1nsai on 2009-12-09
I'm an idiot.  You have to uninstall the 'flashplayer-nonfree' plugin in order to get anything else to work.

Uninstalled the adobe plugin, installed 'mozilla-plugin-gnash' and it's working great.  Hoping this will keep working longer than adobe's.  I are happy :)

---

