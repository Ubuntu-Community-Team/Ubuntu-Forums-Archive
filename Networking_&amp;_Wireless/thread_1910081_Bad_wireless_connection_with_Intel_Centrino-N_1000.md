---
title: "Bad wireless connection with Intel Centrino-N 1000"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by _MiKu_ on 2012-01-16
I'm having wireless connectivity problems in Ubuntu 11.10 with certain networks with the Intel Centrino-N 1000 card on Lenovo Thinkpad T420. The connection is dropping frequently, generally really slow and network manager is reporting either 1 Mb/s or 2 Mb/s speed. A certain speed tester gave me 2.83 Mb/s in Ubuntu but when I booted to Windows 7 I got 16.88 Mb/s in the same network. In Windows, the link is stable and reported as 11g at 54 Mb/s. I tried disabling the N-mode as suggested in [http://ubuntuforums.org/showpost.php?p=11425909&postcount=2](http://ubuntuforums.org/showpost.php?p=11425909&postcount=2) but this didn't solve the problem.

Any ideas about what to try?

Output of the diagnostics:

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:21:cc:6a:42:dd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f3900000-f3920000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:e5:0b:69:aa:5a  
          inet addr:86.50.137.80  Bcast:86.50.139.255  Mask:255.255.252.0
          inet6 addr: fe80::76e5:bff:fe69:aa5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1577 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1533976 (1.5 MB)  TX bytes:231079 (231.0 KB)

```iwconfig
```

wlan0     IEEE 802.11bg  ESSID:"aalto open"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:27:0D:0B:D1:C0   
          Bit Rate=1 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:29   Missed beacon:0

```lsmod | grep "iwl"
```

iwlagn                273937  0 
mac80211              393459  1 iwlagn
cfg80211              172392  2 iwlagn,mac80211

```dmesg | grep "iwl"
```
[   13.207042] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   13.207045] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[   13.207095] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   13.207103] iwlagn 0000:03:00.0: setting latency timer to 64
[   13.207129] iwlagn 0000:03:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[   13.226892] iwlagn 0000:03:00.0: device EEPROM VER=0x15d, CALIB=0x6
[   13.226895] iwlagn 0000:03:00.0: Device SKU: 0X9
[   13.226896] iwlagn 0000:03:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[   13.227914] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   13.227994] iwlagn 0000:03:00.0: irq 43 for MSI/MSI-X
[   13.314173] iwlagn 0000:03:00.0: loaded firmware version 39.31.5.1 build 35138
[   13.331415] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'

```lshw -C network
```

  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:69:aa:5a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-14-generic-pae firmware=39.31.5.1 build 35138 ip=86.50.137.80 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:43 memory:f3800000-f3801fff

```iwlist scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:27:0D:0B:D1:C0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:off
                    ESSID:"aalto open"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007ce8c37178
                    Extra: Last beacon: 45424ms ago
                    IE: Unknown: 000A61616C746F206F70656E
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 0706464920010D14
                    IE: Unknown: 0B050100260000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3603FBCB03
                    IE: Unknown: 851E03008F000F00FF035900742D623330372D61700000000000000001000036
                    IE: Unknown: 9606004096001100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD06004096010104
                    IE: Unknown: DD050040960305
                    IE: Unknown: DD050040960B09
                    IE: Unknown: DD050040961400

```uname -mr
```

3.0.0-14-generic-pae i686 

```

---

### Post by Gwrtheyrn on 2012-02-04
Same problem here... (Thinkpad Edge 13, Intel Centrino-N 1000).

---

### Post by eskararriba on 2012-04-10
same problem on thinkpad e420s - anyone found a solution yet?

---

