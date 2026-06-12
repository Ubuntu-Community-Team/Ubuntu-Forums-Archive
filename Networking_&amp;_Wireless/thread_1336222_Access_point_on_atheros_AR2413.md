---
title: "Access point on atheros AR2413"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by stasheck on 2009-11-24
Another non-standard problem.

I run multiple-uses Linux box: TV, movies, router, SMB and AP. The interesting part is Access Point.

I created it using madwifi drivers, and it's working fine. Except.

Recently I bought Asus R50A. It runs Windows7, and it's wireless card is Marvell SDIO one.

The problem is that when Asus connects to my AP, I get dreaded "missed beacon" bug - which is, from what I read, unsolvable.

So, the question is: are there any other drivers I can create AP on?

The hardware:
04:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

---

### Post by stasheck on 2009-11-30
OK, found that ath5k+hostapd (+kernel >2.6.31) is supposed to work. Only problem, there's no usable howto.

So, please - does anyone know of one?

---

### Post by stasheck on 2009-11-30
This [http://bobcopeland.com/blog/2009/11/ath5k-ap-mode/](http://bobcopeland.com/blog/2009/11/ath5k-ap-mode/) worked flawlessly. All thanks to blog's author :-)

---

