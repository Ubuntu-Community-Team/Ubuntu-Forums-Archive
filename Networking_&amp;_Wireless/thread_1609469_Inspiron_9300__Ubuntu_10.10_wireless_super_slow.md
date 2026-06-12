---
title: "Inspiron 9300 / Ubuntu 10.10 wireless super slow"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by meconlin on 2010-10-30
Wireless connection is very very slow. Mostly have tried firefox and chrome. IPV6 fix in firefox had no better results.  

Any help would be great. Thank you.

```

 >>>lshw -C network
  <...snip>
    *-network:1
         description: Wireless interface
         product: PRO/Wireless 2915ABG [Calexico2] Network Connection
         vendor: Intel Corporation
         physical id: 3
         bus info: pci@0000:03:03.0
         logical name: eth1
         version: 05
         serial: 00:12:f0:47:e1:78
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical wireless
         configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.0.12 latency=64 maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
         resources: irq:17 memory:dfcfd000-dfcfdfff
   
  >>>lspci -nn | grep 'Wireless'
  03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4223] (rev 05)
   
  >>>ifconfig
  eth0      Link encap:Ethernet  HWaddr 00:11:43:78:a9:e5  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:18 
   
  eth1      Link encap:Ethernet  HWaddr 00:12:f0:47:e1:78  
            inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
            inet6 addr: fe80::212:f0ff:fe47:e178/64 Scope:Link
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:45 errors:0 dropped:0 overruns:0 frame:0
            TX packets:43 errors:0 dropped:3 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:4757 (4.7 KB)  TX bytes:6403 (6.4 KB)
            Interrupt:17 Base address:0x4000 Memory:dfcfd000-dfcfdfff 
    lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:10 errors:0 dropped:0 overruns:0 frame:0
            TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:688 (688.0 B)  TX bytes:688 (688.0 B)
    >>> iwconfig
  lo        no wireless extensions.
  eth0      no wireless extensions.
  eth1      IEEE 802.11abg  ESSID:"mechome"  
            Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0C:41:FC:DD:B7   
            Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
            Retry limit:7   RTS thr:off   Fragment thr:off
            Power Management:on
            Link Quality=89/100  Signal level=-30 dBm  Noise level=-89 dBm
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:1
    >>>lsmod | grep 'ipw2200'
  ipw2200               136715  0 
  libipw                 39808  1 ipw2200
  cfg80211              144470  2 ipw2200,libipw
  lib80211                5058  3 lib80211_crypt_wep,ipw2200,libipw
    >>>>dmesg | grep 'ipw2200'
  [   20.006892] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
  [   20.006896] ipw2200: Copyright(c) 2003-2006 Intel Corporation
  [   20.007001] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  [   20.021084] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
  [   20.459574] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
   
  >>>>lsb_release -d
  Description:      Ubuntu 10.10
   
  >>>>uname -mr
  2.6.35-22-generic i686
    
```

---

### Post by DK-one on 2010-11-12
Hello,

I also have troubles with my wifi since a week or so. I run Ubuntu 10.10 on a lenovo T400 with an PRO/Wireless 5100 AGN [Shiloh] Network Connection. Does anyone have a hint for trouble shooting? I can conect over wifi but the connection ist much slower than usually.

Thank you a lot in advance.

DK-One

---

