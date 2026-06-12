---
title: "no wifi on my lenovo Z570"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by Marc1983 on 2013-07-10
hello forum,
i have a Lenovo Z570 with Ubuntu 12.4 installed and the wifi does not work at all. the wifi car is a intel centrino wireless n 1000 
i ran this terminal. dmesg | grep iwl

[   13.366535] iwlwifi: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.366538] iwlwifi: Copyright(c) 2003-2012 Intel Corporation
[   13.366611] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   13.366614] iwlwifi 0000:03:00.0: pci_resource_base = f858c000
[   13.366617] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[   13.366708] iwlwifi 0000:03:00.0: irq 45 for MSI/MSI-X
[   13.501424] iwlwifi 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   13.501576] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   13.501579] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   13.501581] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   13.501582] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   13.501584] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_P2P disabled
[   13.501586] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   13.501646] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   13.508826] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
[   13.522408] iwlwifi 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   13.522411] iwlwifi 0000:03:00.0: Device SKU: 0x50
[   13.522412] iwlwifi 0000:03:00.0: Valid Tx ant: 0x1, Valid Rx ant: 0x3
[   13.522422] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.525049] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

i also ran this one too. rfkill list


0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

if some one could please help me get my wifi working that would be great. thanks in advanded.

---

### Post by TenPlus1 on 2013-07-10
This should help: [http://askubuntu.com/questions/75969/ar9285-wifi-on-lenovo-z570-not-enabled](http://askubuntu.com/questions/75969/ar9285-wifi-on-lenovo-z570-not-enabled)

---

### Post by Marc1983 on 2013-07-12
thanks so much for your help i found that all i needed to do was reset my bios to the defalt settings and that fixed the problem.

---

