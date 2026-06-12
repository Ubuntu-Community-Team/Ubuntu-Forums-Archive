---
title: "read only issue accessing a shared folder in windows vista from ubuntu"
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by tanoloco on 2010-11-25
Hi guys! :p

After successfully networking Ubuntu and Vista together I came across this issue:
I can successfully mount a shared folder on Vista using "connect to server" under "places" menu however the "problem" is that it's mounted with 500 permission while folders and files in it are browseable with 700 permission.

Same effect mounting the shared folder using "network" under "places" menu and browsing to find it.

I tried to change the permission on the mounted shared folder with sudo chmod with obviously no luck.

Is there any chance to configure some option somewhere for the "connect to server" in order to mount them with write mode?
Something as umask=0077 or read only=no I guess ..:confused:

Any help much appreciated!

---

### Post by tanoloco on 2010-11-25
sorry guys! :P

the problem was on vista (as normal)! :D

The vista version is Vista Home Premium .. I ran the "create a shared folder wizard" by executing SHRPUBW.EXE and change the access permission and everything works fine.

The strange thing is that setting the same permission right clicking on the shared folder without using the wizard doesn't work even if everything is correctly checked.
Or at least I don't know where I was wrong ...

Hoping that this could help someone 'cause I spent all my day over that .. sadly :(

---

