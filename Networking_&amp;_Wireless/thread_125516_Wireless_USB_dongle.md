---
title: "Wireless USB dongle"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by jm2003uk on 2006-02-04
Hi everyone!

I've got a Dynamode WL-GI-700S wireless USB dongle which i'm trying to get to work with ndiswrapper. I've tried using the win98 and winXP drivers from the cd and i've managed to get them to install them looking at the resualts of ndiswrapper -l...

james@ubuntu:~$ ndiswrapper -l
Installed ndis drivers:
sis163u driver present, hardware present


I've tried using 'modprobe ndiswrapper' but that just locks the system. Anyone able to help me from here on getting it working?

---

### Post by bscbrit on 2006-02-04
What does 'lsusb' give you?

---

### Post by bscbrit on 2006-02-04
[http://ubuntuforums.org/showthread.php?t=105820](http://ubuntuforums.org/showthread.php?t=105820)

Have you seen this thread?

---

