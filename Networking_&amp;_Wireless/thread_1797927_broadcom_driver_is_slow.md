---
title: "broadcom driver is slow"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by sky5564 on 2011-07-05
So i just installed ubuntu 10.10 on my new acer laptop

my laptop is a - Acer Aspire 5253-BZ893

lscpi -v is below.

```
06:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0520
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0200000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: <access denied>

07:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
	Subsystem: Foxconn International, Inc. Device e021
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at d0100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl

```

On windows 7 this laptop is blazing fast but when im using ubuntu youtube videos dont load fast and download speeds are lackluster at best.

Anyone know what the deal is with this driver?

---

### Post by sky5564 on 2011-07-06
I put my router in wireless N mode this helped speeds slightly but its still slow.

I figure im getting wireless B speeds on a wireless N connection..:confused:

---

### Post by sky5564 on 2011-07-07
I noticed when i installed ubuntu that ubuntu is using the propriatry STA driver by default.

it says this about the driver - "These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware."

iwconfig shows -```
eth0      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:213  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

oddly enough i am actually associated with an AP and connected to the internet, so i have no idea why it is saying "access point not associated"

I dont even know what driver this thing is actually using.

---

