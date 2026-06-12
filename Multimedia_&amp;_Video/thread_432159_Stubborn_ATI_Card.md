---
title: "Stubborn ATI Card"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by RSVampire on 2007-05-03
Hello everybody,

I'm a new member and have started dual booting Ubuntu Fiesty and Windows XP.

I've tried everything I've read on the internet and nothing is allowing my ATI Radeon 9800 Pro to render correctly.

I've edited so no composite was enabled in my /etc/X11/xorg.conf and did the tutorial on Ubuntu's site how to get the 3-d acceleration to work. Now when I try to enable/disable the restricted drivers in the manager panel, it says "your hardware does not need any restricted drivers" and when I enable desktop effects it says "desktop effects could not be enabled". I'm totally lost now and have no clue what to do and need some help. Here are some print outs of my command line.

rsvampire@rsvampire:~$ glxinfo | grep rendering
direct rendering: No
rsvampire@rsvampire:~$

rsvampire@rsvampire:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2

rsvampire@rsvampire:~$

---

### Post by sjnovick on 2007-05-03
Have you tried automatix?  They claim to be able to get your ATI card to work.

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by RSVampire on 2007-05-06
well I downloaded automatix, it doesn't have driver support for ATI cards only Nvidia cards.

---

