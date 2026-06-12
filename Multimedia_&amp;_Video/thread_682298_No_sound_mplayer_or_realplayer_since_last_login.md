---
title: "No sound mplayer or realplayer since last login"
date: 2008-01-29
forum: Multimedia &amp; Video
---

### Post by gilbertt on 2008-01-29
Ever since logging in this evening I've had the following sound issues:

-on trying to open a BBC stream from Firefox, got the message: 'Could not find an appropriate hxplay or realplay in the system path to use as an embedded player'. Did 'about:plugins' in Firefox which showed that 'Helix DNA Plugin: RealPlayer G2 Plug-In Compatible is installed.' Sound from video works fine in firefox

-saved the bbc .ram file and tried to open it with RealPlayer. The buffer loads and the timer starts running, so I presume its processing the stream, but no sound. In the past the radio 4 stream would just automatically open in standalone RealPlayer

-tried running mplayer to play some other radio streams from the command line with an alias command like I usually do. But again no sound, though mplayer is appears to be processing the stream as it fires up normally and the timer, cache indicator etc are active. 

-tried to play the saved .ram file with Amarok, but got the message 'There is no available decoder'

-however, with mp3 playback on Amarok sound output is fine.

The kicker bar disappeared as well. Fixed that but no idea why any of this is happening...

Help much appreciated

---

### Post by gilbertt on 2008-01-31
I installed vlc and now mplayer and realplayer work fine! Is it because all three share the libraries that came with vlc?

libdc1394-13
libdvbpsi4
libdvdnav4
libgsm1
libtar
libwxgtk2.6-0
libxosd2

Really curious as to why it stopped in the first place, and which libraries are reponsible so I can uninstall vlc and keep what I need. Any thoughts?

---

### Post by fanatik on 2008-02-05
I have had a similar issue on my work pc, where I run gutsy. I have noticed that in firefox, if I navigate to a page which has a flash animation/menu etc then the next time i try realplayer then it will fail with "Could not find an appropriate hxplay or realplay in the system path to use as an embedded player" as above. If I then close and re-open the browser and retry realplayer without going to any flash pages first, it works perfectly.

on occasion after i have rebooted for various reasons, i notice that realplayer however i use it (embedded in firefox, or standalone) will not play sound where other apps (xmms etc) will, this does not happen each after every boot. I have discovered that if you run realplayer as following from a command like:

$ aoss realplay

then sound is restored as it is wrappered by alsa somehow.

maybe that helps?

---

### Post by gilbertt on 2008-02-25
Hey fanatik,

Thanks for replying. The problem resurfaced. I found out eventually that the KDE sound server system had somehow been enabled and was hogging audio resources. Turning it off from system preferences worked.

Gilbertt

---

