---
title: "How do I auto-run RealVNC server on boot with Natty Narwhal?"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by cRACKmONKEY421 on 2011-08-25
In trying to upgrade from the default VNC server, I have installed RealVNC on latest Ubuntu Natty Narwhal, and it seems to work fine. But I would like to make it so RealVNC starts in the background when ubuntu is booting. I found the website below, but those procedures seem a little dated, so I thought I would check here first. Does anyone know of a good way to load the vnc.so module on boot? I have nvidia drivers and such installed, so I am afraid adding the load module section in xorg.conf might make it so modules that I don't know about don't load. Any help is appreciated! Thanks!

[http://www.realvnc.com/products/free/4.1/x0.html](http://www.realvnc.com/products/free/4.1/x0.html)

---

### Post by cRACKmONKEY421 on 2011-08-26
Solved my problem by just using user mode and auto-login instead of the server module (added "x0vncserver -nowin" to my startup applications list). That's enough for my needs, but it was kind of annoying that I couldn't get the server module to properly load. The log showed the module tried to load, but failed (something about missing ModuleData data object). This would be a lot more annoying if I wasn't already using auto-login anyway, but it's as good as fixed for me.

---

