---
title: "Asus N15 wireless card issue (reealtek rtl 8188CE)"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by MButterman on 2012-12-03
Hello Forums,

Currently I have 12.04 LTS 64 bit (fully updated as of 12-03) My motherborad is MSI 880GM-E43. CPU is AMD Phenom 2 X6 and have 16 Gb of RAM.

I have successfully compiled the latest driver from the Realtek website and installed with no errors. 

The issue is the when I use speedtest, I get 20 Mbps but at random times it will fall to 2 Mbps. I am using a Netgear CG3000D DOCSIS 3.0 cable modem and router. After talking to COX Communications. My speed should be 20 Mbps and things are fine on their end.

uname -mr

```
3.2.0-34-generic x86_64
```

lspci


```

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Redwood PRO [Radeon HD 5500 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Redwood HDMI Audio [Radeon HD 5000 Series]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
```

lsmod | grep rtl

```
rtl8192ce             137478  0 
rtlwifi               118749  1 rtl8192ce
mac80211              506816  2 rtl8192ce,rtlwifi
cfg80211              205544  2 rtlwifi,mac80211
```

iwconfig

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"B13679"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 84:1B:5E:B1:36:79   
          Bit Rate=144.4 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:57   Missed beacon:0

eth0      no wireless extensions.
```

dmesg | tail -50

```
[41554.844364] cfg80211: Calling CRDA to update world regulatory domain
[41554.853830] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[41554.853839] cfg80211: World regulatory domain updated:
[41554.853844] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[41554.853853] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41554.853860] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41554.853867] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41554.853873] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41554.853880] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41556.110467] wlan0: authenticate with 84:1b:5e:b1:36:79 (try 1)
[41556.112191] wlan0: authenticated
[41556.112556] wlan0: associate with 84:1b:5e:b1:36:79 (try 1)
[41556.115992] wlan0: RX ReassocResp from 84:1b:5e:b1:36:79 (capab=0x411 status=0 aid=1)
[41556.116034] wlan0: associated
[41729.616182] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[41729.616236] wlan0: Connection to AP 84:1b:5e:b1:36:79 lost.
[41729.732425] cfg80211: All devices are disconnected, going to restore regulatory settings
[41729.732437] cfg80211: Restoring regulatory settings
[41729.732445] cfg80211: Calling CRDA to update world regulatory domain
[41729.741782] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[41729.741791] cfg80211: World regulatory domain updated:
[41729.741796] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[41729.741805] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41729.741812] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41729.741819] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41729.741825] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41729.741831] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41730.666507] wlan0: authenticate with 84:1b:5e:b1:36:79 (try 1)
[41730.668398] wlan0: authenticated
[41730.668681] wlan0: associate with 84:1b:5e:b1:36:79 (try 1)
[41730.672034] wlan0: RX ReassocResp from 84:1b:5e:b1:36:79 (capab=0x411 status=0 aid=1)
[41730.672044] wlan0: associated
[41789.736114] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[41789.736147] wlan0: Connection to AP 84:1b:5e:b1:36:79 lost.
[41789.848379] cfg80211: All devices are disconnected, going to restore regulatory settings
[41789.848391] cfg80211: Restoring regulatory settings
[41789.848399] cfg80211: Calling CRDA to update world regulatory domain
[41789.857584] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[41789.857593] cfg80211: World regulatory domain updated:
[41789.857599] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[41789.857607] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41789.857615] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41789.857622] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[41789.857628] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41789.857634] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[41791.114469] wlan0: authenticate with 84:1b:5e:b1:36:79 (try 1)
[41791.116420] wlan0: authenticated
[41791.116722] wlan0: associate with 84:1b:5e:b1:36:79 (try 1)
[41791.125289] wlan0: RX ReassocResp from 84:1b:5e:b1:36:79 (capab=0x411 status=0 aid=1)
[41791.125299] wlan0: associated
```

sudo lshw -C network

```
 *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: f4:6d:04:a2:9f:49
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-34-generic firmware=N/A ip=192.168.0.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 ioport:c800(size=256) memory:fe9fc000-fe9fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 6c:62:6d:eb:9d:c0
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:d800(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff memory:feae0000-feafffff
```

Here is the results of my testing, If you require any further information please let me know and thank you in advance for you help, It's greatly appreciated.

---

### Post by MButterman on 2012-12-29
Needless to say, it has been quite a while since I have started this thread. I have learned the following:

1. the installation of the realtek driver offers no improvement out of the box. I am still looking at a possible configuration issue.

2. If a Ethernet connection is readily available, it is the better choice.

3. Make sure you check to see if you WiFi card is compatible with Ubuntu. In my case, I am running 12.04.

I have switched to a Ethernet connection and still researching the WiFi issue. What I don't understand is that this is the forum to ask network questions and I even went as far as provide all the information up front. 

I want to open this thread to what I could have done to elicit a better response with the question I submitted. I really think I am missing something here. Thank you in advance for your comments and advice.

---

### Post by praseodym on 2012-12-29
Did you try/use pure WPA2-AES encryption? This is more stable than mixed WPA/WPA2. Please check:

```
dmesg | grep rtl8
```
Alternatively, try Wicd instead of the network-manager.

---

