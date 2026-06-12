---
title: "Downgrading VLC 0.9.4 to 0.9.3?"
date: 2008-10-11
forum: Multimedia Software
---

### Post by webaake on 2008-10-11
I'm not happy with vlc 0.9.4, no full screen controller and two windows for one movie. I'd like to go back to 0.9.3 but don't know how to do it.

I have Corn repos activayed i Synaptic, so there's only 0.8.6 and 0.9.4 available.

But I've found these debs:
[https://launchpad.net/ubuntu/intrepid/powerpc/vlc/0.9.3-0ubuntu1](https://launchpad.net/ubuntu/intrepid/powerpc/vlc/0.9.3-0ubuntu1)

As far as I understand I need at least the deb packages;
vlc, vlc-nox and vlc-plugin-pulse.
Any other?

---

### Post by slumbergod on 2008-10-22
did it work?

---

### Post by webaake on 2008-10-23
It did not work, or rather, I gave up on all dependencies.

---

### Post by slumbergod on 2008-10-26
Now, I see 0.9.5 has been released. Apparently, the frustrating bug regarding the embedded video still has not been resolved. In fact, a quick glance suggests that the bug logged has been expanded to included windows as well as linux.

I know people want to see 0.9 included in Intrepid but perhaps it really isn't stable enough at this point.

---

### Post by mc4man on 2008-10-26
Because all the 0.9.x versions have issues I think it may be better to keep moving up with the releases.
I'm running 0.9.5 with embedded enabled with no issues (related to embedding.

If you want to build a 0.9.5 ver. with it enabled see below for source change.

Also re-did korn's ppa 0.9.5 to enable embedded video, link is at the bottom. As long as you have the korn ppa enabled as a software source the package will install any missing dep.'s. (if you try read notes and caveats

Edit : removed link due to korn downgrading to 0.9.3 (mistake as I see it -  0.9.3 is just as likely to have issues from the embedded video and is worse otherwise

note: 0.9.5 is still installing vlc with a launch command of vlc %U. It should be changed after install to vlc %f (edit menus -> sound & video -> properties of vlc

edit: it doesn't hurt to go to home folder -> .config and delete the vlc folder when switching versions

[http://ubuntuforums.org/showthread.php?p=6035102#post6035102](http://ubuntuforums.org/showthread.php?p=6035102#post6035102)

---

