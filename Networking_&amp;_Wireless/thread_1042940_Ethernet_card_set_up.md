---
title: "Ethernet card set up"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by ricardo_78 on 2009-01-18
I have Ubuntu 8.10 set up with on board ethernet eth0 (which is unmanaged), however I have a PCI card eth1 (which is managed).

I can disable the on board ethernet card in Bios. 

How do I reconfigure my system to use the PCI card when I disable the on board ethernet in bios?

---

### Post by sully101 on 2009-01-18
I would assume that your PCI card is faster? You should not need to disable your onboard eth in bios in order to use the PCI card. Just plug your cable into it. What are you connecting to?

---

### Post by Whizam on 2009-01-18
In order to get a list of all the available ethernet cards on your system, run the following command:

```
ifconfig -a
```

If you haven't disabled the onboard adapter you should see more than one.

In order to use the PCI adapter run the following comand, but replace [interface] with the interface returned by ifconfig.

```
sudo ifconfig [interface] up
```

If there's only one interface (other than lo) returned by ifconfig the output of the command lspci would be helpful in debugging farther.

---

### Post by ricardo_78 on 2009-01-18
Output from ipcongfig a

```

eth0      Link encap:Ethernet  HWaddr 00:1b:b9:b1:db:0d  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10577187 (10.5 MB)  TX bytes:1702774 (1.7 MB)
          Interrupt:19 Base address:0xdead 

eth1      Link encap:Ethernet  HWaddr 00:1e:2a:ba:3e:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1540 (1.5 KB)  TX bytes:1540 (1.5 KB)

pan0      Link encap:Ethernet  HWaddr e2:25:43:4f:e9:91  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



```

and Lscpi
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 761/M761 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)


```

---

### Post by Whizam on 2009-01-18
It looks like you're plugged into eth0 currently, and you're using that connection. 

If you want to use eth1 run the following commands:

This will take down your onboard ethernet adapter
```
sudo ifconfig eth0 down
```

This will bring up the PCI adapter
```
sudo ifconfig eth1 up
```

This will attempt to get the correct network settings for the adapter
```
sudo dhclient
```

---

### Post by sully101 on 2009-01-18
The output from sudo ifconfig will give you more info. So will sudo lshw and dmesg or dmesg | grep eth

Is eth1 set to auto in the Network manager? or have you configured it to have a static ip

---

### Post by ricardo_78 on 2009-01-18
eth1 is set to auto in the Network Manager

Whizzup: Tried this but to no avail...

But I appear to have renamed eth0 eth1 and vice versa,,,

```

 sudo dmesg | grep eth
[    3.331272] eth0: RealTek RTL8139 at 0xd800, 00:1e:2a:ba:3e:ed, IRQ 17
[    3.331275] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    3.883592] Driver 'sd' needs updating - please use bus_type methods
[    3.883948]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   14.810364] eth1: GMII mode.
[   14.810373] eth1: Enabling Auto-negotiation.
[   16.804757] udev: renamed network interface eth1 to eth0
[   16.816154] udev: renamed network interface eth0_rename to eth1
[   29.300015] eth0: mii ext = 0000.
[   29.340012] eth0: mii lpa = 45e1 adv = 01e1.
[   29.340015] eth0: link on 100 Mbps Full Duplex mode.
[   44.070657] eth1: link down



```

...Although checking back ifconfig -a gives

```

eth0      Link encap:Ethernet  HWaddr 00:1b:b9:b1:db:0d  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:558581 (558.5 KB)  TX bytes:174993 (174.9 KB)
          Interrupt:19 Base address:0xdead 

eth1      Link encap:Ethernet  HWaddr 00:1e:2a:ba:3e:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xd800 


```

---

### Post by ricardo_78 on 2009-01-18
Resorted to installation disk - Rescue option and installed the PCI card NIC

---

