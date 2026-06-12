---
title: "udev lists unknown MAC addresses"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by ridgerunner7 on 2009-10-17
I'm running Karmic (updated) which was installed clean using the beta iso.

I started on a quest to find out why Ubuntu tags my ethernet card with "eth2" instead of "eth0".

I discovered this in the kern.log:
[COLOR=Red]udev: renamed network interface eth0 to eth2[/COLOR]

After a bit of googling I learned that udev maps physical interfaces in /etc/udev/rules.d/70-persistent-net.rules. This is what mine contains:
[COLOR=Red]# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:3f:7e:ef:4b", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", N$

# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:12:f0:4c:dc:fc", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", N$

# PCI device 0x14e4:0x170c (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:b9:0a:b2:64", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", N$[/COLOR]

The correct one for my nic is the last one which must assign it "eth2" since 0 and 1 are already assigned by the previous rules. I'm perplexed because I only have one nic and I know for a fact there is no Intel wireless card has ever touched this box. I grepped kern.log for those first two MAC addresses but they are nowhere to be found...no surprise to me. No other nic card (usb, pci, etc) has been used since I installed karmic.

lspci only shows one nic which is my on-board nic:
[COLOR=Red]04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)[/COLOR]

My question:
What are those first two rules in 70-persistent-net.rules? Why are they in there?

---

### Post by ridgerunner7 on 2009-10-17
I did:

[COLOR=Red]sudo cp /etc/udev/rules.d/70-persistent-net.rules ./70-persistent-net.rule.backup
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo reboot[/COLOR]

Now my interface is eth0 (as I expect) and the wacky rules are gone. I suppose this means it is solved although I'm still perplexed how those rules appeared in the first place. I presume they were mistakenly left in there when the file was copied from the beta iso

---

