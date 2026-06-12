---
title: "No Ethernet Connection"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by pinbill on 2010-10-12
Hello All-

With lots of help from this forum I just finished a dual boot setup with win7 and ubuntu 10.4 on a week old toshiba satellite a665! Both operating systems are working well and I can connect to the internet from a wireless connection on windows. However I am not able to connect on either system by ethernet connection. I need to connect with the cable to update ubuntu for wireless. I use the cable to run my desktop so I know it works. Does anyone know where I should start looking to solve this?

Thanks,

Bill

---

### Post by pinbill on 2010-10-12
bump.

---

### Post by Iowan on 2010-10-12
**ifconfig -a** should show if the interface is recognized. **sudo lshw -C network** will provide more information. If the interface shows up - you might try **dhclient eth0**.

---

### Post by pinbill on 2010-10-12
Please excuse my newbieness, do I put these commands in windows7 somewhere or a terminal in ubuntu? I know how to open a terminal in ubuntu but not sure how to enter commands in windows,

Thanks for the reply,

Bill

---

### Post by JackNocturne on 2010-10-12
Hello,


You do those commands at the **Terminal** in Ubuntu

---

### Post by pinbill on 2010-10-12
I tried them in the terminal in ubuntu and it was not recognized. Does that mean the port itself is broken.

Thanks for the help,

Bill

---

### Post by JackNocturne on 2010-10-12
Im not sure , could try posting what you got as output?

Also if networking fails in the end, you could download the drivers for the wireless interface from the Ubuntu Repository **manually**(From another computer), save it on a flash disk then transfer it to your own Toshiba Satellite and **install it**(usually in .deb format)

---

### Post by pinbill on 2010-10-13
Here is the report from ifconfig -a:

robertwgrodeska@johnny8:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:54:fc:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:23:15:19:a7:14  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Hope this helps,

Thanks,

Bill

---

### Post by dineshs on 2010-10-13
please also post the output of
```
sudo lshw -C network
```and```
sudo dhclient eth0
```as lowan suggested

---

### Post by pinbill on 2010-10-13
Here is the sudo lshw c network command:

robertwgrodeska@johnny8:~$ sudo lshw -cnetwork
[sudo] password for robertwgrodeska: 
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

    -version        print program version (B.02.14)

format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information

options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

Thanks,

Bill

---

### Post by dineshs on 2010-10-13
> sudo lshw -cnetwork
the command you typed was incorrect.Pl see the previos post #9

---

### Post by pinbill on 2010-10-13
Alright, here is the stuff. Please let me know what you think, thanks again for all the help,
 
Bill
 
robertwgrodeska@johnny8:~$ sudo lshw -C network
[sudo] password for robertwgrodeska: 
*-network 
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: 05
serial: 88:ae:1d:54:fc:fb
size: 10MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
resources: irq:34 ioport:6000(size=256) memory:d0404000-d0404fff(prefetchable) memory:d0400000-d0403fff(prefetchable)
*-network DISABLED
description: Wireless interface
product: WiMAX/WiFi Link 6050 Series
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 57
serial: 00:23:15:19:a7:14
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
resources: irq:36 memory:d4600000-d4601fff
 
 
robertwgrodeska@johnny8:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Listening on LPF/eth0/88:ae:1d:54:fc:fb
Sending on LPF/eth0/88:ae:1d:54:fc:fb
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by dineshs on 2010-10-14
From your first post> However I am not able to connect on either system by ethernet connection
You mean in windows and ubuntu in the same laptop?Then could it be a hardware fault?
> product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
see if [this]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false") link can help

---

### Post by Christofferh on 2010-10-14
I'm not sure whether we have the same problem or not but we're experiencing similiar results on boot. The problem is on a new desktop computer with onboard network card. The motherboard is the "MSI H55-GD65 Gaming Series, H55, Socket-1156 DDRIII, ATX, 2xPCI-Ex(2.0)x16, GbLan, OC Genie, DrMOS".

I've installed a dual boot for windows 7 and ubuntu 10.04(and upgraded to 10.10 yesterday) on boot the wired connection stays down. I can then load a terminal window and write:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```
and the wired connection loads immediately. I'm experiencing similar problems in windows 7 but the connection works after a minute or two. This makes me believe that there might be somekind of hardware fault but I'm hoping it might just be that the drivers aren't up to date.

**ifconfig -a**
```
eth0      Link encap:Ethernet  HWaddr 40:61:86:8c:5c:63  
          inet addr:192.168.10.33  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fe8c:5c63/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3681 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3864498 (3.8 MB)  TX bytes:638402 (638.4 KB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:461 errors:0 dropped:0 overruns:0 frame:0
          TX packets:461 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:97661 (97.6 KB)  TX bytes:97661 (97.6 KB)

virbr0    Link encap:Ethernet  HWaddr f6:f2:2a:cd:ef:1b  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::f4f2:2aff:fecd:ef1b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:17341 (17.3 KB)
```

**dmesg | grep r8169**
```
[    1.912072] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.912093] r8169 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.912142] r8169 0000:04:00.0: setting latency timer to 64
[    1.912196] r8169 0000:04:00.0: irq 44 for MSI/MSI-X
[    1.912596] r8169 0000:04:00.0: eth0: RTL8168d/8111d at 0xffffc900110b2000, 40:61:86:8c:5c:63, XID 081000c0 IRQ 44
[    3.918804] r8169 0000:04:00.0: eth0: link down
```

**sudo lshw -C network**
```
  *-network               
   description: Ethernet interface
   product: RTL8111/8168B PCI Express Gigabit Ethernet controller
   vendor: Realtek Semiconductor Co., Ltd.
   physical id: 0
   bus info: pci@0000:04:00.0
   logical name: eth0
   version: 03
   serial: 40:61:86:8c:5c:63
   size: 10MB/s
   capacity: 1GB/s
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.10.33 latency=0 link=yes multicast=yes port=MII speed=10MB/s
   resources: irq:44 ioport:d800(size=256) memory:f6fff000-f6ffffff memory:f6ff8000-f6ffbfff memory:fbee0000-fbefffff
```

**Has anyway got any ideas on how to proceed?**

----- EDIT -----
I tried to install the drivers from [http://www.realtek.com/downloads...]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=4&PFid=4&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8110S-32/RTL8110SB%28L%29/RTL8169SB%28L%29/RTL8169SC%28L%29%3Cbr%3ERTL8169") but seems like it's not possible to build them on the current kernel(?) at least that is the only response I get from searching through google on the make errors I get.

**make clean modules**
```
make clean modules
make -C src/ clean
make[1]: Entering directory `/home/holmen/Drivers/r8169-6.013.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers rset modules.order Module.markers
make[1]: Leaving directory `/home/holmen/Drivers/r8169-6.013.00/src'
make -C src/ modules
make[1]: Entering directory `/home/holmen/Drivers/r8169-6.013.00/src'
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/holmen/Drivers/r8169-6.013.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/holmen/Drivers/r8169-6.013.00/src/r8169_n.o
/home/holmen/Drivers/r8169-6.013.00/src/r8169_n.c: In function &#8216;rtl8169_set_rx_mode&#8217;:
/home/holmen/Drivers/r8169-6.013.00/src/r8169_n.c:3887: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/home/holmen/Drivers/r8169-6.013.00/src/r8169_n.c:3898: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_list&#8217;
/home/holmen/Drivers/r8169-6.013.00/src/r8169_n.c:3898: error: &#8216;struct net_device&#8217; has no member named &#8216;mc_count&#8217;
/home/holmen/Drivers/r8169-6.013.00/src/r8169_n.c:3899: error: dereferencing pointer to incomplete type
/home/holmen/Drivers/r8169-6.013.00/src/r8169_n.c:3900: error: dereferencing pointer to incomplete type
make[3]: *** [/home/holmen/Drivers/r8169-6.013.00/src/r8169_n.o] Error 1
make[2]: *** [_module_/home/holmen/Drivers/r8169-6.013.00/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/holmen/Drivers/r8169-6.013.00/src'
make: *** [modules] Error 2
```

Anyone have any other idea on this one?

--- EDIT ---
I went to the store today and bought a new Intel gigabit PCIe network card. Works just fine and the speed is at 1Gb/s now.

---

