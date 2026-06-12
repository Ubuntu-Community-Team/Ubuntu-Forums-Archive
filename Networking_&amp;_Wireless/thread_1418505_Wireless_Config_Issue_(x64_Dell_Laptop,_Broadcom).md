---
title: "Wireless Config Issue (x64 Dell Laptop, Broadcom)"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by noloader on 2010-02-28
Hi All,

Dell Studio S1555 laptop, x64. Neither the BCM STA or B43 drivers work. B43 seems to do the best, except that it never connects to the AP.

Any help would be appreciated. Searching for the the terms that are present in the logs returns surprisingly few results. There must be others who have suffered also.

Jeff

BCM STA driver logging
================
dpkg.log:
2010-02-28 16:23:35 startup packages configure
2010-02-28 16:23:35 configure bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4 5.10.91.9+bdcom-0ubuntu4
2010-02-28 16:23:35 status half-configured bcmwl-kernel-source 5.10.91.9+bdcom-0ubuntu4
jockey.log:
2010-02-28 16:23:28,767 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
2010-02-28 16:23:33,879 DEBUG: Installing package: bcmwl-kernel-source
2010-02-28 16:23:34,907 DEBUG: install progress statusChange dpkg-exec 0.000000

B43 driver logging
============
debug.log:
Feb 28 16:34:28 studio kernel: [ 1028.095670] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
Feb 28 16:35:00 studio kernel: [ 1059.667835] tg3 0000:08:00.0: irq 30 for MSI/MSI-X
kernel.log:
Feb 28 16:34:28 studio kernel: [ 1028.070247] cfg80211: Calling CRDA to update world regulatory domain
Feb 28 16:34:28 studio kernel: [ 1028.095274] cfg80211: World regulatory domain updated:
Feb 28 16:34:28 studio kernel: [ 1028.095277]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 28 16:34:28 studio kernel: [ 1028.095280]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 16:34:28 studio kernel: [ 1028.095283]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 28 16:34:28 studio kernel: [ 1028.095285]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb 28 16:34:28 studio kernel: [ 1028.095288]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 16:34:28 studio kernel: [ 1028.095290]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb 28 16:34:28 studio kernel: [ 1028.095647] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Feb 28 16:34:28 studio kernel: [ 1028.095670] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
Feb 28 16:34:28 studio kernel: [ 1028.220421] ssb: Sonics Silicon Backplane found on PCI device 0000:04:00.0
Feb 28 16:34:28 studio kernel: [ 1028.227272] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
Feb 28 16:34:28 studio kernel: [ 1028.320327] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
Feb 28 16:34:28 studio kernel: [ 1028.320393] b43: probe of ssb0:0 failed with error -95
Feb 28 16:34:28 studio kernel: [ 1028.320440] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
Feb 28 16:35:00 studio kernel: [ 1059.642917] tg3 0000:08:00.0: PME# disabled
Feb 28 16:35:00 studio kernel: [ 1059.667835] tg3 0000:08:00.0: irq 30 for MSI/MSI-X
Feb 28 16:35:00 studio kernel: [ 1059.833619] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 28 16:35:34 studio kernel: [ 1094.037063] tg3 0000:08:00.0: PME# disabled
Feb 28 16:35:34 studio kernel: [ 1094.052985] tg3 0000:08:00.0: irq 30 for MSI/MSI-X
Feb 28 16:35:34 studio kernel: [ 1094.199985] ADDRCONF(NETDEV_UP): eth0: link is not ready

Also (but I don't know which driver is doing it):
Feb 28 16:20:10 studio kernel: [  170.238811] modinfo[1901]: segfault at 2f ip 00007f7a16977a87 sp 00007fff487308f0 error 4 in libc-2.10.1.so[7f7a1692f000+166000]
Feb 28 16:20:11 studio kernel: [  171.259655] modinfo[1909]: segfault at 2f ip 00007f96c7dfca87 sp 00007fff368d0080 error 4 in libc-2.10.1.so[7f96c7db4000+166000]
Feb 28 16:20:11 studio kernel: [  171.263552] modinfo[1910]: segfault at 2f ip 00007fed0af62a87 sp 00007fff67253bb0 error 4 in libc-2.10.1.so[7fed0af1a000+166000]

---

### Post by noloader on 2011-03-01
Ubuntu 9.x never worked with the S1555 laptop. For Ubuntu 10.x, I could use the STA driver with Dell's A09 BIOS. When the BIOS was upgraded to A12, I had to use the B43 driver with its updated firmware.

---

