---
title: "Jaunty bonded NIC's route not persistent"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by oshunluvr on 2009-10-12
Network Guru's Please Respond! 

I am new to (k)ubuntu but fairly experienced in rpm based distro's.

I am attempting to bond my two NIC's as I have on my other installs.

Please remember as you answer: 
Hardware works fine under openSUSE and others so that's not it. 
No firewall issues (the router does it, not the install).
Kernel 2.6.28-15-generic
Kubuntu Jaunty new install - updated
Internet/Network connection worked fine before bonding

Here's the deal: I have successfully bonded eth0 and eth1 via:
/etc/network/interfaces
```
# Bonded interfaces
auto bond0
iface bond0 inet static
address 192.168.1.199
netmask 255.255.255.0
gateway 192.168.1.1
slaves eth0 eth1
bond-mode 0
bond-miimon 100
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

```and /etc/modprobe.d/bonding
```
 alias bond0 bonding
 options bonding mode=0 miimon=100
```This appears to work but I am connected to my network, but not to the internet. In my experience this is usually a route issue so I did
```
sudo route add default gw 192.168.1.1
``` and voila I was online. Of course as soon as the network is restarted or the OS rebooted the connection dies and I have to manually re-connect. I was under the misconception that the "Gateway" listed in "interfaces" would be all I needed. So I checked my routing tables and they seem a little odd to me.
Before manual default gw command:
```
Kernel IP routing table       
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 bond0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1 
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1 
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 bond0
```After manual default gw command:
```
Kernel IP routing table       
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 bond0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1 
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 bond0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1 
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 bond0
```So what's up? Any ideas? I guess I can add a manual route command somewhere, but I'd rather know why this is happening and how to fix it...

---

### Post by Iowan on 2009-10-13
Perhaps it's a different topic, but have you seen [this]("https://help.ubuntu.com/community/UbuntuBonding") help page on bonding?

---

### Post by oshunluvr on 2009-10-14
Yeah, I've read that page - here's another that's also relevant 
[https://wiki.ubuntu.com/LinkAggregation](https://wiki.ubuntu.com/LinkAggregation)

However, more relevant to my problem is I read elsewhere that Network Manager doesn't like static IP's which I also did when I bonded my interfaces.

I have removed Network Manager now all my issues have disappeared. My route is persistent and the network and internet appear to load properly after reboot.

---

