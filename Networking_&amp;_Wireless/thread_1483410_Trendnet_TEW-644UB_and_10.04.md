---
title: "Trendnet TEW-644UB and 10.04"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2010-05-14
Howdy All,

So I recently picked up a Trendnet TEW-644UB USB wireless device to use with an older laptop I have that runs 10.04 (it's internal wifi died)

Anyways - when I plus the dongle into the system it detects it right away and it even can see wireless networks! The only problem is that it cannot actually make a connection... I enter the wifi key and then it spins in a circle for awhile before failing :-/

Any suggestions?

~Jeff

---

### Post by beastrace91 on 2010-05-15
For anyone else trying to use this USB wifi card on Ubuntu it works like a charm once you install the backport wireless modules from the repositories.

~Jeff

---

### Post by zms on 2010-11-20
Hey, i installed the same thing but it keeps disconnecting after a couple of mins.Actually disconnected while writing this. Are you having the same problem?

---

### Post by beastrace91 on 2010-11-20
> **zms said:**
> Hey, i installed the same thing but it keeps disconnecting after a couple of mins.Actually disconnected while writing this. Are you having the same problem?

You've installed the backported wireless modules? Those did the trick for me.

~Jeff

---

### Post by zms on 2010-11-21
Im pretty sure i did. This is what I put into terminal...


zain@zain-laptop:~$ sudo apt-get install linux-backports-modules-wireless-lucid-generic


Is that right? Again I thank you in advance for the help.

---

### Post by beastrace91 on 2010-11-22
Yea. Then reboot and you are good to go.

~Jeff

---

### Post by zms on 2010-11-22
Yea thats exactly what i did, but it just keeps disconnecting every couple of mins. I

---

### Post by zms on 2010-11-22
Yea thats exactly what i did, but it just keeps disconnecting every couple of mins. I honestly dont know what to do?

---

### Post by Slim_Jim on 2011-04-15
I had the same problem.  I solved it by editing the file /etc/modprobe.d/blacklist.conf and add the following line: blacklist rt2800usb.  It has been working flawless since.

---

### Post by manoharks on 2011-06-09
If somebody is still interested in this subject, one solution is to install the RT2870USB driver from Ralink corp.'s site at
 [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Compile and install the driver and the wireless usb card works just fine.

---

