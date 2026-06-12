---
title: "WiFi Ad-hoc: change beacon interval and ATIM window"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by jmiggal on 2011-05-11
Hello all,

I am using Ubuntu 10.10 - Maverick Meerkat  with an Intel 3945ABG wireless card:

:/$ dmesg | grep 3945
[   18.678319] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   18.678323] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   18.678422] iwl3945 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.678438] iwl3945 0000:05:00.0: setting latency timer to 64
[   18.732753] iwl3945 0000:05:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.732759] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.732925] iwl3945 0000:05:00.0: irq 47 for MSI/MSI-X
[   18.742928] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.143004] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
[   20.143173] iwl3945 0000:05:00.0: Radio disabled by HW RF Kill switch
[   20.157753] iwl3945 0000:05:00.0: Radio disabled by HW RF Kill switch
[   23.355571] iwl3945 0000:05:00.0: Radio disabled by HW RF Kill switch


I am trying to set up an Ad-hoc WiFi network and modifying the beacon interval and the ATIM period of the network (because I want to save power ). I don't know where to find these parameters. With iwconfig there are two parameters to change them:
     iwconfig wlan0 power period 
     iwconfig wlan0 power timeout 

However when I try to modify them, Linux returns and error that says:
     :~$ sudo iwconfig wlan0 power period 2
     Error for wireless request "Set Power Management" (8B2C) :
     SET failed on device wlan0 ; Invalid argument.

I guess I have to modify these parameters directly in the driver code and recompile it but I read in [http://www.intellinuxwireless.org](http://www.intellinuxwireless.org) that modification and reverse engineering are not allowed. I know that iwl3945 is deprecated. I do not mind to change my driver provided that I can change beacon interval and ATIM window but I would like to know how to do it.

Can you give me a tip about how to achieve it?

Many thanks for your help,
Jorge

---

