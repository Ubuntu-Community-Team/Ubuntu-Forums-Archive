---
title: "xvncviewer server with dyndns.org sometimes work sometimes not"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by ctw on 2009-05-20
Hi everybody,

I connect sometimes with one workstation on my work with xvncviewer (both computers with ubuntu 9.04 x64). 

I have configured the router (linksys wag325n) with a dynamic ip with the option dyndns,
and the router has open the port 5900 for this service. 

Sometimes i can connect without problem, but other times appears :

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:23:14
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed May 20 11:47:02 2009
 main:        unable to connect to host: Connection timed out (110)

Can you help me to configure right my dyndns connection in my workstation.

TIA

---

### Post by dmizer on 2009-05-20
Oh man ... get that turned off but quick. All that's keeping your box from being completely owned is a password. That's like using cardboard as your front door. VNC is NOT NOT NOT meant to be access over the web.

---

### Post by ctw on 2009-05-21
> **dmizer said:**
> Oh man ... get that turned off but quick. All that's keeping your box from being completely owned is a password. That's like using cardboard as your front door. VNC is NOT NOT NOT meant to be access over the web.

wich better option can I use to control remotely  my box?

---

### Post by dmizer on 2009-05-21
Any encrypted protocol like SSH or VPN will do fine. What exactly are you needing to control? The answer may tell you what tools you can use.

I use lots of tools to access my machines from remote, but the main one is SSH. Once I get an SSH connection to my server, then I can use a variety of web tools to do things like access files, maintain virtual machines, start/stop torrents, and stream music. I can also use SSH to open individual GUI applications if necessary. But most everything can be done via the command line anyway.

---

### Post by kryptoz on 2009-05-21
:(

---

### Post by ctw on 2009-05-21
Hi dmizer thanks for the fast answer.

I want to control my desktop remotely.

1-I don't have a static ip, and for this reason I did one count to dyndns.
2- I know only (for to control remotly de Desktop) the vxncserver (workstation) and with my laptop i use the xvncviewer
3- And yes I use only a password to acces on it.

Wich kind of method can I use fot to have a better segurity?

Do you know another program to control the dekstop remotally?

maybe you can help me too, why sometimes I can't connect with xvncviewer and comes this error:

i can connect without problem, but other times appears :

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:23:14
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed May 20 11:47:02 2009
main: unable to connect to host: Connection timed out (110)

TIA

---

### Post by dmizer on 2009-05-21
> **ctw said:**
> 1-I don't have a static ip, and for this reason I did one count to dyndns.
This is fine. You'll still need it. Take a look at your router configuration, as most routers have dyndns update capability. This is your best option.

> **ctw said:**
> 2- I know only (for to control remotly de Desktop) the vxncserver (workstation) and with my laptop i use the xvncviewer
You can still use xvnc to connect to your desktop if necessary (it shouldn't be necessary in most cases).

> **ctw said:**
> 3- And yes I use only a password to acces on it.
Because of this, all someone has to do is sit on port 5900 and wait for you to come by and tell them what the password is. Once they know the password, they can get access to your system and do whatever they like.

> **ctw said:**
> Wich kind of method can I use fot to have a better segurity?
As I suggested earlier, either [SSH](https://wiki.ubuntu.com/AdvancedOpenSSH) or [VPN](http://www.thebakershome.net/?q=node/56). Both of these will get you connected to your local network over and encrypted protocol. Once you are connected to your local network, then you can use xvnc as though you were connected to your router.

> **ctw said:**
> maybe you can help me too, why sometimes I can't connect with xvncviewer and comes this error:

i can connect without problem, but other times appears :

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:23:14
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Wed May 20 11:47:02 2009
main: unable to connect to host: Connection timed out (110)
I suspect that you are getting this error because your dyndns update utility isn't configured correctly, or your IP address is changing faster than your utility is checking IP addresses. For this reason (as I suggested earlier), I highly recommend that you check your router configuration to see if it can automatically update dyndns for you.

---

