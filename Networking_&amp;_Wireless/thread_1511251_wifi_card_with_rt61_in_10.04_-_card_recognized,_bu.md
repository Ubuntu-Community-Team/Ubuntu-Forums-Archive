---
title: "wifi card with rt61 in 10.04 - card recognized, but wont connect"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by pedro1984 on 2010-06-16
Hi,

I just bought some hardware to build a computer. Of course making sure everything was compatible with Ubuntu 10.04.

Everything is working great, except my wireless card.....i guess that shouldnt be a suprise though. The card is a Rosewill RNX-g300lx.  I got it off newegg as the reviews mentioning it was working well in 10.04. And supposedly it has the rt61 chipset.

So here's some info to help troubleshoot.
-Installed Ubuntu from CD then did updates (over LAN)
-Network Manager sees the card and can see wireless networks.
-Tried to connect to my network (DD-wrt router, WPA2 TKIP) but after prompting for the key and trying to connect for a couple minutes, it prompts for the key again.  Same cycle over and over.
-I can connect to my neighbors wireless (linksys, no encrypt) 
-I've tried setting my router to no encrypt, but with no luck
-Other window XP machines & Macs connect fine to my router
-running lspci shows the wifi card using rt61 driver
-i uninstalled NM and replaced with wucid, but with no luck.  It didnt see the card at all

I hope some of this info can help troubleshoot the problem.

Thanks in advance,

Pedro

---

