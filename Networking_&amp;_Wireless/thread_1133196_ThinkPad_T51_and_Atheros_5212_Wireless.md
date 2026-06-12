---
title: "ThinkPad T51 and Atheros 5212 Wireless"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by svenole on 2009-04-22
Hello. 

I've just got an old ThinkPad T41 with Atheros 5212 wireless card installed. I did get trouble with this wireless card several years back, but surprisingly it worked fine with 8.10 also with WPA2 Personal enc. 

However I discovered one problem. Wireless does not reconnect after suspend / resume. I can see activity, the different networks are displayed in Network Manager, but it will not connect. It does not matter if the network is open or encrypted. A rmmod / modprobe ath_pci solves the problem. 

I have tried most tricks to make this rmmod / modprobe process run automatically after resume, but have not succeeded ( script in /etc/acpi/resume.d ) 

I know that I should probably disable this driver and use the drivers in the so called back-port package, but I thought I should ask the forum for some help first.

---

### Post by svenole on 2009-04-23
It seems like this problem is gone in 9.04. The Atheros wireless network card seems to resume fine after this upgrade.

---

### Post by Ryuhayabusa on 2009-04-23
I am having trouble with WPA enterprise and this chip, are you able to connect to wpa enterprise?

---

### Post by svenole on 2009-05-04
I've not tested 9.04 / Atheros with WPA Enterprise. I have no wireless zone available for this test and I am not up to fiddling with my current one... sorry. I use WPA2 Personal and it works.

---

### Post by Ryuhayabusa on 2009-05-05
thanks svenole.

I'll keep trying.

---

