---
title: "connection keep disconnecting"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by mstrap123 on 2009-04-29
i setup an ubuntu 8.04 server for the use of samba file sharing inside workgroup, the installation is fine and samba is running but the connection to the server from window xp keep disconnecting. i tried to ping the server, the server return:
 
[INDENT]Reply from 192.168.0.1: bytes=32 time=3ms TTL=127[/INDENT]

but when i tried to connect it fail, i try using putty and it also fail, after i ping the xp machine from the server then it can connect again, i then ping from the xp machine and it return:

[INDENT]Reply from 192.168.0.1: bytes=32 time=3ms TTL=64[/INDENT]

i have tested many times now and whenever the TTL change to 127, the connection fail. what is the problem here and how i solve it

---

### Post by squeaksof2006 on 2009-04-29
A lot of us are having that problem if we "upgraded" to the 9.04 or whatever it was they put out this month. Good luck, no one seems to have answers right now.

---

### Post by Ralphie on 2009-04-29
This has been happening to me in earlier versions, as well, I was hoping this latest version (9.04) would solve it. But hasn't.

What is your motherboard?
This is mine:
"ASUS P5GPL-X SE LGA 775 Intel 915PL ATX Intel Motherboard"
Using Internet connection driver "sky2"

---

### Post by mstrap123 on 2009-04-30
meaning this is a problem from ubuntu, any1 has the solution ?

---

### Post by Ralphie on 2009-04-30
perhaps if we start listing some computer specs we might be able to find some similarities and later find a solution..

---

### Post by mstrap123 on 2009-05-10
exactly wat is the cause for this problem to occurs..is the os itself disconnect the connection or the hardware component causes it

---

### Post by mstrap123 on 2009-05-17
the server currently using is the:
[INDENT]Dell PowerEdge(TM) SC430 with Intel(R) Pentium(R) 4 Processor 2.8GHz/1MB,800MHz FSB[/INDENT]
[INDENT]1GB (2x512) DDR-2 667MHz ECC 1R Memory[/INDENT]
[INDENT]80GB (7200 RPM) SATA Hard Drive, First Drive[/INDENT]

hope this can be help..btw i cannot find the model of the motherboard in the dell website so i cannot provide the brand and model of the motherboard

---

