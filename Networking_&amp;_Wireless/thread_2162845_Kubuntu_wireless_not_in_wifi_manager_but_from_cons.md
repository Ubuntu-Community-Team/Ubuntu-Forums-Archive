---
title: "Kubuntu wireless not in wifi manager but from console it works.."
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by daaatz on 2013-07-16
Hi,

like on screen tab with wifi if disabled and dunno why because I installed drivers and see using command that my wifi works fine, even iwlist scan shows APs.
Here are some details and screen:

> 

*************** info trace ***************

***** uname -a *****

Linux maciej-HP-Pavilion-g6-Notebook-PC 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18 17:39:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

07:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]
    Subsystem: Hewlett-Packard Company Device [103c:18ec]
    Kernel driver in use: rt2860
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:183e]
    Kernel driver in use: r8169

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 064e:e263 Suyin Corp. 
Bus 001 Device 004: ID 1bcf:0007 Sunplus Innovation Technology Inc. Optical Mouse

***** iwconfig *****

ra0       Ralink STA  ESSID:"UBU"  Nickname:"RT3290STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=26 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-77 dBm  Noise level:-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


***** rfkill *****

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

***** lsmod *****

rt3290sta            1182383  1 

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0  [Ppo&#322;&#261;czenie przewodowe] -------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             62.179.1.62
    DNS:             62.179.1.63



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC address removed>,

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

ra0       Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"gizela"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/100  Signal level=-82 dBm  Noise level=-77 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000101
          Cell 02 - Address: <MAC address removed>
                    Protocol:802.11b/g
                    ESSID:"OSSY"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality=0/100  Signal level=-90 dBm  Noise level=-85 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Protocol:802.11g/n
                    ESSID:"DIRECT-Fg-BRAVIA"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=5/100  Signal level=-88 dBm  Noise level=-83 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD3A0050F204104A00011010440001021049000600372A00012010110012425241564941204B444C2D343257383035411054000800070050F2040001
          Cell 04 - Address: <MAC address removed>
                    Protocol:802.11b/g/n
                    ESSID:"UBU"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/100  Signal level=-80 dBm  Noise level=-75 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F204104A00011010440001021049000600372A000120


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

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
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2x00pci

***** dmesg *****

[    8.574133] rt3290sta: module license 'unspecified' taints kernel.
[    8.574136] rt3290sta: module license 'unspecified' taints kernel.
[    8.576226] rt2860 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.576260] rt2860 0000:07:00.0: setting latency timer to 64
[   22.701222] <==== rt28xx_init, Status=0
[   28.709223] <==== rt28xx_init, Status=0
[   29.365302] <==== rt28xx_init, Status=0

****************** done ******************




[ATTACH=CONFIG]244771[/ATTACH]



Thanks for help!

---

