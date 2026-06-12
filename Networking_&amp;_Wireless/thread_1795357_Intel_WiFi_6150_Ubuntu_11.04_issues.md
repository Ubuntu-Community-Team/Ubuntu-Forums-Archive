---
title: "Intel WiFi 6150 Ubuntu 11.04 issues"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by Deathscythe401 on 2011-07-02
Hi there! Been trying to figure this out for a few days with no luck.
Got a new Lenovo V570, installed Ubuntu to work alongside with Windows. Whenever I turn my WiFi card on, Ubuntu says "Device Not Ready" and cannot connect to any networks. Here's some stuff I got from the term

    *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:32:29:e8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:d0500000-d0501fff


Don't know what other info would be required to help, or if anybody else has had this problem and gotten it fixed?
Thanks in advance.


Scythe

---

### Post by chili555 on 2011-07-02
Please get this from the term:```
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by Deathscythe401 on 2011-07-02
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
```

```
[   15.857251] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   15.857254] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   15.857296] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.857304] iwlagn 0000:02:00.0: setting latency timer to 64
[   15.857330] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   15.870197] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
[   15.870200] iwlagn 0000:02:00.0: Device SKU: 0X9
[   15.870202] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   15.870231] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   15.870526] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
[   15.871706] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.
[   15.904984] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   15.912930] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
```

There's those. Thanks again.

---

### Post by chili555 on 2011-07-02
The Doctor has seen these cases before. The good news is I think we can save the patient. Please refer to the acer-wmi posts here. You have the same issue and the same fix applies. Disregard his Broadcom posts.

 [http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi)

---

### Post by Deathscythe401 on 2011-07-02
You the man, doc. Worked like a charm. Thanks a ton!

---

