---
title: "No networking with Intel 6300"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by jhefferon on 2011-05-24
Hello,

I have a brand new HP Elitebook 8440w and have installed today's Ubuntu 11.  I can't get wireless to come up.

The page at 
  [http://www.linlap.com/wiki/hp+elitebook+8440w](http://www.linlap.com/wiki/hp+elitebook+8440w)
suggested getting a .tgz file and putting the .ucode in /lib/firmware so I guzipped it and copied that file to the directory (replacing a file there that was almost the same size).  Was that right?  In any event, it didn't make any difference that I can see.

Here are some diagnostics, in case they mean more to someone else than they do to me (which is a sure thing).

ifconfig shows eth0 and lo but no wlan0.

dmesg | grep iwl
[   11.289750] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   11.289752] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   11.289801] iwlagn 0000:44:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.289809] iwlagn 0000:44:00.0: setting latency timer to 64
[   11.289844] iwlagn 0000:44:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   11.306017] iwlagn 0000:44:00.0: device EEPROM VER=0x436, CALIB=0x6
[   11.306019] iwlagn 0000:44:00.0: Device SKU: 0Xb
[   11.306021] iwlagn 0000:44:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[   11.306107] iwlagn 0000:44:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   11.306186] iwlagn 0000:44:00.0: irq 43 for MSI/MSI-X
[   11.341049] iwlagn 0000:44:00.0: loaded firmware version 9.193.4.1 build 19710
[   11.348177] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

If anyone could shed some light then I would be very grateful.

Jim

---

### Post by chili555 on 2011-05-25
> rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]That suggests that the wireless switch on your computer is off. When you manipulate the switch, does the light or LED change? Please post:```
lsmod | grep wmi
```> Was that right? In any event, it didn't make any difference that I can see.Probably didn't make a difference. The firmware is installed by default. The specific firmware version is unlikely to make the switch move!

---

