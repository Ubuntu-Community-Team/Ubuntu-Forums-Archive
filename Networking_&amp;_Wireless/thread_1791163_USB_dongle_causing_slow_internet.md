---
title: "USB dongle causing slow internet?"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by Quorlia on 2011-06-26
Hi,

I need some help deciding where to start troubshooting my connection.

I installed a mobile broadband dongle and since then my wifi connection to the landline router has been running really REALLY slowly or failing.  Yes it's the dreaded AR5001 Wifi card but until this it was working flawlessly so I don't want to mess with it unless I have to.  There doesn't seem to be anything wrong with the router as the same behaviour occurs with an alternative router and the laptops connect perfectly (they both have ubuntu on them too).  Wifi works fine under Windows.

Here are some diagnostics:


1 ) Machine Brand and Model (PC/Laptop):

Acer Aspire R3600


2 ) Wireless Brand, Model and Wireless Chipset:
Code:
$ lspci -nn |grep theros
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)

$ lsusb
Bus 001 Device 003: ID 13fd:0842 Initio Corporation 
Bus 001 Device 004: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 04f2:0918 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


3 ) check interface:
Code:
$ ifconfig
<snip lo, eth0>
wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe60:3ce0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2154 (2.1 KB)  TX bytes:12046 (12.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-60-3C-E0-36-30-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ iwconfig
<snip lo, eth0>
wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MyNetwork"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


4 ) Check for modules:
$ lsmod | grep ath
ath5k                 124772  0 
mac80211              181140  1 ath5k
ath                     8060  1 ath5k
led_class               4096  1 ath5k
cfg80211               93052  3 ath5k,mac80211,ath


5 ) Kernel boot messages
$ dmesg | grep ath
[    1.249079] device-mapper: multipath: version 1.1.0 loaded
[    1.249088] device-mapper: multipath round-robin: version 1.0.0 loaded
[   20.222506] ath5k 0000:05:00.0: PCI INT A -> Link[LN4A] -> GSI 19 (level, low) -> IRQ 19
[   20.222526] ath5k 0000:05:00.0: setting latency timer to 64
[   20.222598] ath5k 0000:05:00.0: registered as 'phy0'
[   20.725313] ath: EEPROM regdomain: 0x65
[   20.725324] ath: EEPROM indicates we should expect a direct regpair map
[   20.725335] ath: Country alpha2 being used: 00
[   20.725340] ath: Regpair used: 0x65
[   20.764142] Registered led device: ath5k-phy0::rx
[   20.764199] Registered led device: ath5k-phy0::tx
[   20.764209] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)


6 ) Network configuration
$ sudo lshw -C network 
<snip eth0>
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:60:3c:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.1.64 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:febf0000-febfffff


7 ) Scan for networks:
iwlist scan
<snip lo, eth0>

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"MyNetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001350f7a1ed
                    Extra: Last beacon: 41132ms ago
                    IE: Unknown: 00064C616E637265
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180201F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


8 ) Ubuntu Version: 
$ lsb_release -d
Description:	Ubuntu 9.10

9 ) Kernel/architecture (including 32 vs. 64 bit): 
$ uname -mr
2.6.31-20-generic i686

10 ) Restarting the network:
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]


11) Ping the router (this is on a good day)
$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=840 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=1274 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=1297 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=1628 ms
64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=729 ms
64 bytes from 192.168.1.254: icmp_seq=6 ttl=64 time=446 ms
64 bytes from 192.168.1.254: icmp_seq=7 ttl=64 time=263 ms
^C
--- 192.168.1.254 ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7005ms
rtt min/avg/max/mdev = 263.155/925.716/1628.986/458.151 ms, pipe 2

---

### Post by Quorlia on 2011-06-27
So no one has any ideas?  At the very least you could help me understand all this stuff I've output!

Thanks,

quorlia

---

