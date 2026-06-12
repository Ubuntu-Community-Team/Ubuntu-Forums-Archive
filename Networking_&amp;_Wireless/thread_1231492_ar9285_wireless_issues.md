---
title: "ar9285 wireless issues"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by Mahler122 on 2009-08-04
Hi, I am also having trouble with my wireless. I have a gateway netbook with an amd athlon 64 L110 processor. I have installed ubuntu 9.02 jaunty jackalope (the 64 bit version) alongside a vista installation. Wireless works wonderfully in vista.

Vista claims that I have a Realtek RTL 8102/8103 ethernet card, and a Atheros AR5B95 Wireless Network Adapter.

Here are the outputs for some commands that were useful in other posts.

lspci -nn:

```
mahler@Holst:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
mahler@Holst:~$ 

```

lshw -C Network

```
mahler@Holst:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:db:49:8f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:f4:1d:3d:1a:32
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
mahler@Holst:~$ 

```

dmesg | grep -e ath -e wlan

```
mahler@Holst:~$ dmesg | grep -e ath -e wlan
[    4.844491] device-mapper: multipath: version 1.0.5 loaded
[    4.844495] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.791016] ath9k: Unknown symbol ieee80211_start_tx_ba_cb_irqsafe
[   13.791708] ath9k: Unknown symbol ieee80211_free_hw
[   13.791943] ath9k: Unknown symbol ieee80211_alloc_hw
[   13.792106] ath9k: Unknown symbol ieee80211_start_tx_ba_session
[   13.792391] ath9k: Unknown symbol ieee80211_register_hw
[   13.792607] ath9k: Unknown symbol ieee80211_rate_control_unregister
[   13.792742] ath9k: Unknown symbol ieee80211_get_hdrlen_from_skb
[   13.792879] ath9k: Unknown symbol __ieee80211_get_radio_led_name
[   13.793027] ath9k: Unknown symbol ieee80211_wake_queue
[   13.793206] ath9k: Unknown symbol __ieee80211_get_tx_led_name
[   13.793392] ath9k: Unknown symbol ieee80211_get_buffered_bc
[   13.793666] ath9k: Unknown symbol __ieee80211_get_rx_led_name
[   13.793820] ath9k: Unknown symbol ieee80211_stop_tx_ba_cb_irqsafe
[   13.794300] ath9k: Unknown symbol ieee80211_wake_queues
[   13.794436] ath9k: Unknown symbol ieee80211_rate_control_register
[   13.794761] ath9k: Unknown symbol __ieee80211_rx
[   13.795024] ath9k: Unknown symbol ieee80211_tx_status
[   13.795160] ath9k: Unknown symbol ieee80211_stop_queue
[   13.795295] ath9k: Unknown symbol ieee80211_stop_queues
[   13.795437] ath9k: Unknown symbol __ieee80211_get_assoc_led_name
[   13.795788] ath9k: Unknown symbol ieee80211_unregister_hw
[   13.795974] ath9k: Unknown symbol ieee80211_beacon_get
mahler@Holst:~$ 
```

uname -rm

```
mahler@Holst:~$ uname -rm
2.6.28-14-generic x86_64
mahler@Holst:~$ 

```

sudo iwlist scan

```
mahler@Holst:~$ sudo iwlist scan
[sudo] password for mahler: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

mahler@Holst:~$ 

```

And here are the entries for the ethernet and wireless adapter in lspci -v | less.

```
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Device 028c
        Flags: bus master, fast devsel, latency 0, IRQ 2301
        I/O ports at a000 [size=256]
        Memory at cfdef000 (64-bit, prefetchable) [size=4K]
        Memory at cfdf0000 (64-bit, prefetchable) [size=64K]
        [virtual] Expansion ROM at cfd00000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Foxconn International, Inc. Device e016
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at f0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>


```

Linux believes that I have an ar9285 wireless adapter, so I tried the threads relating to the ar9x drivers, but I have been unsuccessful in this regard. I think something deeper is wrong because wlan0 or wmaster0 does not appear on the iwlist command like it seems to for everybody else.

---

### Post by Mahler122 on 2009-08-04
bump

---

### Post by Mahler122 on 2009-08-04
Nevermind, just found this thread: [http://ubuntuforums.org/showthread.php?t=1230823](http://ubuntuforums.org/showthread.php?t=1230823)

Worked on restart. Posted this from the netbook using wireless :P

---

