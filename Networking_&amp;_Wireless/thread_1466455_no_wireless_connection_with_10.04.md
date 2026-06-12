---
title: "no wireless connection with 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by groundnut on 2010-04-30
Today installed Ubuntu 10.04.

The problem is that I cannot connect to the internet, which was no problem with the previous version (9.10).

I use WiFi for my internet connection.
My network is shown in Ubuntu. However Ubuntu cannot connect to my network. After some time trying it says : wireless network disconnected

How can I resolve this problem?

---

### Post by bobbybiceps on 2010-04-30
I'm having the same problem.  I upgraded to 10.04 on both my desktop and notebook, lost wireless connections on both.  Cannot figure out how to connect.  I have a Linksys wireless n router - everything was working OK before the upgrade.

---

### Post by bkratz on 2010-04-30
> **bobbybiceps said:**
> I'm having the same problem.  I upgraded to 10.04 on both my desktop and notebook, lost wireless connections on both.  Cannot figure out how to connect.  I have a Linksys wireless n router - everything was working OK before the upgrade.




You both might want to go here and see what type of information is usually necessary.

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by groundnut on 2010-04-30
I tried again a couple of hours later. Then I got a connection. I did not change anything. So problem solved!

Thanks anyway bkratz,

---

### Post by bobbybiceps on 2010-04-30
Well, stupid me - there seems to be a box to check that says "make available to all users" when configuring the wireless connection; I checked this box and it is now working OK on my desktop - haven't tried my laptop yet.  Is this something that was added to 10.04?

---

### Post by anthtony1967 on 2010-04-30
I am having the same problem and tried that with no luck.  Any other ideas?

---

### Post by bobbybiceps on 2010-04-30
well, I spoke too soon.  It is now not working again.  I sometimes get connected then sometimes it will not connect.  Very haphazard.  Looks like network manager needs some work done on it.

---

### Post by frenchiewhite on 2010-05-01
got the same problem :(



 *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:93:bc:8c
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.41 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fbfc0000-fbffffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:43:5d:51:d6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fbef0000-fbefffff


thx a lot for your help

---

### Post by ctbarker32 on 2010-05-01
Hi. 

I have written up a tutorial specifically aimed at getting the Ralink RT2860 chipset working with wifi, WPA security, and Ubuntu 10.04. I think I have made it understandable for the novice. I am not a Linux expert by any means so that's where I'm coming from. 

Hope this helps.

[RT2860 and Ubuntu 10.04 wireless tutorial]("http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html")

-CB

---

### Post by marclurr on 2010-05-01
Thanks for your reply but the link you supplied appears to be broken :(

edit: Ignore, posted in the wrong thread :|

---

### Post by Songwind on 2010-05-05
CB:

Thanks for the tutorial.  It was quite clear.  You might want to include a link to a page on how to install Build Essentials for the inexperienced.

I got my eeePC back online without a hitch.

Eric

---

### Post by Sven6210 on 2010-05-07
The link is not broken but blocked by internet filters in some years, e.g China. I had the same problem and used a VPN connection in order to open the webpage. I also posted the manual here:

[http://ubuntuforums.org/showthread.php?p=9255730](http://ubuntuforums.org/showthread.php?p=9255730)

---

