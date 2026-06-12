---
title: "Hardy Mplayer Quicktime Codec Problem"
date: 2009-10-23
forum: Multimedia Software
---

### Post by boulderbum on 2009-10-23
****SOLVED****


Just about 2 weeks ago mozilla-mplayer plugin stopped playing QT video (such as trailers at moviemaze.de).  I have been using it for quite some time without problems, so does anyone know what may have changed?  I completely uninstalled the player, plugin and codecs and reinstalled.  Still no dice.  Should I shift the repositories that I am using to get the codecs?  I did search the forums but could not come up with the same problem that I am having... maybe I missed it.

sources.list:

```
deb http://ca.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

deb http://ca.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates universe

deb http://ca.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse

deb http://packages.medibuntu.org/ hardy free non-free
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
deb http://ca.archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe

```

Thanks for any advice in advance.

****** This problem was due to Apple verifying user agent data  see this [link]("http://ubuntuforums.org/showthread.php?t=1245441&highlight=user+agent&page=4") and go to comment #36

---

### Post by Cato2 on 2009-10-26
See this thread, particularly posting no. 4: [http://ubuntuforums.org/showthread.php?t=1219996](http://ubuntuforums.org/showthread.php?t=1219996)

I just had this problem too, now fixed by this posting.

For some reason the QuickTime plugin (actually part of the MPlayer plugin on Ubuntu) wasn't installed, so I first had to do this in a terminal window (or just search for this package in Synaptic GUI):
```
sudo aptitude install mozilla-mplayer
```

---

### Post by boulderbum on 2009-11-08
Cato2-

Thanks for the assist.  You link didn't solve my problem but led me in the right direction.  Thanks much.

BB

---

