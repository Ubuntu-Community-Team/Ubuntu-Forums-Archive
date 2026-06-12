---
title: "VNC keyboard input not working"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by newroad on 2012-11-01
Hi All,

I'm trying to open up a VNC session on Ubuntu 12.10 64-bit from Windows 7 64-bit.

I power on the Ubuntu box, then use Putty to open a VNC server session with appropriate geometry.  Then I use a VNC viewer the Windows 7 box to connect to it.

It does, and the mouse works (e.g. I can change the Desktop Background) but I can't figure out how to get the VNC session to take keyboard input.  I've tried two VNC viewers, TightVNC and RealVNC - both exhibit the same behaviour, so I'm guessing it's a server side problem/solution ...

As an aside, the Ubuntu session doesn't have the normal stuff on the screen, e.g. the taskbar, but maybe that's by design?  In any case, that's not essential - I can work around that.

Sorry of this is the wrong forum, but it was my best guess as it concerns something at least happening over the network.

Best regards, Newroad

---

### Post by steeldriver on 2012-11-01
My experience on 12.04 was that compiz just doesn't play nice with VNC - I had to specify a ubuntu-2d session in my ~/.vnc/xstartup

```
gnome-session --session=ubuntu-2d &
```

---

### Post by newroad on 2012-11-01
Thanks, SteelDriver.

I'll figure out what your suggestion does, then give it a go!

Regards, Newroad

---

### Post by steeldriver on 2012-11-01
this is pretty much the xstartup file I used:

[https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)

---

