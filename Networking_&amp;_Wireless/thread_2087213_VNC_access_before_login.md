---
title: "VNC access before login"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by alepila on 2012-11-23
Good morning everybody, I want to access to my server using VNC also when I reboot the system in SSH. I tried tigtvnc and x11vnc with no results! Is there a command to lauch VNC in SSH after reboot and before graphical login? In the server is installed Ubuntu 12.04. Thank you very much

---

### Post by Groodles on 2012-11-23
I dont know of a way to obtain VNC access to the machine AT the login prompt as VNC services wont be started until after a user is logged in.

However, what you can do is have a VNC service started BY a user which spawns a desktop at the same time.  (this is totally independent of what is displayed on the grfx card output).  Therefore you can do this on a headless machine (one without a monitor).

The following guide should help you:

[http://skerit.com/en/computer/english-vnc-x11-session-on-ubuntu-12-04-server-without-monitor-or-graphics-card/](http://skerit.com/en/computer/english-vnc-x11-session-on-ubuntu-12-04-server-without-monitor-or-graphics-card/)

---

