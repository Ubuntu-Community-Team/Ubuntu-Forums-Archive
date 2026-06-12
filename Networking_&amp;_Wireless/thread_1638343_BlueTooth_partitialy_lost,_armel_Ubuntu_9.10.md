---
title: "BlueTooth partitialy lost, armel Ubuntu 9.10"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by Gourmand on 2010-12-05
Ubuntu 9.10 on ARM handheld trying connect to desktop running WinXP, Widcomm BT adapter and driver. This desktop tethers BT PAN for notebook with Kubuntu 10.10 as well. Handheld connects to cellular phone Nokia and can get DUN as well too. Even OBEX file transfer works between handheld and desktop. 

But when I try connect handheld to desktop and use one of "permanent" services - connection fails after several seconds. No one service like COM, network sharing, A2DP, keyboard/mouse - no one connects. sudo hcitool cc <address> - BT indicator on XP just turns on then off. No mconnection, no messages, nothing.

$sudo hciconfig hci0 lm

hci0: Type USB
BD <address> ACL MTU: 310:10 SCO MTU: 64:8
Link mode: SLAVE ACCEPT

BlueTooth works...

I use Blueman 1.03 on handheld (it's hard to upgrade without I-net connection). But I tried HCI command line tools with same result - no error messages, no connection.

I looked at dmesg - looks like BlueTooth works well.

But this WORKED for first time. Some days I was able connect handheld to desktop and there was I-net access using bnep0 on handheld. 

What can be wrong with BlueTooth in Ubuntu? I believe hardware on both sides works fine. I believe software on desktop works fine too cause notebook gets PAN over BT.

---

