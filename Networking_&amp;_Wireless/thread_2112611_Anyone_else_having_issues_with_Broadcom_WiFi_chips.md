---
title: "Anyone else having issues with Broadcom WiFi chips?"
date: 2013-02-05
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2013-02-05
I just wanted to check out whether there's just me, or anybody else is experiencing this...
My setup: A Dell Studio 1555 laptop with a Broadcom Wifi chip:
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

So I use the Broadcom STA driver, and it is recognized and presumably working fine. I even didn't have any issues with the driver when I made the distribution upgrade from 11.20 to 12.04. The driver was just working. BUT... I noticed that it has issues.
The most frustrating one is that it breaks connection (roughly after the second rekeying with the AP, which is about every couple of hours), and when I test the speed I get only 5Mbps throughput even though I'm the only user connected to that AP :confused:
And the AP is able to achieve more, I know it, because I tested it with my DWA131 wifi adapter and it gets about 20Mbps, which is a lot more satisfactory. 
So anyone else noticed this issues with the BCM4312 chip running the STA driver on Ubuntu 12.04? Or is it just me :guitar:

---

### Post by lz1dsb on 2013-02-05
Bump...
I can't believe I'm the only Dell customer running Ubuntu who has experienced this :D

---

