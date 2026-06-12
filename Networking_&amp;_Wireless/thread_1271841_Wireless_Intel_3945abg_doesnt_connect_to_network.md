---
title: "Wireless Intel 3945abg doesnt connect to network"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by Arneef on 2009-09-21
Hello :) having a bit of a problem with this, i am fairly new to ubuntu, but been using linux to and from the last 10 years. Now i'mm trying to install ubuntu on my parents laptop, it is working so far perfect with the exception to wireless.

Problem: Wireless Intel 3945ABG will not connect to network.

Have tried different solutions on the forums, including, no encryption on the network, Wicd, manual connection and some other solutions.
So far the only result is that the wireless card is trying to connect but doesnt get any result, with network manager i only get the box stating the network needs a password....etc.
This works on the same machine with Vista, the network is working on another machine with Ubuntu 9.04.

Have provided as much output as i know how to, if there is anything else , i will try to provide it.


This is at the moment a clean install of 9.04, with upgrades from the upgrade manager only.

Machine: Packard Bell easynote laptop
Router is a Belkin Wireless G plus.
1)
```

$lspci

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```2)yes i am running a wired network atm, but not when testing the wireless
```

$ifconfig 

eth0      Link encap:Ethernet  HWaddr 00:18:f3:fc:94:1c  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fefc:941c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1806 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1449 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2112598 (2.1 MB)  TX bytes:182906 (182.9 KB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:36:67:76  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-36-67-76-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```3)
```

$iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```4)
```

$lsmod | grep "iwl" 
iwl3945                97912  0 
mac80211              217592  1 iwl3945
cfg80211               38288  2 iwl3945,mac80211
led_class              12036  2 iwl3945,asus_laptop

```5)
```

$ dmesg | grep "iwl" 
[   10.914351] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   10.914354] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   10.914486] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.914504] iwl3945 0000:03:00.0: setting latency timer to 64
[   10.914568] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   10.914871] iwl3945 0000:03:00.0: irq 2299 for MSI/MSI-X
[   10.969845] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   10.971077] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.826414] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   21.966207] Registered led device: iwl-phy0:radio
[   21.966509] Registered led device: iwl-phy0:assoc
[   21.967432] Registered led device: iwl-phy0:RX
[   21.967461] Registered led device: iwl-phy0:TX

```6)
```

$ sudo lshw -C network
[sudo] password for arne: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:36:67:76
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:fc:94:1c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.4 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:42:db:fd:df:91
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```7)
```

$iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:01:2C:04:08
                    ESSID:"Hjemmenett"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 000A486A656D6D656E657474
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160100190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340100010000000F000000000000000000000000000000
                    IE: Unknown: 050400010000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001a6d79b8180
                    Extra: Last beacon: 904ms ago
          Cell 02 - Address: 00:17:3F:53:D4:F8
                    ESSID:"kristian"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=57/100  Signal level:-74 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 00086B7269737469616E
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030103
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180201F1000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000129f5ee189
                    Extra: Last beacon: 884ms ago
          Cell 03 - Address: 00:1C:F0:69:E8:74
                    ESSID:"kollens"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/100  Signal level:-90 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 00076B6F6C6C656E73
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD070050F202000100
                    IE: Unknown: DD1E00904C334E101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340105070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A6E101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160105010000000F000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001a6d764d180
                    Extra: Last beacon: 912ms ago

pan0      Interface doesn't support scanning.

```8 )
```

$ lsb_release -d
Description:    Ubuntu 9.04

```9 )
```

$ uname -mr
2.6.28-15-generic i686

```10)
```

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

```11)end of dmesg after trying to connect to network
```

$ dmesg
[   21.975808] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.157058] eth0: no IPv6 routers present
[   50.624606] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 1
[   50.824250] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 2
[   51.024078] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 3
[   51.224076] wlan0: direct probe to AP 00:17:3f:53:d4:f8 timed out
[   68.426772] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 1
[   68.624039] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 2
[   68.824196] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 3
[   69.024039] wlan0: direct probe to AP 00:17:3f:53:d4:f8 timed out
[   80.623604] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 1
[   80.820052] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 2
[   81.020064] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 3
[   81.220125] wlan0: direct probe to AP 00:17:3f:53:d4:f8 timed out
[   98.428898] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 1
[   98.429512] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 1
[   98.628079] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 2
[   98.828070] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 3
[   99.028121] wlan0: direct probe to AP 00:17:3f:53:d4:f8 timed out
[ 1466.895564] eth0: link down
[ 1493.996817] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 1
[ 1493.997429] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 1
[ 1494.196077] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 2
[ 1494.396054] wlan0: direct probe to AP 00:17:3f:53:d4:f8 try 3
[ 1494.597089] wlan0: direct probe to AP 00:17:3f:53:d4:f8 timed out


```12)I have not run trough all the steps to connect manually her but the output is the same
```

sudo dhclient wlan0
[sudo] password for arne: 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:18:de:36:67:76
Sending on   LPF/wlan0/00:18:de:36:67:76
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Any help would be appreciated.

---

### Post by Arneef on 2009-09-25
Anyone has any clue ?

---

### Post by jeppo67 on 2011-01-12
more than one year (and more than one version) later but....no solutions and more people (me) with the same problem

---

### Post by jeppo67 on 2011-01-12
RESOLVED

I've added in:
```
/etc/modprobe.d/blacklist.conf
```the line:
```
blacklist asus-laptop
```see [http://ubuntuforums.org/showthread.php?t=1039796&highlight=packard+bell+3945abg](http://ubuntuforums.org/showthread.php?t=1039796&highlight=packard+bell+3945abg) for reference

good luck

---

### Post by achotio on 2012-03-08
Hello!

Modyfing /etc/modprobe.d/blacklist.conf worked for me too!!

I post all my data to help others with the same configuration

1 ) Machine Brand and Model (PC/Laptop):
```
Packard Bell MX45
```

2 ) Wireless Brand, Model and Wireless Chipset:
```
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
```

3 ) check interface:
```
wlan0     IEEE 802.11abg  ESSID:"ONO290099"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

4 ) Check for modules:
```
iwl3945                68727  0 
iwlcore               106149  1 iwl3945
mac80211              205434  2 iwl3945,iwlcore
led_class               2864  4 iwl3945,iwlcore,asus_laptop,sdhci
cfg80211              126528  3 iwl3945,iwlcore,mac80211
```

5 ) Kernel boot messages
```
[   13.701018] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   13.701020] iwl3945: Copyright(c) 2003-2009 Intel Corporation
[   13.701222] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.701237] iwl3945 0000:03:00.0: setting latency timer to 64
[   13.770782] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   13.770785] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   13.770962] iwl3945 0000:03:00.0: irq 28 for MSI/MSI-X
[   14.025308] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.379436] iwl3945 0000:03:00.0: firmware: requesting iwlwifi-3945-2.ucode
[   14.394463] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
```

6 ) Network configuration
```
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:36:cc:80
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:fe1ff000-fe1fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:ab:aa:06
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.19 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:16 ioport:d800(size=256) memory:feafe400-feafe4ff
```


7 ) Scan for networks:
```
wlan0     Scan completed :
          Cell 01 - Address: F4:3E:61:A0:0D:73
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"WLAN_0D72"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000507aa94183
                    Extra: Last beacon: 12720ms ago
                    IE: Unknown: 0009574C414E5F30443732
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:26:5B:A5:0B:88
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ONO0B80"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Unknown/bug
                    Extra:tsf=0000012c24973166
                    Extra: Last beacon: 12788ms ago
                    IE: Unknown: 00074F4E4F30423830
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706455320010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 05040001001C
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1016FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010009127A
                    IE: Unknown: DD07000C4304000000
          Cell 03 - Address: 00:22:2D:43:8E:B1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"AyV"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000047e618f181
                    Extra: Last beacon: 12616ms ago
                    IE: Unknown: 0003417956
                    IE: Unknown: 010882848B968C98B048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 07064E4C20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: E0:69:95:85:BD:CE
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"ONO290099"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000046406187
                    Extra: Last beacon: 12328ms ago
                    IE: Unknown: 00094F4E4F323930303939
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A080000000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```

8 ) Ubuntu Version: 
```
Description:	Ubuntu 10.04.4 LTS
```

9 ) Kernel/architecture (including 32 vs. 64 bit): 
```
2.6.32-39-generic i686
```

---

### Post by sffvba[e0rt on 2012-03-08
Thanks for the added info.

Thread closed.



404

---

