---
title: "Wired Connection problems in Ubuntu 10.04"
date: 2012-04-26
forum: Networking &amp; Wireless
---

### Post by ksp1717 on 2012-04-26
Hi

I have used Ubuntu before on my old laptop and have been using Win 7 since I switched to a new machine around 6 months. So I have finally decided to install Ubuntu again. I downloaded the 10.04 x64 and installed it on an empty partition. As a bonus I lost my win partitions. I spent an hour trying to recover the partition and finally succeeded in recovering everything except windows system partition. But I have different problems now.

1. Before I attempted to recover the partitions my internet was working fine. I have a wired connection as well as a wireless one. So initially only my wired connection was working although slower than what it used to be in the windows. The wireless was going on and off and I thought I should probably install the correct driver for my wireless modem. 

2. While in the process of recovering paritions I realized that my wired connection is not working altogether and the wireless continued doing what it was doing before.

3. After I finished my recovery, my wired connection is not even being detected. I remove the wire and reinsert it, I restarted my system but no luck in getting it working. Now the wireless started working for some reason although slow. It also keeps disconnecting every now and then. The taskbar icon does not show that it is disconnected but the internet stops working. 

I went through some of the threads in the forum but have no luck finding a solution. I have pasted some command outputs of the commands I have seen in the threads.

Any help resolving this is greatly appreciated.

```
ifconfig
```
[HTML]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2091 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:227655 (227.6 KB)  TX bytes:227655 (227.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:c7:30:01:0a  
          inet addr:10.195.120.78  Bcast:10.195.127.255  Mask:255.255.224.0
          inet6 addr: fe80::226:c7ff:fe30:10a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:976304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:375097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:775427460 (775.4 MB)  TX bytes:37293055 (37.2 MB)
[/HTML]

```
wget ftp://ftp.xs4all.nl/pub/test/100mb.bin -O/dev/null

```

[HTML]--2012-04-26 17:02:16--  ftp://ftp.xs4all.nl/pub/test/100mb.bin
           => `/dev/null'
Resolving ftp.xs4all.nl... 194.109.21.26
Connecting to ftp.xs4all.nl|194.109.21.26|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/test ... done.
==> SIZE 100mb.bin ... 104857600
==> PASV ... done.    ==> RETR 100mb.bin ... done.
Length: 104857600 (100M) (unauthoritative)

100%[=========================================>] 104,857,600  234K/s   in 7m 28s  

2012-04-26 17:09:46 (229 KB/s) - `/dev/null' saved [104857600]
[/HTML]

```
lspci -v
```

[HTML]00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0, IRQ 27
	Memory at b0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3050 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at b4406100 (64-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at b4405c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at b4400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b3400000-b43fffff
	Prefetchable memory behind bridge: 00000000b0400000-00000000b13fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: b2400000-b33fffff
	Prefetchable memory behind bridge: 00000000b1400000-00000000b23fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at b4405800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) (prog-if 01)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
	I/O ports at 3048 [size=8]
	I/O ports at 305c [size=4]
	I/O ports at 3040 [size=8]
	I/O ports at 3058 [size=4]
	I/O ports at 3020 [size=32]
	Memory at b4405000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: medium devsel, IRQ 10
	Memory at b4406000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 3000 [size=32]
	Kernel modules: i2c-i801

02:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
	Subsystem: Intel Corporation Device 1315
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at b2400000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0

ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0

ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0

ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0

ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0

ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
	Subsystem: Hewlett-Packard Company Device 1435
	Flags: bus master, fast devsel, latency 0
[/HTML]

```
mtr -r -c5 8.8.8.8
```
[HTML] 1. ro-secure-ms.net.osu          0.0%     5    1.0   1.0   1.0   1.3   0.1
  2. 139.78.1.110                  0.0%     5   74.0  18.2   1.0  74.0  31.4
  3. 139.78.1.98                   0.0%     5   11.4   4.0   1.3  11.4   4.3
  4. thor-thorfw.net.okstate.edu   0.0%     5    1.4   1.5   1.4   1.8   0.2
  5. 164.58.10.65                  0.0%     5   85.4  18.1   1.2  85.4  37.6
  6. 164.58.15.238                 0.0%     5   38.1  11.8   2.7  38.1  14.9
  7. 164.58.15.134                 0.0%     5    3.2   3.0   2.8   3.6   0.4
  8. 156.110.203.2                 0.0%     5    7.5   7.7   7.5   8.0   0.3
  9. 74.125.48.106                 0.0%     5   18.2  37.1  18.0  75.2  25.9
 10. 74.125.48.105                 0.0%     5   18.2  26.4  18.1  40.4  11.4
 11. 209.85.254.128                0.0%     5   19.2  18.7  18.4  19.2   0.3
 12. 72.14.237.130                 0.0%     5   18.5  36.2  18.5 104.7  38.3
 13. 72.14.232.141                 0.0%     5   29.2  33.9  29.1  52.7  10.5
 14. 216.239.43.217                0.0%     5   29.0  28.9  28.9  29.0   0.0
 15. 216.239.47.133                0.0%     5   35.5  44.9  35.5  63.5  10.7
 16. google-public-dns-a.google.c  0.0%     5   28.9  28.9  28.8  29.0   0.0
[/HTML]

--shyam

---

### Post by ksp1717 on 2012-04-27
Hi

I have noticed that everything works fine today. Not sure why it was like that before.

--shyam

---

### Post by josephmills on 2012-04-27
Please file a bug. Devs can not do anything if they do not know about it :) 

[http://www.youtube.com/watch?v=495V7FokwBU](http://www.youtube.com/watch?v=495V7FokwBU)



thanks 

Joseph 

ps glad that it is working.

---

### Post by ksp1717 on 2012-04-30
Thank you joseph

After looking around for a while I turned off the wifi power management and now the wifi kinda seems to be stable and the lan is working too. I will file a bug if it repeats again.

--shyam

---

