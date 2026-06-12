---
title: "Ethernet not reaching expected speed"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by zmr on 2010-09-13
I have been doing a variety of speed tests on my ethernet connection in preparation for upgrading my service and found that the connection on my dell d630 is not getting expected download speeds. In fact, it is getting about a third of the expected speed. This machine is running Lucid. It also dual boots Windows Vista. Checking Vista a moment ago, the speed is fine. What could be the problem that is preventing the ethernet from working at 100%?

---

### Post by zmr on 2010-09-13
If it helps, here is the output for "sudo ethtool eth0":

Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  Not reported
	Advertised pause frame use: No
	Advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: off
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
	Link detected: yes

The speed tests are from the following sites:
(1) [http://www.broadband.gov/qualitytest/mlabs.htm](http://www.broadband.gov/qualitytest/mlabs.htm) (U.S. FCC government site)
(2) [http://speedtest.comcast.net/](http://speedtest.comcast.net/) (Comcast Cable's speed site)
Both are reporting more or less the same download speeds. The average is are 8 Mb/s, while it should be around 20 to 22 Mb/s

---

### Post by BkkBonanza on 2010-09-13
It is not likely to be an ethernet problem. Probably something to do with the client - server interaction. I'm guessing this since you don't have the issue under Windows and they are both running on the same physical connection. 

Try using a different program to test and see if the rate varies. 
eg. from a terminal try using,

wget [http://www.broadband.gov/qualitytest/mlabs.htm](http://www.broadband.gov/qualitytest/mlabs.htm)

and see how that compares. (If wget not found then, sudo apt-get install wget).

Also, transfer rates can vary a lot depending on ISP network traffic so you have to test really at the same time on both systems.

---

### Post by MaindotC on 2010-09-14
The real method to test transfer rate is to do it locally - like from machine to machine.  Plug in a cable between two desktop's or whatever you have, assign them different IP addresses on the same subnet, and try transferring a large file between them using FTP.  Of course whichever protocol you use will also factor into the maximum throughput.

---

### Post by zmr on 2010-09-14
Thanks for the replies. I've gone ahead and cleared the whole disk and did a fresh install using Meerkat. The problem is now fixed although without having found out what caused it. I am wondering if it had anything to do with any of the various server / host configurations I set up over a year or two of using apache and a few other client-server setups locally. No idea really. In the end, clearing off the dual boot system was for the best as there was no reason to keep the Vista partition around any longer.

---

### Post by endotherm on 2010-09-14
glad you got it working. 
just for academics, I did notice that your nic is gigabit, but running at Mb. if you have a gigabit switch, then the problem is likely that you have cabling with less than cat5e certification. otherwise everything lo oks fine. in my part of the world, internet access speeds are far far below 100Mb, so this kind of diagnostic would not be useful for determining the cause of internet slowness.

---

### Post by MaindotC on 2010-09-14
> **zmr said:**
> Thanks for the replies. I've gone ahead and cleared the whole disk and did a fresh install using Meerkat. The problem is now fixed 

This is not how problems in Ubuntu are resolved.  I know you tried and it probably was much less time consuming to just start over but a network issue usually is either a driver or a configuration file.  I'm glad you have what you want now, so you can experience the full benefits of using Ubuntu, but in the future hopefully we can help you more to resolve the matter.  

Also keep in mind that 10.10 is in development phase - you may want to consider reporting this issue on the [Maverick Testing & Discussion](http://ubuntuforums.org/forumdisplay.php?f=385) sub forum.

---

### Post by zmr on 2010-09-14
strAlan-- understood. It would have been nice to resolve this directly and learned something in the process. Next time I guess.

endotherm - i appreciate the academic feedback. Fortunately, I think the cat5e cables are working fine and in good condition.

---

