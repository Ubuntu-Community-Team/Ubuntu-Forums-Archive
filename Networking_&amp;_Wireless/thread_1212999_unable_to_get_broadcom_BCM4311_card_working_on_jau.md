---
title: "unable to get broadcom BCM4311 card working on jaunty"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by dunnns on 2009-07-14
Hi, 
I've recently installed jaunty on my dell inspiron laptop with a broadcom BCM 4311 wireless card. I installed the hardware drivers and it says that broadcom STA wireless driver is activated and currently in use. However, I cannot find a wireless connection! I've had problems with this wireless card and ubuntu before on hardy heron and I thought that maybe installing the latest version might help but to no avail! I hope that someone can help me, I'm not particularly knowledgable about ubuntu!
Thanks in advance for any help anyone can give!
Nicole

---

### Post by superprash2003 on 2009-07-14
post output of** sudo iwlist scanning**

---

### Post by bodyharvester on 2009-07-14
> **dunnns said:**
> dell inspiron laptop with a broadcom BCM 4311 wireless card

which inspiron? im not sure if it matters but i have a (full name) dell inspiron mini 910 and its wireless card (also a broadcom) had to be configured just a teensy weensy bit first

welcome to the forums,
good luck, i hope it gets resolved soon ):P

edit: p.s. i HIGHLY recommend if yours is also a netbook to get the Ubuntu Netbook Remix

---

### Post by dunnns on 2009-07-14
it's an inspiron 6400 and the print out when i did sudo iwlist scanning was:
lo        Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

---

### Post by superprash2003 on 2009-07-15
ok.. take a look at this , i think this is mostly the issue [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html) 

look for the wireless switch in your laptop , on the sides and switch it ON

---

### Post by dunnns on 2009-07-15
ok, it works now! thanks for your help i feel a bit stupid that i'd just not switched it on...! i won't make such a rookie mistake again hopefully!
Thanks again
Nicole

---

