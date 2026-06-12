---
title: "LAN stuck at 4.0 mbps..."
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by juan234 on 2009-03-04
I am trying to transfer 20GB of data between 2 computers, one with a 100meg rate NIC and the other with a 1000meg rate.  

After some searching I found this [http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)  

I installed ethtool and got 

# ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000c5 (197)
	Link detected: yes
and

# mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok

I tried setting the speeds and restarting /etc/init.d/networking the transfer rate still stayed the same 4.0Mbs, whis is really lame when I need to transfer a lot of data.

Does anyone know how I can solve this or a good link to the solution.

---

### Post by N04h on 2009-03-04
Do you see 4mb in a setting somewhere or is it the observed speed of the transfer?

Are they connected over a 10 switch/hub/router by chance?

---

### Post by juan234 on 2009-03-05
yes it is the observed transfer rate.  just before that it was going at 7Mb.  I am using a Zyxel P650H as a switch rated 100Mb speed.  Any ideas?

---

### Post by terazen on 2009-03-05
Is it only 4mb/s in both directions?

---

### Post by Brandon.Viking on 2009-03-05
using :
sudo mii-tool eth0
would tell you if the interface is in full duplex mode.

either that or try a different switch if you can.

Try a cross-over cable directly between the two PCs by passing the switch altogether may also show whether its related to the switch or not.

Just throwing a few ideas out there.

Regards,
Brandon.

---

### Post by juan234 on 2009-03-05
just checked again but different router. still stuck at 4.0 MB/sec

Also just tried the wireless even worse 700KB/sec


laptop 
# mii-tool eth0
eth0: negotiated 100baseTx-FD, flow control link ok

pc
# mii-tool eth0
eth0: negotiated 100baseTx-FD, link ok

I have no clue what is going on.  Not sure on how to use the crossover cable,  Just set an IP on the same subnet, no gateway?

all systems are ubuntu 8.10

---

### Post by juan234 on 2009-03-11
I tried transfering data the other day and speed was 7.0 MB/sec.   I am using a router everything appears to be set a 100 MB/sec.  

Any ideas?

---

### Post by terazen on 2009-03-11
Do you have anything other than the Zyxel P650H to connect your pc's?  The crossover cable idea Brandon.Viking had would work to take the switch out of the equation.

Also what size and number of data files are you transferring?  Transferring a bunch of small files the speed won't be the same as transferring a couple big files.

---

