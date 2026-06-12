---
title: "Intel Corporation Ultimate N WiFi Link 5300 ubuntu 10.10"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by anthony_barker on 2011-01-11
installed 10.10 on a Thinkpad x200 that comes with Intel Corporation Ultimate N WiFi Link 5300.

I'm not able to activate wifi via ubuntu pannel and it seems to be disabled.
=============================================
lspci | grep -i net
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300

==============================================
nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
...
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        00:21:6A:6D:E1:90

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
==============================================
dmesg | grep iw
[    2.896803] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    2.896806] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[    2.896868] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.896878] iwlagn 0000:03:00.0: setting latency timer to 64
[    2.896909] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[    3.042527] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    3.042663] iwlagn 0000:03:00.0: irq 45 for MSI/MSI-X
[    3.190903] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[    3.342578] phy0: Selected rate control algorithm 'iwl-agn-rs'
[  204.528340] iwlagn 0000:03:00.0: PCI INT A disabled
[  218.027182] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  218.027186] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[  218.027285] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  218.027331] iwlagn 0000:03:00.0: setting latency timer to 64
[  218.027589] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[  218.046857] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  218.046975] iwlagn 0000:03:00.0: irq 45 for MSI/MSI-X
[  218.050430] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[  218.051382] phy1: Selected rate control algorithm 'iwl-agn-rs'
[ 2340.941656] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
==============================================
ant@x200:~$ uname -r -m
2.6.35-24-generic-pae i686

==============================================

ant@x200:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
...       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1f:16:28:55:4f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=1.8-3 ip=192.168.1.64 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:43 memory:f2600000-f261ffff memory:f2625000-f2625fff ioport:1840(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:6d:e1:90
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-24-generic-pae firmware=8.24.2.12 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f2500000-f2501fff
ant@x200:~$

---

### Post by chili555 on 2011-01-11
The answer is given in the question:> RF_KILL bit toggled to disable radio.Please move the wireless switch to 'On.'

---

### Post by anthony_barker on 2011-01-11
Very stupid.... there is a button on the right side of the x200 which disables wireless (on top of the Fn + F5)...

changed the button and it seems to be working now....

---

