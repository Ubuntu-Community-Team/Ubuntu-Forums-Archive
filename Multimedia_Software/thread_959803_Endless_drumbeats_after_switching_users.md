---
title: "Endless drumbeats after switching users"
date: 2008-10-26
forum: Multimedia Software
---

### Post by ragtag on 2008-10-26
I'm not sure exactly when this happens, but sometimes when switching users (one using the Fast User Swithc and other using Quit... and then switch users), the login drumbeat keeps playing forever after login at 1 second intervals.

This does not happen every time I switch users, only every now and then. The sound will keep playing even if I switch back to the previous user. When it happened just now, the user I switched from crashed (was no longer logged in...though there were still leftover processes I had to kill), though I don't think that has happened every time.

I'm using PuleAudio and Hardy Heron. Output from lspci looks like this:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller
00:1e.0 ISA bridge: ALi Corporation PCI to LPC Controller (rev 31)
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:1f.1 RAID bus controller: ALi Corporation ULi 5287 SATA (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 19)
03:12.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

Any ideas on this?

---

