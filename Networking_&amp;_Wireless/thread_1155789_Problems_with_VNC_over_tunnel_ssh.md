---
title: "Problems with VNC over tunnel ssh"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by ierpe on 2009-05-11
Hi,

So I've got this server with xtightvnc installed.
I used to be able to connect fine. After opening the ssh connection, i would just start vncviewer on the localhost:2 (my tunnel is on 5902) and then connect to it.

I can still connect under windows, but not with ubuntu... any idea why?
I get a 111 error "connection refused"...

after some testing, I am now sure that the problem comes only from my ubuntu distrib (I just upgraded to the 9.04), as I can connect fine from other machines...

I tried reinstalling the vnc client but didnt work.

Any idea anyone?

---

### Post by Peter09 on 2009-05-11
Are you getting the ssh connection OK. Also note that if you are using certificates your machine may be not recognised due to its rebuild. Look in the log files 

/var/log/auth.log

---

### Post by ierpe on 2009-05-11
The ssh connection seems to be fine... Im connected as root and can execute commands np...

How can I cleanup the certificates?

---

### Post by Peter09 on 2009-05-11
Check that the target machines firewall is not blocking the port.

---

### Post by ierpe on 2009-05-11
I have a second laptop with a winXP running and I can connect fine (with putty and same config)

---

### Post by Peter09 on 2009-05-11
sorry, I mean the target machine is the one that you are trying to hit with your VNC connection. I think I understand that you are setting up ssh like > machine A->machine B and VNC as > machine B->Machine A

so can you check the firewall ports for VNC on machine A

---

### Post by ierpe on 2009-05-11
Sorry but I dont get you really...

Anyway, how can I check which port vnc is trying to use on my ubuntu?

---

### Post by Peter09 on 2009-05-11
OK when you start vncviewer it should by default open port 5900.

So this means that vncviewer must be running before you try to connect.

When you start xtightvnc it will by default connect on port 5900.

Make sure both sides are using the same port number.

---

### Post by ierpe on 2009-05-11
How can I check which ports are being used?

It was working before, so I guess the ports are right...

How can I clean the certificates I accepted with putty?

---

### Post by Peter09 on 2009-05-11
If you can establish an ssh connection then your certificates should be OK.

try running vncviewer in a terminal to check the output, have a look at what it sees at that end.

do the same for xtightvnc, see what it says.

---

### Post by ierpe on 2009-05-11
In putty the forwarded port is: L5902  localhost:5902

_- With vncviewer:_

root@ubuntu:/# vncviewer localhost:2

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

Mon May 11 14:11:19 2009
 main:        unable to connect to host: Connection refused (111)


_- With Xtightvncviewer_

root@ubuntu:/# xtightvncviewer localhost:2
xtightvncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server



This was working only a while ago, I don't understand what happened.

---

### Post by Peter09 on 2009-05-11
Confused, are you running vncviewer at both ends?

---

### Post by ierpe on 2009-05-11
the server runs xtightvnc (server), but I used to be able to connect with both vncviewer (client) and xtightvnc (client)

I might just try to uninstall reinstall my vnc client, since I upgraded, it might be linked and a fresh install couldnt be bad...

---

