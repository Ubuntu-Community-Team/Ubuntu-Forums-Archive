---
title: "x11vnc server options"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by lisanels47 on 2012-07-01
I've been running x11vnc server on ubuntu 11.10 and 12.04 for some time now, but get some lockups on it at times, as well as disconnects.

Plus I would like to have the server only use 16bit color.  

Here are two server lines I'm working with.  Can anyone tell me how to make the server only use 16bit color?

/usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /tmp/x11vnc.log

/usr/bin/x11vnc -auth /var/run/lightdm/root/:0 -wireframe -noxrecord -noxfixes -rfbauth /etc/x11vnc.pass -loop -o /var/log/x11vnc.log

---

### Post by krunge on 2012-09-08
In the VNC protocol it is the VNC client that decides what his color depth will be, and the VNC server must oblige or drop the connection.  So you need to ask your VNC viewer to request 16bit color (which it will do automatically if it's display screen is 16bpp).

BTW: The SSVNC ssvncviewer has a hack where it can ask the VNC server for 16bpp and then transform locally to what the local display bpp is.

---

