---
title: "network issues"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2010-08-10
I have two identical boards with integrated ethernet ports.  I took the hard drive from a working board and put it on a different one.  Now the network does not work.  I am assuming it is because of the difference between the MAC addresses of the first board and the second one.  

How do I fix Ubuntu so that it recognizes the new MAC addresses and allows me to get on to the Internet.

---

### Post by Iowan on 2010-08-10
*Probably* not the easiest way (and may not work)...
Edit */etc/udev/rules.d/70-persistent-net.rules* and change the MAC address to the one you have.

---

### Post by MAFoElffen on 2010-08-10
> **Iowan said:**
> *Probably* not the easiest way (and may not work)...
Edit */etc/udev/rules.d/70-persistent-net.rules* and change the MAC address to the one you have.
Here's a good tutorial on changing MAC addresses in Ubuntu:
   [Change your NIC/MAC Address in Ubuntu]("http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html")
But the tutorial assumes you already have macchanger installed already... You can install it by: ```
sudo apt-get install macchanger

```Hope this helps.... If that's what you "want" to do.

---

### Post by Z.K. on 2010-08-10
> **Iowan said:**
> *Probably* not the easiest way (and may not work)...
Edit */etc/udev/rules.d/70-persistent-net.rules* and change the MAC address to the one you have.

Actually, I found a similar post and I did modify the 70-persistent-net.rules file, but it would not work until I installed network-manager and rebooted.

Thanks anyway though.

:D

---

### Post by Z.K. on 2010-08-10
> **MAFoElffen said:**
> Here's a good tutorial on changing MAC addresses in Ubuntu:
   [Change your NIC/MAC Address in Ubuntu]("http://www.ubuntugeek.com/change-your-network-card-mac-address-on-ubuntu.html")
But the tutorial assumes you already have macchanger installed already... You can install it by: ```
sudo apt-get install macchanger

```Hope this helps.... If that's what you "want" to do.

The only problem is without a network connection, it is hard to install software with apt-get.  Still, I might look into that as something to do next time.  I did get it working though.

:)

---

