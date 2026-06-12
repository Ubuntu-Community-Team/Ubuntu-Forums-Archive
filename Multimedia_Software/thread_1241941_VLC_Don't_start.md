---
title: "VLC Don't start"
date: 2009-08-16
forum: Multimedia Software
---

### Post by AndreaZ on 2009-08-16
Hi all.

I'm going crazy.

I have reinstalled VLC at least 10 times, but when I click the icon in "Applications--> "sound and video" nothing happens. The same when I try to open a media file with it.
When I type VLC in the Terminal, the reply is:

VLC media player 1.0.1 Goldeneye
Bus error

I have tried to purge it and reinstall, didn't help.
I have tried vlc --reset-config, did not help.

Anyone know what to do? I really use VLC for every video I have. Don't feel like reinstalling Ubuntu all over again.

Some tech info:
Release: Ubuntu 9.04 
Kernel: 2.6.28-14-generic
GNOME 2.26.1


I can't be the only one in the universe with this problem?

Thanks for all help in advance

---

### Post by mc4man on 2009-08-16
Haven't seen that error before, try this (go for a complete removal vs. a reset

Open up home folder (show hidden files, Ctrl+h or edit -> show hidden... if no . folders are visible

Find and delete 3 vlc folders, locations are

.local/share
.config
.cache

Then try vlc again, if needed use debug output
```
vlc -vvv
```

---

### Post by RedSingularity on 2009-08-16
The default VLC that comes with 9.04 gave me problems too.  Add the new VLC from the Repos located [here](https://launchpad.net/~c-korn/+archive/vlc), to your third party sources list.  Then try reinstalling it.

---

### Post by AndreaZ on 2009-08-25
Already tried that repository. Did not work any different :/
I have "upgraded" to Linx mint for the moment, and it works good there...

THANK you for the help :). I will try it when I install ubuntu 9.10 if I have problems ;)

---

