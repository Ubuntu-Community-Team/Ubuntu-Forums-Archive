---
title: "WiFi connection instantly disconnects"
date: 2019-01-11
forum: MINT
---

### Post by jonny62 on 2019-01-11
Hello,

need help to get internet connection via wifi or Ethernet on Linux Mint 18.3 Cinnamon 64-bit
both connections, wired or wi-fi, gets instantly disconnected after connection established.
system message: “disconnected - you are now offline”
router event log: connecting via wifi but no name and no IP-address; 25sec later disconnecting
WLAN-Gerät angemeldet (2,4 GHz). Name: -, IP-Adresse: -, MAC-Adresse: 38E:AD:35:6C:27, Geschwindigkeit 300 Mbit/s.
WLAN-Gerät abgemeldet (2,4 GHz). Name: -, MAC-Adresse: 38E:AD:35:6C:27.

any idea?
Thanks!

```

########## wireless info START ##########

Report from: 11 Jan 2019 14:33 CET +0100

Booted last: 11 Jan 2019 00:00 CET +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia

##### kernel ############################

Linux 4.15.0-43-generic #46~16.04.1-Ubuntu SMP Fri Dec 7 13:31:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Dual Band Wireless-AC 8260 [8086:0010]
    Kernel driver in use: iwlwifi

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a70]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0461:4d22 Primax Electronics, Ltd
Bus 001 Device 003: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 002: ID 04a9:1801 Canon, Inc.
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 006: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

iwlmvm                364544  0
wl                   6447104  0
mac80211              778240  1 iwlmvm
iwlwifi               282624  1 iwlmvm
cfg80211              622592  4 wl,iwlmvm,iwlwifi,mac80211
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: wlp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm  
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1004     1  0 14:22 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260 (Dual Band Wireless-AC 8260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.15.0-43-generic
GENERAL.FIRMWARE-VERSION:               34.0.1
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                      
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e748ac0b-32ba-4199-9f6e-cc13e65012ed | MAJOR-TOM

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:              
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                      
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS:

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  *
MAJOR-TOM            <MAC 'MAJOR-TOM' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
WLAN-750721          <MAC 'WLAN-750721' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA2         no        
o2-WLAN88            <MAC 'o2-WLAN88' [AC7]>  Infra  10    2457 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2         no        
WLANHub              <MAC 'WLANHub' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
WLAN-750721          <MAC 'WLAN-750721' [AC6]>  Infra  100   5500 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA2         no        
Unitymedia WifiSpot  <MAC 'Unitymedia WifiSpot' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA2 802.1X  no        
Elsey+Paderborn      <MAC 'Elsey+Paderborn' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2         no        
Unitymedia WifiSpot  <MAC 'Unitymedia WifiSpot' [AC9]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA2 802.1X  no        
UPC99C9542           <MAC 'UPC99C9542' [AC8]>  Infra  11    2462 MHz  54 Mbit/s  30      &#9602;___  WPA1 WPA2    no        
UPC3783577           <MAC 'UPC3783577' [AC10]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA1 WPA2    no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/MAJOR-TOM]] (600 root)
[connection] id=MAJOR-TOM | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=MAJOR-TOM
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      4   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'MAJOR-TOM' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"MAJOR-TOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000032337a5
                    Extra: Last beacon: 432ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Elsey+Paderborn' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Elsey+Paderborn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000072a1bafdb
                    Extra: Last beacon: 560ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WLAN-750721' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"WLAN-750721"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bc7a7612c3
                    Extra: Last beacon: 428ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'WLANHub' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"WLANHub"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008a6e4d8f22
                    Extra: Last beacon: 156ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Unitymedia WifiSpot' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Unitymedia WifiSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008a6e4da0e1
                    Extra: Last beacon: 196ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'WLAN-750721' [AC6]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"WLAN-750721"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bc7ab1cc2a
                    Extra: Last beacon: 92ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'o2-WLAN88' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN88"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026c866d34ab
                    Extra: Last beacon: 240ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'UPC99C9542' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"UPC99C9542"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000071b3961c9e
                    Extra: Last beacon: 176ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'Unitymedia WifiSpot' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Unitymedia WifiSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000071b250c10d
                    Extra: Last beacon: 21508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC 'UPC3783577' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"UPC3783577"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d134b94ac5
                    Extra: Last beacon: 18912ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     84D6FD7BC225615672A8C5B
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       4.15.0-43-generic SMP mod_unload
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[wl]
filename:       /lib/modules/4.15.0-43-generic/updates/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.0-43-generic SMP mod_unload
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[mac80211]
filename:       /lib/modules/4.15.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     10B87D6D65DDD085D1326C9
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-43-generic SMP mod_unload
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-34.ucode
firmware:       iwlwifi-8000C-34.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-34.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-34.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-34.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-34.ucode
srcversion:     773231C3AA2E3CAB7CBD42B
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.15.0-43-generic SMP mod_unload
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.15.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-43-generic SMP mod_unload
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

mount -t ext4 /dev/sdb3 /media/norbert/DATA

mount --bind /media/norbert/DATA/Bilder  /home/norbert/Bilder
mount --bind /media/norbert/DATA/Videos  /home/norbert/Videos
mount --bind /media/norbert/DATA/Musik  /home/norbert/Musik

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    3.246415] iwlwifi 0000:01:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
[    3.258606] wl: loading out-of-tree module taints kernel.
[    3.258609] wl: module license 'MIXED/Proprietary' taints kernel.
[    3.261444] wl: module verification failed: signature and/or required key missing - tainting kernel
[    3.268641] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    3.339734] iwlwifi 0000:01:00.0: base HW address: <MAC 'wlp1s0' [IF2]>
[    3.415700] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.416806] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    3.859588] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    3.861522] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    3.922564] r8169 0000:02:00.0 enp2s0: link down
[    3.922645] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[  561.564077] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[  569.899781] wlp1s0: authenticate with <MAC 'MAJOR-TOM' [AC1]>
[  569.902449] wlp1s0: send auth to <MAC 'MAJOR-TOM' [AC1]> (try 1/3)
[  569.911807] wlp1s0: authenticated
[  569.913285] wlp1s0: associate with <MAC 'MAJOR-TOM' [AC1]> (try 1/3)
[  569.935473] wlp1s0: RX AssocResp from <MAC 'MAJOR-TOM' [AC1]> (capab=0x431 status=0 aid=1)
[  569.938143] wlp1s0: associated
[  569.974796] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  601.017357] wlp1s0: deauthenticating from <MAC 'MAJOR-TOM' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

---

### Post by jeremy31 on 2019-01-11
```
 sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo apt remove bcmwl-kernel-source
```
Reboot

---

### Post by jonny62 on 2019-01-11
thanks for your quick response!
no change; wi-fi gets instantly disconnected after connection established.
system message: “disconnected - you are now offline”

```

########## wireless info START ##########

Report from: 11 Jan 2019 15:56 CET +0100

Booted last: 11 Jan 2019 00:00 CET +0100

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    LinuxMint
Description:    Linux Mint 18.3 Sylvia
Release:    18.3
Codename:    sylvia

##### kernel ############################

Linux 4.15.0-43-generic #46~16.04.1-Ubuntu SMP Fri Dec 7 13:31:08 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Cinnamon

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Dual Band Wireless-AC 8260 [8086:0010]
    Kernel driver in use: iwlwifi

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168]  (rev 15)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1462:7a70]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 003: ID 046a:0023 Cherry GmbH CyMotion Master Linux Keyboard G230
Bus 001 Device 002: ID 04a9:1801 Canon, Inc. 
Bus 001 Device 006: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 005: ID 090c:1000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

iwlmvm                364544  0
mac80211              778240  1 iwlmvm
iwlwifi               282624  1 iwlmvm
cfg80211              622592  3 iwlmvm,iwlwifi,mac80211
intel_wmi_thunderbolt    16384  0
mxm_wmi                16384  0
wmi                    24576  2 intel_wmi_thunderbolt,mxm_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback 

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: wlp1s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:eek:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:ff
          

##### route #############################

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/resolvconf/resolv.conf']

##### network managers ##################

Installed:

    NetworkManager

Running:

root       969     1  0 15:55 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260 (Dual Band Wireless-AC 8260)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.15.0-43-generic
GENERAL.FIRMWARE-VERSION:               34.0.1
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e748ac0b-32ba-4199-9f6e-cc13e65012ed | MAJOR-TOM

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.6/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                 BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
MAJOR-TOM            <MAC 'MAJOR-TOM' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  99      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
WLAN-750721          <MAC 'WLAN-750721' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  79      &#9602;&#9604;&#9606;_  WPA2         no        
o2-WLAN88            <MAC 'o2-WLAN88' [AC4]>  Infra  10    2457 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2         no        
Elsey+Paderborn      <MAC 'Elsey+Paderborn' [AC2]>  Infra  1      2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2         no        
Unitymedia WifiSpot  <MAC 'Unitymedia WifiSpot' [AC6]>  Infra  11     2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2 802.1X  no        
WLANHub              <MAC 'WLANHub' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA1 WPA2    no        
WLAN-750721          <MAC 'WLAN-750721' [AC7]>  Infra  100   5500 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2         no        
WLAN-UDZS47          <MAC 'WLAN-UDZS47' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2         no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 2

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/MAJOR-TOM]] (600 root)
[connection] id=MAJOR-TOM | type=wifi | autoconnect=false | permissions=user:norbert:;
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=MAJOR-TOM
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'MAJOR-TOM' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:eek:n
                    ESSID:"MAJOR-TOM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000912074e
                    Extra: Last beacon: 2600ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Elsey+Paderborn' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:eek:n
                    ESSID:"Elsey+Paderborn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000008525c525a
                    Extra: Last beacon: 2944ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'WLAN-750721' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:eek:n
                    ESSID:"WLAN-750721"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bda34ae5b7
                    Extra: Last beacon: 2724ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'o2-WLAN88' [AC4]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:eek:n
                    ESSID:"o2-WLAN88"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026daf4029b7
                    Extra: Last beacon: 2568ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'WLANHub' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:eek:n
                    ESSID:"WLANHub"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008b97217dbd
                    Extra: Last beacon: 2528ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Unitymedia WifiSpot' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:eek:n
                    ESSID:"Unitymedia WifiSpot"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008b9721a0f2
                    Extra: Last beacon: 2520ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC 'WLAN-750721' [AC7]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:eek:n
                    ESSID:"WLAN-750721"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001bda393f84e
                    Extra: Last beacon: 1504ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'WLAN-UDZS47' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:eek:n
                    ESSID:"WLAN-UDZS47"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001211e439640
                    Extra: Last beacon: 15372ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     84D6FD7BC225615672A8C5B
depends:        iwlwifi,mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           iwlmvm
vermagic:       4.15.0-43-generic SMP mod_unload 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:razz:ower management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.15.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     10B87D6D65DDD085D1326C9
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-43-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:grin:efault rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.15.0-43-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-34.ucode
firmware:       iwlwifi-8000C-34.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0-34.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-b0-jf-b0-34.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-hr-a0-34.ucode
firmware:       iwlwifi-QuQnj-a0-jf-b0-34.ucode
firmware:       iwlwifi-QuQnj-f0-hr-a0-34.ucode
firmware:       iwlwifi-Qu-a0-jf-b0-34.ucode
firmware:       iwlwifi-Qu-a0-hr-a0-34.ucode
srcversion:     773231C3AA2E3CAB7CBD42B
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           iwlwifi
vermagic:       4.15.0-43-generic SMP mod_unload 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full,  2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:grin:isable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.15.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-43-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:grin:isable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

mount -t ext4 /dev/sdb3 /media/norbert/DATA

mount --bind /media/norbert/DATA/Bilder  /home/norbert/Bilder
mount --bind /media/norbert/DATA/Videos  /home/norbert/Videos
mount --bind /media/norbert/DATA/Musik  /home/norbert/Musik

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    3.252262] iwlwifi 0000:01:00.0: loaded firmware version 34.0.1 op_mode iwlmvm
[    3.274326] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    3.355514] iwlwifi 0000:01:00.0: base HW address: <MAC 'wlp1s0' [IF2]>
[    3.431969] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.433857] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    3.745458] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[    3.983147] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    4.042659] r8169 0000:02:00.0 enp2s0: link down
[    4.042740] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    4.103166] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   22.874429] wlp1s0: authenticate with <MAC 'MAJOR-TOM' [AC1]>
[   22.877583] wlp1s0: send auth to <MAC 'MAJOR-TOM' [AC1]> (try 1/3)
[   22.886646] wlp1s0: authenticated
[   22.888250] wlp1s0: associate with <MAC 'MAJOR-TOM' [AC1]> (try 1/3)
[   22.891954] wlp1s0: RX AssocResp from <MAC 'MAJOR-TOM' [AC1]> (capab=0x431 status=0 aid=1)
[   22.895637] wlp1s0: associated
[   22.917671] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[   55.007166] wlp1s0: deauthenticating from <MAC 'MAJOR-TOM' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############

```

---

### Post by jonny62 on 2019-01-12
any other idea to solve the problem?
is there an easy way to remove all network settings and reinstall the network-manager to have a new untouched installation
this might be easier as figure out the details for that problem.....

---

### Post by agklimit on 2019-02-01
I've seen a lot of wifi dropping out (after a while - usually 20-30 min. of connection) for no reason on both Mint and Ubuntu going back at least to versions 16/17 of both OSs.

Haven't seen this case when it drops out instantly, though.

Perhaps some of these things can help (I just had to apply them to my Mint 19.1, so I'm still no 100% sure that it will work.)

> 

Solution for wifi dropping out:

[http://seyferseed.ru/en/life-en/ubuntu-realtek-rtl8723ae-driver-fix-slow-wifi-speed-fix.html#sthash.UxI93rDK.dpbs](http://seyferseed.ru/en/life-en/ubuntu-realtek-rtl8723ae-driver-fix-slow-wifi-speed-fix.html#sthash.UxI93rDK.dpbs)

Also: [https://forums.linuxmint.com/viewtopic.php?t=230759](https://forums.linuxmint.com/viewtopic.php?t=230759) 



---

### Post by jeremy31 on 2019-02-01
You could change encryption on your wifi router to WPA2 only, no WEP/TKIP.  Then change Network Manager settings for the connection to disable IPv6

---

### Post by agklimit on 2019-02-01
^^Just to quickly confirm that this worked for me - got no wi-fi dropping out since these alterations (suggested in those links).

---

