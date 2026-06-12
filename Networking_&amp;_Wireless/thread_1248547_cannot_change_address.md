---
title: "cannot change address"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by jrev on 2009-08-24
Hi, 
I got a computer whose Eth0 module on the mother board has an address that cannot be changed.
That is 169.254.6.214

I need to put the following address 192.168.0.1 in order to make it work with my local networking PC's 192.168.0.2 and 192.168.0.3
Any help ?

Thanks in advance  

:)

When I modify the /etc/hosts of the other 2 PC's it doesn't help the local network to establish

---

### Post by superprash2003 on 2009-08-24
is this for the desktop version? have you tried system->preferences->network connection

---

### Post by Iowan on 2009-08-24
You have tried editing */etc/networking/interfaces* (via **sudo nano)** or **gksudo gedit**?

---

### Post by jrev on 2009-08-27
I re-installed my local network with a new computer on ubuntu 8.04.
I will put the questionable computer on the bench with the 9.04 to-morrow to test it ...

Thanks for your answers :)

---

### Post by jrev on 2009-08-27
> **superprash2003 said:**
> is this for the desktop version? have you tried system->preferences->network connection

yes I did :(

---

