---
title: "VNC session steals active window using XP"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by mgoldey on 2009-09-27
Here's a vexing problem:  VNC viewer keeps making itself the active window on my XP desktop when I run vncserver on Ubuntu.  

Here's the skinny.  

I've got two Ubuntu machines.  Both happen to be Dells.  One is quite old (came w/ Win98 ) and the other dates from about 2002.  Both run Ubuntu desktop.  The old one is running Intrepid, updated over time from Edgy or lord knows where I got started back whenever that was.  The newer machine is running Jaunty, installed last week.  

Both Ubuntu machines run headless and I access them via VNC.  The older machine is usually running  vncserver 3.3.7-14ubuntu1 and the newer one runs vnc4server 4.1.1+xorg1.0.2-0ubuntu7.  

On the viewing side, I've got a handful of XP SP3 machines, various makes and models.  I use RealVNC and TighVNC, and both work fine, so long as the VNC window is active.

The problem:  If the VNC viewer window on the XP machine is not the active window, then every 8 to 10 seconds or so, the VNC viewer program steals focus and makes itself the active window . . . sort of.  It doesn't matter whether the VNC viewer window is maximized or just hidden:  all of a sudden, I'm typing into my Ubuntu desktop session, and the title bar on the XP program that I'm using is greyed-out.  The worst part is, the VNC viewer window does not even open on the desktop or come to the front of the desktop   Instead, the VNC viewer icon on the XP taskbar becomes "depressed" just like it should for whatever window is normally active.

I believe this is a Ubuntu issue because, in addition to what's set forth above, it never happens when I VNC into a Debian or Red Hat machine.  Also, this didn't happen when the older machine was running Gutsy, I'm pretty sure.  At some point, I updated it to Hardy and then Intrepid, and noticed this problem.  I figured it was a one-off until I built the Jaunty machine and discovered it there, too.  I'm thinking that there is some "do not sent events to viewer" setting that I'm missing, but I can't imagine what.  

Any help would be greatly appreciated, this is driving me nuts.   Thanks.

---

