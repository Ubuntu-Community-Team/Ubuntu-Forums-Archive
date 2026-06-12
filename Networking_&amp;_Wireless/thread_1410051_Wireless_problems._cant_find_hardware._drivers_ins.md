---
title: "Wireless problems. cant find hardware. drivers installed?"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by omgBUNNY on 2010-02-18
I'm having problems getting the wifi to work on my toshiba satellite pro l40 (psl4be).
My laptop has a wifi card built in but linux cant seem to be able to find it. I tryed following [these]("http://ubuntuforums.org/showthread.php?p=6183681") instructions and i got this output:
```
james@james-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
james@james-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
james@james-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:e8:38:3b  
          inet addr:10.0.0.7  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fee8:383b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:125350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:167533119 (159.7 MB)  TX bytes:6964147 (6.6 MB)
          Interrupt:16 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146717 (143.2 KB)  TX bytes:146717 (143.2 KB)

james@james-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

james@james-laptop:~$ 

```
as you can see its telling me i have no wifi card, even though i am fully aware i do. ive tryed using ndiswrapper to install the windows drivers of the ethernet adaptor but my wifi still doesnt work, im guessing ethernet has nothing to do with wifi.
 I intend to convert from windows, however if i cant get the wifi to work i can only see linux at a major disadvantage as i use my wifi alot. any help would be appreciated as i would much prefer to stick with linux if possible.

---

### Post by chili555 on 2010-02-18
Is the wireless switch on the front on or off? Is the wireless LED on, off or flickering? If it was off and is now on, please run:```
lspci -nn
```Please post the results.

---

### Post by omgBUNNY on 2010-02-18
i get this:
```
james@james-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)

```
which im pretty sure is the same. my wifi switch is turned to on.

---

### Post by Vakman on 2010-02-18
So if you know the wireless card name; we can use the Windows file driver so to speak if you are okay with the driver being non-open source.
Install a program called "ndiswrapper". Once that is installed download the driver file for your machine, inf file.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
That link should help. This is a really easy way to install wireless drivers in my opinion.

---

### Post by Julita on 2010-02-18
If ndiswrapper wouldn't work, try this: [http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html) (this is specifically for your card) or (largely the same, but with more useful info) here: [http://ubuntuforums.org/showpost.php?p=4104386&postcount=1](http://ubuntuforums.org/showpost.php?p=4104386&postcount=1)

---

### Post by chili555 on 2010-02-18
> Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Is this, by chance, your wireless device? Having an internal device connected through a USB bus is not unheard of. Does it help to do:```
sudo modprobe rtl8187
```Does a wireless interface now appear in:```
iwconfig
```

---

### Post by Julita on 2010-02-18
> **chili555 said:**
> Is this, by chance, your wireless device? Having an internal device connected through a USB bus is not unheard of. Does it help to do:```
sudo modprobe rtl8187
```Does a wireless interface now appear in:```
iwconfig
```

No, Realtek is for wired internet, the wireless is atheros 5007EG.

---

### Post by chili555 on 2010-02-18
> 05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [[COLOR="Blue"]10ec:8139[/COLOR]] (rev 10)This is the wired ethernet, I believe.

---

### Post by Julita on 2010-02-18
> **chili555 said:**
> This is the wired ethernet, I believe.

That's what is said. The OP has problems with wifi (Atheros) because this particular model is currently unsupported in Linux, but with manipulations that I have given links to it is possible to make it work.

---

### Post by chili555 on 2010-02-18
I am sure I am missing something quite obvious, but please help me. Where does the data provided say 'Atheros?' Do you have one of these laptops? Do they all have Atheros wireless cards?

---

### Post by omgBUNNY on 2010-02-18
unfortunately none of these seem to work, [http://www.ubuntugeek.com/atheros-50...-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")
links to a file that no longer exists and i cannot find anywhere else and when using the winxp drivers for the atheros AR5007EG ndiswrapper tells me that my computer doesnt have the hardware. I've spent the past hour trying to find the files that youre telling me i need somewhere else but to no avail. the closest one i can find is "madwifi-nr-r3366+ar5007.tar.gz" but that doesnt seem to work.

---

### Post by Julita on 2010-02-18
> **chili555 said:**
> I am sure I am missing something quite obvious, but please help me. Where does the data provided say 'Atheros?' Do you have one of these laptops? Do they all have Atheros wireless cards?

I know that this particular laptop uses this particular card. For any further inquiries, please see [http://staff.stir.ac.uk/p.g.ward/toshiba_satellite_pro_l40.html](http://staff.stir.ac.uk/p.g.ward/toshiba_satellite_pro_l40.html)

---

### Post by Julita on 2010-02-18
> **omgBUNNY said:**
> unfortunately none of these seem to work, [http://www.ubuntugeek.com/atheros-50...-platform.html]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")
links to a file that no longer exists and i cannot find anywhere else and when using the winxp drivers for the atheros AR5007EG ndiswrapper tells me that my computer doesnt have the hardware. I've spent the past hour trying to find the files that youre telling me i need somewhere else but to no avail. the closest one i can find is "madwifi-nr-r3366+ar5007.tar.gz" but that doesnt seem to work.

Please post the lshw output!

---

### Post by chili555 on 2010-02-18
> I know that this particular laptop uses this particular card.OK. I will be most interested in your progress.

---

### Post by Julita on 2010-02-18
> **chili555 said:**
> OK. I will be most interested in your progress.

And here I though you'd be most interested in the solution of the problem and be the active participant, not the watcher :D

---

### Post by omgBUNNY on 2010-02-18
lshw output:
```
james@james-laptop:~$ sudo lshw
james-laptop              
    description: Notebook
    product: Satellite Pro L40
    vendor: TOSHIBA
    version: PSL4BE-00S005EN
    serial: 28093899R
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=notebook cpus=2 uuid=D23281DC-E225-A38F-0A00-001E8CE8383B
  *-core
       description: Motherboard
       product: Satellite Pro L40
       vendor: TOSHIBA
       physical id: 0
       version: 1.0
       serial: BSN12345678901234567
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: V1.80 (12/28/2007)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2330  @ 1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: Socket 478
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-back instruction
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1a
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: SODIMM Synchronous
             product: N/A
             vendor: Manufacturer0
             physical id: 0
             serial: AssetTagNum0
             slot: SODIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: SODIMM [empty]
             product: N/A
             vendor: Manufacturer1
             physical id: 1
             serial: AssetTagNum1
             slot: SODIMM1
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1600MHz
          capacity: 1600MHz
          capabilities: ht cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:05:07.0
                logical name: eth0
                version: 10
                serial: 00:1e:8c:e8:38:3b
                size: 100MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.7 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RW  DVR-K17A
                vendor: PIONEER
                physical id: 0.0.0
                bus info: scsi@3:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 3.52
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0 module=ahci
           *-disk
                description: ATA Disk
                product: FUJITSU MHY2080B
                vendor: Fujitsu
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 0040
                serial: K425T8227S9Y
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=8e9eecb1
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: afea20fb-721d-480e-af3a-6038b3e9cb74
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2010-02-18 17:38:57 filesystem=ext3 modified=2010-02-18 18:28:26 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2010-02-18 17:56:30 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 2933MiB
                   capacity: 2933MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2933MiB
                      capabilities: nofs

```

---

### Post by Julita on 2010-02-18
OK, I see... Try please this post: [http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html](http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html) there were positive responses from those who have the same hardware as you.

---

### Post by omgBUNNY on 2010-02-18
this is my output:
```
james@james-laptop:~$ cd /home/james/Drivers
james@james-laptop:~/Drivers$ tar xzvf rtl8187b-modified-dist.tar.gz
rtl8187b-modified/
rtl8187b-modified/makedrv
rtl8187b-modified/ReadMe.txt
rtl8187b-modified/install
rtl8187b-modified/rtl8187/
rtl8187b-modified/rtl8187/r8180_rtl8225z2.c
rtl8187b-modified/rtl8187/install
rtl8187b-modified/rtl8187/copying
rtl8187b-modified/rtl8187/Modules.symvers
rtl8187b-modified/rtl8187/r8187.o
rtl8187b-modified/rtl8187/ieee80211.h
rtl8187b-modified/rtl8187/r8180_93cx6.h
rtl8187b-modified/rtl8187/.tmp_versions/
rtl8187b-modified/rtl8187/.tmp_versions/r8187.mod
rtl8187b-modified/rtl8187/ieee80211_crypt.h
rtl8187b-modified/rtl8187/.r8180_rtl8225z2.o.cmd
rtl8187b-modified/rtl8187/r8180_rtl8225.o
rtl8187b-modified/rtl8187/r8187.mod.c
rtl8187b-modified/rtl8187/r8180_rtl8225.c
rtl8187b-modified/rtl8187/.r8187.mod.o.cmd
rtl8187b-modified/rtl8187/tags
rtl8187b-modified/rtl8187/license
rtl8187b-modified/rtl8187/r8187.h
rtl8187b-modified/rtl8187/r8180_wx.o
rtl8187b-modified/rtl8187/r8180_93cx6.o
rtl8187b-modified/rtl8187/r8180_hw.h
rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
rtl8187b-modified/rtl8187/r8180_wx.c
rtl8187b-modified/rtl8187/readme
rtl8187b-modified/rtl8187/r8180_93cx6.c
rtl8187b-modified/rtl8187/r8180_pm.c
rtl8187b-modified/rtl8187/r8180_wx.h
rtl8187b-modified/rtl8187/r8187_core.o
rtl8187b-modified/rtl8187/r8187.mod.o
rtl8187b-modified/rtl8187/authors
rtl8187b-modified/rtl8187/r8187_core.c
rtl8187b-modified/rtl8187/Module.symvers
rtl8187b-modified/rtl8187/.r8187.ko.cmd
rtl8187b-modified/rtl8187/r8187.ko
rtl8187b-modified/rtl8187/.r8180_rtl8225.o.cmd
rtl8187b-modified/rtl8187/r8180_pm.h
rtl8187b-modified/rtl8187/.r8187_core.o.cmd
rtl8187b-modified/rtl8187/.r8180_93cx6.o.cmd
rtl8187b-modified/rtl8187/r8180_rtl8225.h
rtl8187b-modified/rtl8187/.r8180_wx.o.cmd
rtl8187b-modified/rtl8187/.r8187.o.cmd
rtl8187b-modified/rtl8187/changes
rtl8187b-modified/rtl8187/Makefile
rtl8187b-modified/wlan0up
rtl8187b-modified/wlan0rmv
rtl8187b-modified/wlan0down
rtl8187b-modified/wpa_supplicant-0.5.3/
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sim.c
rtl8187b-modified/wpa_supplicant-0.5.3/common.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/networkconfig.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpamsg.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpa_gui.pro
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/networkconfig.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpagui.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/userdatarequest.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/main.cpp
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/userdatarequest.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/scanresults.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/wpagui.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/eventhistory.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/scanresults.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui/eventhistory.ui
rtl8187b-modified/wpa_supplicant-0.5.3/eloop_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/md5.h
rtl8187b-modified/wpa_supplicant-0.5.3/base64.h
rtl8187b-modified/wpa_supplicant-0.5.3/pmksa_cache.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tlv.c
rtl8187b-modified/wpa_supplicant-0.5.3/version.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_wext.h
rtl8187b-modified/wpa_supplicant-0.5.3/main_winsvc.c
rtl8187b-modified/wpa_supplicant-0.5.3/aes_wrap.c
rtl8187b-modified/wpa_supplicant-0.5.3/pcsc_funcs.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_dbus.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_dbus.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sake_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_vendor_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/eloop_win.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_udp.c
rtl8187b-modified/wpa_supplicant-0.5.3/main_winmain.c
rtl8187b-modified/wpa_supplicant-0.5.3/eloop.c
rtl8187b-modified/wpa_supplicant-0.5.3/pmksa_cache.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver.h
rtl8187b-modified/wpa_supplicant-0.5.3/copying
rtl8187b-modified/wpa_supplicant-0.5.3/wpa.c
rtl8187b-modified/wpa_supplicant-0.5.3/wireless_copy.h
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet.h
rtl8187b-modified/wpa_supplicant-0.5.3/.config
rtl8187b-modified/wpa_supplicant-0.5.3/driver_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_hostap.h
rtl8187b-modified/wpa_supplicant-0.5.3/priv_netlink.h
rtl8187b-modified/wpa_supplicant-0.5.3/crypto.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant.h
rtl8187b-modified/wpa_supplicant-0.5.3/config_types.h
rtl8187b-modified/wpa_supplicant-0.5.3/os_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls.h
rtl8187b-modified/wpa_supplicant-0.5.3/base64.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_pax_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/openssl-tls-extensions.patch
rtl8187b-modified/wpa_supplicant-0.5.3/eapol_sm.h
rtl8187b-modified/wpa_supplicant-0.5.3/common.c
rtl8187b-modified/wpa_supplicant-0.5.3/nmake.mak
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_linux.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tlv.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_pax.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_passphrase.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_gtc.c
rtl8187b-modified/wpa_supplicant-0.5.3/sha1.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sim_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_ttls.h
rtl8187b-modified/wpa_supplicant-0.5.3/config_file.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_ctrl.h
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_freebsd.c
rtl8187b-modified/wpa_supplicant-0.5.3/ndis_events.c
rtl8187b-modified/wpa_supplicant-0.5.3/md5.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sim_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sake_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/preauth.h
rtl8187b-modified/wpa_supplicant-0.5.3/radius.c
rtl8187b-modified/wpa_supplicant-0.5.3/eloop.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap.c
rtl8187b-modified/wpa_supplicant-0.5.3/build_config.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_prism54.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa.h
rtl8187b-modified/wpa_supplicant-0.5.3/rc4.h
rtl8187b-modified/wpa_supplicant-0.5.3/os_win32.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant.conf
rtl8187b-modified/wpa_supplicant-0.5.3/radius_client.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndiswrapper.c
rtl8187b-modified/wpa_supplicant-0.5.3/rc4.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_sake.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_methods.h
rtl8187b-modified/wpa_supplicant-0.5.3/drivers.c
rtl8187b-modified/wpa_supplicant-0.5.3/config_winreg.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tls.c
rtl8187b-modified/wpa_supplicant-0.5.3/todo.txt
rtl8187b-modified/wpa_supplicant-0.5.3/radius_client.c
rtl8187b-modified/wpa_supplicant-0.5.3/preauth.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_wext.c
rtl8187b-modified/wpa_supplicant-0.5.3/tags
rtl8187b-modified/wpa_supplicant-0.5.3/doc/
rtl8187b-modified/wpa_supplicant-0.5.3/doc/doxygen.fast
rtl8187b-modified/wpa_supplicant-0.5.3/doc/ctrl_iface.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/mainpage.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/driver_wrapper.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/testing_tools.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/eap.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/code_structure.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/doxygen.full
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_passphrase.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_passphrase.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_background.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.conf.5
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.conf.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_background.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_cli.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_cli.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.sgml
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/wpa_supplicant.8
rtl8187b-modified/wpa_supplicant-0.5.3/doc/docbook/Makefile
rtl8187b-modified/wpa_supplicant-0.5.3/doc/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/doc/porting.doxygen
rtl8187b-modified/wpa_supplicant-0.5.3/doc/wpa_supplicant.fig
rtl8187b-modified/wpa_supplicant-0.5.3/doc/kerneldoc2doxygen.pl
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndis_.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/eapol_sm.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_pax_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/ms_funcs.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_psk_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_leap.c
rtl8187b-modified/wpa_supplicant-0.5.3/ChangeLog
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface_unix.c
rtl8187b-modified/wpa_supplicant-0.5.3/aes.c
rtl8187b-modified/wpa_supplicant-0.5.3/sha1.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_md5.c
rtl8187b-modified/wpa_supplicant-0.5.3/config.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_peap.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ipw.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_atmel.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_mschapv2.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_psk.c
rtl8187b-modified/wpa_supplicant-0.5.3/radius.h
rtl8187b-modified/wpa_supplicant-0.5.3/defs.h
rtl8187b-modified/wpa_supplicant-0.5.3/defconfig
rtl8187b-modified/wpa_supplicant-0.5.3/eapol_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndis.c
rtl8187b-modified/wpa_supplicant-0.5.3/ctrl_iface.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_cli.c
rtl8187b-modified/wpa_supplicant-0.5.3/crypto_gnutls.c
rtl8187b-modified/wpa_supplicant-0.5.3/pcsc_funcs.h
rtl8187b-modified/wpa_supplicant-0.5.3/readme
rtl8187b-modified/wpa_supplicant-0.5.3/eap_methods.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls_openssl.c
rtl8187b-modified/wpa_supplicant-0.5.3/win_example.reg
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tls_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_testing.txt
rtl8187b-modified/wpa_supplicant-0.5.3/hostapd.h
rtl8187b-modified/wpa_supplicant-0.5.3/crypto.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_i.h
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_pcap.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_ndis.h
rtl8187b-modified/wpa_supplicant-0.5.3/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/eap_ttls.c
rtl8187b-modified/wpa_supplicant-0.5.3/crypto_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/README-Windows.txt
rtl8187b-modified/wpa_supplicant-0.5.3/events.c
rtl8187b-modified/wpa_supplicant-0.5.3/l2_packet_winpcap.c
rtl8187b-modified/wpa_supplicant-0.5.3/os_unix.c
rtl8187b-modified/wpa_supplicant-0.5.3/win_if_list.c
rtl8187b-modified/wpa_supplicant-0.5.3/ndis_events.cpp
rtl8187b-modified/wpa_supplicant-0.5.3/aes_wrap.h
rtl8187b-modified/wpa_supplicant-0.5.3/config_ssid.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/networkconfig.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpamsg.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpa_gui.pro
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/networkconfig.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpagui.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/userdatarequest.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/main.cpp
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/userdatarequest.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/scanresults.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/.cvsignore
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/setup-mingw-cross-compiling
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/wpagui.ui
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/eventhistory.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/scanresults.ui.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_gui-qt4/eventhistory.ui
rtl8187b-modified/wpa_supplicant-0.5.3/eap_otp.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_wired.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_aka.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_madwifi.c
rtl8187b-modified/wpa_supplicant-0.5.3/state_machine.h
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_ctrl.c
rtl8187b-modified/wpa_supplicant-0.5.3/config.c
rtl8187b-modified/wpa_supplicant-0.5.3/tls_schannel.c
rtl8187b-modified/wpa_supplicant-0.5.3/driver_hostap.c
rtl8187b-modified/wpa_supplicant-0.5.3/includes.h
rtl8187b-modified/wpa_supplicant-0.5.3/tls_gnutls.c
rtl8187b-modified/wpa_supplicant-0.5.3/preauth_test.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_tls_common.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_broadcom.c
rtl8187b-modified/wpa_supplicant-0.5.3/wpa_supplicant_i.h
rtl8187b-modified/wpa_supplicant-0.5.3/driver_bsd.c
rtl8187b-modified/wpa_supplicant-0.5.3/main.c
rtl8187b-modified/wpa_supplicant-0.5.3/ms_funcs.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_i.h
rtl8187b-modified/wpa_supplicant-0.5.3/eap_psk_common.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_defs.h
rtl8187b-modified/wpa_supplicant-0.5.3/examples/
rtl8187b-modified/wpa_supplicant-0.5.3/examples/plaintext.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/ieee8021x.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/wpa2-eap-ccmp.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/wpa-psk-tkip.conf
rtl8187b-modified/wpa_supplicant-0.5.3/examples/wep.conf
rtl8187b-modified/wpa_supplicant-0.5.3/config_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/Makefile
rtl8187b-modified/wpa_supplicant-0.5.3/os.h
rtl8187b-modified/wpa_supplicant-0.5.3/main_none.c
rtl8187b-modified/wpa_supplicant-0.5.3/eap_fast.c
rtl8187b-modified/ifcfg-wlan0
rtl8187b-modified/README.FIRST
rtl8187b-modified/ieee80211/
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
rtl8187b-modified/ieee80211/.ieee80211_rx.o.cmd
rtl8187b-modified/ieee80211/internal.h
rtl8187b-modified/ieee80211/ieee80211_crypt_wep.c
rtl8187b-modified/ieee80211/autoload.c
rtl8187b-modified/ieee80211/rtl_crypto.h
rtl8187b-modified/ieee80211/.ieee80211_crypt-rtl.ko.cmd
rtl8187b-modified/ieee80211/digest.c
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
rtl8187b-modified/ieee80211/ieee80211_module.o
rtl8187b-modified/ieee80211/ieee80211_crypt.c
rtl8187b-modified/ieee80211/Modules.symvers
rtl8187b-modified/ieee80211/michael_mic.c
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
rtl8187b-modified/ieee80211/ieee80211-rtl.mod.c
rtl8187b-modified/ieee80211/proc.c
rtl8187b-modified/ieee80211/ieee80211_rx.o
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
rtl8187b-modified/ieee80211/ieee80211.h
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip-rtl.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp-rtl.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.c
rtl8187b-modified/ieee80211/ieee80211_softmac.o
rtl8187b-modified/ieee80211/ieee80211_wx.o
rtl8187b-modified/ieee80211/.tmp_versions/
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt_ccmp-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt_wep-rtl.mod
rtl8187b-modified/ieee80211/.tmp_versions/ieee80211_crypt_tkip-rtl.mod
rtl8187b-modified/ieee80211/ieee80211_crypt.h
rtl8187b-modified/ieee80211/.ieee80211_tx.o.cmd
rtl8187b-modified/ieee80211/ieee80211_tx.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep-rtl.ko.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/scatterwalk.h
rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
rtl8187b-modified/ieee80211/kmap_types.h
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
rtl8187b-modified/ieee80211/arc4.c
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c
rtl8187b-modified/ieee80211/cipher.c
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.c
rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip-rtl.ko.cmd
rtl8187b-modified/ieee80211/.ieee80211_module.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
rtl8187b-modified/ieee80211/.ieee80211_softmac_wx.o.cmd
rtl8187b-modified/ieee80211/tags
rtl8187b-modified/ieee80211/license
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
rtl8187b-modified/ieee80211/aes.c
rtl8187b-modified/ieee80211/ieee80211_rx.c
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.c
rtl8187b-modified/ieee80211/ieee80211_wx.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_wep-rtl.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt-rtl.o.cmd
rtl8187b-modified/ieee80211/.ieee80211_crypt.o.cmd
rtl8187b-modified/ieee80211/.ieee80211-rtl.ko.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
rtl8187b-modified/ieee80211/ieee80211-rtl.ko
rtl8187b-modified/ieee80211/.ieee80211_softmac.o.cmd
rtl8187b-modified/ieee80211/readme
rtl8187b-modified/ieee80211/ieee80211_module.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt.o
rtl8187b-modified/ieee80211/ieee80211_softmac.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp.o.cmd
rtl8187b-modified/ieee80211/api.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_ccmp-rtl.ko.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
rtl8187b-modified/ieee80211/scatterwalk.c
rtl8187b-modified/ieee80211/Module.symvers
rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
rtl8187b-modified/ieee80211/ieee80211_softmac_wx.c
rtl8187b-modified/ieee80211/ieee80211-rtl.o
rtl8187b-modified/ieee80211/.ieee80211_wx.o.cmd
rtl8187b-modified/ieee80211/.ieee80211-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/.ieee80211-rtl.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
rtl8187b-modified/ieee80211/compress.c
rtl8187b-modified/ieee80211/.ieee80211_crypt-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/ieee80211_tx.o
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.c
rtl8187b-modified/ieee80211/.ieee80211_crypt_tkip-rtl.mod.o.cmd
rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
rtl8187b-modified/ieee80211/Makefile
rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
rtl8187b-modified/wlan0dhcp
rtl8187b-modified/release_note
james@james-laptop:~/Drivers$ sudo ./makedrv
sudo: ./makedrv: command not found
james@james-laptop:~/Drivers$ cd /home/james/Drivers/rtl8187b-modified
james@james-laptop:~/Drivers/rtl8187b-modified$ sudo ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/james/Drivers/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/james/Drivers/rtl8187b-modified/ieee80211/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/james/Drivers/rtl8187b-modified/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/james/Drivers/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/james/Drivers/rtl8187b-modified/rtl8187/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[1]: *** [_module_/home/james/Drivers/rtl8187b-modified/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
james@james-laptop:~/Drivers/rtl8187b-modified$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
james@james-laptop:~/Drivers/rtl8187b-modified$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

james@james-laptop:~/Drivers/rtl8187b-modified$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

james@james-laptop:~/Drivers/rtl8187b-modified$ 

```
as you can see, it doesnt want to work for me -.- any advice?

---

### Post by Julita on 2010-02-18
Please install linux-restricted-modules package from synaptic that corresponds to your kernel. Please reboot and post the outcome of the command
iwconfig

---

### Post by omgBUNNY on 2010-02-18
i got some newer version of the drivers from [here]("http://www.datanorth.net/%7Ecuervo/blog/rtl8187b-drivers-and-patches/") that seem to of installed and work. my output this time was:
```
james@james-laptop:~/Drivers/rtl8187b-modified$ sudo ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/james/Drivers/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.o
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:433: warning: initialisation from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:432: warning: unused variable ‘dwork’
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_probe_resp’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:710: warning: ISO C90 forbids mixed declarations and code
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_retry_wq’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2253: warning: initialisation from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2252: warning: unused variable ‘dwork’
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2475: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2476: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2477: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2478: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2479: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2480: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_rx_frame_softmac’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1666: warning: ‘chlen’ may be used uninitialised in this function
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1554:4: warning: #warning CHECK_LOCK_HERE
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1594:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_rx.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_tx.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_wx.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_module.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:87: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:109: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:125: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:141: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:423: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211-rtl.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211-rtl.ko
  CC      /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/james/Drivers/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.o
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:934: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_manage_urbsubmit’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:954: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_rtx_disable’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:1255: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2220: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2227: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2277: warning: ISO C90 forbids mixed declarations and code
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2281: warning: ISO C90 forbids mixed declarations and code
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2310: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2256: warning: unused variable ‘i’
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_deleteendpoints’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2328: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: At top level:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: ‘struct struct_work’ declared inside parameter list
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: its scope is only this definition or declaration, which is probably not what you want
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_wmm_param_update’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2437: warning: initialisation from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2439: warning: initialisation from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2654: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:2702: warning: assignment from incompatible pointer type
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_adapter_start’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:3054: warning: unused variable ‘bInvalidWirelessMode’
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:3053: warning: unused variable ‘SupportedWirelessMode’
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:3052: warning: unused variable ‘InitWirelessMode’
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:3051: warning: unused variable ‘ieee’
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/james/Drivers/rtl8187b-modified/rtl8187/r8187_core.c:3769: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/james/Drivers/rtl8187b-modified/rtl8187/r8180_93cx6.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/rtl8187/r8180_wx.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/rtl8187/r8180_rtl8225.o
  CC [M]  /home/james/Drivers/rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/rtl8187/r8187.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_wx_get_freq" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko] undefined!
  CC      /home/james/Drivers/rtl8187b-modified/rtl8187/r8187.mod.o
  LD [M]  /home/james/Drivers/rtl8187b-modified/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
james@james-laptop:~/Drivers/rtl8187b-modified$ sudo ./wlan0up
james@james-laptop:~/Drivers/rtl8187b-modified$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=2  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

james@james-laptop:~/Drivers/rtl8187b-modified$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:B0:DC:33:10
                    ESSID:"happy22"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:15  Signal level:0  Noise level:72
                    Extra: Last beacon: 457ms ago

james@james-laptop:~/Drivers/rtl8187b-modified$ 

```
which seems to of worked, however, i cannot find the wireless manager, i must of accidentally deleted it from the top panel, any ideas on how to get it back so i can test if this is working?

---

### Post by Julita on 2010-02-18
The wireless manager is also that of ethernet - Network Manager (icon with computers) You have to click on it. If it is missing, type in terminal 
sudo nm-applet
it will appear.

---

### Post by omgBUNNY on 2010-02-18
ok, ive managed to connect to my network now (well ubuntu is telling me i have) but i cant actually connect to the internet.. -.-

---

### Post by Julita on 2010-02-18
For wlan0 to work, try disabling eth0 by System->Administration->Networking, properties for eth0, uncheck the box and reboot. (You can check this box when this connection is needed; you will just need to reboot)

---

### Post by omgBUNNY on 2010-02-18
i dont see this "networking" in administration, i've just realized im running an old version of ubuntu (8.04) however, when i decide to download the updates the ethernet stops working (i had to reinstall when this happened), i'll try updating again and see if wifi works then.

---

### Post by Julita on 2010-02-18
Please install linux-restricted-modules package! It might be that your card is supported via this package and reboot! I had no idea you had 8.04; however, since it is LTS, there should be included the newest updates.

---

