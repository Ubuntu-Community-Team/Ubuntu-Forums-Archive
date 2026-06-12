---
title: "Driver installed using ndiswrapper, hardware detected but No such device for wlan0 .."
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by arundracula on 2010-09-14
I have a Belkin F5D7000ak Wireless G Card. I've its windows driver. And I've installed it using ndiswrapper.

**lspci -nn:**
```

00:00.0 RAM memory [0500]: nVidia Corporation MCP61 LPC Bridge [10de:03e2] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e1] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:06.0 Ethernet controller [0200]: Belkin Device [1799:700f] (rev 20)
02:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce 9800 GT] [10de:0614] (rev a2)


```**ndiswrapper -l**
```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
belkin : driver installed
    device (1799:700F) present (alternate driver: rtl8180)

```**ifconfig**
```

eth0      Link encap:Ethernet  HWaddr 00:26:18:8b:9a:70  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1060 (1.0 KB)  TX bytes:1060 (1.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.254.164.179  P-t-P:192.168.52.12  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:21713 errors:1 dropped:0 overruns:0 frame:0
          TX packets:16975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:24602650 (24.6 MB)  TX bytes:1878039 (1.8 MB)

```**iwconfig **
```


lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

```

sudo lshw -C Network
```

  *-network UNCLAIMED     
       description: Ethernet controller
       product: Belkin
       vendor: Belkin
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:d800(size=256) memory:dbfffc00-dbfffdff

```

And also 
**lspci | grep Ethernet**
```
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
01:06.0 Ethernet controller: Belkin Device 700f (rev 20)
```Please help...

---

