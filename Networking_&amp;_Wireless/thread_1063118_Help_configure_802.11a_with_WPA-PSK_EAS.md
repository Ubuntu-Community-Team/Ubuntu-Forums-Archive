---
title: "Help configure 802.11a with WPA-PSK/ EAS"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by cubical10 on 2009-02-07
I need help to configure my wifi connection.
My access point is configured as follows:
Wireless Band: 802.11a (not g)
Authentication: WPA-PSK
Cypher type: AES

My notebook (Acer 5672)
OS: Ubuntu 8.10
Network Adaptor: Intel(R) PRO/Wireless 3945ABG/BG Network

I tried to connect using the connection manager, but it seems to only want to use the TKIP cypher type.  I can connect to other wifi networks with this PC.  And my Macbook can connect to the AP without issue.
I am not sure how to configure this connection manually.


```
cubical10@acer5672:~$ uname -a
Linux acer5672 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

```

```
cubical10@acer5672:~$ dmesg |grep -i 3945
[   15.727704] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   15.727709] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   15.729585] iwl3945 0000:03:00.0: enabling device (0000 -> 0002)
[   15.729598] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.729619] iwl3945 0000:03:00.0: setting latency timer to 64
[   15.729641] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   15.837891] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.838477] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.457846] iwl3945 0000:03:00.0: PCI INT A disabled
[   30.449845] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   30.449999] iwl3945 0000:03:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   30.450482] firmware: requesting iwlwifi-3945-1.ucode
[   55.796944] iwl3945: No space for Tx
[   55.796949] iwl3945: Error sending REPLY_LEDS_CMD: iwl3945_enqueue_hcmd failed: -28
[   55.796963] iwl3945: No space for Tx
[   55.796966] iwl3945: Error sending REPLY_LEDS_CMD: iwl3945_enqueue_hcmd failed: -28

```

---

