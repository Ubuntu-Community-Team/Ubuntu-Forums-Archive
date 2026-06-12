---
title: "Network *semi* works"
date: 2009-01-10
forum: Networking &amp; Wireless
---

### Post by whaledawg on 2009-01-10
So I've been a linux user before but this is my first(full) attempt at installing Ubuntu. My problem is connecting to my WiFi:

My own network is unencrypted and with a public SSID. I see it just fine but every time I try to connect it gives up after a while. I would blame my router for the problem except that I was easily connect to it in windows immediately before I installed Ubuntu.

There is another unencrypted network within range(that's how I'm posting) and I can connect to that but my connect slows to a crawl for 20 minute periods and then speeds up to 'slow'.

I've tried multiple trouble shooting guides and forum posts but they seem to deal mostly with the wireless card not being recognized at all. Mine is, it's just not hooking up with my network. 

Here's the output of _lshw -C network_ while I'm successfully connected to the neighbor network:
```
  *-network:0             
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wmaster0
       version: 20
       serial: 00:18:e7:35:7b:43
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.2.4 latency=32 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
```

Any suggestions of where to start?

---

### Post by whaledawg on 2009-01-10
Any ideas? 

My hardware seems fine, since I can connect to my neighbors wireless. But every time I try to connect to mine I get dropped after I request an IP address.

And I booted into Windows and it worked just fine. :/

---

### Post by whaledawg on 2009-01-10
Solved:

I followed Mutt's advice in [this thread]("http://ubuntuforums.org/showthread.php?t=1035762&page=2") and then rebooted.

Again this is for the RTL-8185 chipset in my airlink PCI card.

---

