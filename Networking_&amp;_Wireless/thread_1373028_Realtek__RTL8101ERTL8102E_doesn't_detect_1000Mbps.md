---
title: "Realtek  RTL8101E/RTL8102E doesn't detect 1000Mbps"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by alasarr on 2010-01-05
Hi!

I'm trying to configure the following network card to work with a 1000Mbps switch:

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
```

I think the problem is the network card module. When I run 
ethtool eth0 nothing of 100Mbps is showed:

```
root@anubis:/home/alasarr# ethtool eth0
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
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

I've installed the latest driver that I've found but the problem persist:
 [http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false]("http://www.realtek.com.tw/DOWNLOADS/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false")

This driver was updated 2009/11/17 so It's not very old

Any ideas??

Thanks Alberto

---

### Post by alasarr on 2010-01-05
is it posible the card was not gigabit??

---

### Post by thanasis57 on 2012-03-02
I am having the same problem. It seems that RTL8101E/RTL8102E is only a 10/100 adapter:
[http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4](http://www.realtek.com/products/productsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4)

---

