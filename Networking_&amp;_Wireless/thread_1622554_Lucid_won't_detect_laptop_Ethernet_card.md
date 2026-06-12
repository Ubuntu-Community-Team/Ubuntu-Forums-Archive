---
title: "Lucid won't detect laptop Ethernet card"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by white-seraph on 2010-11-15
Hi everyone,
 
so, when i first got my laptop it came with vista and the ethernet worked fine, then when I decided to install Karmic about 9 months ago it still worked fine. After a while the update for lucid came out so I upgraded to that and then the ethernet started getting buggy. It would only work about half the time that i wanted it too and the other half of the time it would just stare at me and not move anywhere. So along with a couple other bugs I decided to format my harddrive and downgrade back to karmic and await the 10.10 release. unfortunatly my ethernet woes carried with me and they still would only show up on occasion.
then about half way through my time with karmic round 2 it stopped altogether, and with the upgrade back to lucid it hasn't seemed to solve itself.
 
I ran through ifconfig -a, lspci and sudo ifup -a but they all tell me that the device doesn't exist.
 
anyhelp would be appreciated because we recently switched to an entirely hardlined home and I'd like to use my laptop again.
 
-WS

---

### Post by uncaspi on 2010-11-15
Will you please post sudo /sbin/lshw -C network and dmesg

---

### Post by white-seraph on 2010-11-15
thanks for the reply,

heres the lshw -C network:

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:15:08:70
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 ip=192.168.1.66 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:f4000000-f4000fff

and the dmesg is in the attachment for convenience.

---

### Post by uncaspi on 2010-11-15
The link is ready according to dmesg.

ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

What do you get from sudo /sbin/iwlist scan

and rfkill list

---

### Post by uncaspi on 2010-11-15
Sorry. It's the ethernet card and not the wireless you have problems with. No it doesen't show up in dmesg either. Lets see if it's in the hardware listing if you post. sudo /sbin/lshw -C network

---

### Post by white-seraph on 2010-11-15
Yeah, I posted the lshw, all that showed up for network was the wireless card.anything for the ethernet doesn't show up anywhere in it. and I know the card is getting power because when I plug in a cable it lights up.

---

### Post by uncaspi on 2010-11-16
Seems to me that it is something wrong with the hw since you tried so many versions of ubuntu and it not shows up in lshw.

---

