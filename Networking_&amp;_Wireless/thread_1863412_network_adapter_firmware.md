---
title: "network adapter firmware"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by sabatron on 2011-10-17
im currently using ubuntu via usb stick on my mom's laptop.  she has a dell latitude d410. i am connected via ethernet cord now but i can not connect wirelessly.  ubuntu is telling me i need firmware. i tried to have the OS find the driver via "additional drivers" but it says that there are no propriety drivers or something to that effect.  the network card i believe is the last line of code here:

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
02:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)

any ideas?  i found it online through the dell site but its an .exe so i cant update it that way.  helppppppppp pleaaaaaaaasse

*edit:  i am using the newest version of ubuntu right now.  and im also startign to think that maybe her wireless card is not supported?  i just looked at the wiki and it is not there.  there are broadcom cards on there but it is strictly 4300 series stuff

---

### Post by wildmanne39 on 2011-10-17
Hi, if you are using a persistent usb and you have enough room on it then do this please:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
When it is done disconnect your wired connection and do this:
```
sudo modprobe b43
```
if it works would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

