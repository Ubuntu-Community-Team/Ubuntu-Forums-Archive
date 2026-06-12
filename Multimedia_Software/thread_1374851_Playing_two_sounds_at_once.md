---
title: "Playing two sounds at once"
date: 2010-01-07
forum: Multimedia Software
---

### Post by mathgirl on 2010-01-07
So I don't use gnome, KDE, or XFCE, but I'm running Xubuntu.  I'm constantly playing music via nvlc.  While that music's still playing, I'd like to be able to hear a sound I run from the command line via
```
cvlc beep.mp3
```

I've tried on and off over the years messing with pulse, esd, etc. output options for vlc, but never figured out exactly how to do this.  In Windows, having a batchfile play a .wav at the same time as an mp3 player is playing music "just works" I know there must be a "just works" solution for Linux.

Any ideas great cloud of smarties?  :D

---

### Post by 01mf02 on 2010-01-07
Hi! When you run cvlc, which output driver does it use? Have you tried to run VLC as a new user or with completely removed configuration files in your home directory? Very often some old configuration file makes things not work.
Also, is your system up-to-date?
The cloud has spoken. ;)

---

