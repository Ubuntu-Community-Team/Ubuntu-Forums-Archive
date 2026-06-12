---
title: "Wireless suddenly stops working on Eee PC 1018p, Ubuntu 11.10"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by ubarch on 2012-02-04
Hello,

  I just installed 11.10 on my Eee PC 1018p.  Wireless worked out of the box, but after about a day of operation, upgrades, being put into suspension and coming out again, it stopped working.  

  I have WEP enabled.  Instead of connecting to my router immediately, I see the wireless icon trying to connect for a minute or two before it prompts me for my WEP passphrase.  If I give it the passphrase (which it already had), it grinds for a while longer and repeats.

  Output of lspci:
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```  I enabled the Broadcom STA driver, and this didn't fix anything.  I'm not sure what else I can do-- Especially since I have no idea what changed which made the wireless system suddenly fail.

Any ideas?

---

