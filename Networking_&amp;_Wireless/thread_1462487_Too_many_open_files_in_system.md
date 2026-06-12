---
title: "Too many open files in system"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by themrfox on 2010-04-25
After a few days of scouring these and other forums like this I've come across many "possible solutions" but nothing seems to work for me. Heres the story

I have an HP Mini 110 running ubuntu 9.10 so my wireless card was already a hassle I have it running Broadcom STA wireless driver (proprietary)

When I try to change my MAC address it has no problems changing my ether port however when i use the same command I recieve an error looks like this 

sudo eth1 down hw ether xx:xx:xx:xx:xx:xx
[sudo] password for fox:
SIOCSIFHWADDR: Too many open files in system

Help is appreciated in advance thanks :D

---

### Post by ratcheer on 2010-04-25
Run command "ulimit" and tell me what it says.

Tim

---

### Post by themrfox on 2010-04-25
unlimited

---

### Post by ratcheer on 2010-04-26
> **themrfox said:**
> unlimited

Ok, that is what it should be. Beyond that, I do not know what the problem is.

Tim

---

### Post by kirb3 on 2010-06-11
I got this error, too!  I think it has to do with MAC address changes not being supported by the driver for the wireless NIC.  I also use a Broadcom one.

I'm trying to find a USB Wi-Fi adaptor that will help me get around this problem, but no luck so far.

---

