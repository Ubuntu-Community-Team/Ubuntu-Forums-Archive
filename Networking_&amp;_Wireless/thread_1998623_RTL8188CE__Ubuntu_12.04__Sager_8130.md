---
title: "RTL8188CE / Ubuntu 12.04 / Sager 8130"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by JHSN on 2012-06-07
Hello, I recently installed Ubuntu 12.04 64-bit with Wubi on my laptop which has Windows 7 64-bit. Even though the wireless was recognized and worked out of the box, it is very unstable. I have tried to find solutions online but my situation differs from the general slow wireless problem. My wireless is not slow but unstable. I am using Chrome and I constantly see Error 102 (net::ERR_CONNECTION_REFUSED) and Error 137 (net::ERR_NAME_RESOLUTION_FAILED) or it takes a longer than usual time to load a page but when a website is opened successfully, the connection is fast and I can download at normal speed. I tried Firefox too but it did not solve the problem. I have tried these solutions: [http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/) and setting the MTU to 1500 (from automatic) as well as some others.

I am new to linux so please write out the commands you mention so I can copy paste them. I will try to post as much information as I can, hopefully they will all be helpful for solving this issue. Since the current router settings work normally in Windows I am hoping to not change the router settings such as disabling N and using B/G instead as that would be avoiding the problem and not solving it.

```
Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:90:f5:b7:c4:eb  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:53 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50389 (50.3 KB)  TX bytes:50389 (50.3 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:cf:37:25  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45127805 (45.1 MB)  TX bytes:2381810 (2.3 MB)


iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Sleipnir"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:0E:52:A4   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:336   Missed beacon:0

eth0      no wireless extensions.


lsmod
Module                  Size  Used by
rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce


dmesg | grep rtl
[    9.638595] rtl8192ce 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.638605] rtl8192ce 0000:04:00.0: setting latency timer to 64
[    9.987448] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.987849] rtlwifi: wireless switch is on
[   14.857832] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   15.393241] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin


sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:b7:c4:eb
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.8 duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:53 memory:f6320000-f6323fff ioport:d100(size=128) ioport:d000(size=256) memory:f6310000-f631ffff memory:f6300000-f630ffff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 48:5d:60:cf:37:25
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-24-generic firmware=N/A ip=192.168.1.108 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 ioport:c000(size=256) memory:f6200000-f6203fff


iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 58:6D:8F:0E:52:A4
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Sleipnir"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004538c0818e
                    Extra: Last beacon: 4308ms ago
                    IE: Unknown: 0008536C6569706E6972
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B0001031047001036918C47F88B8D2739AA36757336690E10210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101
                    IE: Unknown: DD090010180201F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

---

### Post by kalaschnikow on 2012-06-07
Hi,

I'm experiencing the same unstable connection on Ubuntu 12.04 with the RTL8188CE on a Toshiba Satellite C660.

The same occurs with Linux Mint 13 Mate, which makes sense since it's based on Ubuntu.

Using Windows 7 the connection is stable, so I'm guessing this is related to the drivers.

It got so unstable that after 1min of connection to the WLAN Router, I had to dis- and reconnect to be able to use the internet for another 1-2min until it broke down again. Ubuntu will show me that I'm connected to the router with a strong signal even when the problem occurs. Strangely the connection has been quite stable for the last 30min. Maybe it's also related to heavy network usage (downloading using full bandwidth)

```

~$ lspci | grep Network
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr dc:0e:a1:46:f5:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:152613 (152.6 KB)  TX bytes:152613 (152.6 KB)

wlan0     Link encap:Ethernet  HWaddr 9c:b7:0d:99:9e:8a  
          inet addr:192.168.0.35  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9eb7:dff:fe99:9e8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:188307204 (188.3 MB)  TX bytes:7104601 (7.1 MB)

~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"BWLAN"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 80:C6:AB:1D:AC:E1   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by lornstone on 2012-07-21
Hi,

I know it's an old topic but I've got the same problem with the RTL8188CE driveron a Toshiba Satellite C???(don't remember the exact number)
I'm wondering if the problem has been solved now.

Thanks!

---

