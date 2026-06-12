---
title: "Distorted video playback on Compaq Armada 1700"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by MickeW on 2007-01-24
I'm a newbie having problems with distorted video playback on an old Compaq Armada 1700.

Installing 6.06.1 or 6.10 on this laptop sets "DefaultDept 24" (24-bit) in xorg.conf, which leads to a maximum usable resolution of 800x600.
The video controller is correctly detected as "Chips and Technologies F65555 HiQVPro" and the driver "chips" is choosen.

In order to use the whole screen, I have changed to 16-bit in xorg.conf as described in earlier postings in the forums.

Everything works OK, except for video playback!
It's "perfect" in 24-bit mode, but distorted ("multicolored spots") and useless in 16-bit mode.
The video player used doesn't seem to matter - in 16-bit mode both the default player and vlc gives the same disappointing results with all kinds of video files I've tried.
Quite annoying...

Since there seems to be other Armada 1700 Ubuntu/Xubuntu users, I guess someone else must have ran into the same problem - and hopefully solved it?
I haven't been able to find anything useful in the Ubuntu forums or on the net, though...

I'd be very grateful if someone could help me with this...

---

