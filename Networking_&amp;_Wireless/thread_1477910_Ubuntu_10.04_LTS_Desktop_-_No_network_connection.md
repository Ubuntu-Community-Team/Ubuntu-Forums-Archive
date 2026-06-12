---
title: "Ubuntu 10.04 LTS Desktop - No network connection"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by kulashish on 2010-05-09
I recently installed Ubuntu 10.04 on my Compaq Presario X6000. Since then. I have been struggling to get either wired or wireless network up on it. This is my first serious attempt at installing and setting up a laptop with a Linux distro. Could somebody please help?

Here's the output of lspci - 
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Thanks
Ashish

---

### Post by Iowan on 2010-05-09
A couple more things to check/post (from a terminal):
**sudo lshw -C network**
**ifconfig -a**

---

### Post by kulashish on 2010-05-09
Thanks Iowan!
Here's the result of running those commands :
lshw - 
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:8e:52:82
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:5000(size=256) memory:c8209400-c82094ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:c8206000-c8207fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:a6:17:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
------------------------------------------------------------------------------------------
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:8e:52:82  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x5000 

eth0:avahi Link encap:Ethernet  HWaddr 00:c0:9f:8e:52:82  
          inet addr:169.254.8.123  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:652 errors:0 dropped:0 overruns:0 frame:0
          TX packets:652 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52032 (52.0 KB)  TX bytes:52032 (52.0 KB)

pan0      Link encap:Ethernet  HWaddr de:5b:0b:16:a5:5d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a6:17:16  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thanks
Ashish

---

### Post by eltonw on 2010-05-09
You may need to install the Realtek drivers, available HERE:
[http://www.opendrivers.com/company/2358/realtek-free-driver-download.html]("http://www.opendrivers.com/company/2358/realtek-free-driver-download.html")

HTH...

---

### Post by kulashish on 2010-05-10
Thanks eltonw!
I did not find an RTL8139 driver for Linux in that list. Am I missing something?

~Ashish.

---

### Post by kulashish on 2010-05-10
Hi
Do I need to provide any other information? Have still not been able to locate a suitable RTL driver for ubuntu. Any suggestions??

~Ashish

---

### Post by Iowan on 2010-05-10
Dunno if there's a newer/better driver than the 8139too that you system is currently using. [This]("http://ubuntuforums.org/showthread.php?t=580773") is an old thread, but there's an interesting tidbit near the end.> **Ehtetur said:**
> Finally, I took a look at System --> Preferences --> Sessions... Bluetooth Manger was enabled... my desktop doesn't have bluetooth so I disabled it.. 
After rebooting, I got on the network fine.

---

### Post by talkingwires on 2010-05-12
I'm having the same problem with this chipset. I posted one [potential solution that didn't work for me in another thread]("http://ubuntuforums.org/showpost.php?p=9259652&postcount=4"). Maybe you'll have better luck?

---

### Post by talkingwires on 2010-05-14
Bump.

---

### Post by Worp8d on 2010-05-18
Seems a very similar problem to the one I'm having [here]("http://swiss.ubuntuforums.org/showthread.php?p=9323229#post9323229").

---

### Post by mtdesign on 2010-07-31
I am also having this issue on a Compaq Presario F500, any fixes yet?

---

### Post by ruimarto on 2011-08-02
I've had some problems that were solved after I used the jumper on the board to reset the BIOS.

[http://ubuntuforums.org/showthread.php?p=11111292#post11111292](http://ubuntuforums.org/showthread.php?p=11111292#post11111292)

---

