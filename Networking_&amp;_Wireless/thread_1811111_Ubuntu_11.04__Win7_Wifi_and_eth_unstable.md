---
title: "Ubuntu 11.04 || Win7 Wifi and eth unstable"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by christiananton on 2011-07-24
Hello Ubuntu Community,

I am new to Ubuntu 11.04 and Linux @ all. At the moment I try to port everything from win to linux … It would be great if you could help me with this problem I currently have with my Installation.

Packard Bell: Easy Note Tk85-JO-046GE
Installation is parallel to WIN7 

Problem description:
1.) Using my laptop in an Hotel where I stay for 3Months. => no access to the infrastrutcture servers routers etc.
2.) Connection to hotelnetwork with RJ45-Networkcabel. => sometimes I get connected with Ubuntu 11.04, sometimes not (more often not)
3.) If I connect to the Network via WIN7 with Networkcabel => directly connected works perfect.
4.) If I connect to the Network via an Accespoint (D-Link DIR-615 in AP-Mode plugged to the same cable used for direct connection before) I sometimes get access / sometimes not like in point 2.)
5.) With WIN7 this connection (point 4.) ) works immediately after start up 
6.) Ubuntu and Windows don't give me back the same name for the wifi device win: atheros ar5b97; Ubuntu : atheros AR9287 and 
7.) Before I get access to the internet (win7 & Ubuntu) i have to enter a username and password on a redirected website of the hotel. Address of this server is 172.16.0.1 it tells me to be a MASH login.
8.) In order to get it working I tried to use ndiswrapper with the win driver, I tried severall other tips like  reinstallation of Ubuntu and so on...
9.) Now I have a fresh clean installed Ubuntu without any changes and the following information asked:
TOP1:
christian@christian-EasyNote-TK85:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
christian@christian-EasyNote-TK85:~$

TOP2:
christian@christian-EasyNote-TK85:~$  lsusb
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
christian@christian-EasyNote-TK85:~$

TOP3:
christian@christian-EasyNote-TK85:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 1c:75:08:1d:dc:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  Hardware Adresse 5c:ac:4c:0a:28:ca  
          inet Adresse:172.16.1.16  Bcast:172.16.255.255  Maske:255.255.0.0
          inet6-Adresse: fe80::5eac:4cff:fe0a:28ca/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3916 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:5777924 (5.7 MB)  TX bytes:622815 (622.8 KB)


TOP4:
christian@christian-EasyNote-TK85:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 14:D6:4D:C5:D9:86   
          Bit Rate=144.4 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-14 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:1   Missed beacon:0


TOP5:
christian@christian-EasyNote-TK85:~$ lsmod |grep 'ath9k'
ath9k                 103669  0 
mac80211              257001  1 ath9k
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
cfg80211              156212  3 ath9k,mac80211,ath
christian@christian-EasyNote-TK85:~$ 

TOP6:
christian@christian-EasyNote-TK85:~$ dmesg | grep 'wlan0'
[   18.773909] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.282867] wlan0: authenticate with 14:d6:4d:c5:d9:86 (try 1)
[   40.284749] wlan0: authenticated
[   40.305362] wlan0: associate with 14:d6:4d:c5:d9:86 (try 1)
[   40.312231] wlan0: RX AssocResp from 14:d6:4d:c5:d9:86 (capab=0xc31 status=0 aid=1)
[   40.312236] wlan0: associated
[   40.321238] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.853394] wlan0: no IPv6 routers present

christian@christian-EasyNote-TK85:~$ dmesg | grep 'cfg80211'
[   18.461049] cfg80211: Calling CRDA to update world regulatory domain
[   18.554469] cfg80211: World regulatory domain updated:
[   18.554472] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.554475] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.554478] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.554481] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.554483] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.554486] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.713539] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.713543] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713546] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.713549] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713552] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.713555] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713557] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.713561] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713563] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.713566] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713569] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.713572] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713574] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.713578] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713580] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.713583] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713586] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.713589] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713592] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.713595] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713597] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.713600] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713603] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   18.713606] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713609] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   18.713612] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   18.713614] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.715664] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[   40.321545] cfg80211: Calling CRDA for country: GB
[   40.325306] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   40.325310] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325311] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   40.325313] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325315] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   40.325317] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325318] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   40.325320] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325322] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   40.325324] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325325] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   40.325327] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325329] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   40.325331] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325332] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   40.325334] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325335] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   40.325337] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325339] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   40.325341] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325342] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   40.325344] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325346] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   40.325347] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325349] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   40.325351] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   40.325352] cfg80211: Disabling freq 2484 MHz
[   40.325355] cfg80211: Regulatory domain changed to country: GB
[   40.325357] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   40.325358] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.325360] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.325362] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   40.325364] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
christian@christian-EasyNote-TK85:~$ 

TOP7:
christian@christian-EasyNote-TK85:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:1d:dc:8e
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 memory:b3000000-b300ffff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 5c:ac:4c:0a:28:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-10-generic-pae firmware=N/A ip=172.16.1.16 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b2000000-b200ffff
christian@christian-EasyNote-TK85:~$ 

TOP8:
christian@christian-EasyNote-TK85:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 14:D6:4D:C5:D9:86
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000076b6a186
                    Extra: Last beacon: 63528ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0501002D127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000400000000000000000000000000000000000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown: DD750050F204104A00011010440001021041000100103B0001031047001065D76ECCE0FB28ED179014D64DC5D98610210006442D4C696E6B102300074449522D363135102400074449522D3631351042000830303030303030301054000800060050F2040001101100074449522D363135100800020086


TOP9:
christian@christian-EasyNote-TK85:~$ lsb_release -d
Description:	Ubuntu 11.04

TOP10:
christian@christian-EasyNote-TK85:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                                  Ignoring unknown interface wlan0=wlan0.






Thank you for any tips how to solve this.
Christian

---

### Post by christiananton on 2011-07-24
Really no ideas? maybe tomorrow...
Cu thx for any answer...

---

