---
title: "&quot;Intel Wifi Link 5300&quot; work at 2.6.31-14-generic-pae ?"
date: 2009-11-21
forum: Networking &amp; Wireless
---

### Post by sundol on 2009-11-21
"Intel Wifi Link 5300" is disabled at my Ubuntu 9.10.
How can I enable this?

Once I installed "http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz", which contained 'iwlwifi-5000-2.ucode' but it didn't work so that I uninstalled it.

```
id@pc:~$ uname -a
Linux mypcname 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux

```

```
id@pc:~$ lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:50:69:0a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f2500000-f2501fff

```

```
id@pc:~$ ls /lib/firmware/iwlwifi-*
/lib/firmware/iwlwifi-1000-3.ucode  /lib/firmware/iwlwifi-4965-2.ucode
/lib/firmware/iwlwifi-3945-1.ucode  /lib/firmware/iwlwifi-5000-1.ucode
/lib/firmware/iwlwifi-3945-2.ucode  /lib/firmware/iwlwifi-5150-2.ucode
/lib/firmware/iwlwifi-4965-1.ucode  /lib/firmware/iwlwifi-6000-4.ucode 
```

```
id@pc:~$ ls /lib/firmware/2.6.31-14-generic-pae/lbm-iwlwifi-*
/lib/firmware/2.6.31-14-generic-pae/lbm-iwlwifi-3945-2.ucode
/lib/firmware/2.6.31-14-generic-pae/lbm-iwlwifi-4965-2.ucode
/lib/firmware/2.6.31-14-generic-pae/lbm-iwlwifi-5000-1.ucode
/lib/firmware/2.6.31-14-generic-pae/lbm-iwlwifi-5150-1.ucode
```

---

### Post by chili555 on 2009-11-21
>  *-network ***DISABLED***
       description: Wireless interface
       product: Wireless WiFi Link 5300
DISABLED sometimes, but not always, means that the wireless switch or key combination (Fn+F5 on my laptop) has been pushed over to 'off.' Will you please check?

---

### Post by sundol on 2009-11-21
> **chili555 said:**
> DISABLED sometimes, but not always, means that the wireless switch or key combination (Fn+F5 on my laptop) has been pushed over to 'off.' Will you please check?

Wireless of my laptop is always disabled.
I can use wireless at Windows (dual booting) but never, yet, at linux.

---

### Post by chili555 on 2009-11-21
Let's see if we can troubleshoot. Please open a terminal and do:```
sudo cat /var/log/messages | grep iwl
```Please post the result.

---

### Post by sundol on 2009-11-21
> **chili555 said:**
> Let's see if we can troubleshoot. Please open a terminal and do:```
sudo cat /var/log/messages | grep iwl
```Please post the result.

Messages containing **iwlcore** were produced when I installed 'http://www.orbit-lab.org/kernel/compat-wireless-2.6/2009/11/compat-wireless-2009-11-21.tar.bz2'.
Before I installed it and after I uninstalled it again, messages containing **iwlagn** were produced
```
ov 14 22:02:25 pcname kernel: [    4.122533] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 14 22:02:25 pcname kernel: [    4.122535] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 14 22:02:25 pcname kernel: [    4.122600] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 14 22:02:25 pcname kernel: [    4.122643] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 14 22:02:25 pcname kernel: [    4.175720] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 14 22:23:30 pcname kernel: [    3.967939] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 14 22:23:30 pcname kernel: [    3.967942] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 14 22:23:30 pcname kernel: [    3.968059] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 14 22:23:30 pcname kernel: [    3.968140] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 14 22:23:30 pcname kernel: [    4.012278] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 15 00:48:52 pcname kernel: [    3.923777] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 15 00:48:52 pcname kernel: [    3.923780] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 15 00:48:52 pcname kernel: [    3.923872] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 15 00:48:52 pcname kernel: [    3.923952] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 15 00:48:52 pcname kernel: [    3.965573] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 15 10:58:42 pcname kernel: [    3.894654] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 15 10:58:42 pcname kernel: [    3.894656] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 15 10:58:42 pcname kernel: [    3.894714] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 15 10:58:42 pcname kernel: [    3.894749] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 15 10:58:42 pcname kernel: [    3.933961] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 15 13:42:15 pcname kernel: [    3.760255] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 15 13:42:15 pcname kernel: [    3.760258] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 15 13:42:15 pcname kernel: [    3.760318] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 15 13:42:15 pcname kernel: [    3.760353] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 15 13:42:15 pcname kernel: [    3.802000] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 15 23:23:01 pcname kernel: [    3.816561] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 15 23:23:01 pcname kernel: [    3.816564] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 15 23:23:01 pcname kernel: [    3.816625] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 15 23:23:01 pcname kernel: [    3.816662] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 15 23:23:01 pcname kernel: [    3.872624] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 16 11:29:59 pcname kernel: [    3.956879] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 16 11:29:59 pcname kernel: [    3.956882] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 16 11:29:59 pcname kernel: [    3.956935] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 16 11:29:59 pcname kernel: [    3.956966] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 16 11:29:59 pcname kernel: [    3.997343] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 16 13:52:28 pcname kernel: [    4.123731] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 16 13:52:28 pcname kernel: [    4.123734] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 16 13:52:28 pcname kernel: [    4.123823] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 16 13:52:28 pcname kernel: [    4.123906] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 16 13:52:28 pcname kernel: [    4.170852] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 16 13:54:43 pcname kernel: [    4.015309] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 16 13:54:43 pcname kernel: [    4.015312] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 16 13:54:43 pcname kernel: [    4.015371] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 16 13:54:43 pcname kernel: [    4.015455] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 16 13:54:43 pcname kernel: [    4.053243] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 16 13:57:13 pcname kernel: [    4.115381] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 16 13:57:13 pcname kernel: [    4.115384] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 16 13:57:13 pcname kernel: [    4.115479] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 16 13:57:13 pcname kernel: [    4.115557] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 16 13:57:13 pcname kernel: [    4.155189] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 16 14:04:22 pcname kernel: [    4.122241] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 16 14:04:22 pcname kernel: [    4.122244] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 16 14:04:22 pcname kernel: [    4.122328] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 16 14:04:22 pcname kernel: [    4.122424] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 16 14:04:22 pcname kernel: [    4.159656] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 17 11:13:01 pcname kernel: [    4.453161] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 17 11:13:01 pcname kernel: [    4.453163] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 17 11:13:01 pcname kernel: [    4.453229] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 17 11:13:01 pcname kernel: [    4.453280] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 17 11:13:01 pcname kernel: [    4.491702] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 17 13:11:06 pcname kernel: [    4.364893] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 17 13:11:06 pcname kernel: [    4.364896] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 17 13:11:06 pcname kernel: [    4.364982] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 17 13:11:06 pcname kernel: [    4.365064] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 17 13:11:06 pcname kernel: [    4.402694] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 17 17:58:49 pcname kernel: [    4.331373] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 17 17:58:49 pcname kernel: [    4.331375] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 17 17:58:49 pcname kernel: [    4.331441] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 17 17:58:49 pcname kernel: [    4.331476] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 17 17:58:49 pcname kernel: [    4.370167] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 18 14:08:59 pcname kernel: [    3.769500] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 18 14:08:59 pcname kernel: [    3.769503] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 18 14:08:59 pcname kernel: [    3.769572] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 18 14:08:59 pcname kernel: [    3.769628] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 18 14:08:59 pcname kernel: [    3.807785] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 18 15:30:58 pcname kernel: [    4.139741] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 18 15:30:58 pcname kernel: [    4.139744] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 18 15:30:58 pcname kernel: [    4.139810] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 18 15:30:58 pcname kernel: [    4.139846] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 18 15:30:58 pcname kernel: [    4.178667] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 20 22:20:25 pcname kernel: [    4.106414] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 20 22:20:25 pcname kernel: [    4.106416] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 20 22:20:25 pcname kernel: [    4.106503] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 20 22:20:25 pcname kernel: [    4.106538] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 20 22:20:25 pcname kernel: [    4.143952] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 21 16:11:23 pcname kernel: [    4.054684] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 21 16:11:23 pcname kernel: [    4.054687] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 21 16:11:23 pcname kernel: [    4.054768] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 21 16:11:23 pcname kernel: [    4.054891] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 21 16:11:23 pcname kernel: [    4.094474] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 21 16:33:08 pcname kernel: [    4.274216] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
Nov 21 16:33:08 pcname kernel: [    4.274219] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 21 16:33:08 pcname kernel: [    4.274309] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 21 16:33:08 pcname kernel: [    4.274397] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 21 16:33:08 pcname kernel: [    4.312292] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 21 16:45:25 pcname kernel: [    4.170757] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Nov 21 16:45:25 pcname kernel: [    4.170760] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 21 16:45:25 pcname kernel: [    4.170850] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 21 16:45:25 pcname kernel: [    4.170936] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 21 16:45:25 pcname kernel: [    4.208644] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 21 16:47:33 pcname kernel: [    4.229387] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Nov 21 16:47:33 pcname kernel: [    4.229389] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 21 16:47:33 pcname kernel: [    4.229484] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 21 16:47:33 pcname kernel: [    4.229566] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 21 16:47:33 pcname kernel: [    4.271294] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 21 17:47:32 pcname kernel: [ 3603.880643] iwlagn 0000:03:00.0: PCI INT A disabled
Nov 21 17:47:36 pcname kernel: [ 3608.525607] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.525610] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.525852] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
Nov 21 17:47:36 pcname kernel: [ 3608.525854] iwlcore: Unknown symbol ieee80211_alloc_hw
Nov 21 17:47:36 pcname kernel: [ 3608.525996] iwlcore: disagrees about version of symbol ieee80211_wake_queue
Nov 21 17:47:36 pcname kernel: [ 3608.525998] iwlcore: Unknown symbol ieee80211_wake_queue
Nov 21 17:47:36 pcname kernel: [ 3608.526061] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
Nov 21 17:47:36 pcname kernel: [ 3608.526063] iwlcore: Unknown symbol ieee80211_get_tkip_key
Nov 21 17:47:36 pcname kernel: [ 3608.526152] iwlcore: disagrees about version of symbol ieee80211_find_sta
Nov 21 17:47:36 pcname kernel: [ 3608.526154] iwlcore: Unknown symbol ieee80211_find_sta
Nov 21 17:47:36 pcname kernel: [ 3608.526252] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.526254] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.526425] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.526426] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.526562] iwlcore: Unknown symbol ieee80211_sta_block_awake
Nov 21 17:47:36 pcname kernel: [ 3608.526641] iwlcore: disagrees about version of symbol ieee80211_wake_queues
Nov 21 17:47:36 pcname kernel: [ 3608.526643] iwlcore: Unknown symbol ieee80211_wake_queues
Nov 21 17:47:36 pcname kernel: [ 3608.526771] iwlcore: disagrees about version of symbol ieee80211_stop_queue
Nov 21 17:47:36 pcname kernel: [ 3608.526773] iwlcore: Unknown symbol ieee80211_stop_queue
Nov 21 17:47:36 pcname kernel: [ 3608.526836] iwlcore: disagrees about version of symbol ieee80211_stop_queues
Nov 21 17:47:36 pcname kernel: [ 3608.526838] iwlcore: Unknown symbol ieee80211_stop_queues
Nov 21 17:47:36 pcname kernel: [ 3608.526921] iwlcore: disagrees about version of symbol ieee80211_scan_completed
Nov 21 17:47:36 pcname kernel: [ 3608.526923] iwlcore: Unknown symbol ieee80211_scan_completed
Nov 21 17:47:36 pcname kernel: [ 3608.527185] iwlcore: Unknown symbol ieee80211_beacon_get_tim
Nov 21 17:47:36 pcname kernel: [ 3608.527485] iwlcore: Unknown symbol mac80211_ieee80211_rx
Nov 21 17:47:36 pcname kernel: [ 3608.530186] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.530189] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.530417] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
Nov 21 17:47:36 pcname kernel: [ 3608.530419] iwlcore: Unknown symbol ieee80211_alloc_hw
Nov 21 17:47:36 pcname kernel: [ 3608.530561] iwlcore: disagrees about version of symbol ieee80211_wake_queue
Nov 21 17:47:36 pcname kernel: [ 3608.530563] iwlcore: Unknown symbol ieee80211_wake_queue
Nov 21 17:47:36 pcname kernel: [ 3608.530626] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
Nov 21 17:47:36 pcname kernel: [ 3608.530628] iwlcore: Unknown symbol ieee80211_get_tkip_key
Nov 21 17:47:36 pcname kernel: [ 3608.530717] iwlcore: disagrees about version of symbol ieee80211_find_sta
Nov 21 17:47:36 pcname kernel: [ 3608.530719] iwlcore: Unknown symbol ieee80211_find_sta
Nov 21 17:47:36 pcname kernel: [ 3608.530817] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.530818] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.530989] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.530991] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:47:36 pcname kernel: [ 3608.531124] iwlcore: Unknown symbol ieee80211_sta_block_awake
Nov 21 17:47:36 pcname kernel: [ 3608.531203] iwlcore: disagrees about version of symbol ieee80211_wake_queues
Nov 21 17:47:36 pcname kernel: [ 3608.531205] iwlcore: Unknown symbol ieee80211_wake_queues
Nov 21 17:47:36 pcname kernel: [ 3608.531333] iwlcore: disagrees about version of symbol ieee80211_stop_queue
Nov 21 17:47:36 pcname kernel: [ 3608.531335] iwlcore: Unknown symbol ieee80211_stop_queue
Nov 21 17:47:36 pcname kernel: [ 3608.531398] iwlcore: disagrees about version of symbol ieee80211_stop_queues
Nov 21 17:47:36 pcname kernel: [ 3608.531400] iwlcore: Unknown symbol ieee80211_stop_queues
Nov 21 17:47:36 pcname kernel: [ 3608.531483] iwlcore: disagrees about version of symbol ieee80211_scan_completed
Nov 21 17:47:36 pcname kernel: [ 3608.531485] iwlcore: Unknown symbol ieee80211_scan_completed
Nov 21 17:47:36 pcname kernel: [ 3608.531746] iwlcore: Unknown symbol ieee80211_beacon_get_tim
Nov 21 17:47:36 pcname kernel: [ 3608.532058] iwlcore: Unknown symbol mac80211_ieee80211_rx
Nov 21 17:48:54 pcname kernel: [    4.136283] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:48:54 pcname kernel: [    4.136286] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:48:54 pcname kernel: [    4.136571] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
Nov 21 17:48:54 pcname kernel: [    4.136573] iwlcore: Unknown symbol ieee80211_alloc_hw
Nov 21 17:48:54 pcname kernel: [    4.136734] iwlcore: disagrees about version of symbol ieee80211_wake_queue
Nov 21 17:48:54 pcname kernel: [    4.136736] iwlcore: Unknown symbol ieee80211_wake_queue
Nov 21 17:48:54 pcname kernel: [    4.136809] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
Nov 21 17:48:54 pcname kernel: [    4.136811] iwlcore: Unknown symbol ieee80211_get_tkip_key
Nov 21 17:48:54 pcname kernel: [    4.136912] iwlcore: disagrees about version of symbol ieee80211_find_sta
Nov 21 17:48:54 pcname kernel: [    4.136914] iwlcore: Unknown symbol ieee80211_find_sta
Nov 21 17:48:54 pcname kernel: [    4.137095] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
Nov 21 17:48:54 pcname kernel: [    4.137097] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
Nov 21 17:48:54 pcname kernel: [    4.137288] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:48:54 pcname kernel: [    4.137290] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:48:54 pcname kernel: [    4.137432] iwlcore: Unknown symbol ieee80211_sta_block_awake
Nov 21 17:48:54 pcname kernel: [    4.137550] iwlcore: disagrees about version of symbol ieee80211_wake_queues
Nov 21 17:48:54 pcname kernel: [    4.137552] iwlcore: Unknown symbol ieee80211_wake_queues
Nov 21 17:48:54 pcname kernel: [    4.137698] iwlcore: disagrees about version of symbol ieee80211_stop_queue
Nov 21 17:48:54 pcname kernel: [    4.137700] iwlcore: Unknown symbol ieee80211_stop_queue
Nov 21 17:48:54 pcname kernel: [    4.137780] iwlcore: disagrees about version of symbol ieee80211_stop_queues
Nov 21 17:48:54 pcname kernel: [    4.137782] iwlcore: Unknown symbol ieee80211_stop_queues
Nov 21 17:48:54 pcname kernel: [    4.137876] iwlcore: disagrees about version of symbol ieee80211_scan_completed
Nov 21 17:48:54 pcname kernel: [    4.137878] iwlcore: Unknown symbol ieee80211_scan_completed
Nov 21 17:48:54 pcname kernel: [    4.138174] iwlcore: Unknown symbol ieee80211_beacon_get_tim
Nov 21 17:48:54 pcname kernel: [    4.138572] iwlcore: Unknown symbol mac80211_ieee80211_rx
Nov 21 17:50:15 pcname kernel: [   84.867656] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:50:15 pcname kernel: [   84.867659] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 17:50:15 pcname kernel: [   84.867896] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
Nov 21 17:50:15 pcname kernel: [   84.867898] iwlcore: Unknown symbol ieee80211_alloc_hw
Nov 21 17:50:15 pcname kernel: [   84.868061] iwlcore: disagrees about version of symbol ieee80211_wake_queue
Nov 21 17:50:15 pcname kernel: [   84.868063] iwlcore: Unknown symbol ieee80211_wake_queue
Nov 21 17:50:15 pcname kernel: [   84.868142] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
Nov 21 17:50:15 pcname kernel: [   84.868144] iwlcore: Unknown symbol ieee80211_get_tkip_key
Nov 21 17:50:15 pcname kernel: [   84.868253] iwlcore: disagrees about version of symbol ieee80211_find_sta
Nov 21 17:50:15 pcname kernel: [   84.868254] iwlcore: Unknown symbol ieee80211_find_sta
Nov 21 17:50:15 pcname kernel: [   84.868367] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
Nov 21 17:50:15 pcname kernel: [   84.868369] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
Nov 21 17:50:15 pcname kernel: [   84.868557] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:50:15 pcname kernel: [   84.868559] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 17:50:15 pcname kernel: [   84.868696] iwlcore: Unknown symbol ieee80211_sta_block_awake
Nov 21 17:50:15 pcname kernel: [   84.868782] iwlcore: disagrees about version of symbol ieee80211_wake_queues
Nov 21 17:50:15 pcname kernel: [   84.868784] iwlcore: Unknown symbol ieee80211_wake_queues
Nov 21 17:50:15 pcname kernel: [   84.868920] iwlcore: disagrees about version of symbol ieee80211_stop_queue
Nov 21 17:50:15 pcname kernel: [   84.868922] iwlcore: Unknown symbol ieee80211_stop_queue
Nov 21 17:50:15 pcname kernel: [   84.868992] iwlcore: disagrees about version of symbol ieee80211_stop_queues
Nov 21 17:50:15 pcname kernel: [   84.868994] iwlcore: Unknown symbol ieee80211_stop_queues
Nov 21 17:50:15 pcname kernel: [   84.869085] iwlcore: disagrees about version of symbol ieee80211_scan_completed
Nov 21 17:50:15 pcname kernel: [   84.869086] iwlcore: Unknown symbol ieee80211_scan_completed
Nov 21 17:50:15 pcname kernel: [   84.869356] iwlcore: Unknown symbol ieee80211_beacon_get_tim
Nov 21 17:50:15 pcname kernel: [   84.869672] iwlcore: Unknown symbol mac80211_ieee80211_rx
Nov 21 18:03:37 pcname kernel: [  886.745336] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.745339] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.745595] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
Nov 21 18:03:37 pcname kernel: [  886.745598] iwlcore: Unknown symbol ieee80211_alloc_hw
Nov 21 18:03:37 pcname kernel: [  886.745756] iwlcore: disagrees about version of symbol ieee80211_wake_queue
Nov 21 18:03:37 pcname kernel: [  886.745758] iwlcore: Unknown symbol ieee80211_wake_queue
Nov 21 18:03:37 pcname kernel: [  886.745829] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
Nov 21 18:03:37 pcname kernel: [  886.745831] iwlcore: Unknown symbol ieee80211_get_tkip_key
Nov 21 18:03:37 pcname kernel: [  886.745931] iwlcore: disagrees about version of symbol ieee80211_find_sta
Nov 21 18:03:37 pcname kernel: [  886.745933] iwlcore: Unknown symbol ieee80211_find_sta
Nov 21 18:03:37 pcname kernel: [  886.746043] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.746045] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.746236] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.746238] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.746389] iwlcore: Unknown symbol ieee80211_sta_block_awake
Nov 21 18:03:37 pcname kernel: [  886.746477] iwlcore: disagrees about version of symbol ieee80211_wake_queues
Nov 21 18:03:37 pcname kernel: [  886.746479] iwlcore: Unknown symbol ieee80211_wake_queues
Nov 21 18:03:37 pcname kernel: [  886.746623] iwlcore: disagrees about version of symbol ieee80211_stop_queue
Nov 21 18:03:37 pcname kernel: [  886.746625] iwlcore: Unknown symbol ieee80211_stop_queue
Nov 21 18:03:37 pcname kernel: [  886.746696] iwlcore: disagrees about version of symbol ieee80211_stop_queues
Nov 21 18:03:37 pcname kernel: [  886.746698] iwlcore: Unknown symbol ieee80211_stop_queues
Nov 21 18:03:37 pcname kernel: [  886.746791] iwlcore: disagrees about version of symbol ieee80211_scan_completed
Nov 21 18:03:37 pcname kernel: [  886.746793] iwlcore: Unknown symbol ieee80211_scan_completed
Nov 21 18:03:37 pcname kernel: [  886.747088] iwlcore: Unknown symbol ieee80211_beacon_get_tim
Nov 21 18:03:37 pcname kernel: [  886.747426] iwlcore: Unknown symbol mac80211_ieee80211_rx
Nov 21 18:03:37 pcname kernel: [  886.750206] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.750209] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.750468] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
Nov 21 18:03:37 pcname kernel: [  886.750470] iwlcore: Unknown symbol ieee80211_alloc_hw
Nov 21 18:03:37 pcname kernel: [  886.750628] iwlcore: disagrees about version of symbol ieee80211_wake_queue
Nov 21 18:03:37 pcname kernel: [  886.750630] iwlcore: Unknown symbol ieee80211_wake_queue
Nov 21 18:03:37 pcname kernel: [  886.750701] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
Nov 21 18:03:37 pcname kernel: [  886.750703] iwlcore: Unknown symbol ieee80211_get_tkip_key
Nov 21 18:03:37 pcname kernel: [  886.750803] iwlcore: disagrees about version of symbol ieee80211_find_sta
Nov 21 18:03:37 pcname kernel: [  886.750805] iwlcore: Unknown symbol ieee80211_find_sta
Nov 21 18:03:37 pcname kernel: [  886.750915] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.750917] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.751108] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.751110] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 18:03:37 pcname kernel: [  886.751259] iwlcore: Unknown symbol ieee80211_sta_block_awake
Nov 21 18:03:37 pcname kernel: [  886.751347] iwlcore: disagrees about version of symbol ieee80211_wake_queues
Nov 21 18:03:37 pcname kernel: [  886.751349] iwlcore: Unknown symbol ieee80211_wake_queues
Nov 21 18:03:37 pcname kernel: [  886.751493] iwlcore: disagrees about version of symbol ieee80211_stop_queue
Nov 21 18:03:37 pcname kernel: [  886.751495] iwlcore: Unknown symbol ieee80211_stop_queue
Nov 21 18:03:37 pcname kernel: [  886.751566] iwlcore: disagrees about version of symbol ieee80211_stop_queues
Nov 21 18:03:37 pcname kernel: [  886.751568] iwlcore: Unknown symbol ieee80211_stop_queues
Nov 21 18:03:37 pcname kernel: [  886.751661] iwlcore: disagrees about version of symbol ieee80211_scan_completed
Nov 21 18:03:37 pcname kernel: [  886.751663] iwlcore: Unknown symbol ieee80211_scan_completed
Nov 21 18:03:37 pcname kernel: [  886.751958] iwlcore: Unknown symbol ieee80211_beacon_get_tim
Nov 21 18:03:37 pcname kernel: [  886.752297] iwlcore: Unknown symbol mac80211_ieee80211_rx
Nov 21 18:10:09 pcname kernel: [    4.229632] iwlcore: disagrees about version of symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 18:10:09 pcname kernel: [    4.229635] iwlcore: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
Nov 21 18:10:09 pcname kernel: [    4.229909] iwlcore: disagrees about version of symbol ieee80211_alloc_hw
Nov 21 18:10:09 pcname kernel: [    4.229911] iwlcore: Unknown symbol ieee80211_alloc_hw
Nov 21 18:10:09 pcname kernel: [    4.230071] iwlcore: disagrees about version of symbol ieee80211_wake_queue
Nov 21 18:10:09 pcname kernel: [    4.230073] iwlcore: Unknown symbol ieee80211_wake_queue
Nov 21 18:10:09 pcname kernel: [    4.230145] iwlcore: disagrees about version of symbol ieee80211_get_tkip_key
Nov 21 18:10:09 pcname kernel: [    4.230147] iwlcore: Unknown symbol ieee80211_get_tkip_key
Nov 21 18:10:09 pcname kernel: [    4.230248] iwlcore: disagrees about version of symbol ieee80211_find_sta
Nov 21 18:10:09 pcname kernel: [    4.230250] iwlcore: Unknown symbol ieee80211_find_sta
Nov 21 18:10:09 pcname kernel: [    4.230358] iwlcore: disagrees about version of symbol ieee80211_tx_status_irqsafe
Nov 21 18:10:09 pcname kernel: [    4.230360] iwlcore: Unknown symbol ieee80211_tx_status_irqsafe
Nov 21 18:10:09 pcname kernel: [    4.230571] iwlcore: disagrees about version of symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 18:10:09 pcname kernel: [    4.230574] iwlcore: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
Nov 21 18:10:09 pcname kernel: [    4.230725] iwlcore: Unknown symbol ieee80211_sta_block_awake
Nov 21 18:10:09 pcname kernel: [    4.230813] iwlcore: disagrees about version of symbol ieee80211_wake_queues
Nov 21 18:10:09 pcname kernel: [    4.230815] iwlcore: Unknown symbol ieee80211_wake_queues
Nov 21 18:10:09 pcname kernel: [    4.230968] iwlcore: disagrees about version of symbol ieee80211_stop_queue
Nov 21 18:10:09 pcname kernel: [    4.230970] iwlcore: Unknown symbol ieee80211_stop_queue
Nov 21 18:10:09 pcname kernel: [    4.231033] iwlcore: disagrees about version of symbol ieee80211_stop_queues
Nov 21 18:10:09 pcname kernel: [    4.231035] iwlcore: Unknown symbol ieee80211_stop_queues
Nov 21 18:10:09 pcname kernel: [    4.231132] iwlcore: disagrees about version of symbol ieee80211_scan_completed
Nov 21 18:10:09 pcname kernel: [    4.231134] iwlcore: Unknown symbol ieee80211_scan_completed
Nov 21 18:10:09 pcname kernel: [    4.231411] iwlcore: Unknown symbol ieee80211_beacon_get_tim
Nov 21 18:10:09 pcname kernel: [    4.231762] iwlcore: Unknown symbol mac80211_ieee80211_rx
Nov 21 18:11:49 pcname kernel: [    4.278979] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Nov 21 18:11:49 pcname kernel: [    4.278982] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 21 18:11:49 pcname kernel: [    4.279061] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 21 18:11:49 pcname kernel: [    4.279143] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 21 18:11:49 pcname kernel: [    4.318628] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 21 18:46:13 pcname kernel: [    4.258949] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Nov 21 18:46:13 pcname kernel: [    4.258952] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 21 18:46:13 pcname kernel: [    4.259045] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 21 18:46:13 pcname kernel: [    4.259126] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 21 18:46:13 pcname kernel: [    4.296408] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 21 21:08:59 pcname kernel: [ 8568.976100] iwlagn 0000:03:00.0: enabling device (0000 -> 0002)
Nov 21 21:08:59 pcname kernel: [ 8568.976313] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
Nov 22 00:49:44 pcname kernel: [    3.940579] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Nov 22 00:49:44 pcname kernel: [    3.940582] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 22 00:49:44 pcname kernel: [    3.940633] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 22 00:49:44 pcname kernel: [    3.940667] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 22 00:49:44 pcname kernel: [    3.987167] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
```

---

### Post by chili555 on 2009-11-21
Your iwlagn messages look healthy; the driver gets loaded and there are no firmware complaints or other warnings or errors. Let's see what happens...or doesn't...when the interface gets created and tries to connect. Please post:```
sudo cat /var/log/messages | grep wlan
sudo cat /var/log/messages | grep -i Network
```Thanks.

---

### Post by sundol on 2009-11-21
> **chili555 said:**
> Your iwlagn messages look healthy; the driver gets loaded and there are no firmware complaints or other warnings or errors. Let's see what happens...or doesn't...when the interface gets created and tries to connect. Please post:```
sudo cat /var/log/messages | grep wlan
sudo cat /var/log/messages | grep -i Network
```Thanks.

sudo cat /var/log/messages | grep -i Network
```
Nov 22 01:47:04 mypcname kernel: [    1.760781] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Nov 22 01:47:04 mypcname kernel: [    1.905022] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Nov 22 01:47:04 mypcname kernel: [    3.979598] udev: renamed network interface eth0 to eth2

```

sudo cat /var/log/messages/ | grep -i wlan
didn't give any lines.

all other possibly related lines (that I think)
```
Nov 22 01:47:04 mypcname kernel: [    1.905019] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1f:16:1c:a1:d9
Nov 22 01:47:04 mypcname kernel: [    1.905049] 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1008ff-0ff
Nov 22 01:47:04 mypcname kernel: [    4.070158] thinkpad_acpi: ThinkPad ACPI Extras v0.23
Nov 22 01:47:04 mypcname kernel: [    4.070161] thinkpad_acpi: http://ibm-acpi.sf.net/
Nov 22 01:47:04 mypcname kernel: [    4.070163] thinkpad_acpi: ThinkPad BIOS 6DET60WW (3.10 ), EC 7XHT22WW-1.04
Nov 22 01:47:04 mypcname kernel: [    4.070165] thinkpad_acpi: Lenovo ThinkPad X200s, model 7465CTO
Nov 22 01:47:04 mypcname kernel: [    4.073985] thinkpad_acpi: **radio switch found; *radios are disabled***
Nov 22 01:47:04 mypcname kernel: [    4.074088] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
Nov 22 01:47:04 mypcname kernel: [    4.074092] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
Nov 22 01:47:04 mypcname kernel: [    4.080953] cfg80211: Calling CRDA to update world regulatory domain
Nov 22 01:47:04 mypcname kernel: [    4.094872] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 22 01:47:04 mypcname kernel: [    4.098492] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
Nov 22 01:47:04 mypcname kernel: [    4.100200] **input: ThinkPad Extra Buttons as */devices/virtual/input/input7***
Nov 22 01:47:04 mypcname kernel: [    4.144482] cfg80211: World regulatory domain updated:
Nov 22 01:47:04 mypcname kernel: [    4.144486] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Nov 22 01:47:04 mypcname kernel: [    4.144488] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 01:47:04 mypcname kernel: [    4.144491] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 01:47:04 mypcname kernel: [    4.144493] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Nov 22 01:47:04 mypcname kernel: [    4.144499] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 01:47:04 mypcname kernel: [    4.144512] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov 22 01:47:04 mypcname kernel: [    4.187535] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Nov 22 01:47:04 mypcname kernel: [    4.187538] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Nov 22 01:47:04 mypcname kernel: [    4.187628] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Nov 22 01:47:04 mypcname kernel: [    4.187709] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
Nov 22 01:47:04 mypcname kernel: [    4.224565] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Nov 22 01:47:05 mypcname kernel: [    4.539244] ip6_tables: (C) 2000-2006 Netfilter Core Team
Nov 22 01:47:05 mypcname kernel: [    4.649496] ADDRCONF(NETDEV_UP): eth2: link is not ready
Nov 22 01:47:06 mypcname kernel: [    6.241280] 0000:00:19.0: eth2: 10/100 speed: disabling TSO
Nov 22 01:47:06 mypcname kernel: [    6.241464] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
```

Other hotkey such as Fn+Home(to increase screen brightness) works well but Fn+F5(to enable/disable wireless) does not work.

/devices/virtual/input/input7 doesn't exists but exist in /sys/devices/virtual/input/input7

/sys/devices/platform/thinkpad_acpi/hotkey_radio_sw exist and contains only a single character '0'. 
ls -l /sys/devices/platform/thinkpad_acpi/hotkey_radio_sw
```
-r--r--r-- 1 root root 4096 2009-11-22 11:10 hotkey_radio_sw
```

---

### Post by chili555 on 2009-11-22
I have googled this extensively and I suggest you do so as well. Please check here: [http://old.nabble.com/Fn-%2B-F5-disconnects-WLAN-td21016088.html](http://old.nabble.com/Fn-%2B-F5-disconnects-WLAN-td21016088.html)

Does your wireless LED work at all?

You might try this:```
sudo su
echo "1" > /sys/devices/platform/thinkpad_acpi/hotkey_radio_sw
```Does that get the switch working?

---

### Post by hfdragon on 2009-12-16
I also have this card, and also use the -pae kernels.

The card seems to be functionning, but it is unstable, if disable the wifi, then enable it-back, It can't detect any wifi anymore.

Also, connection sharing (sometimes I need to share my cable or 3G connection) isn't working anymore..

---

### Post by bazb on 2009-12-19
i have the same problem with this wireless card on my laptop, i can see the wireless station points but doesn't connect, i got it connected a few times but when i re-start the laptop it doesn't seem to connect. any suggestions? i'm new to ubuntu 9.10/linux

---

