---
title: "Atheros Wifi fails intermittently"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by manthony121 on 2009-06-24
I have read many threads about the Atheros AR2413-related chipset having problems, but I have never seen this particular problem described:  SOMETIMES my laptop boots just fine, and at other times it fails to recognize the wifi chip: wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13). When this happens, I can reliably get Ubuntu to recognize the chip by booting into WinXP, letting XP connect to the wireless network, then rebooting into Ubuntu.  Sometimes just rebooting Ubuntu gets it to work, but the XP boot works every time.

I would like to get XP off my laptop entirely, but until the issue with wifi is resolved, I have to keep it.  It's a real pain to boot into Ubuntu, have the chip fail, reboot into XP, then boot into Ubuntu again.

My system is an Acer Aspire 3502wLCi laptop.
wifi chipset: Atheros AR2413 802.11bg NIC (as reported by 'lshw')
Ubuntu 8.04
madwifi, ath_pci 0.9.4, ath_hal 0.9.18.0

What would cause this erratic behavior?  Was it the position of the stars when I was born?  Any advice would be most appreciated.

---

