---
title: "Desktop internet randomly stops working"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by ghost25 on 2011-03-02
Hey guys, got another question for ya.

Not sure if I've listed the specs of this machine before, so I'll do it again. I'm running an HP Pavilion 760n with 512MB of RAM and (I think?) a Pentium III processor... not sure on that one right now. It's currently running a laptop version of Ubuntu 10.04.

I went to log into my online classes tonight only to find that the computer wasn't responding at all. I did a hot shutdown and restarted it, and now the system isn't detecting the internet connection at all. It should be noted that the connection was working perfectly fine earlier today, perhaps 6 or 7 hours ago. I know it's something to do with my computer and not my router, as I'm on my wireless network from a Windows 7 laptop and it's connecting just fine.

In viewing another thread, [http://ubuntuforums.org/showthread.php?t=1505697&highlight=desktop+network+problems+-wireless](http://ubuntuforums.org/showthread.php?t=1505697&highlight=desktop+network+problems+-wireless), I found a bunch of commands that it was said would be helpful diagnosing this issue. That said, below is the output of all the commands that I could think of.

**Sudo ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:e0:18:5c:45:7a  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0 
          inet6 addr: fe80::2e0:18ff:fe5c:457a/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:385 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5526 (5.5 KB)  TX bytes:81437 (81.4 KB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:225 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:27043 (27.0 KB)  TX bytes:27043 (27.0 KB) 

**lspci**
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04) 
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05) 
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05) 
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05) 
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05) 
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05) 
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05) 
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15) 
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03) 
02:09.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 04) 
02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02) 

**ifup eth0**
ifup: interface eth0 already configured 

**cat /etc/network/interfaces** 
auto eth0 
iface eth0 inet static 
address 192.168.2.1 
netmask 255.255.255.0 
network 192.168.2.0 
broadcast 192.168.2.255 

**cat /etc/NetworkManager/nm-system-settings.conf**
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file: 
# 
# /etc/default/NetworkManager 
# 

[main] 
plugins=ifupdown,keyfile 

[ifupdown] 
managed=false 

**dmesg | grep -e eth0 -e bcm** 
[    2.072423] e100: eth0: e100_probe: addr 0xf3800000, irq 20, MAC addr 00:e0:18:5c:45:7a 
[   18.230196] ADDRCONF(NETDEV_UP): eth0: link is not ready 
[   18.232170] e100: eth0 NIC Link is Up 100 Mbps Full Duplex 
[   18.232554] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
[   28.736010] eth0: no IPv6 routers present 
[  166.816333] e100: eth0 NIC Link is Down 
[  202.816151] e100: eth0 NIC Link is Up 100 Mbps Full Duplex 
[  212.816319] e100: eth0 NIC Link is Down 
[  214.816190] e100: eth0 NIC Link is Up 100 Mbps Full Duplex 

**lshw -C Network** 
  *-network               
       description: Ethernet interface 
       product: 82801BA/BAM/CA/CAM Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 03 
       serial: 00:e0:18:5c:45:7a 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.1 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s 
       resources: irq:20 memory:f3800000-f3800fff ioport:d800(size=64) 

**lspci -nn** 
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04) 
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 05) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 05) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 05) 
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 05) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 05) 
00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 05) 
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 05) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] [10de:002d] (rev 15) 
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03) 
02:09.0 FireWire (IEEE 1394) [0c00]: Agere Systems FW322/323 [11c1:5811] (rev 04) 
02:0b.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:044e] (rev 02)

---

### Post by ghost25 on 2011-03-03
Bump.

Just a quick update here... I pulled the system apart to add a new case fan to the rig, and fired it back up. Still no internet. Anyone?

---

