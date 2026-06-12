---
title: "Problem connecting Ubuntu 10.04 and 8.04"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by Marat ZH on 2010-06-05
Hi
I have computer with ubuntu 8.04 installed. There are samba shares on it, and also it works like NAT for my other computers.
I have no problem accessing it from windows xp, but when i installed ubuntu 10.04 it seems like it constantly loses connection with ubuntu 8.04.
The internet works fine (and much faster than on xp), but there are problems when i'm trying access samba shares on 8.04, or control it via ssh.
I have two samba shares on 8.04, one with just one file, i can access it from 10.04, and another with a lot of files, nautilus says connection timeout.
I can connect and login via ssh, but sometimes, when i'm trying to cat some file, or start mc or smth, it just stops printing anything.
And also vinagre connects to 8.04 desktop and draw some garbage.
I have no such problems with other hosts (e.g on the internet)

And the strangest thng is, that when i run ubuntu 10.04 on the same computer in VirtualBox under Windows XP everything works fine.
I have yet no experience to solve this problem myself, can anyone suggest a solution&

Problem solved now by manually setting MTU to 1492

---

