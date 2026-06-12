---
title: "networking"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by hirohitosan on 2009-04-29
Hi there. I installed both Server and Desktop on the same box and have dual boot to see the differences.
I have static IP
I edited /etc/network/interfaces and add my network parameters:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address xxx.yyy.zzz.777
netmask 255.255.255.abc
gateway aaa.bbb.ccc.ddd

```
and after that edit /etc/resolv.conf and set the DNS
I did this at both, server and Desktop
but I cannot use web browsers or updates
I can ssh or ping to other servers but when it comes to update, apt-get install or browsing the net I cannot connect.

At Desktop I try with NetworkManager Applet
Right click > Edit > Wired -> add 
IPv4 Settings Manual and all values but still cannot browse the Internet

Did I miss something?

Thanks

---

### Post by sahabcse on 2009-04-29
For network set-up pls follow below url

[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)

---

### Post by hirohitosan on 2009-04-29
> **sahabcse said:**
> For network set-up pls follow below url

[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)
thanks sahabcse, I followed instructions from that site and here what I have:```
sudo mii-tool -v
SIOCGMIIREG on eth0 failed: Input/output error
SIOCGMIIREG on eth0 failed: Input/output error
eth0: negotiated 100baseTx-FD, link ok
  product info: vendor 00:aa:00, model 57 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
```
what does it means?
thx

---

### Post by sahabcse on 2009-04-29
Past the o/p of 
#sudo ethtool eth0

For installing the ethtool

#sudo apt-get install ethtool

---

### Post by hirohitosan on 2009-04-30
> **sahabcse said:**
> Past the o/p of 
#sudo ethtool eth0
sorry for replaying so late. It took some time to obtain this: 
```
ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbag
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

```

---

### Post by sahabcse on 2009-05-02
as per your o/p there in no issue in network interface

---

