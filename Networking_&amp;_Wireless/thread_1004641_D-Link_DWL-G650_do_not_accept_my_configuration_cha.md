---
title: "D-Link DWL-G650 do not accept my configuration change"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by redification on 2008-12-07
Dear Sir,
Please help me to figure out the problem for my D-Link DWL-G650 PCMCIA card. I have latest version of Madwifi compiled and installed but the driver do not accept my iwpriv configuration change and remain at 802.11b, first channel, and the failing configuration commands just finished silently (no error message sigh). 
e.g. I tried:
iwpriv ath0 mode 11g
iwconfig ath0 channel 10
The commands finish without any error prompt but the iwconfig doesn't change.
Here is the listing of information requested by the HOWTO:

1) Libretto L2

2) lspci:
01:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)

3) ifconfig:
ath0      Link encap:Ethernet  HWaddr 00:1b:11:b4:c0:9f  
          inet6 addr: fe80::21b:11ff:feb4:c09f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:00:39:51:6b:99  
          inet addr:192.168.1.201  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe51:6b99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1099050 (1.0 MB)  TX bytes:122774 (119.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1B-11-B4-C0-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:976
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"Golden"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-98 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4) lsmod | grep ath
ath_rate_sample        14208  1 
ath_pci               100896  0 
wlan                  207088  3 ath_rate_sample,ath_pci
ath_hal               192592  3 ath_rate_sample,ath_pci

5) dmesg extract
[  181.100515] pccard: CardBus card inserted into slot 0
[  181.686118] ath_hal: module license 'Proprietary' taints kernel.
[  181.704535] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[  182.106037] wlan: 0.9.4
[  182.190872] ath_pci: 0.9.4
[  182.194607] PCI: Enabling device 0000:01:00.0 (0000 -> 0002)
[  182.196560] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[  182.966319] ath_rate_sample: 1.2 (0.9.4)
[  182.989609] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[  182.989729] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  182.990454] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[  182.990498] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[  182.990540] wifi0: mac 7.9 phy 4.5 radio 5.6
[  182.990639] wifi0: Use hw queue 1 for WME_AC_BE traffic
[  182.990653] wifi0: Use hw queue 0 for WME_AC_BK traffic
[  182.990667] wifi0: Use hw queue 2 for WME_AC_VI traffic
[  182.990679] wifi0: Use hw queue 3 for WME_AC_VO traffic
[  182.990691] wifi0: Use hw queue 8 for CAB traffic
[  182.990702] wifi0: Use hw queue 9 for beacons
[  183.018170] unable to load wlan_scan_sta
[  183.027226] wifi0: Atheros 5212: mem=0x14000000, irq=11
[  191.812690] ath0: no IPv6 routers present
[  200.600957] [drm] Initialized drm 1.1.0 20060810
[  200.710824] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[  200.710937] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[  200.716447] [drm] Initialized savage 2.4.1 20050313 on minor 0

6) sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: e
       bus info: pci@0000:00:0e.0
       logical name: eth0
       version: 08
       serial: 00:00:39:51:6b:99
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.201 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: AR5001-0000-0000
       product: Wireless LAN Reference Card
       vendor: Atheros Communications, Inc.
       physical id: 0
       version: 00
       slot: Socket 0
       resources: irq:11
  *-network
       description: Wireless interface
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:1b:11:b4:c0:9f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11b

7) iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      No scan results

8) lsb_release -d
Description:    Ubuntu 8.04.1

9) uname -mr
2.6.24-19-generic i686

10) sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                            [ OK ] 


10) /etc/init.d/networking restart

---

### Post by redification on 2008-12-07
Hi guys,

Problem solved :)
My previous problem is due to a stale setting in /etc/modprobe.d/ralink entry "wlan* rt73" that I set before for a USB WLAN thumb. That is the same problem mentioned from:
[http://madwifi-project.org/ticket/1737](http://madwifi-project.org/ticket/1737)

I successfully setup WPA2-AES with wpa_supplicant too, yay!!!!

---

### Post by Ryuhayabusa on 2009-04-30
Hey man,

I've had a lot of problems trying to connect to my university network WPA-TKIP-MSCHAPV2

are you connecting to AES-CCP. with network manager aswell?

I am able to connect to wpa-psk at home.

---

