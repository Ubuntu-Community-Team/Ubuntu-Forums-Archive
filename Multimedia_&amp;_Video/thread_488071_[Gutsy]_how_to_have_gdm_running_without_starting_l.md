---
title: "[Gutsy] how to have gdm running without starting local X"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by piripallo on 2007-06-29
Hi
I'm usual to install Linux on a box that will continue working without a monitor.
So I enable xdmcp and disable local X server by commenting the line
0=Local
in /etc/gdm/gdm.conf.
But this won't work in gutsy in fact local X start anyway (also after deleting /etc/gdm/gdm.conf).
I have comment out the line also in factory-gdm.conf (but I thing that gdm don't use this file).
Is there any other way to have gdm running without starting local server?
Thank You.

---

