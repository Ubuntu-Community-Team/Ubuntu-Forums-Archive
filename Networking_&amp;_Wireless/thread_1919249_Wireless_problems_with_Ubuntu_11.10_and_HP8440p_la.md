---
title: "Wireless problems with Ubuntu 11.10 and HP8440p laptop"
date: 2012-02-02
forum: Networking &amp; Wireless
---

### Post by jonttix on 2012-02-02
I have some issue with my wireless connection. It sometimes work but often not. This is what "dmesg | grep iwl" gives. Someone have a clue what might be the problem?

[    5.833449] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    5.833454] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    5.833542] iwlagn 0000:44:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.833552] iwlagn 0000:44:00.0: setting latency timer to 64
[    5.833595] iwlagn 0000:44:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[    5.849387] iwlagn 0000:44:00.0: device EEPROM VER=0x436, CALIB=0x6
[    5.849390] iwlagn 0000:44:00.0: Device SKU: 0Xb
[    5.849393] iwlagn 0000:44:00.0: Valid Tx ant: 0X7, Valid Rx ant: 0X7
[    5.850926] iwlagn 0000:44:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    5.851008] iwlagn 0000:44:00.0: irq 46 for MSI/MSI-X
[    6.181420] iwlagn 0000:44:00.0: loaded firmware version 9.221.4.1 build 25532
[    6.187639] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    7.967165] iwlagn 0000:44:00.0: Error sending REPLY_TX_LINK_QUALITY_CMD: time out after 500ms.
[    8.465917] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[    8.465922] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[    8.964653] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[    8.964658] iwlagn 0000:44:00.0: set power fail, ret = -110
[    8.964698] iwlagn 0000:44:00.0: Unable to initialize device.
[   15.161102] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[   15.161109] iwlagn 0000:44:00.0: set power fail, ret = -110
[   15.161146] iwlagn 0000:44:00.0: Unable to initialize device.
[   17.810494] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[   17.810501] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   18.309284] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[   18.309292] iwlagn 0000:44:00.0: set power fail, ret = -110
[   18.309330] iwlagn 0000:44:00.0: Unable to initialize device.
[   18.915782] iwlagn 0000:44:00.0: Error sending REPLY_TX_LINK_QUALITY_CMD: time out after 500ms.
[   19.414521] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[   19.414528] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   19.913315] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[   19.913323] iwlagn 0000:44:00.0: set power fail, ret = -110
[   19.913373] iwlagn 0000:44:00.0: Unable to initialize device.
[   32.733095] iwlagn 0000:44:00.0: Error sending REPLY_TX_LINK_QUALITY_CMD: time out after 500ms.
[   33.231838] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[   33.231845] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[   33.730622] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[   33.730628] iwlagn 0000:44:00.0: set power fail, ret = -110
[   33.730666] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2890.567285] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[ 2890.567291] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[ 2891.066034] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2891.066040] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2891.066076] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2891.692467] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2891.692473] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2891.692510] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2894.824617] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[ 2894.824623] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[ 2895.323364] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2895.323369] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2895.323405] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2895.937829] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[ 2895.937835] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[ 2896.436574] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2896.436579] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2896.436615] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2900.274106] iwlagn 0000:44:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 2900.274139] iwlagn 0000:44:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd3200004)
[ 2900.274146] iwlagn 0000:44:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2900.274155] iwlagn 0000:44:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 2907.741080] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[ 2907.741086] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[ 2908.239830] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2908.239834] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2908.239876] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2908.850298] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[ 2908.850305] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[ 2909.349049] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2909.349056] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2909.349097] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2992.640273] iwlagn 0000:44:00.0: Error sending REPLY_CT_KILL_CONFIG_CMD: time out after 500ms.
[ 2992.640279] iwlagn 0000:44:00.0: REPLY_CT_KILL_CONFIG_CMD failed
[ 2993.139020] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2993.139026] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2993.139062] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2996.514563] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2996.514569] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2996.514606] iwlagn 0000:44:00.0: Unable to initialize device.
[ 2998.752951] iwlagn 0000:44:00.0: Error sending POWER_TABLE_CMD: time out after 500ms.
[ 2998.752957] iwlagn 0000:44:00.0: set power fail, ret = -110
[ 2998.752998] iwlagn 0000:44:00.0: Unable to initialize device

---

