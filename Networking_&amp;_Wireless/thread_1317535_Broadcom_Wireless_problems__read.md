---
title: "Broadcom Wireless problems?  read"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by Tony Ricena on 2009-11-06
This should work for the majority of broadcom wireless users, I know it worked for me.  this works especially if you have a Ubuntu 9.10 cd.. please read:lolflag:

The Broadcam firmware/driver is on your ubuntu 9.10 cd! I had the same problem with my laptop, but looked on the internet and found the solution. 

Goto your Software sources and check the Installable from cd/dvd, put your CD/DVD in

Goto the Synaptic Package Manager, and search for bcmwl-kernel-source.. check and install.. restart computer and boom it works

---

### Post by iliketv01 on 2009-11-06
can you do this from an image file of the live cd or does there have to be a cd in the drive?

---

### Post by nhanquy on 2009-11-06
Good info here! Thanks! (In my case I have DELL E5500):

1. Put Ubuntu 9.10 LiveCD in
2. Select  (System -> Administration -> Software Sources -> Other Software) **Add CD-ROM**

Now  use (System -> Administration -> Synaptic Package Manager) and add ***bcmwl-kernel-source***.

---

### Post by Mahngiel on 2009-11-07
note: this only works for BCM4311 and later chipsets. i'm still researching how to get my 4306 rev03 to work

---

### Post by amitkenny on 2009-11-07
It is not working for me

---

