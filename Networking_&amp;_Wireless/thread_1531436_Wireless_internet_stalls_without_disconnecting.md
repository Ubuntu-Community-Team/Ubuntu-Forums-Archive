---
title: "Wireless internet stalls without disconnecting"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by asenine on 2010-07-15
Hi,

I am in a conference center at the moment, and for some reason my internet keeps on slowing down to the point where I cannot ping anything, and any downloads that are in progress just display as downloading at 0kb/s. After about 30 seconds it usually comes back, but it is incredibly annoying. This happens about once every 3 minutes or so, it seems to happen particularly when I am downloading files. Nobody else in this building is having this problem, so it isn't the access points, and I am one of the network admins here so I am sure it is not some sort of intentional throttling (our setup doesn't have anything like that).

My wireless adapter uses a static IP, so I guess it isn't a problem with DHCP. This does not happen when I use ethernet.

Any ideas? Not sure what people want shown, but here are a few things I thought might be useful:

iwconfig:
```
wlan0     IEEE 802.11bg  ESSID:"IOFC"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:0E:7F:53:06   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:23:4d:14:14:82  
          inet addr:172.16.2.180  Bcast:172.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::223:4dff:fe14:1482/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3005 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3435078 (3.4 MB)  TX bytes:466454 (466.4 KB)
```

lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

Anything else you might need to help diagnose the issue, just ask.

Thanks a lot :)

---

