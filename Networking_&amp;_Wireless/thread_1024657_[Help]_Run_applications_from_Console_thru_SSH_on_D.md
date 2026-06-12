---
title: "[Help] Run applications from Console thru SSH on Desktop"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by Peter Smile on 2008-12-29
I use SSH to connect to my home computer as host from my Windows XP running Office PC (sadly).

Usually i stablish the connection and thru console run applications on my computer (such as update, download, etc) but my problem is that when i close the SSH connection all the running processes thru it are also closed.

So, **Is it possible to run thru a SSH connection applications that will remain active after i finish the remote session?**

---

### Post by jgoguen on 2008-12-29
Yes, but you'll need to install Screen to do so.  I think it's automatically installed, but run this command to make sure:
```
sudo aptitude install screen
```From there, read the Screen manpage (man screen) to find out about all its options.  When you're ready to leave, simply close Screen, log out, then when you log in again you can reattach the old screen session.

I know your post didn't specify graphical apps, but in case anyone else is interested... If you want to leave graphical apps running, Screen isn't good for that AFAIK.  You'd need to use some sort of remote desktop solution (VNC for example) to achieve this.

---

