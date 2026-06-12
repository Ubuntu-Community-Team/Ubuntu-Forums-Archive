---
title: "Wifi not working after installing 12.10, but working on live usb"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by ryan88 on 2013-01-10
I just installed Ubuntu 12.10 using a live usb stick.  During this installation, the wifi worked correctly and connected to the network and downloaded language packs and packages.  However when I booted in to the system after installation had finished, the wifi card is recognised, but it does not find any wireless networks.  I took a wireless dongle out of one of my other machines and this works fine, so it suggests it is not liking the wireless card for some reason.  Does anyone have any ideas?

Output from lspci:
```

    ryan@ryan-comp:~$ lspci
    00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Complex
    00:00.2 IOMMU: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) I/O Memory Management Unit
    00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7660D]
    00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
    00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port
    00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
    00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
    00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (rev 40)
    00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
    00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
    00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
    00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
    00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14)
    00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
    00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
    00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
    00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
    00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 0
    00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 1
    00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 2
    00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 3
    00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 4
    00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Function 5
    01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    02:06.0 Ethernet controller: Belkin F5D7000 v7000 Wireless G Desktop Card [Realtek RTL8185] (rev 20)

```
Output from ifconfig:
```

ryan@ryan-comp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:2b:34:a7:3d:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94028 (94.0 KB)  TX bytes:94028 (94.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:d3:c7:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
Output from iwconfig:
```

ryan@ryan-comp:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
Output from cat /etc/network/interfaces:
```

ryan@ryan-comp:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

