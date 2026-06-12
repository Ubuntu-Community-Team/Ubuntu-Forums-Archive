---
title: "Wireless help Ticket"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by mattweed9 on 2009-11-01
[B]Constant loss of internet connection. The connection seems to reset every so many seconds causing the download speed to go from 2 or more mb/s, to 0 mb/s. This repeats until the connection is lost completely and I am forced to restart to be able to reconnect. 

 Machine Brand and Model (PC/Laptop)[/B]:
Gateway NV5214u laptop


[B]Wireless Brand, Model and Wireless Chipset:
[/B]```
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
mobile@mobile-laptop:~$ lspci -nn | grep  AR928X
09:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)

```**check interface:**
```
mobile@mobile-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:ca:95:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20625 (20.6 KB)  TX bytes:20625 (20.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:79:1b:5b  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe79:1b5b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1116341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:553489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1600759356 (1.6 GB)  TX bytes:71419995 (71.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-79-1B-5B-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

mobile@mobile-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WeedNet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1C:F0:54:32:75   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=22/70  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``` **Check for modules:**
```
cfg80211      109144  3 ath9k,mac80211,ath

ath9k                 278176  0 
mac80211              210104  1 ath9k
led_class               5256  2 ath9k,acer_wmi
ath                    10304  1 ath9k
cfg80211              109144  3 ath9k,mac80211,ath

```  **Network configuration**
```
   *-network               
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:1f:16:ca:95:7c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f0300000-f030ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:79:1b:5b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k ip=192.168.0.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0400000-f040ff 
```[B]Scan for networks:
[/B]```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:5F:F9:6D
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=2/70  Signal level=-108 dBm  
                    Encryption key:off
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e31708c18b
                    Extra: Last beacon: 5680ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F4000000
          Cell 02 - Address: 00:21:29:92:A8:11
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/70  Signal level=-116 dBm  
                    Encryption key:off
                    ESSID:"seretti"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000159c1e76183
                    Extra: Last beacon: 5680ms ago
                    IE: Unknown: 000773657265747469
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180201F4000000

```**Ubuntu Version: **
```
 Ubuntu 9.10 
```**Kernel/architecture (including 32 vs. 64 bit): **
```
2.6.31-14-generic x86_64
```[B]Restarting the network:
[/B]```
mobile@mobile-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```
Edit:
Here is the debug log right when I lose connection and can not reconnect

Nov  1 00:29:34 mobile-laptop kernel: [  780.034546] ath9k: DMA failed to stop in 10 ms AR_CR=0x00000024 AR_DIAG_SW=0x40000020
mobile-laptop NetworkManager: <debug> [1257050736.005911] periodic_update(): Roamed from BSSID (none) ((none)) to 00:1C:F0:54:32:75 (WeedNet)

---

### Post by mattweed9 on 2009-11-01
I wouldn't say this is really a fix, but I installed Wicd network manager and the connection is now stable. I am only getting about 500 kb/s when downloading when it should be higher. Seems to be a temporary fix allowing me to at least now use this laptop with out constant connection loss. Would be nice to have it working better, but I am glad I figured something out, Ubuntu about got canned. 

Anyone know why this might be? I don't know enough about the two network managers to better understand the issue. I know when the original one was installed, it reached much higher speeds before it zeroed out. This Wicd one, seems to stay a steady 500-600 kb/s. Any way to join them together lol?

---

