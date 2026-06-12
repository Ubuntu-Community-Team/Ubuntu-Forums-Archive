---
title: "Wireless Error in WICD. Works in Network Manager GNOME. Any ideas?"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by isoscelesrectangle on 2010-12-26
1 ) Machine Brand and Model (PC/Laptop):
Dell Studio 1458
2 ) Wireless Brand, Model and Wireless Chipset:
LSPCI Output: 
```
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)


```
LSUSB Output: 
```
kevin-laptop Documents # lsusb
Bus 002 Device 007: ID 413c:8160 Dell Computer Corp. 
Bus 002 Device 006: ID 413c:8162 Dell Computer Corp. 
Bus 002 Device 005: ID 413c:8161 Dell Computer Corp. 
Bus 002 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6407 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
Code:
$ lspci -nn | grep 'Wireless Brand': No output. 
3 ) check interface:
ifconfig Output: 
```
kevin-laptop Documents # ifconfig
eth1      Link encap:Ethernet  HWaddr 00:24:e8:83:cb:2c  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:72f4:4d89:0:224:e8ff:fe83:cb2c/64 Scope:Global
          inet6 addr: fe80::224:e8ff:fe83:cb2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3127 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3015141 (2.8 MiB)  TX bytes:349601 (341.4 KiB)
          Interrupt:16 

eth2      Link encap:Ethernet  HWaddr f0:7b:cb:5e:16:ff  
          inet6 addr: fe80::f27b:cbff:fe5e:16ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6526 errors:0 dropped:0 overruns:0 frame:6356
          TX packets:7025 errors:248 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6725423 (6.4 MiB)  TX bytes:1122813 (1.0 MiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:130840 (127.7 KiB)  TX bytes:130840 (127.7 KiB)

```
iwconfig: 
```
$ kevin-laptop Documents # iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth2      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:16 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:110  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
iwconfig eth2: 
```
kevin-laptop Documents # iwconfig eth2
eth2      IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:16 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:110  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:0   Missed beacon:0

```
4 ) Check for modules:
Code:
```
wl                   1937867  0
```
Code:
$ lsmod | grep "wlan_module_name"
```
kevin-laptop Documents # lsmod | grep wl
wl                   1937867  0 
lib80211                3654  2 lib80211_crypt_tkip,wl
```
5 ) Kernel boot messages
dmesg: 
```
[ 6364.669435] tg3 0000:03:00.0: PME# enabled
[ 6364.669454] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6364.691632] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6364.691674] tg3 0000:03:00.0: PME# disabled
[ 6364.707047] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6364.728803] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6365.047539] tg3: eth1: Link is down.
[ 6368.044782] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[ 6368.044788] tg3: eth1: Flow control is on for TX and on for RX.
[ 6368.045716] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6375.386507] eth2: no IPv6 routers present
[ 6434.176615] tg3 0000:03:00.0: PME# enabled
[ 6434.176636] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6434.202005] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6434.202047] tg3 0000:03:00.0: PME# disabled
[ 6434.216149] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6434.238024] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6434.612330] tg3 0000:03:00.0: PME# enabled
[ 6434.612351] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6434.632811] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6434.632853] tg3 0000:03:00.0: PME# disabled
[ 6434.647808] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6434.657549] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6434.991325] tg3: eth1: Link is down.
[ 6437.988687] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[ 6437.988693] tg3: eth1: Flow control is on for TX and on for RX.
[ 6437.989610] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6444.493518] eth2: no IPv6 routers present
[ 6460.349527] tg3 0000:03:00.0: PME# enabled
[ 6460.349548] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6460.373985] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6460.374025] tg3 0000:03:00.0: PME# disabled
[ 6460.391056] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6460.412939] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6460.967613] tg3: eth1: Link is down.
[ 6463.964623] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[ 6463.964629] tg3: eth1: Flow control is on for TX and on for RX.
[ 6463.965568] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6471.033064] eth2: no IPv6 routers present
[ 6529.925804] tg3 0000:03:00.0: PME# enabled
[ 6529.925826] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6529.947608] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6529.947650] tg3 0000:03:00.0: PME# disabled
[ 6529.963363] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6529.989217] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6530.368299] tg3 0000:03:00.0: PME# enabled
[ 6530.368322] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6530.392926] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6530.392965] tg3 0000:03:00.0: PME# disabled
[ 6530.407721] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6530.433512] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6530.904337] tg3: eth1: Link is down.
[ 6533.900220] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[ 6533.900223] tg3: eth1: Flow control is on for TX and on for RX.
[ 6533.900724] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6537.070023] tg3 0000:03:00.0: PME# enabled
[ 6537.070044] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6537.095523] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6537.095564] tg3 0000:03:00.0: PME# disabled
[ 6537.112875] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6537.122584] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6537.173773] tg3 0000:03:00.0: PME# enabled
[ 6537.173787] tg3 0000:03:00.0: wake-up capability enabled by ACPI
[ 6537.349378] tg3 0000:03:00.0: wake-up capability disabled by ACPI
[ 6537.349421] tg3 0000:03:00.0: PME# disabled
[ 6537.365331] tg3 0000:03:00.0: irq 34 for MSI/MSI-X
[ 6537.375123] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6537.896919] tg3: eth1: Link is down.
[ 6540.893908] tg3: eth1: Link is up at 1000 Mbps, full duplex.
[ 6540.893914] tg3: eth1: Flow control is on for TX and on for RX.
[ 6540.894843] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6547.700004] eth2: no IPv6 routers present
```
6 ) Network configuration
Code:
$ sudo lshw -C network
7 ) Scan for networks:
Scan output: 
```
kevin-laptop Documents # iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 68:7F:74:C5:E4:E6
                    ESSID:"wings"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-92 dBm
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B000103104700108A518836FF1D4F7DF67B241D34C37C2910210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 68:7F:74:C5:E4:E8
                    ESSID:"wings-guest"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 00:21:27:65:94:0C
                    ESSID:"TP-LINK_65940C"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-76 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:25:86:5B:95:A8
                    ESSID:"TP-LINK"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:25:86:2C:13:3A
                    ESSID:"TP-LINK"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 68:7F:74:1A:37:C6
                    ESSID:"wings-over"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-30 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 07 - Address: 6A:7F:74:1A:37:C7
                    ESSID:"dd-wrt_vap"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-30 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 08 - Address: F0:7D:68:7A:C6:F6
                    ESSID:"fangyuan12"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD850050F204104A0001101044000101103B0001031047001063041253101920061228F07D687AC6F61021000E442D4C696E6B2053797374656D73102300074449522D363135102400074449522D3631351042000D32303037303431332D303030311054000800060050F20400011011000F576972656C65737320526F75746572100800020086
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 09 - Address: 68:7F:74:C5:E4:E7
                    ESSID:"wings"
                    Mode:Managed
                    Frequency=5.745 GHz
                    Quality:2/5  Signal level:-75 dBm  Noise level:-92 dBm
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700108A518836FF1D4F7DF67B241D34C37C2910210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084103C000103
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s

pan0      Interface doesn't support scanning.


```
8 ) Linux Mint Debian
9 ) Kernel/architecture (including 32 vs. 64 bit): 
uname -mr: 
```
kevin-laptop Documents # uname -mr
2.6.32-5-amd64 x86_64

```
Code:
Networking Restart: 
```
kevin-laptop Documents # /etc/init.d/networking restart
Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces ... (warning).
Reconfiguring network interfaces...done.
```

Problem: I can connect to Wings using GNOME Network Manager, but I installed KDE, and KDE Network Manager didn't work well with it. I installed WICD, and WICD doesn't work with it. It is supposed to be a WEP 40/128 Bit Key or something like that. How can I connect? 
Cheers, 
The Isosceles Rectangle

---

### Post by isoscelesrectangle on 2010-12-26
Nevermind that. I reinstalled KNetworkManager and instead of using 128-bit encryption, I selected 64/128bit hex. Its working now. Sorry guys.

---

