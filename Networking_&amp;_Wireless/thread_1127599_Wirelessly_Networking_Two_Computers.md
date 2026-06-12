---
title: "Wirelessly Networking Two Computers?"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by Polyrhythm_oly on 2009-04-16
Im having difficulty setting up a wireless network between computers. I have a computer with internet access and wanting to send internet to another. The other computer has my music etc on 

Both machines are running 9.04

Can anyone help??

---

### Post by renoturx on 2009-04-16
Are you trying to use internet connection sharing??
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

or are you trying to access one computer through a router?

---

### Post by Polyrhythm_oly on 2009-04-17
well one computer is receiving internet via ethernet and i want to access the other machine through a network. also send internet to the other machine through a home network

---

### Post by leandromartinez98 on 2009-04-17
You need to set the the configuration of the router to provide fixed IPs to the machines. Then, you will probably be able to access the machines using
standard ssh connections using those IPs.

There may be problems if you router has settings not allowing the machines in the local network to communicate, but I have the impresion that for these routers one can normaly buy this is not the case, at least this has worked for me.

---

### Post by superprash2003 on 2009-04-17
you would need to setup an adhoc network.. check out sys->pref->network configuration .. and under wireless .. click on ADD and create one

---

