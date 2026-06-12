---
title: "Broadcom Corporation BCM4312 802.11b/g"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by pragyasurjan on 2009-01-16
Hello,
I have a BCM4312. I want to take it into master mode , so as to set up an access point. i tried using madwifi but i theres is no sucess.can u please help me.

---

### Post by pragyasurjan on 2009-01-16
I wanna set up my laptop as access point . i have a bcm4312 , but some how it doesnt go into master mode when i tried the change the mode from the terminal. can any one help ?

---

### Post by pragyasurjan on 2009-01-16
i have bcm4312 in my dell .The wireless seems to be working fine but I am not able to switch the card in master mode , when i say 

sudo iwconfig eth1 mode master

i get --> failed on device eth1 .

what should i do ??

do i need to get hostpad ?? if yes the which one ?? plz help. madwifi or prism 54.  please help.

---

### Post by pragyasurjan on 2009-01-16
I have a query regarding my bcm4312-

I am trying to get my BCM4312 in master mode . but no success .I need to make my laptop into access point by going in infrastructure mode/master mode. which hostpad should i use . It says in the documentation that BCM43xx supports  master  support and all i need to do is  to enable softmac wireless extension and BCM4312 driver. I am able to connect to internet. doesnt that mean that the driver is  enabled. Can you please help.

---

### Post by Ayuthia on 2009-01-16
If you have a 14e4:4315 card, the b43 module cannot be used at this time.  They are still doing work on the card so that it can be supported.  The only options are ndiswrapper and wl (Broadcom STA) but they do not provide monitor/master support.

---

### Post by bapoumba on 2009-01-18
Posts in different threads all merged here.

---

### Post by N4RPS on 2011-08-22
Having installed 11.04 on my HP Mini 210, it's nice to finally have a version of Linux that works right out of the box without a whole lot of grief.

Have they figured out how to make the BCM4312 LP-PHY card in master mode in 11.04 yet? This would be a nice feature to have. :confused:

---

