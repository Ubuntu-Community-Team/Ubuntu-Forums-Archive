---
title: "pfSense and Virtualbox"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Kuros on 2010-02-21
Hi everyone,

I am trying to set up pfSense as a guest OS under Ubuntu 9.10 (netbook remix, working on a asus eeepc). I have my cable modem attached to the USB port, and an ethernet cable attaching the eeepc to the rest of my network. The host gets an ip from the modem fine, and I can browse the internet. I can also ping the rest of my network, so both interfaces are running fine, it seems.

However, I have installed pfSense as a guest OS under VirtualBox 3.1.2. I put 2 virtual nics in the guest os, and bridged one with eth0 (the internal interface) and one with eth1 (the wan interface). I cannot ping the LAN ip of the pfSense guest, and it won't get a WAN IP. 

My /etc/network/interface file is as follows:

# The LAN network interface
auto eth0
iface eth0 inet static
        address 192.168.30.1
        netmask 255.255.255.0
        gateway 192.168.30.254

# The WAN network interface
auto eth1
iface eth1 inet manual

Any suggestions would be greatly appreciated!

---

