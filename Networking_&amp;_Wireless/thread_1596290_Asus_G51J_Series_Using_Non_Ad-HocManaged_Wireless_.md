---
title: "Asus G51J Series: Using Non Ad-Hoc/Managed Wireless Modes"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by kthakore on 2010-10-14
Hello,

My school network is constantly warning me to not use Ad-Hoc mode for my wireless connection. I checked my network-manager for the connection and it says 'Infrastructure'. So I checked my iwconfig wlan0 and it says 'Ad-Hoc' so I tried 'Managed' mode. But then I got the same warning from my school. 

So I tried the other modes 'Repeater', 'Secondary', 'Master' or 'Auto' but they all say they are invalid. 

```

Error for wireless request "Set Mode" (8B06) :
   SET failed on device wlan0 ; Operation not supported.

```

Here is the command I ran
```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode repeater
sudo ifconfig wlan0 up

```

secondary, master, auto gives me 'Invalid Argument' instead of 'Operation not supported' .

I am on Ubuntu 10.04.

My wireless card's output for lspci is:

```

03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

ifconfig
```

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:8b:f0:14  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe8b:f014/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5007 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3542682 (3.5 MB)  TX bytes:798196 (798.1 KB)

```

iwconfig
```

wlan0     IEEE 802.11bgn  ESSID:"CXSFDF"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:12:27:22:3D   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lshw

```

*-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 01
                serial: 1c:4b:d6:8b:f0:14
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath9k driverversion=2.6.32-25-generic firmware=N/A ip=192.168.1.138 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:f4800000-f480ffff

```

---

### Post by kthakore on 2010-10-14
bump?

---

