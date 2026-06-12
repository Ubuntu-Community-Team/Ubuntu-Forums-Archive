---
title: "Be careful with these xorg-edgers updates!"
date: 2011-01-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2011-01-23
```
Aptitude 0.6.3: log report
Sun, Jan 23 2011 23:01:29 +0000

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 4 packages, and remove 0 packages.
16.4 kB of disk space will be used
===============================================================================
[UPGRADE] debhelper 8.0.0ubuntu1 -> 8.0.0ubuntu2
[UPGRADE] [COLOR="Red"]xserver-common 2:1.9.99.901+git20110111.6358a600-0ubuntu0chris5 -> 2:1.9.99.901+git20110124.be3be758-0ubuntu0chris
[UPGRADE] xserver-xephyr 2:1.9.99.901+git20110111.6358a600-0ubuntu0chris5 -> 2:1.9.99.901+git20110124.be3be758-0ubuntu0chris
[UPGRADE] xserver-xorg-core 2:1.9.99.901+git20110111.6358a600-0ubuntu0chris5 -> 2:1.9.99.901+git20110124.be3be758-0ubuntu0chris[/COLOR]
===========================================================================
```

After these xserver updates I couldn't boot to the desktop.

Ended up purging the edgers ppa for now to fix it.

---

### Post by anders_c_ on 2011-01-23
just updated those packages on 64 bit natty with a HD5850, will try to reboot now :P

Edit: Didn't work for me either, posting from Maverick :P

---

### Post by paul_in_london on 2011-01-23
What I did was purge the ppa (in recovery mode) and then reinstall **xserver-xorg-video-all** (which I wasn't able to do before I purged the ppa because of dependency conflicts).

It may just have been coincidence, but 2.6.38-rc2 wasn't booting properly in the middle of all this, but (touch wood) it seems to be ok now that I've reinstalled it :p

---

### Post by tgm4883 on 2011-01-23
Thanks for the heads up, although I would expect some breakage from a PPA which is defined as running on the edge and links to another PPA that has more stable updates.

---

### Post by anders_c_ on 2011-01-23
Guess I will have to keep the ppa purged until this is fixed. Unfortunately I can't start unity without it so I'm stuck in classic mode for now. Thanks for the warning!

---

### Post by Harry33 on 2011-01-24
> **anders_c_ said:**
> Guess I will have to keep the ppa purged until this is fixed. Unfortunately I can't start unity without it so I'm stuck in classic mode for now. Thanks for the warning!

The latest update of xorg-edgers
xserver 1.9.99.901+git20110124.be3be758-0ubuntu0chris
is broken.
It segfaults on boot.

The xserver 1.10 series is still far from being ready.
So if you use it, always keep the latest working version backed up in your home directory.
Then you can always downgrade to it with dpkg (recovery mode: drop to the shell).

---

### Post by rburkartjo on 2011-01-24
paul tks for the heads up

---

### Post by pferraro on 2011-01-24
> **Harry33 said:**
> The latest update of xorg-edgers
xserver 1.9.99.901+git20110124.be3be758-0ubuntu0chris
is borken.
It segfaults on boot.

The xserver 1.10 series is still far from being ready.
So if you use it, always keep the latest working version backed up in your home directory.
Then you can always downgrade to it with dpkg (recovery mode: drop to the shell).

apt also stores previous versions of packages in:
/var/cache/apt/archives/

---

### Post by Harry33 on 2011-01-24
> **pferraro said:**
> apt also stores previous versions of packages in:
/var/cache/apt/archives/

Sure it does, depending on the settings.
See Synaptics menu:
Settings - Preferences - Files

---

### Post by Harry33 on 2011-01-24
> **Harry33 said:**
> The latest update of xorg-edgers
xserver 1.9.99.901+git20110124.be3be758-0ubuntu0chris
is broken.
It segfaults on boot.
...


Aaron Plattner from NVidia explained this issue here:
[http://www.nvnews.net/vbulletin/showthread.php?t=158983](http://www.nvnews.net/vbulletin/showthread.php?t=158983)

> Also, as a heads-up, I should mention that another ABI break went into the X server source tree, so xserver 1.10 RC 2 will not be compatible with the limited support in 270.18.

Meaning we must wait for another driver update.

---

### Post by pferraro on 2011-01-24
> **Harry33 said:**
> Aaron Plattner from NVidia explained this issue here:
[http://www.nvnews.net/vbulletin/showthread.php?t=158983](http://www.nvnews.net/vbulletin/showthread.php?t=158983)



Meaning we must wait for another driver update.

All (or most) of the drivers have already been rebuilt.  New xserver-xorg-core packages are working fine here after intel driver update.  NVidia folks will need to wait for another blob update.

---

### Post by anders_c_ on 2011-01-24
Radeon driver works again :)

---

