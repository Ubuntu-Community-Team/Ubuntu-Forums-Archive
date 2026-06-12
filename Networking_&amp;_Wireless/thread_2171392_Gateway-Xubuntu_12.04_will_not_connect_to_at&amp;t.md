---
title: "Gateway-Xubuntu 12.04 will not connect to at&amp;t u-verse wifi;connects w all other wifi"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by xgieryn on 2013-08-30
I have a gateway lt4004u netbook running Xubuntu 12.04 LTS (xfce4). I just hooked up at&t highspeed internet = u-verse, and all the other devices I've tried with it connect fine, but my netbook will only attempt over and over before disconnecting entirely. It also connects fine via the ethernet cable.

Already tried (and believe was successful) to install the b43 cutter through  b43-fwcutter-installer. Not sure if there is some setting that I do not have set correctly? Double checked obvos (eg ssid, WPA2 passcode). Not sure the IPv4/6 has anything to do with... Or if my mac address would be set correctly automatically [is C0:18:85:55:15:A6 (eth1)]

Please and thanks for help! 
-nn00bb

---

### Post by xgieryn on 2013-08-30
if useful: Results from [COLOR=#000000][FONT=Droid Sans]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:0624]
	Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e042]
	Kernel driver in use: wl

---

### Post by chili555 on 2013-08-30
Please see here: [http://ubuntuforums.org/showthread.php?t=2169844&highlight=4727](http://ubuntuforums.org/showthread.php?t=2169844&highlight=4727)

You have the same device and need the same fix.

---

