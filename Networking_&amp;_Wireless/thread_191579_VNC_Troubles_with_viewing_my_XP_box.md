---
title: "VNC Troubles with viewing my XP box"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Mr. Shifty on 2006-06-07
Hello all,

     So... i'm intrigued by Ubuntu and use it on one of my main machines but I haven't figured out how to get all my hardware working (driver problems for modem and wireless card) So for the time being I would like to be able to VNC to my XP box so i can controll stuff from there like the internet connection, File Sharing, Spy on Sisters computer activity... etc. etc. etc..... 

I can connect to my Ubuntu box from my XP box but i cant connect to my XP box from my Ubuntu box.  This means that something is wrong with the server app on my XP box. Right? Here is what i get when It wont connect:

shifty@Shubuntu:~$ vncviewer 192.168.0.1
VNC viewer version 3.3.7 - built Sep 27 2005 11:12:00
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
shifty@Shubuntu:~$


Any Ideas? please help, thanks,

-Shifty

---

### Post by linuchsan on 2006-06-07
is your Windows firewall on, and did you use the right display number...like :0 or :1

---

### Post by nowadays who knows on 2006-06-09
what flavor of vnc are you using in ubuntu? If xp firewall is on then put vnc veiwer and vnc server in the list of items to allow trough the firewall.

---

