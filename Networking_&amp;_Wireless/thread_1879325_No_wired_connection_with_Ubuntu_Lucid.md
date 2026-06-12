---
title: "No wired connection with Ubuntu Lucid"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by ferruccio.sarra on 2011-11-11
Bag your pardon if I ask community's help on a so discussed problem... but I'm going mad. I don't know why but I can't access internet  through a cabled connection. I also tried to install wicd but no results. I'm wandering  if drivers are correctly installed since no eth0 connection appears on the network manager.
Thank you!
Ferruccio

---

### Post by hgladney on 2011-11-11
I have a new occurrence of what might be the same problem.

Specifically, after long usage of Ubuntu 10, a few days my machine seems to fail to connect to the Internet.  Specific symptom: familiar applications, including Mozilla browser, all report "can't browse the Web" or something equivalent.  And previously working LAN connections do not work.  (BTW, the current posting is made from another machine.)

How do I diagnose the source of the problem?  What remedies might work?

---

### Post by jonobr on 2011-11-11
ferruccio.sarra could you explain your setup some more,

how are you setup? Im guessing dhcp?

Could you post results of 
lshw 
ifconfig 
/etc/network/interfaces
/etc/resolv.conf
and also

dmesg | grep eth

hgladney recommend you get the same info and open a thread yourself as the problem seems different

---

### Post by ferruccio.sarra on 2011-11-15
So long time without replying. I'm so sorry. Jonobr. I'll be able to post everything this evening. Thank you!
Ferro

---

### Post by ferruccio.sarra on 2011-11-20
Here I am.

Yess, I'm in DHCP

ferruccio@ferruccio-laptop:~$ sudo lshw
ferruccio-laptop          
    description: Notebook
    product: 417882G
    vendor: LENOVO
    version: ThinkPad T420
    serial: R8P1AMD
    width: 32 bits
    capabilities: smbios-2.6 dmi-2.6
    configuration: administrator_password=disabled chassis=notebook power-on_password=disabled uuid=0162BBC6-2551-CB11-BF43-D81617A9B7A8
  *-core
       description: Motherboard
       product: 417882G
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZJJS15B1ZX
       slot: Not Available
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.10.7
          serial: 0002-06A7-0000-0000-0000-0000
          slot: CPU
          size: 800MHz
          capacity: 800MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm ida arat tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: id=3
        *-cache:0
             description: L1 cache
             physical id: 2
             slot: L1-Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-through data
        *-cache:1
             description: L2 cache
             physical id: 3
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through data
        *-cache:2
             description: L3 cache
             physical id: 4
             slot: L3-Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-back unified
        *-logicalcpu:0
             description: Logical CPU
             physical id: 3.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 3.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 3.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 3.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 3.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 3.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 3.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 3.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 3.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 3.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 3.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 3.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 3.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 3.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 3.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 3.10
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 5
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: 16JSF51264HZ-1G4D1
             vendor: Micron
             physical id: 0
             serial: E17751C1
             slot: ChannelA-DIMM0
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: ChannelB-DIMM0
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: e
          version: 83ET57WW (1.27 ) (05/17/2011)
          size: 128KiB
          capacity: 8128KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb biosbootspecification
     *-pci
          description: Host bridge
          product: Intel Corporation
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Sandy Bridge PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 09
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:5000(size=4096) memory:f0000000-f10fffff ioport:c0000000(size=301989888)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: nVidia Corporation
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress cap_list
                configuration: latency=0
                resources: memory:f0000000-f0ffffff memory:c0000000-cfffffff(prefetchable) memory:d0000000-d1ffffff(prefetchable) ioport:5000(size=128) memory:f1000000-f107ffff(prefetchable)
        *-display UNCLAIMED
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list
             configuration: latency=0
             resources: memory:f1400000-f17fffff memory:e0000000-efffffff(prefetchable) ioport:6000(size=64)
        *-communication UNCLAIMED
             description: Communication controller
             product: Cougar Point HECI Controller #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f3925000-f392500f
        *-network UNCLAIMED
             description: Ethernet controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:f3900000-f391ffff memory:f392b000-f392bfff ioport:6080(size=32)
        *-usb:0
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #2
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:f392a000-f392a3ff
        *-multimedia
             description: Audio device
             product: Cougar Point High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:f3920000-f3923fff
        *-pci:1
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25
        *-pci:2
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:f3800000-f38fffff
           *-network
                description: Wireless interface
                product: WiFi Link 1000 Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 8c:a9:82:ae:9b:aa
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:30 memory:f3800000-f3801fff
        *-pci:3
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 ioport:4000(size=4096) memory:f3000000-f37fffff ioport:f1800000(size=8388608)
        *-pci:4
             description: PCI bridge
             product: Cougar Point PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: b4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:3000(size=4096) memory:f2800000-f2ffffff ioport:f2000000(size=8388608)
           *-generic UNCLAIMED
                description: System peripheral
                product: Ricoh Co Ltd
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:0d:00.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: msi pm pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f2800000-f28000ff
        *-usb:1
             description: USB Controller
             product: Cougar Point USB Enhanced Host Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:f3929000-f39293ff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: Cougar Point 6 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:29 ioport:60a8(size=8) ioport:60bc(size=4) ioport:60a0(size=8) ioport:60b8(size=4) ioport:6060(size=32) memory:f3928000-f39287ff
           *-disk
                description: ATA Disk
                product: ST9500420AS
                vendor: Seagate
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0003
                serial: 5VJCD5C7
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=531f3d4c
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 3e96-c2af
                   size: 1198MiB
                   capacity: 1200MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-09-10 00:12:39 filesystem=ntfs label=SYSTEM_DRV state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /media/Windows7_OS
                   version: 3.1
                   serial: 2ed69801-8f30-1b44-b35b-d804d3d8ee96
                   size: 278GiB
                   capacity: 278GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-09-10 00:12:53 filesystem=ntfs label=Windows7_OS modified_by_chkdsk=true mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 mounted_on_nt4=true resize_log_file=true state=mounted upgrade_on_mount=true
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: fa102af1-f3d9-054e-8ed3-25aaf339e88f
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-07-08 01:27:54 filesystem=ntfs label=Lenovo_Recovery state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   size: 170GiB
                   capacity: 170GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 163GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 7137MiB
                      capabilities: nofs
           *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GT33N
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: LT20
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: Cougar Point SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f3924000-f39240ff ioport:efa0(size=32)
  *-battery
       product: 42T4911
       vendor: LGC
       physical id: 1
       slot: Rear
       capacity: 47520mWh
       configuration: voltage=10.8V
ferruccio@ferruccio-laptop:~$ 

      UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13920 (13.9 KB)  TX bytes:13920 (13.9 KB)

usb0      Link encap:Ethernet  HWaddr 7e:2e:b3:4c:ae:50  
          inet addr:192.168.42.191  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::7c2e:b3ff:fe4c:ae50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1008695 (1.0 MB)  TX bytes:461002 (461.0 KB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:ae:9b:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

interface content:
auto lo
iface lo inet loopback

resolv.conf content:
# Generated by NetworkManager
nameserver 192.168.42.129

ferruccio@ferruccio-laptop:~$ dmesg | grep eth
[   13.255613] usbcore: registered new interface driver cdc_ether
[   99.326574] rndis_host 2-1.1:6.0: rndis get ethaddr, -71
ferruccio@ferruccio-laptop:~$

---

### Post by jonobr on 2011-11-21
Hello

so you using some kind of USB device

Can you ping the following IP addresses

 ping 192.168.42.191

ping 74.125.224.80

If the above works, can you put that in a browser?

[http://74.125.224.80](http://74.125.224.80)

what happens?

Can you ping 192.168.42.129

---

### Post by ferruccio.sarra on 2011-11-21
Thank you for  your attention jonrob. Actually I'm using a tethering connection through my smartphone at home and it works fine. The issue is that I can't succeed in connecting to the internet through my office ethernet connection. Particularly, when I boot my PC under win OS everything goes right but if a use my Ubuntu OS my cabled eth connection doesn't work.
Maybe I made a mistake. When I launchd lshw,... etc, I wasn't connected by my wired eth cable. Do I have to repeat everything when I'm connected to the LAN by a eth cable?
Thank you,
Ferro

---

### Post by jonobr on 2011-11-21
Hi 


When you get to the office

find out what ip address your getting from your DHCP server.
You can do that by doing
ifconfig

Look for eth0 or eth1 or something like that in the output.

If your not getting that, then let me know, if you are then try the pinging stuff I mentioned earlier.

---

### Post by fdrake on 2011-11-21
your problem is in these lines
```

-network [COLOR="Red"]_**UNCLAIMED**_[/COLOR]
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:f3900000-f391ffff memory:f392b000-f392bfff ioport:6080(size=32)

```
it looks like you do not have a driver installed for you ethernet controller. what kind of computer and model you use . just want to make sure before i point you to download and install the right driver. from the lshw list the description is quite generic.
can you also post your ```
lspci
```

---

### Post by ferruccio.sarra on 2011-11-22
Ok jonobr, as soon as I'll reach my office I'll repeat all wihile connected.

In the meanwhile hgladney I post my lspci. My PC is a Lenovo Thinkpad T420. I bought it for its great compatibility with most of Linux distribution.

Thank you!

ferruccio@ferruccio-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c4f (rev 04)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation Device 1057 (rev a1)
03:00.0 Network controller: Intel Corporation WiFi Link 1000 Series
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
ferruccio@ferruccio-laptop:~$

---

### Post by fdrake on 2011-11-22
can you post the out put of these commands
```

sudo lspci -vvv -s 00:19.0
lsmod
ifconfig -v -a

```

---

### Post by ferruccio.sarra on 2011-11-28
Jonobr still out of office, sorry. I'll make ifconfig while connected as soon as possible

...in the meanwhile...
fdrake here below are the outputs you asked for, I have a Lenovo Thinkpad T420, thank you both!

ferruccio@ferruccio-laptop:~$ sudo lspci -vvv -s 00:19.0
[sudo] password for ferruccio: 
00:19.0 Ethernet controller: Intel Corporation Device 1502 (rev 04)
	Subsystem: Lenovo Device 21ce
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 10
	Region 0: Memory at f3900000 (32-bit, non-prefetchable) [size=128K]
	Region 1: Memory at f392b000 (32-bit, non-prefetchable) [size=4K]
	Region 2: I/O ports at 6080 [size=32]
	Capabilities: [c8] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [e0] PCIe advanced features <?>



ferruccio@ferruccio-laptop:~$ lsmod
Module                  Size  Used by
rndis_wlan             20617  0 
cdc_wdm                 8218  0 
cdc_acm                14754  0 
usbhid                 36110  0 
hid                    67288  1 usbhid
binfmt_misc             6587  1 
joydev                  8740  0 
ppdev                   5259  0 
rndis_host              5756  1 rndis_wlan
cdc_ether               3541  1 rndis_host
snd_hda_intel          22069  2 
snd_hda_codec          74201  1 snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
arc4                    1153  2 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
usbnet                 14943  3 rndis_wlan,rndis_host,cdc_ether
nouveau               467048  0 
ttm                    50103  1 nouveau
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                106911  0 
mii                     4381  1 usbnet
uvcvideo               57374  0 
drm_kms_helper         29329  1 nouveau
iwlcore               106149  1 iwlagn
videodev               34361  1 uvcvideo
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                1999  1 fbcon
mac80211              205402  2 iwlagn,iwlcore
v4l1_compat            13251  2 uvcvideo,videodev
led_class               2864  1 iwlcore
drm                   162377  3 nouveau,ttm,drm_kms_helper
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
video                  17375  0 
snd                    54244  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
cfg80211              126144  4 rndis_wlan,iwlagn,iwlcore,mac80211
tpm_tis                 7488  0 
psmouse                63677  0 
serio_raw               3978  0 
tpm                    13936  1 tpm_tis
tpm_bios                5266  1 tpm
vga16fb                11385  1 
output                  1871  1 video
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  3 

ferruccio@ferruccio-laptop:~$ ifconfig -v -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

usb0      Link encap:Ethernet  HWaddr 96:a0:60:2b:ec:de  
          inet addr:192.168.42.26  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::94a0:60ff:fe2b:ecde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28241 errors:4 dropped:0 overruns:0 frame:4
          TX packets:33379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12637503 (12.6 MB)  TX bytes:6440177 (6.4 MB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:ae:9b:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by praseodym on 2011-11-28
Can you load the module by hand?

```
sudo modprobe -v e1000e
sudo /etc/init.d/networking restart
```
Check:
```
ifconfig -a
dmesg | grep e1000
```
If it works, make it permanent via:
```
echo e1000e | sudo tee -a /etc/modules
```
If it doesnt, try [this]("http://thesorcerer.wordpress.com/2011/07/01/guide-intel-82573l-gigabit-ethernet-with-ubuntu-11-04-and-fix-pxe-e05/")

---

### Post by ferruccio.sarra on 2011-11-30
Ok praseodym. I made everything while not connected by eth cable. Is it normal that no "eth0" connection appear in the ifconfig? 
Thanks.

...laptop:~$ sudo modprobe -v e1000e
[sudo] password for ferruccio: 
insmod /lib/modules/2.6.32-33-generic/kernel/drivers/net/e1000e/e1000e.ko 
ferruccio@ferruccio-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface usb0=usb0.
                                                                         [ OK ]
...laptop:~$ 

...laptop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

usb0      Link encap:Ethernet  HWaddr 96:a0:60:2b:ec:de  
          inet addr:192.168.42.26  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::94a0:60ff:fe2b:ecde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10958 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12011 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7241811 (7.2 MB)  TX bytes:2276785 (2.2 MB)

wlan0     Link encap:Ethernet  HWaddr 8c:a9:82:ae:9b:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

...laptop:~$ 


...laptop:~$ dmesg | grep e1000
[    0.000000] ACPI: UEFI bafe1000 0003E (v01 LENOVO TP-83    00001270 PTL  00000002)
[    0.000000]   #5 [00008e1000 - 00008e40ed]              BRK ==> [00008e1000 - 00008e40ed]
[ 3206.175136] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[ 3206.175144] e1000e: Copyright (c) 1999-2008 Intel Corporation.
...laptop:~$

---

### Post by bluexrider on 2011-11-30
> **jonobr said:**
> ferruccio.sarra could you explain your setup some more,

how are you setup? Im guessing dhcp?

Could you post results of 
lshw 
ifconfig 
/etc/network/interfaces
/etc/resolv.conf
and also

dmesg | grep eth

hgladney recommend you get the same info and open a thread yourself as the problem seems different

It may have been easier to post 

sudo lshw -c network
then to have requested ALL of lshw

Just a suggestion

---

