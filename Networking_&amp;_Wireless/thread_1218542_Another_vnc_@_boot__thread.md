---
title: "Another vnc @ boot  thread"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by scrupul0us on 2009-07-20
So I've spent quite a few days trying to get several implementations of tightvncserver, xllvnc and vnc4server
 to start at boot so I can simply boot my server, vnc in from where ever and log in as whatever user I see fit

I'm running 9.04 LTS [server] with gnome

Any help would be greatly appreciated

---

### Post by komputes on 2009-07-20
vnc4server is what you are going for if you want a system wide VNC server.

Otherwise you can set up the user on the server to log in automatically and then set up Remote desktop (vino) which is the VNC server that comes with Ubuntu.

---

### Post by scrupul0us on 2009-07-21
Can you offer any links/mans for setting it up correctly? I really only have two users on my system, my login and root so I'd really only need it to operate for just my login (although the need may arise for additional users so I'd ideally like to be greeted by gnome login vs an already logged in desktop)

any in-depth assistance would be greatly appreciated

---

### Post by komputes on 2009-07-21
> **scrupul0us said:**
> Can you offer any links

Sure can:
[http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

---

