---
title: "Slow WLAN AP association with AR5212/Ubuntu 8.10/IBM T42"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by zzuser on 2009-03-10
Hi!

I'd be grateful for any pointers on how to fix the extremely slow WLAN AP association problem om my IBM T42 laptop (Atheros AR5212) running Ubuntu 8.10. The problem is not that the WLAN does not work, the problem is that it takes in the order of a minute or more to connect to any WLAN access point after suspend. It does not matter if the WLAN uses encryption or not. My Ubuntu is a default install from a USB stick Live CD made with unetbootin this weekend.

1 ) Machine Brand and Model (PC/Laptop): IBM T42
2 ) Wireless Brand, Model and Wireless Chipset: 
Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
3 ) check interface:

ath0      Link encap:Ethernet  HWaddr 00:14:a4:67:bb:24  
          inet addr:192.168.0.107  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe67:bb24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:651264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:309223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:875922738 (875.9 MB)  TX bytes:31628227 (31.6 MB)

wifi0     Link encap:UNSPEC  HWaddr 00-14-A4-67-BB-24-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1082853 errors:0 dropped:0 overruns:0 frame:78444
          TX packets:311034 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:950033423 (950.0 MB)  TX bytes:39132673 (39.1 MB)
          Interrupt:11 

4 ) Check for modules: 

lsmod | grep wlan
wlan_tkip              19456  0 
wlan_ccmp              15104  0 
wlan_scan_sta          20608  1 
wlan                  211952  6 ath_pci,wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample

lsmod | grep ath
ath_pci                99096  0 
ath_rate_sample        19968  1 
wlan                  211952  6 ath_pci,wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample
ath_hal               198864  3 ath_pci,ath_rate_sample

5 ) Kernel boot messages

[   15.005237] ath_hal: module license 'Proprietary' taints kernel.
[   15.007020] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   15.196123] ath_pci: 0.9.4
[   15.669059] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   16.395153] ath_rate_sample: 1.2 (0.9.4)
[  233.044042] ath0: no IPv6 routers present
[ 1806.316839] ath_pci 0000:02:02.0: PCI INT A disabled
[ 1807.820135] ath_pci 0000:02:02.0: restoring config space at offset 0x3 (was 0x5008, writing 0xa808)
[ 1807.820150] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1809.871775] ADDRCONF(NETDEV_UP): ath0: link is not ready
[ 1815.811831] ath_pci 0000:02:02.0: PCI INT A disabled
[ 1817.308137] ath_pci 0000:02:02.0: restoring config space at offset 0x3 (was 0x5008, writing 0xa808)
[ 1817.308152] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1819.511348] ADDRCONF(NETDEV_UP): ath0: link is not ready
[ 1982.838569] ADDRCONF(NETDEV_UP): ath0: link is not ready
[ 1992.646183] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[ 2002.808038] ath0: no IPv6 routers present
[ 6505.312219] ath_pci 0000:02:02.0: PCI INT A disabled
[ 6505.312292] ath_pci: driver unloaded
[ 6511.764321] ath_pci: 0.9.4
[ 6511.766000] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 6527.992031] ath0: no IPv6 routers present
[10777.364089] ath_pci 0000:02:02.0: PCI INT A disabled
[10777.365069] ath_pci: driver unloaded
[10784.635075] ath_pci: 0.9.4
[10784.636442] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[10799.928036] ath0: no IPv6 routers present
[22975.884120] ath_pci 0000:02:02.0: PCI INT A disabled
[22975.884732] ath_pci: driver unloaded
[22983.655824] ath_pci: 0.9.4
[22983.657170] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[22998.616034] ath0: no IPv6 routers present
[45814.648120] ath_pci 0000:02:02.0: PCI INT A disabled
[45814.648645] ath_pci: driver unloaded
[45821.608199] ath_pci: 0.9.4
[45821.609648] ath_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[45840.156024] ath0: no IPv6 routers present

dmesg |grep wlan
[   15.127226] wlan: 0.9.4
dmesg |grep wifi
[   16.395714] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   16.395724] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   16.395754] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   16.395766] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   16.395772] wifi0: mac 5.9 phy 4.3 radio 3.6
[   16.395777] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   16.395779] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   16.395782] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   16.395784] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   16.395786] wifi0: Use hw queue 8 for CAB traffic
[   16.395789] wifi0: Use hw queue 9 for beacons
[   16.400724] wifi0: Atheros 5212: mem=0xc0210000, irq=11
[ 6512.744950] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 6512.744964] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[ 6512.744970] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[ 6512.744982] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[ 6512.744987] wifi0: mac 5.9 phy 4.3 radio 3.6
[ 6512.744994] wifi0: Use hw queue 1 for WME_AC_BE traffic
[ 6512.744996] wifi0: Use hw queue 0 for WME_AC_BK traffic
[ 6512.744999] wifi0: Use hw queue 2 for WME_AC_VI traffic
[ 6512.745001] wifi0: Use hw queue 3 for WME_AC_VO traffic
[ 6512.745004] wifi0: Use hw queue 8 for CAB traffic
[ 6512.745006] wifi0: Use hw queue 9 for beacons
[ 6512.748040] wifi0: Atheros 5212: mem=0xc0210000, irq=11
[10785.126168] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[10785.126183] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[10785.126188] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[10785.126200] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[10785.126206] wifi0: mac 5.9 phy 4.3 radio 3.6
[10785.126216] wifi0: Use hw queue 1 for WME_AC_BE traffic
[10785.126219] wifi0: Use hw queue 0 for WME_AC_BK traffic
[10785.126221] wifi0: Use hw queue 2 for WME_AC_VI traffic
[10785.126224] wifi0: Use hw queue 3 for WME_AC_VO traffic
[10785.126226] wifi0: Use hw queue 8 for CAB traffic
[10785.126228] wifi0: Use hw queue 9 for beacons
[10785.131446] wifi0: Atheros 5212: mem=0xc0210000, irq=11
[22984.136408] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[22984.136423] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[22984.136429] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[22984.136441] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[22984.136446] wifi0: mac 5.9 phy 4.3 radio 3.6
[22984.136453] wifi0: Use hw queue 1 for WME_AC_BE traffic
[22984.136456] wifi0: Use hw queue 0 for WME_AC_BK traffic
[22984.136458] wifi0: Use hw queue 2 for WME_AC_VI traffic
[22984.136461] wifi0: Use hw queue 3 for WME_AC_VO traffic
[22984.136463] wifi0: Use hw queue 8 for CAB traffic
[22984.136465] wifi0: Use hw queue 9 for beacons
[22984.142261] wifi0: Atheros 5212: mem=0xc0210000, irq=11
[45825.152930] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[45825.152946] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[45825.152952] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[45825.152964] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[45825.152970] wifi0: mac 5.9 phy 4.3 radio 3.6
[45825.152980] wifi0: Use hw queue 1 for WME_AC_BE traffic
[45825.152983] wifi0: Use hw queue 0 for WME_AC_BK traffic
[45825.152985] wifi0: Use hw queue 2 for WME_AC_VI traffic
[45825.152988] wifi0: Use hw queue 3 for WME_AC_VO traffic
[45825.152990] wifi0: Use hw queue 8 for CAB traffic
[45825.152993] wifi0: Use hw queue 9 for beacons
[45825.161734] wifi0: Atheros 5212: mem=0xc0210000, irq=11

6 ) Network configuration
  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:14:a4:67:bb:24
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.0.107 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

7 ) Scan for networks:

ath0      Scan completed :
          Cell 01 - Address: 00:13:49:A4:6E:07
                    ESSID:"ZyXEL"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-47 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:wme_ie=dd180050f2020101000003a4140027a4000042435e0062322f00

8 ) Ubuntu Version: 

 lsb_release -d
Description:	Ubuntu 8.10

9 ) Kernel/architecture (including 32 vs. 64 bit): 

2.6.27-11-generic i686

---

