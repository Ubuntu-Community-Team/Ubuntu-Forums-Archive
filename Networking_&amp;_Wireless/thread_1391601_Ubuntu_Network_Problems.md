---
title: "Ubuntu Network Problems"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by chikiwighi on 2010-01-27
Stupid little problems like this are why I hate linux. 

Anyway, I have no idea what is going on here.

I turned on the computer and it comes up with "device is unmanaged" on the GUI network control. So I boot into the command line and set the IP address, netmas, dns, etc with ifconfig.

It has an ip address on the network, has dns, gateway, subnet mask configured properly, yet it will not connect.

Anyone have any suggestions?


The IP address on eth0 (the only one that wants to work now) ...
192.168.0.115
Gateway 192.168.0.1
DNS 192.168.0.1
Netmask 255.255.255.0

I know the gateway computer works as I am posting from a computer going through it right now.

---

### Post by Iowan on 2010-01-27
The "unmanaged" message is because NM isn't controlling the interface - did you set it up through NM or */etc/network/interfaces*? Did you restart networking after configuration?

---

