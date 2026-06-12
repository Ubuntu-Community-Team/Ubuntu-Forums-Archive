---
title: "Wireless internet going on and off - Ubuntu 11.04 - ASUS A52F"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by BenettFreeman on 2012-02-05
I'd be very grateful if anyone could help with this niggling problem I've encountered. I upgraded from 10.10 to 11.04 in order to fix a microphone issue I was having with this ASUS A52F laptop (microphone stopped working and no fix would work short of upgrading, which solved it instantly). 

HOWEVER, I now have an issue with the wireless, which works perfectly for a short while, before dropping off. Sometimes it goes back on of its own accord, sometimes I disconnect from network and reconnect and the bitrate goes back up to where it had been. 

During these 'anomalies', network manager shows that I am still connected, but all downloads etc. drop to 0 bytes. My knowledge of networking on Linux is not advanced enough to really provide much more information than that.

[This thread]("http://ubuntuforums.org/showthread.php?t=1460790") focusing on known issues with my laptop doesn't mention the problem, and I can't find anyone else having the same problem, so am starting this thread.

If anyone with decent knowledge of Linux networking could walk me through a troubleshooting of this issue, I'd be extremely grateful.

The only command I found whose output might be useful as a starting point is:-

```
sudo lshw -C network
```which provides:-

```
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:7c:11:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-13-generic firmware=N/A ip=192.168.0.27 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2c00000-d2c0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: eth0
       version: 03
       serial: 20:cf:30:53:dc:d4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 memory:d0400000-d0403fff ioport:a100(size=128) ioport:a000(size=256)
```

---

### Post by praseodym on 2012-02-05
Hi,

which encryption mode do you use? The NM has problems with mixed WPA/WPA2, better use WPA2-AES if possible. Please show additionally:

```
iwconfig
ifconfig -a
cat /etc/resolv.conf
sudo iwlist scan
```

---

### Post by BenettFreeman on 2012-02-05
**iwconfig**

```
*-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:f0:6d:7c:11:42
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-13-generic firmware=N/A ip=192.168.0.27 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2c00000-d2c0ffff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:04:00.5
       logical name: eth0
       version: 03
       serial: 20:cf:30:53:dc:d4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 memory:d0400000-d0403fff ioport:a100(size=128) ioport:a000(size=256)
ben@ben-K52F:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WillsRoad"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C4:3D:C7:2F:F1:1A   
          Bit Rate=65 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:211   Missed beacon:0

```**ifconfig -a **

```
eth0      Link encap:Ethernet  HWaddr 20:cf:30:53:dc:d4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19859 (19.8 KB)  TX bytes:19859 (19.8 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:7c:11:42  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76f0:6dff:fe7c:1142/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:511754 errors:0 dropped:0 overruns:0 frame:0
          TX packets:388047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:597726401 (597.7 MB)  TX bytes:195460433 (195.4 MB)

```**cat /etc/resolv.conf**

```
# Generated by NetworkManager
nameserver 194.168.4.100
nameserver 194.168.8.100
```[B]sudo iwlist scan
[/B]
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C4:3D:C7:2F:F1:1A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"WillsRoad"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000039850019a
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 000957696C6C73526F6164
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343830100800020088
                    IE: Unknown: DD090010180208F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001700000000000000000000000000000000000000
          Cell 02 - Address: E0:91:F5:41:00:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"BML_AP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007a79601180
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 0006424D4C5F4150
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 05040001000A
                    IE: Unknown: 0706444520010D14
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 03 - Address: 00:1C:DF:DA:1B:BF
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Cromer-W"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000017809857b1a
                    Extra: Last beacon: 344ms ago
                    IE: Unknown: 000843726F6D65722D57
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000C4307000000
          Cell 04 - Address: E0:91:F5:DE:BA:4A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"BML-WIFI-2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000004cd37024
                    Extra: Last beacon: 996ms ago
                    IE: Unknown: 000A424D4C2D574946492D32
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010ED870D64A74979583C6AC370CED533371021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180200F0010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:24:17:A9:7F:C1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"O2wireless102916"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000062cb6818a
                    Extra: Last beacon: 348ms ago
                    IE: Unknown: 00104F32776972656C657373313032393136
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD060010180200F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:14:85:BC:46:48
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"default"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007818498181
                    Extra: Last beacon: 1036ms ago
                    IE: Unknown: 000764656661756C74
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0C00037F020101000002A30000
          Cell 07 - Address: 7C:03:4C:77:50:8B
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SKY7508A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000380a121b1d6
                    Extra: Last beacon: 1004ms ago
                    IE: Unknown: 0008534B593735303841
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 08 - Address: 00:1F:D0:1C:3E:39
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"BMLOFFICE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b5236c6181
                    Extra: Last beacon: 6588ms ago
                    IE: Unknown: 0009424D4C4F4646494345
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0C00037F020101160002A30000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 09 - Address: 00:26:91:1C:09:FC
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"SKY02555"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f4561a3009
                    Extra: Last beacon: 1272ms ago
                    IE: Unknown: 0008534B593032353535
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 02:24:E4:2C:31:28
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"HP866565"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000004fdf7923d1
                    Extra: Last beacon: 784ms ago
                    IE: Unknown: 00084850383636353635
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 0706455520010D14
```Also, I don't know what type of encryption I'm using. How can I find out or change this? (I don't have administrator access to router, but could ask landlord if necessary)

Danke sehr!

---

### Post by bkratz on 2012-02-05
Which of the A/P's are you trying to connect too (essid). There are 4 or 5 on both channels 1 and 6, is this one of them? (lots of interference) and an ad-hoc network on channel 10. The encryption type in shown in the sudo iwlist command above.

---

### Post by BenettFreeman on 2012-02-05
I want to connect to WillsRoad

Do you mean to say the other Wireless networks are interfering with my adapter? Is there any way I can make it ignore them?

---

### Post by praseodym on 2012-02-05
Encryption mode is WPA2:
> ```
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
You can see WPA in Cells 2 and 3, mixed mode in Cell 4.

I think the driver ath9k is buggy concerning the hardware encryption of the device. You can deactivate this encryption via:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf [COLOR="Red"]# this is one line![/COLOR]
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by BenettFreeman on 2012-02-06
> **praseodym said:**
> Encryption mode is WPA2:

You can see WPA in Cells 2 and 3, mixed mode in Cell 4.

I think the driver ath9k is buggy concerning the hardware encryption of the device. You can deactivate this encryption via:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf [COLOR=Red]# this is one line![/COLOR]
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

This SEEMS to have done the trick! Thank you so much :)

---

### Post by BenettFreeman on 2012-02-09
Alas, I spoke too soon. The problem has not gone away, and the relatively longer period during which it was not playing up seems to have just been coincidence or something. 

Does anyone have more ideas as to why my network connection is periodically stopping from flowing?

Thanks.

---

### Post by BenettFreeman on 2012-02-12
BUMP

Does anyone with networking knowledge have a lasting solution to this issue?

---

