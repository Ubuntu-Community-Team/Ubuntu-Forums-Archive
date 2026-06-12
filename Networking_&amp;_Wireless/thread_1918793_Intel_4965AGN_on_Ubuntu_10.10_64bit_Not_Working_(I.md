---
title: "Intel 4965AGN on Ubuntu 10.10 64bit Not Working (Installed in Gateway SX2840-01)"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by tnicewicz on 2012-02-01
I have installed ubuntu 10.10 on my Gateway SX2840-01 with a Intel Wireless 4965AGN installed onto the motherboard.  All is working well besides the wireless connection.  It scans and shows listed networks, however, it will not connect to anything. No secure or non-secure networks.

below I am listing some results that might help to identify the problem.

tom@tom:~$ dmesg | grep iwl

[    7.242873] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[    7.242875] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[    7.242919] iwl4965 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.242925] iwl4965 0000:03:00.0: setting latency timer to 64
[    7.242945] iwl4965 0000:03:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[    7.285710] iwl4965 0000:03:00.0: device EEPROM VER=0x36, CALIB=0x5
[    7.285730] iwl4965 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    7.285796] iwl4965 0000:03:00.0: irq 50 for MSI/MSI-X
[    7.561459] iwl4965 0000:03:00.0: loaded firmware version 228.61.2.24
[    7.571723] ieee80211 phy0: Selected rate control algorithm 'iwl-4965-rs'

tom@tom:~$ ls /etc/modprobe.d
alsa-base.conf             blacklist-firewire.conf     blacklist-rare-network.conf
blacklist-ath_pci.conf     blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist.conf             blacklist-modem.conf
blacklist-cups-usblp.conf  blacklist-oss.conf

tom@tom:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

