---
title: "How to change MAC address permanently for Ubuntu 9.04"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by demontager on 2009-05-14
I need to change MAC adress permanently, but without loosing networkAppet. I tried to add MAC to /etc/network/interfaces, but no success
auto lo
iface lo inet loopback
hwaddress ether 00:18:f3:3a:2e:dd
Could anybody give a script solution or other method?

---

### Post by DFord425 on 2009-05-14
I think the MAC address is permenitly hardwired to the network port. I dont think there is a way to change it unless you get a new NIC.

---

### Post by demontager on 2009-05-14
In order to change MAC I'm using macchanger-gtk at this time, but i should do that every boot time.

---

### Post by dandnsmith on 2009-05-14
add it into the startup scripts, but do a little research to make sure you get it in the right place. I think they're in /etc/scripts.d, but don't hold me to that (also look in inittab)

---

### Post by Joeb454 on 2009-05-14
MAC addresses are hardware based, the software you are using is basically a MAC address spoofer, so I would assume you need to change it every boot, or get a different network card

---

### Post by bluestreek on 2009-05-14
This works for me.

sudo gedit /etc/rc.local

Add the lines

ifconfig networkinterface down
ifconfig networkinterface hw ether 00:00:00:00:00:00
ifconfig networkinterface up

You can also try just adding the middle line there.

---

### Post by demontager on 2009-05-14
Thanks a lot your script works!

---

### Post by abnaxus on 2009-06-07
> **bluestreek said:**
> 

ifconfig networkinterface hw ether 00:00:00:00:00:00



hey guys!

i'm presuming that the ether 00:00... is the NEW mac adress? or is it the old mac i want to change?:roll:

---

### Post by patryk77 on 2009-09-14
> **abnaxus said:**
> hey guys!

i'm presuming that the ether 00:00... is the NEW mac adress? or is it the old mac i want to change?:roll:

Yes, it is the new MAC Address. To spoof eth0 with a new address of de:ad:be:ef:aa:bb, you use the following line:

```
ifconfig eth0 hw ether de:ad:be:ef:aa:bb
```

The 'ifconfig eth0 down' and 'ifconfig eth0 up' lines were not necessary in my case.

---

### Post by oktapod on 2010-08-08
Thank you bluestreek!
I did it in Ubuntu 10.04 and it works.

---

### Post by Alias1 on 2011-09-15
> **oktapod said:**
> Thank you bluestreek!
I did it in Ubuntu 10.04 and it works.
Well it does not work for me yes the mac address changes but I cant access the internet

---

### Post by cariboo on 2011-09-15
@Alias1, I'd suggest you start a new thread, as things have changed quite a bit since 9.04 was released well over 2 years ago. Closed.

---

