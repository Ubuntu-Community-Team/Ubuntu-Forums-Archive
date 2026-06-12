---
title: "x11vnc crashes host X"
date: 2010-10-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by seattle vic on 2010-10-01
I have all the latest updates and have noticed for the past couple days that when I connect from my laptop to a desktop (both running 10.10) using x11vnc, frequently the desktop (host) will drop the X server.  The OS does not reboot, but X goes to the login screen.

---

### Post by krunge on 2010-10-01
Try to use x11vnc 0.9.12 or 0.9.13 (no debian or ubuntu packages for these, you need to build from source or d/l 3rd party binary.) Some of this X crashing problem has been worked around in recent x11vnc versions.

Feel free to file a bug report with Xorg that you can kill the X server with a simple client.

---

