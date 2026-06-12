---
title: "Atheros card worked on 6.06 livecd but stopped working when I upgraded from badger"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by beepboop on 2006-06-04
The atheros based  pcmcia card was working on the lived and in badger.
I did dist-upgrade, but had to turn off my laptop during the install.
I am having a few problems with gnome, but I can fix them easily if I can get back online.

lshow output:
*-network UNCLAIMED
description: ethernet controller
product: atheros Communications, Inc
Physical id: 2
bus info: pci@05:00.0
version 01
width 32bits
clock 33mhz
capabilities cap_list
resources: iomemory:5000000-500ffff irq:10

I am pretty sure I have the module, but I am not sure how to proceed from here. I dont want to use ndiswrapper, as this has a native linux driver that works well.

Thanks in advance

edit:got it to show up using modprobe ath_pci
edited /etc/network/interfaces with
auto ath0
iface ath0 inet dhcp
wireless-essid NETGEAR

Still cant get on :/

Tried using iwconfig to set the channel, ssid, ap MAC and rate.

Looking forward to your replies in the morning :)

Got this working using the network manager, but I would really like to know why it didnt work to begin with.
Maybe because I didnt set the enc type to off?

---

