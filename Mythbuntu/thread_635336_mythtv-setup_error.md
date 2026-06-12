---
title: "mythtv-setup error"
date: 2007-12-08
forum: Mythbuntu
---

### Post by Steve2/75 on 2007-12-08
running mythtv back end on 6.06lts server. The machine is a bit over powered for this application, however I got it for next to nothing.

Its a Prolient DL580
4 x PIII Xenon 700s with 1 Meg cach
1 gig of ram
OS on included scsi raid

I have it all set and from a terminal window ran:

user@mythtv:~$ sudo mythtv-setup
Password:
2007-12-08 16:27:42.375 Using runtime prefix = /usr/local
2007-12-08 16:27:42.399 DPMS is disabled.
2007-12-08 16:27:42.437 New DB connection, total: 1
2007-12-08 16:27:42.464 Connected to database 'mythconverg' at host: localhost
2007-12-08 16:27:42.468 Total desktop dim: 800x600, with 1 screen[s].
2007-12-08 16:27:42.489 Using screen 0, 800x600 at 0,0
Illegal instruction
user@mythtv:~$

ok hints? I am lost thanks in advanced

---

### Post by barney_1 on 2007-12-09
Do you have a graphical desktop setup on that machine?

If not, try to tunnel into it using ssh with X forwarding, then run the command.

Install the ssh server on your backend maching:
```
sudo apt-get install openssh-server
```

Tunnel into it with X forwarding from a different computer:
```
ssh -X YOURUSERNAMEHERE@SERVERIPADDRESSHERE
```

---

