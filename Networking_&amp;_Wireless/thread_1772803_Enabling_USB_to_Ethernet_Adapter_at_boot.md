---
title: "Enabling USB to Ethernet Adapter at boot"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by kexben on 2011-06-01
Hi

I've been googling for a while now trying to find the proper config for enabling a USB to Ethernet adapter at boot. My problem is that my adapter...

Bus 001 Device 002: ID 9710:7830 MosChip Semiconductor MCS7830 10/100 Mbps Ethernet adapter

...isn't enabled at system startup. It has been given interface eth1. 
Starting it after boot time works fine, ifconfig eth1 up and all that. 
But the lines I've put in /etc/network/interfaces doesn't seem to work. I've tried both:
auto eth1 and 
allow-hotplug eth1, to no avail.

I know there is some basic config I'm missing here.. I just don't know what. If anyone has an idea, thanks a lot for any help!

BR
Kexben

---

