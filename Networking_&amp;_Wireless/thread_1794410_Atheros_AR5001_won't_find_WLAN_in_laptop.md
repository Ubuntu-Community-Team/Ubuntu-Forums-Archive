---
title: "Atheros AR5001 won't find WLAN in laptop"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by enetrez on 2011-07-01
[LEFT]Hey folks, absolute beginner here. I had NEVER used a Linux OS before, but I got really tired of Fuckindows and decided to do drugs... which means getting a new OS = Linux. I chose Ubuntu for apparently being the most simple one for beginners, and the one about which I found the biggest number of forums. I installed it two days ago and that was my first contact with it ever.[/LEFT]
 
[LEFT]So, brief story, this is it, I know nothing. It is installed and everything seems to be working perfectly except for the wireless internet. I've already looked for other threads with the same problem I have but none really solved mine, so I've created this one.[/LEFT]
 
 
[LEFT]ENOUGH OF TALKING![/LEFT]
 
[LEFT]The laptop is a HP Pavillion g60, the Ubuntu version is 11.04 dated April 2011. The wireless switch is turned on and the internet router is working perfectly (I'm posting this from my dad's VAIO w/ W7).[/LEFT]
 
[LEFT]Here is the log from the commands the "Help and Support" docs told me to do. Is there anything else I should paste here to help you doctors diagnose my sickness? Looking forward to hear from you, thanks anyway.[/LEFT]
 
 
 
[LEFT]moises@Dantas:~$ nm-tool
NetworkManager Tool
State: disconnected
- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: forcedeth
State: unavailable
Default: no
HW Address: 00:1F:16:DF:3B:54
Capabilities:
Carrier Detect: yes
Wired Properties
Carrier: off[/LEFT]
 
[LEFT]- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: ath5k
State: unavailable
Default: no
HW Address: 00:24:2C:9C:CD:95
Capabilities:
Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes
Wireless Access Points [/LEFT]
 
[LEFT]moises@Dantas:~$ sudo lshw -C network
[sudo] password for moises: 
*-network 
description: Ethernet interface
product: MCP77 Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:1f:16:df:3b:54
capacity: 100Mbit/s
width: 32 bits
clock: 66MHz
capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
resources: irq:41 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
*-network DISABLED
description: Wireless interface
product: AR5001 Wireless Network Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:07:00.0
logical name: wlan0
version: 01
serial: 00:24:2c:9c:cd:95
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
resources: irq:23 memory:c2000000-c200ffff[/LEFT]

---

### Post by Dangertux on 2011-07-01
Welcome to the forum,

I had this problem the other day on my wife's laptop. I was able to come to a reasonable solution (it will still disconnect randomly but reconnects shortly after automagically ;-) )

I posted my solution to it at the end of this thread.

[http://ubuntuforums.org/showthread.php?t=1790779](http://ubuntuforums.org/showthread.php?t=1790779)

Hopefully it works for you as well.

---

### Post by enetrez on 2011-07-13
Hey Dangertux,

Thanks for your immediate response. I tried basically everything you posted there but it still doesn't work. I also tried ndiswrapper and a few other things I can't really remember because of the so many things I tried...

One thing that happened and I find really weird is that my laptop has a WLAN button to turn it on/off. Before, it was blue (ON) and wouldn't turn off. After I installed ndiswrapper it became orange (OFF) and now it won't turn ON...

Still trying.

---

