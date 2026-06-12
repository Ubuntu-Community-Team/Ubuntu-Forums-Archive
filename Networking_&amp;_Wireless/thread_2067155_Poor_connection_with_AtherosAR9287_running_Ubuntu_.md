---
title: "Poor connection with AtherosAR9287 running Ubuntu 12.04"
date: 2012-10-06
forum: Networking &amp; Wireless
---

### Post by Zomgrick on 2012-10-06
Hello all,

My wireless connection in Ubuntu is very slow, while the connection is perfect in Windows 7. It also seems to switch between a good and a poor signal, as my browser sometimes loads sites instantly and sometimes takes ages. Also I'm currently trying to install java via the terminal and it's taking forever, with download speeds varying from 1B/s to 200kb/s. Again: I don't have any of these problems on Windows. I'm new with Ubuntu but I've tried to gather some information for you which might be helpful. 

Here is some info:

I'm using an Acer Aspire 5552G Laptop. 

$ iwlist scan:

```
wlan0     Scan completed :
          Cell 01 - Address: 00:02:6F:C0:96:B4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"EnGeniusC096B4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008c7ef199139
                    Extra: Last beacon: 52176ms ago

```sudo lshw -c network

```
*-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 20:7c:8f:28:0a:03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-31-generic firmware=N/A ip=192.168.178.29 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1000000-f100ffff

```iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:"EnGeniusC096B4"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:02:6F:C0:96:B4   
          Bit Rate=162 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10992  Invalid misc:124   Missed beacon:0

```

---

### Post by Zomgrick on 2012-10-06
I'm sure someone can help me.. Would be much appreciated!

---

### Post by Zomgrick on 2012-10-07
Bump.. Someone please, pretty pretty please, help me!

---

### Post by kurt18947 on 2012-10-07
No guarantees but you could try what post #5 in this thread says:

[http://ubuntuforums.org/showthread.php?t=1998100&highlight=atheros+hardware+encryption](http://ubuntuforums.org/showthread.php?t=1998100&highlight=atheros+hardware+encryption)

---

