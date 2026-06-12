---
title: "Intel Pro 1000 PF, working but not working?"
date: 2010-08-23
forum: Networking &amp; Wireless
---

### Post by dtd646 on 2010-08-23
I am installing an Intel Pro 1000 PF (fibre ethernet) card into my ubuntu 10.04 server.  The drivers appear to be loading correctly and the device is listed in the lspci.  I made the neccessary changes to my /etc/network/interfaces file and created 2 ethernet connections similar to the following:
 
auto eth0
iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1
 
auto eth1
iface eth1 inet static
address 192.168.1.21
netmask 255.255.255.0
 
When I do an ifconfig, it lists the 2 nics and up.  I have also install ethtool and everything looks good there.  I am getting a small amount of traffic on eth1 but almost all traffic is going though eth0.
 
My problem is that when I unplug eth0, eth1 (Fibre) and eth0 are no longer ping able from a computer on the same subnet.  If I unplug eth1, there is no change to either IP address and both IP addresses are pingable.  SO, it seems that even though I am specifiying 2 different interfaces, the ip addresses seem to be assoicated with eth0.  Any ideas why this would be occuring?  All I am looking to do is put this new fibre nic in for increased speed, don't even really need the other one.
 
I have tried eliminating eth0 and using only eth1 BUT I get no connectivity.  I am thinking the problem could possibly be on the switch that my fibre card is plugged into but I am having a hard time figuring out where the problem is, the fibre switch OR on the ubuntu server side.  What is the best way to confirm which end the issue is on?
 
Thanks

---

