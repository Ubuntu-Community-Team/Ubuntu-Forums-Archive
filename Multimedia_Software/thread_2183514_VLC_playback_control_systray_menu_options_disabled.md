---
title: "VLC playback control systray menu options disabled"
date: 2013-10-25
forum: Multimedia Software
---

### Post by Zunino on 2013-10-25
Hello.

I have recently installed VLC (2.0.8 Twoflower) on Ubuntu 13.10 64-bit; a great media player indeed. However, I have noticed that most of the playback control options in the application's systray menu are always disabled, namely "Stop", "Previous" and "Next". Is this a known bug? I have tried searching around for related posts but didn't find anything.

P.S.: A minor issue, but I find it a little odd that the "Play" menu item doesn't change to "Pause" when you actually start playback.

Thank you.

---

### Post by mc4man on 2013-10-25
The vlc indicator is using sni-qt & has been broken like you've seen since the day it was implemented a couple of yr.s past.
[https://bugs.launchpad.net/ubuntu/+source/sni-qt/+bug/859499](https://bugs.launchpad.net/ubuntu/+source/sni-qt/+bug/859499)

The only way around is to return the system tray whitelist to unity, add vlc to list & remove the sni-qt package

---

