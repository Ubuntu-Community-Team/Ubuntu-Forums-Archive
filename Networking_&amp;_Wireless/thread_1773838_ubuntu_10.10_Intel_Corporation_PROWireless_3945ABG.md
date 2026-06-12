---
title: "ubuntu 10.10 Intel Corporation PRO/Wireless 3945ABG deactivated?"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Briped on 2011-06-02
I'm somewhat nonplussed here. The Intel Corporation PRO/Wireless 3945ABG card doesn't scan for networks. This happened after installing heaps of updates, but I'm far from sure these have anything to do with it.

dmesg | grep iwl
[ 19.770184] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[ 19.770189] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[ 19.770375] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 19.770391] iwl3945 0000:05:00.0: setting latency timer to 64
[ 19.824472] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[ 19.824476] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[ 19.824631] iwl3945 0000:05:00.0: irq 44 for MSI/MSI-X
[ 19.833727] phy0: Selected rate control algorithm 'iwl-3945-rs'

rfkill list all:
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes

I have tried:
1/ toggling network card on/off (Fn + F8 )
2/ rebooting using older kernels
3/ booting up on pinguy (usb stick)
4/ booting up the old win xp partition, which should work as I haven't installed updates or altered any settings.

No luck. Before installing all the updates everything worked fine, but that's probably coincidental.
Anybody has any bright ideas, please? It's an old Toshiba Satellite.

Thanks a lot,
Britta

---

