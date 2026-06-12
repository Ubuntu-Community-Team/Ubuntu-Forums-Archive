---
title: "Multi-monitor full screen problems"
date: 2010-09-06
forum: Multimedia Software
---

### Post by QuinRiva on 2010-09-06
I trying set up a basic HTPC configuration, running XBMC on the TV and a secondary monitor for general use.  When I start XBMC, it goes into full screen centering across the two monitors.

Set-up:
[LIST]
[*]Ubuntu 10.10 beta
[*]2 monitors resolutions: 1600x1200 & 1280x720
[*]Ati Radeon X1300/1550 series video card
[*]Default open source drivers
[*]Connecting via SSH & UltraVNC (yes the monitors are directly connected to the Linux box, I'm just accessing it from my main computer so I don't have to crouch on the floor to configure it).
[/LIST]

I discovered [this page]("http://blog.burlock.org/xbmc/77-fullscreen-xbmc-without-locking-the-mouse") that describes a script to get XMBC running on the second monitor, however attempting to run the script yields:
```
Error: unable to open display :0.1
```

I've also tried configure Xorg (/etc/X11/xorg.conf  does not exist), by running Xorg -configure, but I get the error:
```
Server is already running for display 0
```

Any help would be appreciated.

---

