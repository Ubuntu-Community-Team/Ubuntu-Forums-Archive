---
title: "trouble connecting to internet"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by dennisofnewport on 2012-09-10
Thank you for your help

I am using a netgear router to connect to the Internet.

O/p ubuntu 12
new motherboard gigabyte
new cpu AMD
old hard drive from older build

1) cannot connect to Internet when I come straight off my Time Warner modem.
2) Connects when I plug into the netgear modem

I am fearful the netgear router is about to fail and I am not sure why I can not connect straight from cable modem.

 When I use

O/p ubuntu 10.??

1) cannot connect to Internet at all.

Using o/p ubuntu 12 and this command.

lspci -v


02:00.0 Ethernet controller: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet (rev c0)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at fdec0000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at df00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

---

### Post by steeldriver on 2012-09-10
A couple of possibilities

1. cable modems are usually set up by the isp to only connect to a device with a specific MAC address (i.e. your router) - depending on the modem you may be able to force it to bind to the computer's MAC by some combination of power cycling / connecting the PC, or you may have to ask your ISP to reconfigure it from their side, or use MAC spoofing

2. the cable modem might not be providing DHCP service

---

