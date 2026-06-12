---
title: "Vinagre fails to launch"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by edwardjames on 2012-08-23
The problem:
I installed vinagre, and got it working. During this initial session vinagre stalled, and crashed. After I tried starting it fails to load. It flickers for awhile, causing my machine to slow down until ctrl c vinagre or kill it from the launcher.

What I've done to troubleshoot:
RealVNC works on my windows session which leads me to believe that my issue is local, not remote. Just the same, the command I use to run my vncserver is x11vnc -nap -many -rfbauth ~/.vnc/passwd -ncache 10

I tried apt-get remove vinagre, then reinstalled it. The problem persists.

I tried searching for the config file, but could not find it. Supposedly it's located ~/.gconf/apps/vinagre but no such directory exists.


If anyone has any great ideas that'd be awesome. This is my first post. Apparently there are much better VNC viewers for linux, so I suppose I could try them, but I'm curious why this one isn't working.
Thanks,
edwardjames

---

