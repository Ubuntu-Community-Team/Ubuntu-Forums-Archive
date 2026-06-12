---
title: "Intel Wifilink 5300 always drops 802.11n connection"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by Agnaramasi on 2010-02-16
Following poohstickz's advice from [this thread]("http://ubuntuforums.org/showthread.php?p=8830925"), I enabled AES wireless security in my Netgear WNDR3700 router in order to achieve a 802.11n connection on my laptop with the Intel Wifilink 5300 adapter. Through the AES encryption my adapter was indeed able to connect at full wireless-n speeds, with NFS file transfer speeds measuring 10 MB/s (three times faster than before).
With this configuration, however, I also encountered a new, persistent problem: my wireless network connection would initially work, but then "drop" after anywhere from 10 seconds to 10 minutes or more. By "drop", I mean that my machine could no longer make network connections, either to the LAN (including the router itself) or WAN. The only way to resolve this is to reconnect to the network, at which time the process repeats itself.
As a result, I have had to change my encryption to TKIP and abandon the sweet, albeit short-lived 802.11n speeds.
I am not sure if the problem is related to the iwlagn driver, the router, or something else.  I am running Ubuntu 9.10 64 bit.  Any help would be most appreciated.

---

### Post by iponeverything on 2010-02-18
You might give 9.10 a try using the live CD/USB to see if the issue is related to something specific to 8.10.

---

### Post by Agnaramasi on 2010-02-18
Sorry for the ridiculous typo, but I actually am running 9.10.  Thanks for your help.

---

### Post by jorgerivera on 2010-02-18
I had a similar problem with a Linksys router today. I don't know if it has anything to do with the problem you're having with your Netgear.

I found that on very wifi-congested areas the "auto" channel setting tends to have the same effect you describe. In my case I used a Wifi Analyzer app (on my android phone) to find the cleanest channel and fixed the channel to it. It did fix my problem. 

Again, it might not be at all related, but it might be worth a try.

---

### Post by Agnaramasi on 2010-02-21
Jorgerivera, I'm not sure our problems are the same, as mine manifests on both 2.4ghz and 5ghz networks.  What software did you use to determine the optimum channel setting?

I have some more observations to share about the strange behaviour of my wireless connection.  The problem seems to apply to the 802.11n mode itself, rather than to the AES encryption that enables it. When I enable AES encryption but reduce the maximum speed of the wireless network from 300Mbps (presumably N) to 54Mbps (presumably ABG) in my Netgear firmware, the connection remains stable. The problem arises only on 802.11n connections. (I can confirm that these are genuine N connections because I can achieve NFS file transfer speeds of up to 12MBps before they crash.)

I also have more information about the frequency of these occurrences. The 802.11n connection can remain stable for sometimes up to a day or longer.  But the network connection invariably dies at some point, and then will repeatedly die almost immediately upon reconnecting to the wireless network until I change the router settings to prevent 802.11n connections altogether.

I have tried reloading the wireless drivers, restarting network-manager, rebooting my laptop, disconnecting all other machines from the network, and rebooting the router itself.  Nothing seems to solve the problem but preventing the 802.11n connecting from happening at all.

I would like to clarify that the problem is not that the wireless connection itself disconnects, but that network communication (both LAN and WAN) becomes impossible over the intact wireless connection. For instance, I cannot connect to the router at 192.168.1.1.

There does not seem to be any dmesg output related to these crashes. Any other logs I should check?

---

### Post by LordofPens on 2010-05-19
I seem to have the same problem as described by the others above.
[LIST]
[*] The router I'm using is the Linksys WRT160N
[*] My network card is the Intel WiFi Link 5300 (ThinkPad x200s)
[*] My OS is Ubuntu 9.10 i386
[/LIST]
My wireless network connection drops after about a day of connectivity. Changing from "Mixed" (802.11 B, G and N) to "BG Mixed" (802.11 B and G) in my router's wireless settings does not seem make a difference.

---

