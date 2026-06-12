---
title: "Marvell Technology Group Ltd. 88w8335 Wifi Card Just Doesnt Work on 9.04 64bit"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by neoideo on 2009-10-02
i've been over 3 hours trying to figure out why after following all the setup guides, my wifi card just cant get the driver properly installed with ndiswrapper.

im in ubuntu 9.04 64 bit.
my lspci output is:
```

neoideo@neoideo-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce 750a LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:11.0 PCI bridge: nVidia Corporation Device 0779 (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
**01:09.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)**
01:0a.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX+] (rev a2)

```the wireless card manufacter is "Tenda" and the model is "TWL521P"

so i downloaded this driver which is supossed to be for my chipset Marvell 88w8335, and comes inside with the 64but version

**[http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+bs.Windows+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=bs.Windows](http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=&term=typ.treiber+bs.Windows+produkt.SK-54C1&produkt=produkt.SK-54C1&typ=typ.treiber&system=bs.Windows)**

and also this one which is 64bit too
**[http://www.versiontracker.com/dyn/moreinfo/win/131948](http://www.versiontracker.com/dyn/moreinfo/win/131948)**

then i did the traditional steps to install the driver with ndiswrapper.
```

[B]sudo ndiswrapper -i mrv8335x64.inf 
sudo ndiswrapper -m[/B]

```when i check the driver i get this output.
```

neoideo@neoideo-desktop:~/Desktop/WinX64$ **ndiswrapper -l**
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
[B]mrv8335x64 : driver installed
    device (11AB:1FAA) present[/B]
neoideo@neoideo-desktop:~/Desktop/WinX64$ 

```then i do
```

neoideo@neoideo-desktop:~/Desktop/WinX64$ **sudo modprobe ndiswrapper **
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
neoideo@neoideo-desktop:~/Desktop/WinX64$ 

```and when i check with ifconfig or iwconfig i get this output
```

neoideo@neoideo-desktop:~/Desktop/WinX64$** ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:01:2e:25:bd:99  
          inet addr:192.168.1.26  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe25:bd99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5628 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6643522 (6.6 MB)  TX bytes:788615 (788.6 KB)
          Interrupt:250 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
 
neoideo@neoideo-desktop:~/Desktop/WinX64$** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.  

```if i run lsmod i get this output.
```

**neoideo@neoideo-desktop:~/Desktop/WinX64$ lsmod | grep ndis***
ndiswrapper           250624  0 

```this is interesting:
```

neoideo@neoideo-desktop:~/Desktop/WinX64$ **sudo lshw -C network**
[B]  *-network UNCLAIMED     
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32[/B]
  *-network
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:01:2e:25:bd:99
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.26 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e6:b8:b1:2d:ca:f7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
neoideo@neoideo-desktop:~/Desktop/WinX64$ 

```i really dont know what is happening.

 i've read this other thread where a guy has the same problem and what i took from there is the 64 bit drivers but it still cannot work

**[http://art.ubuntuforums.org/showthread.php?t=1135812](http://art.ubuntuforums.org/showthread.php?t=1135812)**

 i've followed the troubleshooting guide on the hot topics too, and  not success :(

this is some aditional output from logs
```

neoideo@neoideo-desktop:~/Desktop/WinX64$ **dmesg | grep ndis**
[  957.330242] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[  957.387151] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[  957.387917] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
[  957.388514] ndiswrapper 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[  957.389034] ndiswrapper: using IRQ 17
[  957.402312] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[  957.402316] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[  957.402324] ndiswrapper (mp_halt:262): device ffff8801138e3800 is not initialized - not halting
[  957.402326] ndiswrapper: device eth%d removed
[  957.402338] ndiswrapper 0000:01:09.0: PCI INT A disabled
[  957.402350] ndiswrapper: probe of 0000:01:09.0 failed with error -22
[  957.402391] usbcore: registered new interface driver ndiswrapper

```should i surrender o keep looking?
im interested in previous experiencies of people if they succeed or not.

sorry for large post, 
Cristobal

---

### Post by domlayfield on 2013-02-12
Hi neoideo,

The link you posted for the 64-bit driver is dead.  The skd.de site now forwards to Marvell, and I cannot find the driver on their site.  

Any chance you could upload the driver?  i.e mrv8335x64.inf and .sys

Thanks,
-- Dom

---

### Post by QIII on 2013-02-12
This thread is many years old.  If a thread is more than about a year old, it is not worth reviving.

Thank you for sharing.

Thread closed.

---

