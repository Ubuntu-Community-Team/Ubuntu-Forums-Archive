---
title: "[Lucid x86] Unclaimed wireless network adapter AR5001X+"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by Marcelo Ruiz on 2010-10-13
Hi All,

I have this very weird problem with my aunt's laptop (Toshiba Satellite A30) which had Ubuntu 8.10 running with no problems.
I upgraded it to 10.04 and I run into several problems, but one of them is major: The PCMCIA wireless card is not supported anymore (DLink DWL-G650 -supported out of the box in 8.10).
I had to add the "xforcevesa pci=assign-busses pcmcia-socket-startup" to the kernel boot options to make most of it work, but the wireless card is not working (it turns on one of the green lights, but I have no wireless option in the Network Manager).
I then tried to use ndiswrapper, but no luck. I uninstalled (completely remove) and I get this funny message in syslog:

```

pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
yenta_cardbus 0000:01:04.0: EnE: chaning testregister 0xC9, 04 -> 04
ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
usbcore: registered new interface driver ndiswrapper

```

running lshw -C Network gives me the following:

```

susana@susana-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:ce:8c:5d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.42.43.10 latency=32 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:21 ioport:3000(size=256) memory:e0200000-e02000ff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
       resources: memory:58000000-5800ffff

```

This problem is driving me crazy! :confused::confused::confused:
Any ideas of what might be wrong?
Thanks!

---

### Post by Marcelo Ruiz on 2010-10-13
Just in case, using the Ubuntu 9.04 Live CD (where everything works out of the box too), I get the folloing in syslog:

```

pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
pci 0000:03:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
yenta_cardbus 0000:02:04.0: EnE: chaning testregister 0xC9, 04 -> 04
cfg80211: Calling CRDA to update world regulatory domain
cfg80211: World regulatory domain updated:
^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
^I(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
^I(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
ath5k_pci 0000:03:00.0: enabling device (0000 -> 0002)
ath5k_pci 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
ath5k_pci 0000:03:00.0: registered as 'phy0'
phy0: Selected rate control algorithm 'pid'
ath5k phy0: Atheros AR5212 chip found (MAC: 0x56, PHY: 0x41)
ath5k phy0: RF2112B 2GHz radio found (0x46)
nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_0d_88_9c_b4_63_0, iface: wlan0): not well known
NetworkManager: <info>  (wlan0): driver supports SSID scans (scan_capa 0x01). 
NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ath5k_pci') 
NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_0d_88_9c_b4_63_0 
NetworkManager: <info>  (wlan0): device state change: 1 -> 2 
NetworkManager: <info>  (wlan0): bringing up device. 

```

I don't know if that will give someone more info to see what can be wrong in Lucid.
Thanks!

---

### Post by Marcelo Ruiz on 2010-10-13
Well, it's solved. Would you like to know the secret? Brute Force!
Just completely erased EVERY reference to ndiswrapper from the disk (folders and files anything containing ndiswrapper). That did the trick!
I guess the problem was caused in the upgrade to Lucid...
Anyway, I hope this helps someone else!
:guitar:

---

