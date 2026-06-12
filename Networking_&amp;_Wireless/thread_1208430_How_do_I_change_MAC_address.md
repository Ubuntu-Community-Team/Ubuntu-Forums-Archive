---
title: "How do I change MAC address"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by napsterved on 2009-07-09
I'm using Ubuntu 9.04..
My ISP has MAC bounded my service on my Laptop's MAC Address (Physical Address), in windows I used to change (mask) the MAC address using an application called MAC Address Changer.
Is there any solution in Ubuntu for chaging the MAC Address temporarily. And to connect net I have to type "sudo pon dsl-provider"..
How can I create a dialer of it?

---

### Post by vikrant82 on 2009-07-09
How about:

> sudo ifconfig eth1 down hw ether aa:aa:aa:aa:aa:aa
sudo ifconfig eth1 up

eth1 depends upon interface you are using. For wired network, it would be eth0

---

### Post by napsterved on 2009-07-09
It gives me an error
> sudo: ipconfig: command not found

---

### Post by vikrant82 on 2009-07-09
i**[COLOR="Red"]f[/COLOR]**config

---

### Post by napsterved on 2009-07-09
Thanx a ton..
it worked 4 me..

---

### Post by martcharb on 2010-12-08
> **vikrant82 said:**
> How about:



eth1 depends upon interface you are using. For wired network, it would be eth0

when i try:
     sudo ifconfig ra0 down hw ether D8:5D:4C:8E:58:ED

is say: 
     SIOCSIFHWADDR: Invalid argument

---

