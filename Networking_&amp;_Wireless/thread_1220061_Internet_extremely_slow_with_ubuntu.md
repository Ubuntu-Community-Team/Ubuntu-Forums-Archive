---
title: "Internet extremely slow with ubuntu"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by vmanisme on 2009-07-22
I have FiOS and my speeds average about 65000kbps on Windows 7 in Ubuntu my speeds are .50-4kbps same thing with my upload speeds...

I did _sudo ethtool eth0_ maybe it will somehow help...

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: Unknown! (65535)
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: no

MY WIRELESS CARD:  Realtek RTL8187B

---

### Post by martinbaselier on 2009-07-22
The output shows the lan is not connected. For the rtl8187B you might take a look in this thread:

[http://ubuntuforums.org/showthread.php?t=1199271](http://ubuntuforums.org/showthread.php?t=1199271)

At least you can connect to the wlan. It helps if you change the speed to 11mbps.
**sudo iwconfig wlan0 rate 11M**

Mine won't even connect if I don't do that.

---

### Post by vmanisme on 2009-07-22
Yea I looked at that topic it didn't help at all so I'm back on Windows and formating my Ubuntu portion in a day or 2 if I dont get my hibernate/suspend and this internet issues fixed... Heres the speed results I get its ridiculous...  I fell in love with Ubuntu and it has to do that crap to me...

**THIS IS WITH WINDOWS 7**

[[IMG]http://www.speedtest.net/result/520214886.png[/IMG]](http://www.speedtest.net)  

**THIS IS WITH UBUNTU 9.04 (SAD:()**

[[IMG]http://www.speedtest.net/result/522927527.png[/IMG]](http://www.speedtest.net)

---

### Post by Arup on 2009-07-22
Did you set your MTU, in my case with Realtek 8168, I get way better speeds than Vista or 7.

---

### Post by iAmRedempting on 2009-07-22
> [B]
THIS IS WITH UBUNTU 9.04 (SAD:()[/B]

[[IMG]http://www.speedtest.net/result/522927527.png[/IMG]]("http://www.speedtest.net")

Consider yourself lucky. I'm lucky if I even reach 1MB download and 20KB/s upload.

---

### Post by vmanisme on 2009-07-22
> **Arup said:**
> Did you set your MTU, in my case with Realtek 8168, I get way better speeds than Vista or 7.

I'm on Realtek RTL8187B not 8168

---

### Post by vmanisme on 2009-07-22
> **iAmRedempting said:**
> Consider yourself lucky. I'm lucky if I even reach 1MB download and 20KB/s upload.

I cant use Ubuntu because I cant even stream anything... its really sad this issue has been brought up since Ubuntu 7.xx and nobody took this seriously its been like 3 years... Same thing with hibernating/suspending the computer... Ive been trying to get a moderator to pay attention to that issue for almost 2 years now... I'm running 1200watt power supply if I cant put my computer to sleep my electric bill will be like $600... Windows here I come...!

---

