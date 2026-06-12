---
title: "Realtek RTL8168 REV.6 cannot reach up 1000mbps in Kubuntu 11.4 / 64 bits version"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by youngpatrick on 2011-05-02
I have installed Kubuntu 11.4 / 64 bits in my laptop HP DM-1 3000au and the built-in Realtek RTL8168 rev.6 gigabit lan card. The first thing I have downloaded the source file and compiled the correct lan card from Realtek web-site. I have also blacklisted the RTL8169 driver and success to load driver r8168 in system. 

The problem is my router Netgear WNDR3700 detect the lan signal in 100mbps instead of 1000mbps. The signal led indicator has blinked in amber color (100mbps signal) instead of green color (1000mbps). I have uploaded some files from NAS to my laptop using samba. The transfer rate read as below 8MB/s (I suppose the normal rate should read as over 20MB/s). That is I confirm the compiled lan card driver cannot perform in Gigabit transfer rate. 

Is there any tricky method to force the lan card transfer rate in 1000mbps instead of 100mpbs?

Patrick  [http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)

---

### Post by mmad on 2011-05-02
> **youngpatrick said:**
> I have installed Kubuntu 11.4 / 64 bits in my laptop HP DM-1 3000au and the built-in Realtek RTL8168 rev.6 gigabit lan card. The first thing I have downloaded the source file and compiled the correct lan card from Realtek web-site. I have also blacklisted the RTL8169 driver and success to load driver r8168 in system. 

The problem is my router Netgear WNDR3700 detect the lan signal in 100mbps instead of 1000mbps. The signal led indicator has blinked in amber color (100mbps signal) instead of green color (1000mbps). I have uploaded some files from NAS to my laptop using samba. The transfer rate read as below 8MB/s (I suppose the normal rate should read as over 20MB/s). That is I confirm the compiled lan card driver cannot perform in Gigabit transfer rate. 

Is there any tricky method to force the lan card transfer rate in 1000mbps instead of 100mpbs?

Patrick  [http://ubuntuforums.org/images/smilies/icon_razz.gif](http://ubuntuforums.org/images/smilies/icon_razz.gif)


It's funny you should post this, I had the same problem with the same drivers not two days ago. My problem was that the cat 5e cable I was using was incapable of the speed. Replacing it with a cat6e cable sorted everything. 

However to do some diagnostics:

install ethtool then run, **ethtool eth0** <assuming it is eth0> will tell you your supported and advertised link modes. If it says 1000base T/Full or 100baseT/Half then it means your driver is fine and your switch or cable is to blame.

---

### Post by roy.nico on 2011-09-13
Hello, 

i have the same problem, with my laptop Hp Touchsmart Tm2 2105. 
I installed the drivers 8168 from Realtek. It is loaded, and the command ethtool returns :

```
sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```

It looks like if it was in Gigabit modus. But a download test with another PC on my LAn under Windows shows a rate of 130 Mb.
The Hardware is ok, since the same test, with the sames PCs, but the laptop under Windows shows a download rate of app. 500Mb.

Quite depressing...

nicolas

---

### Post by roy.nico on 2011-09-15
hello . 

new test yesterday, with iperf. 
I get app. 600 Mbps !!

What is then the problem ? I tested the HD-speed with hdparm and get 
1700MBps and 80MBbs. So the problem is not the HD.

What else then ? 

nicolas

---

