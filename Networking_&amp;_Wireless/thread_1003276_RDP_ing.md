---
title: "RDP ing"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by quikone8 on 2008-12-05
I have been trying to find a way to get remote access to my server which is running intrepid with a KDE 3 front end.  The client I am using is a laptop with Intrepid with gnome or Ubuntu.  I have tried various ways to go Ubuntu to Ubuntu with no luck.  Tonight I switched the server to KDE in hopes of finding a way to accomplish the connection.  All I want to do is either control the current running desktop remotely or start a new desktop much like what Windoze Terminal Services does.  I would also like to accomplish this on a non-standard port.  

Someone out there has to know this so I don't have to hit my head against a wall too much more.

Thanks

---

### Post by quikone8 on 2008-12-06
bump

---

### Post by jonobr on 2008-12-06
Just checking if Im reading this right,

You want to Remote desktop to your ubuntu machine and its not working?

Did you enable sharing using
system->preferences->remote desktop

Thanks..

---

### Post by quikone8 on 2008-12-06
> **jonobr said:**
> Just checking if Im reading this right,

You want to Remote desktop to your ubuntu machine and its not working?

Did you enable sharing using
system->preferences->remote desktop

Thanks..

Yes.

I tried a small experiment today.  I used telnet to check ports and found that only two of the ports I thought were open actually are.  Of those 443 gets all the way through and says; SSH-2.0- OpenSSH_5.1p1 Debian-3ubuntu1.  When I use port 22 the computer responds SSH-2.0-OpenSSH_4.0.

Does anyone know the difference?  On 443 the system asks for a password and the system accepts it, the only problems is no desktop.  When I use port 22, the system responds, but when I type the password, the system refuses it.

Any help, or ideas would be appreciated.

Ron

---

### Post by quikone8 on 2008-12-06
> **quikone8 said:**
> Yes.

I tried a small experiment today.  I used telnet to check ports and found that only two of the ports I thought were open actually are.  Of those 443 gets all the way through and says; SSH-2.0- OpenSSH_5.1p1 Debian-3ubuntu1.  When I use port 22 the computer responds SSH-2.0-OpenSSH_4.0.

Does anyone know the difference?  On 443 the system asks for a password and the system accepts it, the only problems is no desktop.  When I use port 22, the system responds, but when I type the password, the system refuses it.

Any help, or ideas would be appreciated.

Ron

bump

---

