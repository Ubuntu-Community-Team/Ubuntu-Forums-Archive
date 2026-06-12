---
title: "Wireless 3945abg gets very slow after 10 min of usage"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by yochaigal on 2010-08-19
I have an ubuntu 10.04 laptop (a Dell D620).  
My Intel PRO/Wireless 3945ABG has two problems:

1) It gets only 7mpbs down speed (according to speakeasy.net among others), while on ethernet it gets 14mbps or higher.  This did not occur with my previous broadcom card (I had hibernation issues with THAT one). 

2) The larger problem is that after around 15 min of use, my speed drops to less than 1mbps (around .8, in fact).  After restarting network manager, or wicd (I've tried both), or restarting the pc, the speed jumps back up again.

Any ideas?

here is some info:

yochai@yochai-laptop:~$ uname -mr
2.6.32-24-generic i686

yochai@yochai-laptop:~$ lsmod |grep iw
iwl3945                68727  0 
iwlcore               105922  1 iwl3945
mac80211              205146  2 iwl3945,iwlcore
led_class               2864  2 iwl3945,iwlcore
cfg80211              126517  3 iwl3945,iwlcore,mac80211

yochai@yochai-laptop:~$ dmesg | grep iwl
[    6.456433] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    6.456437] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[    6.456559] iwl3945 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.456575] iwl3945 0000:0c:00.0: setting latency timer to 64
[    6.526459] iwl3945 0000:0c:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[    6.526464] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[    6.526626] iwl3945 0000:0c:00.0: irq 27 for MSI/MSI-X
[    7.390391] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   10.395174] iwl3945 0000:0c:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   10.462553] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9

yochai@yochai-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan2
       version: 02
       serial: 00:1b:77:01:07:8e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.70 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:27 memory:dfdff000-dfdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:f5:9e:d7
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5752-v3.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:dfcf0000-dfcfffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by lafcina on 2011-11-21
Hi,
I have exactly the same problem with this Wifichip using Ubuntu 11.10. No solution jet :(

Anybody ?

Regards

---

### Post by kohoutek1 on 2011-11-22
I've never noticed a slowdown on my Gateway. I'll pay closer attention and see if I observe anything.

---

### Post by mikewhatever on 2011-11-22
> **lafcina said:**
> Hi,
I have exactly the same problem with this Wifichip using Ubuntu 11.10. No solution jet :(

Anybody ?

Regards

This thread is old. You should start a new one and post more info on your networking setup.

---

