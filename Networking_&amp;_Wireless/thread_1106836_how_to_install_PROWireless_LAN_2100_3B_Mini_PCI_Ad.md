---
title: "how to install PRO/Wireless LAN 2100 3B Mini PCI Adapter"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by ianx6 on 2009-03-26
Thanks in advance

Sir installed ubuntu 8.04 on my toshiba satellite 2410-303 and i upgraded it i installed PRO/Wireless LAN 2100 3B Mini PCI Adapter that came from an old IBM my problem is i  dont know how no make it work using ipw2100 driver im just new to linux and i dont know how to install the driver i put some command on the terminal

 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

dmesg | grep -e ipw -e iwl -e eth1
[ 1133.322725] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[ 1133.322738] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[ 1133.327124] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[  799.773206] ipw2100: eth1: Error initializing Symbol
[  799.773220] ipw2100: eth1: Error loading microcode: -5
[  799.773249] ipw2100: eth1: Failed to power on the adapter.
[  799.773253] ipw2100: eth1: Failed to start the firmware.
[  799.774414] ipw2100Error calling register_netdev.
[  799.775539] ipw2100: probe of 0000:02:0a.0 failed with error -5

 lshw -C Network

*-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=64 maxlatency=34 mingnt=2

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

please i dont know how to fix this.. thanks

---

