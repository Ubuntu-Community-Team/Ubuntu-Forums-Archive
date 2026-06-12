---
title: "ath9k wireless errors with 2.6.38/2.6.39"
date: 2011-08-18
forum: Networking &amp; Wireless
---

### Post by Xylian on 2011-08-18
Hi,
after the upgrade to kernel 2.6.38 I'm experiencing a lot of problems with my ath9k wireless driver... I'm using this driver on my home server, which is used as access point also with the following wireless mini-pci card:
```

00:0e.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
        Subsystem: Atheros Communications Inc. Device 2096
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 168, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 5
        Region 0: Memory at effd0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=100mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

After downloading some MBs (file transfers or video streaming or whatever else) from the home server with my laptop, the following errors appear:

```

ath: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x42000020 DMADBG_7=0x00006040
ath: Could not stop RX, we could be confusing the DMA engine when we start RX up

```

or

```

ath: Failed to stop TX DMA!
Aug 18 23:17:00 ubuntu-alix-server kernel: [1766351.872539] ath: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x42000020 DMADBG_7=0x00026040

```

I've created a background-running script that checks for this error in the syslog and restarts the hostapd daemon when the error happens... did any of you experienced the same error? I'm running the following kernel and I tried both with the stock ath9k and the back ported (from 2.6.39) ath9k driver:

```

# uname -r
2.6.38-10-generic

# modinfo ath9k
filename:       /lib/modules/2.6.38-10-generic/updates/cw-2.6.39/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     E294464C8E7A07D31B8967B
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,cfg80211,ath9k_common,ath
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

```

Do you think it's an ath9k driver issue or may it be related to hostapd?

Thank you in advance for any help!

---

### Post by chili555 on 2011-08-18
> Do you think it's an ath9k driver issueYes. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/736171)

See post #32 and its link.

---

