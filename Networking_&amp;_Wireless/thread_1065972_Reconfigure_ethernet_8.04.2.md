---
title: "Reconfigure ethernet 8.04.2"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by Otto-C on 2009-02-10
Last Saturday I updated my Hardy install. It is totally up to date.
I have now lost my ethernet. 
Is there a way to reconfigure the ethernet setting to those of new install?

tia
otto-c

---

### Post by DiGiTGOD on 2009-02-10
You need to be more specific about

I've lost my Ethernet.

---

### Post by Otto-C on 2009-02-10
Cannot connect using my ethernet. My ISP tells me that I'm connected
but cannot access internet using [www..](www..)., or ping a site.
I would like to think 1. The update was the cause or 2. My nic card
has failed. or 3. Something I have no knowledge of.
Tell me what you want and I'll try to get it.

tia
otto-c

---

### Post by pdtpatrick on 2009-02-10
out following 

dmesg | grep -i network 

lspci | grep -i ethernet

cat /etc/networks/interfaces 

this should get the process started for helping you out . 

also see if this help

sudo /etc/init.d/networking restart;ifconfig

and post that output as well.

---

### Post by Otto-C on 2009-02-11
Boy am I red faced. While I swapped cables around on the ISP's
tech advise, I have found that one of the cables was the culprit.
All is well. 
Thanks to pdtpatrick for taking the time to make his suggestions.
Consider this item closed.
otto-c

---

