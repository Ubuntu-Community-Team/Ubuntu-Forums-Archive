---
title: "Can't connect to broadband"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by Ryuzog on 2010-03-29
Just downloaded, worked fine with wireless, automatically detected but couldn't work with dorm broadband. I am completely new to this. I use broadband by paying for cards that give me a password and user code to connect. In windows I could right click broadband and input the things and connect. 

Tried it with Linux, couldn't find it, closest was mobile broadband which was 3g

long story short I don't have network manager anymore and I can't connEct to anything. This was sent from my iPhone.

So two issues: can't dl network manager bc not connected. Could surf wireless previously. 
Can't connect broadband wired.

---

### Post by Iowan on 2010-03-29
Post results (if possible) of **sudo lshw -C network** - that should give some idea of your interfaces.

---

### Post by Ryuzog on 2010-03-30
*-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:2f:d6:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:55100000-5510ffff
  *-network
       description: Ethernet interface
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:23:5a:f1:3c:f9
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:53000000-5303ffff ioport:1000(size=128)

copy and pasted through a usb.

for more information, I am a foreign student in china, cards are from China Unicom. Campus wired connections refuse all foreign websites, which is just strange b/c the campus wireless doesn't, dorm wire also doesn't.

---

### Post by Ryuzog on 2010-03-30
I also can't find "networking" in the administrations menu.

The only thing that has to do with networks there is "network tools".

I've tried all these:
[http://art.ubuntuforums.org/showthread.php?t=1418092&highlight=broadband+pppoe](http://art.ubuntuforums.org/showthread.php?t=1418092&highlight=broadband+pppoe)
[http://art.ubuntuforums.org/showthread.php?t=1402168&highlight=broadband+pppoe](http://art.ubuntuforums.org/showthread.php?t=1402168&highlight=broadband+pppoe)
[http://ubuntuforums.org/showthread.php?t=1308020&highlight=PPPoE](http://ubuntuforums.org/showthread.php?t=1308020&highlight=PPPoE)
[http://ubuntuforums.org/showthread.php?t=1308020&highlight=PPPoE](http://ubuntuforums.org/showthread.php?t=1308020&highlight=PPPoE)

I'm trying to figure out the one where I can input my username and password into the settings, but it says to click networking in administration, which just isn't there. It's the same for mint and netbook remix for me.

---

### Post by dineshs on 2010-03-30
PPPoE method is explained here
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by Ryuzog on 2010-03-30
I already tried that...being as that is the first thing that comes up in google.

I'm translating kuang dai as broadband, but I just saw something about dial up broadband, are they the same thing? 

The cards I buy come in speeds of 4 mbs and 8 mbs if that's useful...

username is f2009######## (some numbers...)
pass is 8 digits.

---

