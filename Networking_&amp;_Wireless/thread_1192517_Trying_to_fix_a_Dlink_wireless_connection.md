---
title: "Trying to fix a Dlink wireless connection"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by Speedwagon on 2009-06-20
Seems to be a common problem, but I can't seem to find a solid fix upon searching.  Reading through some other threads, I gathered the following information, in hopes that it might help others help me.  Connects consistently, but only at 1 Mb/s, and eventually stops responding until I reconnect it.

> **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Midzwerker Net"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1B:11:71:5E:2A   
          **Bit Rate=1 Mb/s**   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Power Management: off
          Link Quality=64/100  Signal level:-53 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

> **lspci**
00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
**03:01.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)**
03:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)


> **grep wlan /var/log/kern.log**
Jun 15 05:31:31 mitch-desktop kernel: [608025.874736] wlan0: deauthenticated
Jun 15 05:31:32 mitch-desktop kernel: [608026.873039] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 1
Jun 15 05:31:32 mitch-desktop kernel: [608026.877381] wlan0 direct probe responded
Jun 15 05:31:32 mitch-desktop kernel: [608026.877387] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 15 05:31:32 mitch-desktop kernel: [608026.879626] wlan0: authenticated
Jun 15 05:31:32 mitch-desktop kernel: [608026.879632] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 15 05:31:32 mitch-desktop kernel: [608026.883372] wlan0: RX ReassocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=1)
Jun 15 05:31:32 mitch-desktop kernel: [608026.883377] wlan0: associated
Jun 15 19:30:10 mitch-desktop kernel: [658344.766841] wlan0: deauthenticated
Jun 15 19:30:11 mitch-desktop kernel: [658345.765018] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 1
Jun 15 19:30:11 mitch-desktop kernel: [658345.769230] wlan0 direct probe responded
Jun 15 19:30:11 mitch-desktop kernel: [658345.769233] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 15 19:30:11 mitch-desktop kernel: [658345.770946] wlan0: authenticated
Jun 15 19:30:11 mitch-desktop kernel: [658345.770948] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 15 19:30:11 mitch-desktop kernel: [658345.774707] wlan0: RX ReassocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=1)
Jun 15 19:30:11 mitch-desktop kernel: [658345.774710] wlan0: associated
Jun 15 21:18:48 mitch-desktop kernel: [   23.929942] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 15 21:19:05 mitch-desktop kernel: [   41.602434] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 1
Jun 15 21:19:05 mitch-desktop kernel: [   41.606659] wlan0 direct probe responded
Jun 15 21:19:05 mitch-desktop kernel: [   41.606665] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 15 21:19:05 mitch-desktop kernel: [   41.608369] wlan0: authenticated
Jun 15 21:19:05 mitch-desktop kernel: [   41.608371] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 15 21:19:05 mitch-desktop kernel: [   41.612835] wlan0: RX AssocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=1)
Jun 15 21:19:05 mitch-desktop kernel: [   41.612839] wlan0: associated
Jun 15 21:19:05 mitch-desktop kernel: [   41.628517] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 15 21:19:16 mitch-desktop kernel: [   52.269016] wlan0: no IPv6 routers present
Jun 15 21:19:54 mitch-desktop kernel: [   90.124188] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 1
Jun 15 21:19:54 mitch-desktop kernel: [   90.128066] wlan0: disassociating by local choice (reason=3)
Jun 15 21:19:54 mitch-desktop kernel: [   90.141453] wlan0 direct probe responded
Jun 15 21:19:54 mitch-desktop kernel: [   90.141465] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 15 21:19:54 mitch-desktop kernel: [   90.147522] wlan0: authenticated
Jun 15 21:19:54 mitch-desktop kernel: [   90.147532] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 15 21:19:54 mitch-desktop kernel: [   90.150936] wlan0: RX AssocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=1)
Jun 15 21:19:54 mitch-desktop kernel: [   90.150944] wlan0: associated
Jun 15 21:19:54 mitch-desktop kernel: [   90.160531] wlan0: disassociating by local choice (reason=3)
Jun 15 21:19:54 mitch-desktop kernel: [   90.172185] wlan0: deauthenticated
Jun 17 21:45:55 mitch-desktop kernel: [   25.193938] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 17 21:47:14 mitch-desktop kernel: [  100.495666] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 17 21:47:14 mitch-desktop kernel: [  100.497614] wlan0: authenticated
Jun 17 21:47:14 mitch-desktop kernel: [  100.497623] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 17 21:47:14 mitch-desktop kernel: [  100.501854] wlan0: RX AssocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=2)
Jun 17 21:47:14 mitch-desktop kernel: [  100.501862] wlan0: associated
Jun 17 21:47:14 mitch-desktop kernel: [  100.512772] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 17 21:47:25 mitch-desktop kernel: [  110.692022] wlan0: no IPv6 routers present
Jun 17 21:48:00 mitch-desktop kernel: [  145.815577] wlan0: disassociating by local choice (reason=3)
Jun 17 22:19:11 mitch-desktop kernel: [ 2016.845922] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 17 22:19:11 mitch-desktop kernel: [ 2016.992040] wlan0: authenticated
Jun 17 22:19:11 mitch-desktop kernel: [ 2016.992051] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 17 22:19:11 mitch-desktop kernel: [ 2016.997858] wlan0: RX AssocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=2)
Jun 17 22:19:11 mitch-desktop kernel: [ 2016.997863] wlan0: associated
Jun 18 16:21:25 mitch-desktop kernel: [66950.773039] wlan0: No ProbeResp from current AP 00:1b:11:71:5e:2a - assume out of range
Jun 18 16:21:25 mitch-desktop kernel: [66951.541395] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 1
Jun 18 16:21:26 mitch-desktop kernel: [66951.740041] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 2
Jun 18 16:21:26 mitch-desktop kernel: [66951.941058] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 3
Jun 18 16:21:26 mitch-desktop kernel: [66952.141064] wlan0: direct probe to AP 00:1b:11:71:5e:2a timed out
Jun 18 16:21:41 mitch-desktop kernel: [66967.159172] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 1
Jun 18 16:21:41 mitch-desktop kernel: [66967.357043] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 2
Jun 18 16:21:41 mitch-desktop kernel: [66967.557045] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 3
Jun 18 16:21:42 mitch-desktop kernel: [66967.757214] wlan0: direct probe to AP 00:1b:11:71:5e:2a timed out
Jun 18 16:21:44 mitch-desktop kernel: [66970.523122] wlan0 direct probe responded
Jun 18 16:21:44 mitch-desktop kernel: [66970.523133] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 18 16:21:45 mitch-desktop kernel: [66970.721039] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 18 16:21:45 mitch-desktop kernel: [66970.920042] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 18 16:21:45 mitch-desktop kernel: [66971.120041] wlan0: authentication with AP 00:1b:11:71:5e:2a timed out
Jun 18 16:21:52 mitch-desktop kernel: [66977.851125] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 18 16:21:52 mitch-desktop kernel: [66978.049039] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 18 16:21:52 mitch-desktop kernel: [66978.249035] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 18 16:21:52 mitch-desktop kernel: [66978.448050] wlan0: authentication with AP 00:1b:11:71:5e:2a timed out
Jun 18 16:22:02 mitch-desktop kernel: [66988.538916] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 18 16:22:02 mitch-desktop kernel: [66988.540812] wlan0: authenticated
Jun 18 16:22:02 mitch-desktop kernel: [66988.540817] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 18 16:22:02 mitch-desktop kernel: [66988.545280] wlan0: RX AssocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=1)
Jun 18 16:22:02 mitch-desktop kernel: [66988.545287] wlan0: associated
Jun 19 11:06:41 mitch-desktop kernel: [134466.149885] wlan0: deauthenticated
Jun 19 11:06:42 mitch-desktop kernel: [134467.149034] wlan0: direct probe to AP 00:1b:11:71:5e:2a try 1
Jun 19 11:06:42 mitch-desktop kernel: [134467.153544] wlan0 direct probe responded
Jun 19 11:06:42 mitch-desktop kernel: [134467.153550] wlan0: authenticate with AP 00:1b:11:71:5e:2a
Jun 19 11:06:42 mitch-desktop kernel: [134467.155141] wlan0: authenticated
Jun 19 11:06:42 mitch-desktop kernel: [134467.155147] wlan0: associate with AP 00:1b:11:71:5e:2a
Jun 19 11:06:42 mitch-desktop kernel: [134467.160283] wlan0: RX ReassocResp from 00:1b:11:71:5e:2a (capab=0x431 status=0 aid=1)
Jun 19 11:06:42 mitch-desktop kernel: [134467.160289] wlan0: associated


---

