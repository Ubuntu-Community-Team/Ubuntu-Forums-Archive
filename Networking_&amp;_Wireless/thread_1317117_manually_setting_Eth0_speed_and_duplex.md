---
title: "manually setting Eth0 speed and duplex"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by birotoffee on 2009-11-06
Hallo everyone. Quite new user here.

I've seen lots of internet postings citing the use of EthTool to set speed and duplex of eth0 to 100 Full, but is it possible to do it from the /etc/network/interfaces file?

I ask as the Ubuntu64 server (8.04 I think) we use does not have internet access, so i can't connect it to the internet to ' apt-get install' the packages for EthTool.

At the moment auto-negiotiation of speed and duplex is used, see config snippet below, but our elderly Cisco 3548 XL EN workgroup switch isn't too hot at getting the right settings, hence a desire to nail both sides to 100F.

[snippet from /etc/network/interfaces]

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.44.80.20
        netmask 255.255.255.0
        network 10.44.80.0
        broadcast 10.44.80.255
        gateway 10.44.80.1
        dns-nameservers 10.44.80.60


[snippet from lshw]

*-network
   description: Ethernet interface
   product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
   vendor: Broadcom Corporation
   physical id: 0
   bus info: pci@0000:02:00.0
   logical name: eth0


If its not, I'll just have to relocate it onto a network with internet access and use apt-get install ...

Thanks in advance.

---

### Post by chili555 on 2009-11-06
I'd suggest adding to /etc/rc.local:```
ethtool -s eth0 duplex full speed 100
```Is not ethtool installed by default?

---

### Post by birotoffee on 2009-11-07
Thank you for the quick reply Chili555. I will do as you suggest.

---

