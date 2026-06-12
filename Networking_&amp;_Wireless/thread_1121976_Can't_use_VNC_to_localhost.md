---
title: "Can't use VNC to localhost"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by Stoodle on 2009-04-10
I want to set up VNC for use but I can't do it to localhost! It keeps saying the connection is refused and I don't know why if I'm doing it to myself! I wanted to to use SSH to connect to my computer and use VNC after connecting.

I've used VNC a bunch of times to connect to my own computer before and it worked once today. I haven't changed anything but it doesn't work now.

---

### Post by khelben1979 on 2009-04-10
Maybe [TightVNC]("http://en.wikipedia.org/wiki/Tightvnc") works better? Have you tried it?

---

### Post by Stoodle on 2009-04-10
Yeah.

Huh, I just tried both vncviewer and xtightvncviewer and I got
```

:~$ xvncviewer localhost

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Fri Apr 10 17:24:05 2009
 CConn:       connected to host localhost port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
 CConnection: No matching security types
 main:        No matching security types

```

---

### Post by superprash2003 on 2009-04-11
try typing 127.0.0.1 instead of localhost

---

### Post by Stoodle on 2009-04-11
```

:~$ xtightvncviewer 127.0.0.1
Connected to RFB server, using protocol version 3.7
Server did not offer supported security type

```

---

### Post by Stoodle on 2009-04-11
I think I have vino and vncserver on.

---

### Post by superprash2003 on 2009-04-13
type only vncviewer 127.0.0.1

---

### Post by Stoodle on 2009-04-13
```

 vncviewer 127.0.0.1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Mon Apr 13 17:10:28 2009
 CConn:       connected to host 127.0.0.1 port 5900
 CConnection: Server supports RFB protocol version 3.7
 CConnection: Using RFB protocol version 3.7
 CConnection: No matching security types
 main:        No matching security types

```

---

### Post by khelben1979 on 2009-04-14
What firewall are you using? And how is it configured? Maybe it causes problems.

---

### Post by j.crilly on 2009-04-14
Hi,

I am in a similar boat.  I used to be able to SSH and VNC from my XP notebook to my server, then last week an update happened on the server and lost all ability to do either.

Figure that the firewall may be halting them.  I can still access my website on the server, but after a few more apps to work.

I look forward to your help.

Cheers
Jamie

---

### Post by superprash2003 on 2009-04-14
have you tried remote desktop? System->preferences

---

### Post by Stoodle on 2009-04-14
It wasn't working for a while, but yes, remote deskop (vino) works. I would like VNC though, so I could connect from any computer (Windows or Mac) to X Terminal on this computer.

I'm using Firestarter which is configured to allow connections from 127.0.0.1 to port 5900.

It's something about security that won't let me connect. Other than that, I might be able to.

---

### Post by Stoodle on 2009-04-19
Glorious bump.

---

