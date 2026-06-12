---
title: "VNC start with system rather than log-in"
date: 2010-02-20
forum: Mythbuntu
---

### Post by GyroTech on 2010-02-20
I've installed Mythbuntu 9.10 as a back-end only system and I was wondering if it is possible to set the VNC service to start at boot time rather than log-in. I don't want to leave this machine logged in all the time, but I would like to be able to VNC into it and get the proper XFCE login screen (after entering password for VNC).

Is this possible, and if so how would I go about configuring it? Also, if it could log-out the current user when the VNC session closes that would be the best.

Any ideas??

TIA

GyroTech

---

### Post by nickrout on 2010-02-20
you need to run vnc-server rather than x11vnc

---

### Post by krunge on 2010-02-20
I'm not sure exactly what you want to do.  If you just want a virtual desktop that is not associated with any physical graphics display, then use vncserver  as the previous post suggests.

If you want to use x11vnc to export the login greeter on the physical display it is described here:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
in the section named 'Continously'.

---

