---
title: "Problem in connecting to WiFi in Ubuntu 11.04"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by siteregsam on 2012-10-10
Hi,

The Enable Network and Enable Wireless are checked in network manager. But the WiFi connections are not listed but rarely it lists and connects to WiFi.

  I have checked the wireless troubleshooting guide as well as scoured  the internet to find a solution but have found nothing that has worked.   I will post all recommended information as mentioned in [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681).

> acer@acer-Aspire-5050:~$ lspci -nn | grep 'Atheros'
08:04.0 Ethernet controller [0200]: Atheros Communications Inc. AR2413 802.11bg NIC [168c:001a] (rev 01)> acer@acer-Aspire-5050:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:f4:c6:d9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28928 (28.9 KB)  TX bytes:28928 (28.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7d:c3:fc:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

> acer@acer-Aspire-5050:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSIDff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementff> acer@acer-Aspire-5050:~$ lsmod | grep "ath5k"
ath5k                 144412  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211> 
acer@acer-Aspire-5050:~$ sudo lshw -C network
*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:f4:c6:d9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:a000(size=256) memory:b0211c00-b0211cff

  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:c3:fc:e7
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-8-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:21 memory:b0200000-b020ffff> acer@acer-Aspire-5050:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
> acer@acer-Aspire-5050:~$ lsb_release -d
Description:    Ubuntu 11.04> acer@acer-Aspire-5050:~$ uname -mr 
2.6.38-8-generic i686> acer@acer-Aspire-5050:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                [ OK ] > acer@acer-Aspire-5050:~$ dmesg | grep wlan0
[   19.849280] ADDRCONF(NETDEV_UP): wlan0: link is not ready
acer@acer-Aspire-5050:~$ dmesg | egrep 'ath|firm'
[    1.482592] device-mapper: multipath: version 1.2.0 loaded
[    1.482595] device-mapper: multipath round-robin: version 1.0.0 loaded
[   19.058900] ath5k 0000:08:04.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   19.059878] ath5k 0000:08:04.0: registered as 'phy0'
[   19.778274] ath: EEPROM regdomain: 0x63
[   19.778279] ath: EEPROM indicates we should expect a direct regpair map
[   19.778285] ath: Country alpha2 being used: 00
[   19.778288] ath: Regpair used: 0x63
[   19.802944] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)> acer@acer-Aspire-5050:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: noI am trying to connect to an appartment provided WiFi, so I don't have an option to connect to a wired network and trouble shoot. But eth0 works fine. 

Please help me in getting this fixed. Thanks in advance !!!

---

