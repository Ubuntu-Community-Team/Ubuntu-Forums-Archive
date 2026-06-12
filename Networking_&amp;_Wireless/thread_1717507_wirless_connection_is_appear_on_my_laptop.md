---
title: "wirless connection is appear on my laptop"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by Rakeshvijayan on 2011-03-30
Hi friends 

I think wireless driver is  not installed on my laptop .I am using COMPAQ Presario CQ40 

how can I check the wireless driver is installed or not ?If it is not installed who can I install 

the driver? am using ubuntu 10.04

---

### Post by papibe on 2011-03-30
Check the wireless tab on your Network Manager. Check this [link]("https://help.ubuntu.com/community/NetworkManager0.7").

Good Luck!

---

### Post by Enigmapond on 2011-03-30
Navigate to Administration/Additional Drivers (or Hardware Drivers) with a wired connection and if it's not installed, it will.

Cheers!

---

### Post by cye05 on 2011-03-30
you can try these commads.
open the terminnal 
lspci -k | grep Net

or 
dmesg

---

### Post by Rakeshvijayan on 2011-03-31
> **Enigmapond said:**
> Navigate to Administration/Additional Drivers (or Hardware Drivers) with a wired connection and if it's not installed, it will.

Cheers!


Thanks I got it.Now I a have a new question is the same as on desktop 

I did the instruction desktop which doesn't see any thing

---

### Post by Rakeshvijayan on 2011-03-31
> **cye05 said:**
> you can try these commads.
open the terminnal 
lspci -k | grep Net

or 
dmesg


I use this command on my desktop  . On my desktop D-Link DWA-510 adapter is installed 

but it shows this

---

