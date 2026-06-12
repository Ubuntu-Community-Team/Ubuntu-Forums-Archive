---
title: "Slow wlan connection"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by Angelic on 2010-10-16
I've installed 10.10 on my laptop but I am experiencing extremely slow wlan speeds. I've tried two different wlan cards but it doesn't make a difference. 

As soon as a file is found it downloads like it should, it just takes forever to locate a page or file online. It does differ though, when I keep browsing within the same page it's usually not too bad, but when I go to a new page it often needs up to 8 seconds to find the page.

I've done a traceroute to google.com with both cards but it doesn't seem to make much of a difference:

First card:

```
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 1c:4b:d6:c6:c8:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:febf0000-febfffff

```

```
traceroute to www.google.com (74.125.79.104), 30 hops max, 60 byte packets
 1  openrg.home (192.168.1.1)  3.041 ms  3.834 ms  4.993 ms
 2  83.119.128.1 (83.119.128.1)  24.016 ms  25.087 ms  25.889 ms
 3  194.134.187.50 (194.134.187.50)  27.054 ms  28.893 ms *
 4  194.134.162.12 (194.134.162.12)  31.325 ms  32.042 ms  34.885 ms
 5  194.134.161.102 (194.134.161.102)  35.714 ms  36.463 ms  37.193 ms
 6  72.14.198.29 (72.14.198.29)  38.030 ms  18.935 ms  18.632 ms
 7  209.85.254.250 (209.85.254.250)  19.567 ms 209.85.254.92 (209.85.254.92)  22.672 ms  23.794 ms
 8  64.233.175.246 (64.233.175.246)  27.039 ms  28.543 ms  29.552 ms
 9  72.14.239.199 (72.14.239.199)  31.507 ms 209.85.255.166 (209.85.255.166)  38.340 ms 72.14.239.197 (72.14.239.197)  33.297 ms
10  209.85.255.126 (209.85.255.126)  34.547 ms  36.084 ms 209.85.255.130 (209.85.255.130)  36.957 ms
11  74.125.79.104 (74.125.79.104)  39.036 ms  23.253 ms  24.174 ms

```

Second card: 

```

  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan1
       serial: 00:19:70:07:0a:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.35-22-generic firmware=N/A ip=192.168.1.16 link=yes multicast=yes wireless=IEEE 802.11bg

```

```
traceroute to www.google.com (74.125.79.104), 30 hops max, 60 byte packets
 1  openrg.home (192.168.1.1)  2.034 ms  4.718 ms  5.423 ms
 2  83.119.128.1 (83.119.128.1)  23.014 ms  24.193 ms  25.903 ms
 3  194.134.187.50 (194.134.187.50)  27.104 ms  29.161 ms *
 4  194.134.162.12 (194.134.162.12)  29.910 ms  31.903 ms  32.610 ms
 5  194.134.161.102 (194.134.161.102)  77.582 ms  78.426 ms  79.530 ms
 6  72.14.198.29 (72.14.198.29)  36.564 ms  18.997 ms  19.942 ms
 7  209.85.254.250 (209.85.254.250)  21.081 ms 209.85.254.92 (209.85.254.92)  22.786 ms 209.85.254.250 (209.85.254.250)  24.739 ms
 8  72.14.233.114 (72.14.233.114)  29.186 ms 64.233.175.246 (64.233.175.246)  26.971 ms  28.039 ms
 9  209.85.255.143 (209.85.255.143)  32.964 ms 72.14.239.197 (72.14.239.197)  31.931 ms  33.767 ms
10  209.85.255.122 (209.85.255.122)  41.528 ms 209.85.255.130 (209.85.255.130)  22.375 ms 209.85.255.122 (209.85.255.122)  26.140 ms
11  74.125.79.104 (74.125.79.104)  25.226 ms  27.539 ms  28.384 ms

```

---

