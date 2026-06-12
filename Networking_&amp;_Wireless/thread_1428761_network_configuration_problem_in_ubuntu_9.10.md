---
title: "network configuration problem in ubuntu 9.10"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by wangsuper on 2010-03-13
I met some problem when I configure network after installation.
 
I revise /etc/network/interfaces as follows:
 
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 58.196.140.8
hwaddress ether 00:05:BA:58:C5:CC
netmask 255.255.255.0
gateway 58.196.128.1
dns-nameservers 202.120.2.101
 
Then, I typed: 
/etc/init.d/networking restart
 
But the system said:
 
*Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0
 
Can anyone tell me the reason? Thanks a lot!

---

### Post by wangsuper on 2010-03-14
Help me!

---

### Post by wangsuper on 2010-03-14
It works when I change the gateway to 58.196.140.1
It's weird since 58.196.128.1 works well in windows XP

---

### Post by Iowan on 2010-03-14
I was a bit curious about the gateway address - since it wasn't in the subnet. 
So, the machine is connecting? Reason I ask - a couple of us are researching whether Network Manager and */etc/network/interfaces* still work together.

---

### Post by chili555 on 2010-03-14
Is Network Manager installed? Is it set to start on boot?

---

