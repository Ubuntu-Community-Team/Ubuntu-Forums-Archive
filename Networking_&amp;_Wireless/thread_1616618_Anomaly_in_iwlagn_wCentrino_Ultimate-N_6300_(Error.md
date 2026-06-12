---
title: "Anomaly in iwlagn w/Centrino Ultimate-N 6300 (Error sending */No space for Tx)"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by dendroid on 2010-11-08
Hello, iwlagn is working great for my Dell Latitude E6510 with a Centrino adapter, but I just had a strange interruption. NetworkManager saw it as a disassociation and couldn't re-associate. nm-applet spun for a while and prompted me for the key a few times. I saw this in dmesg (just a lot of the same thing over and over again):

```

[ 3839.768384] NVRM: os_raise_smp_barrier(), invalid context!
[ 3839.783114] NVRM: os_raise_smp_barrier(), invalid context!
[ 3849.410342] NVRM: os_raise_smp_barrier(), invalid context!
[ 3849.426963] NVRM: os_raise_smp_barrier(), invalid context!
[ 3858.989739] iwlagn 0000:03:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 3858.989746] iwlagn 0000:03:00.0: set power fail, ret = -110
[ 3861.483586] No probe response from AP 00:12:17:01:91:e3 after 500ms, disconnecting.
[ 3862.211789] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3862.211796] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3862.710555] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 3863.209327] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3863.209333] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3863.708088] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3863.708093] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3868.196990] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3868.196994] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3868.695739] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 3869.194564] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3869.194571] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3869.693275] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3869.693282] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3874.182259] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3874.182265] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3874.681031] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[ 3875.179800] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3875.179805] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3875.678573] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3875.678580] iwlagn 0000:03:00.0: Error setting new RXON (-110)

... snip ...

[ 3886.822840] NVRM: os_raise_smp_barrier(), invalid context!
[ 3886.838648] NVRM: os_raise_smp_barrier(), invalid context!
[ 3887.150273] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[ 3887.150279] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[ 3887.150289] iwlagn 0000:03:00.0: No space for Tx
[ 3887.150292] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[ 3887.150295] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[ 3887.150304] iwlagn 0000:03:00.0: No space for Tx
[ 3887.150307] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[ 3891.639996] iwlagn 0000:03:00.0: No space for Tx
[ 3891.640004] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28

```rmmod/modprobe of iwlagn fixed everything:

```

[ 4013.210222] iwlagn 0000:03:00.0: PCI INT A disabled
[ 4016.818524] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 4016.818527] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 4016.818629] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4016.818684] iwlagn 0000:03:00.0: setting latency timer to 64
[ 4016.818817] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 6000 Series 3x3 AGN REV=0x74
[ 4016.846155] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 4016.846227] iwlagn 0000:03:00.0: irq 36 for MSI/MSI-X
[ 4016.847431] phy1: Selected rate control algorithm 'iwl-agn-rs'
[ 4016.853918] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-6000-4.ucode
[ 4016.855954] iwlagn 0000:03:00.0: loaded firmware version 9.221.4.1
[ 4017.165280] Registered led device: iwl-phy1::radio
[ 4017.165303] Registered led device: iwl-phy1::assoc
[ 4017.165326] Registered led device: iwl-phy1::RX
[ 4017.165347] Registered led device: iwl-phy1::TX

```So what happened? It doesn't look entirely like iwlagn's fault...

uname -a:

```

Linux devlaptop4 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux

```Upgraded to 10.10 from 10.04 but stayed with previous kernel to avoid suspend/hibernate problems.

---

