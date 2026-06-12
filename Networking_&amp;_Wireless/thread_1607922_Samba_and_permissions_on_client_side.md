---
title: "Samba and permissions on client side"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by miguelastico on 2010-10-28
Hi everyone.
I have a samba share on a centos server.
If I try to connect to it with the "connect to server" with nautilus (10.10) it works perfectly, I can create and delete files/folders based on the permission my user has on the server.

Then I wanted to mount the share as a disk to use it for several other task, and the problems start.
I followed [this guide on mounting windows shares permanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") and tried some others, but no luck.
The folder is mounted, but the permissions for my user are not used, since I see the user id of my user on the server. It acts like I didn't logged as that user.
In particular, the user on the server has id 500, and on the client I have 1000.
I tried with the forceuser, the uid option, but nothing.
Any ideas? How come that nautilus (and finder in my mac os machine, and some other windows machine) work correctly?

---

