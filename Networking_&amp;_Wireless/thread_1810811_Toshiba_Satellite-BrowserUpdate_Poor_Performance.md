---
title: "Toshiba Satellite-Browser/Update Poor Performance"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by MrFingerz on 2011-07-23
I am dual booting Bodhi Linux on a Toshiba Satellite L30-10S, the other OS is Vista.

The problem I'm having is with browsing and updates. I have used both Chrome and Firefox and the same problem occurs. Some web pages take what seems like forever to load and some don't load at all. Updating via the terminal hangs and also via synaptic. It's like some sites are blacklisted. HTTPS pages wont load at all.

I can see by searching that I'm not the first person to have a problem with a Toshiba and Linux wireless. Usually though it seems that people have had the problem where it wont have any wireless connection at all. If using a wired connection, it's fine. The output of lspci is below.

00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

Any ideas appreciated.

Regards

MrFingerz

---

### Post by MrFingerz on 2011-07-25
Incidentally, I have ran Ubuntu lts, Mint and PCLinux from live cds on the laptop and the behavior of the browser is the same.

---

### Post by swedenfox on 2011-07-30
i solved with madwifi 
same card here satellite l30-10x
Atheros Communications Inc. AR2413

[http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)

---

