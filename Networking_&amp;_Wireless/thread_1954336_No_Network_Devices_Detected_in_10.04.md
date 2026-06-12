---
title: "No Network Devices Detected in 10.04"
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by Kvothe on 2012-04-07
I just bought an **Acer Aspire 7739Z-4804** and I am installing 10.04 on it. I am not able to connect to either ethernet or wifi with a clean install. There appear to be no internet drivers on it. If anyone could point me to the drivers I need and how to install them, I would greatly appreciate it. The Wifi card listed for my laptop is "**Acer Nplify**". Here is the lshw output if you need it.

```
computer               
    description: Notebook
    product: Aspire 7739Z
    vendor: Acer
    version: V1.04
    serial: LXRL702033150022207200
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: chassis=notebook uuid=004234EA-33CC-5C81-3797-386077EBB74E
  *-core
       description: Motherboard
       product: HMA71_CP
       vendor: Acer
       physical id: 0
       version: Type2 - Board Version
       serial: Type2 - Board Serial Number
       slot: Type2 - Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: V1.04 (10/11/2011)
          size: 1MiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb biosbootspecification
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns) [empty]
             physical id: 0
             serial: 00000000
             slot: DIMM0
             width: 8 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: EBJ41UF8BCS0-DJ-F
             vendor: ELPIDA
             physical id: 1
             serial: 0A133ADB
             slot: DIMM1
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) CPU        P6200  @ 2.13GHz
          vendor: Intel Corp.
          physical id: 1e
          bus info: cpu@0
          version: Intel(R) Pentium(R) CPU        P6200  @ 2.13GHz
          slot: U3E1
          size: 2133MHz
          capacity: 4GHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm popcnt lahf_lm arat cpufreq
        *-cache:0
             description: L3 cache
             physical id: 1f
             slot: L3 Cache
             size: 3MiB
             capacity: 3MiB
             capabilities: synchronous internal write-through unified
        *-cache:1
             description: L2 cache
             physical id: 21
             slot: L2 Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous internal write-through unified
        *-cache:2
             description: L1 cache
             physical id: 22
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: synchronous internal write-through instruction
     *-cache
          description: L1 cache
          physical id: 20
          slot: L1 Cache
          size: 32KiB
          capacity: 32KiB
          capabilities: synchronous internal write-through data
     *-pci:0
          description: Host bridge
          product: Core Processor DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Core Processor Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:28 memory:b0000000-b03fffff memory:a0000000-afffffff(prefetchable) ioport:3050(size=8)
        *-communication UNCLAIMED
             description: Communication controller
             product: 5 Series/3400 Series Chipset HECI Controller
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 06
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:b0604000-b060400f
        *-usb:0
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:16 memory:b060a000-b060a3ff
        *-multimedia
             description: Audio device
             product: 5 Series/3400 Series Chipset High Definition Audio
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:22 memory:b0600000-b0603fff
        *-pci:0
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 ioport:4000(size=4096) memory:b0800000-b09fffff memory:b0a00000-b0bfffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:5000(size=4096) memory:b0500000-b05fffff memory:b0c00000-b0dfffff(prefetchable)
           *-network UNCLAIMED
                description: Network controller
                product: Atheros Communications Inc.
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:b0500000-b057ffff memory:b0c00000-b0c0ffff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: 5 Series/3400 Series Chipset PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:2000(size=4096) memory:b0400000-b04fffff memory:b0e00000-b0ffffff(prefetchable)
           *-network UNCLAIMED
                description: Ethernet controller
                product: AR8152 v2.0 Fast Ethernet
                vendor: Atheros Communications
                physical id: 0
                bus info: pci@0000:03:00.0
                version: c1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list
                configuration: latency=0
                resources: memory:b0400000-b043ffff ioport:2000(size=128)
        *-usb:1
             description: USB Controller
             product: 5 Series/3400 Series Chipset USB2 Enhanced Host Controller
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:b0609000-b06093ff
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a5
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
        *-isa
             description: ISA bridge
             product: Mobile 5 Series Chipset LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-storage
             description: SATA controller
             product: 5 Series/3400 Series Chipset 4 port SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi1
             logical name: scsi4
             version: 05
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:27 ioport:3048(size=8) ioport:305c(size=4) ioport:3040(size=8) ioport:3058(size=4) ioport:3020(size=32) memory:b0608000-b06087ff
           *-disk
                description: ATA Disk
                product: WDC WD5000BPVT-2
                vendor: Western Digital
                physical id: 0
                bus info: scsi@1:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXD1E91PCRE6
                size: 465GiB (500GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=a014e150
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: 6ad7-84d7
                   size: 13GiB
                   capacity: 13GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-12-13 07:50:48 filesystem=ntfs label=PQSERVICE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: a2d8-40dd
                   size: 98MiB
                   capacity: 100MiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-12-13 07:50:51 filesystem=ntfs label=SYSTEM RESERVED state=clean
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 68874b65-92c7-ad4d-aa95-c8df2084d209
                   size: 125GiB
                   capacity: 125GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-12-13 07:50:52 filesystem=ntfs label=Acer modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@1:0.0.0,4
                   logical name: /dev/sda4
                   size: 326GiB
                   capacity: 326GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 954MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 325GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ8B0AW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 5 Series/3400 Series Chipset SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 05
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b0606000-b06060ff ioport:3000(size=32)
        *-generic UNCLAIMED
             description: Signal processing controller
             product: 5 Series/3400 Series Chipset Thermal Subsystem
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 05
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: latency=0
             resources: memory:b0607000-b0607fff
     *-pci:1
          description: Host bridge
          product: Core Processor QuickPath Architecture Generic Non-core Registers
          vendor: Intel Corporation
          physical id: 101
          bus info: pci@0000:3f:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Core Processor QuickPath Architecture System Address Decoder
          vendor: Intel Corporation
          physical id: 102
          bus info: pci@0000:3f:00.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Core Processor QPI Link 0
          vendor: Intel Corporation
          physical id: 103
          bus info: pci@0000:3f:02.0
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Core Processor QPI Physical 0
          vendor: Intel Corporation
          physical id: 104
          bus info: pci@0000:3f:02.1
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 105
          bus info: pci@0000:3f:02.2
          version: 02
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Core Processor Reserved
          vendor: Intel Corporation
          physical id: 106
          bus info: pci@0000:3f:02.3
          version: 02
          width: 32 bits
          clock: 33MHz
     *-scsi
          physical id: 1
          bus info: usb@2:1.1
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdb
```

Thank you ahead of time.

---

### Post by roelforg on 2012-04-07
It does detect the cards.
Post the content of /etc/network/interfaces

You do that while i find and clean my tech support hat...*should be here somewhere*

---

### Post by Kvothe on 2012-04-08
> **roelforg said:**
> It does detect the cards.
Post the content of /etc/network/interfaces

You do that while i find and clean my tech support hat...*should be here somewhere*
Here is what I have:

```
auto lo
iface lo inet loopback
```
Somehow I suspect this is bad.

---

### Post by dylan07 on 2012-04-08
Ubuntu 10.04 is ancient. Try 11.10 as it has more wireless drivers, and  more recent ones. Also, don't follow instructions from old versions of  Ubuntu as they are unlikely to work. Especially 4-year-old instructions.

---

### Post by Kvothe on 2012-04-08
> **dylan07 said:**
> Ubuntu 10.04 is ancient. Try 11.10 as it has more wireless drivers, and  more recent ones. Also, don't follow instructions from old versions of  Ubuntu as they are unlikely to work. Especially 4-year-old instructions.
I would prefer to stick to my more flexible and LTS versions, thank you. I don't like the new interface...

If you can prove that this driver will work on 11.10, then I will consider it, but until then I am not moving. Please offer relevant input next time rather than a one-size-fits-all "upgrade it" response.

---

### Post by dylan07 on 2012-04-08
I am sorry to appear rude, if I did indeed do so.

IMHO there is a bug in package management system.
connman grabbed every time the d-bus management from network-manager, that was the reason for those error messages above.
The only thing you need to do is to remove connman:
     
     ```
sudo aptitude remove connman
```

EDIT: I am quoting this from a SOLVED forum, here, with same issue.
[http://ubuntuforums.org/showthread.php?t=1594566](http://ubuntuforums.org/showthread.php?t=1594566)

---

### Post by roelforg on 2012-04-08
Ah, plain config files, no gui, just the way i like it!

Now i'll have to look up wlan but lan is easy:
add this to /etc/network/interfaces:
```

auto eth0
iface eth0 inet dhcp

```
and reboot

---

### Post by roelforg on 2012-04-08
Ah, found it!
If you use WPA/WPA2: [http://nixcraft.com/ubuntu-debian/13278-etc-network-interfaces-wireless-wifi-example.html](http://nixcraft.com/ubuntu-debian/13278-etc-network-interfaces-wireless-wifi-example.html)
This should cover other cases: [http://linuxconfig.org/etcnetworkinterfacesto-connect-ubuntu-to-a-wireless-network](http://linuxconfig.org/etcnetworkinterfacesto-connect-ubuntu-to-a-wireless-network) (you want the dhcp section)

---

### Post by Kvothe on 2012-04-08
> **dylan07 said:**
> I am sorry to appear rude, if I did indeed do so.

IMHO there is a bug in package management system.
connman grabbed every time the d-bus management from network-manager, that was the reason for those error messages above.
The only thing you need to do is to remove connman:
     
     ```
sudo aptitude remove connman
```

EDIT: I am quoting this from a SOLVED forum, here, with same issue.
[http://ubuntuforums.org/showthread.php?t=1594566](http://ubuntuforums.org/showthread.php?t=1594566)
You don't need to feel bad, I was rude too. I just really dislike not using LTS and the new interface. I would sooner switch to **Debian** or something.

Thanks, I'll try that if **roelforg**'s idea doesn't fix it.

> **roelforg said:**
> Ah, plain config files, no gui, just the way i like it!

Now i'll have to look up wlan but lan is easy:
add this to /etc/network/interfaces:
```

auto eth0
iface eth0 inet dhcp

```
and reboot
> **roelforg said:**
> Ah, found it!
If you use WPA/WPA2: [http://nixcraft.com/ubuntu-debian/13278-etc-network-interfaces-wireless-wifi-example.html](http://nixcraft.com/ubuntu-debian/13278-etc-network-interfaces-wireless-wifi-example.html)
This should cover other cases: [http://linuxconfig.org/etcnetworkinterfacesto-connect-ubuntu-to-a-wireless-network](http://linuxconfig.org/etcnetworkinterfacesto-connect-ubuntu-to-a-wireless-network) (you want the dhcp section)
Okay, that's good, but what about an unpassworded network? What do I change in the second link? And wouldn't I need to manually add in each connection this way?

---

### Post by roelforg on 2012-04-08
> **Kvothe said:**
> You don't need to feel bad, I was rude too. I just really dislike not using LTS and the new interface. I would sooner switch to **Debian** or something.

Thanks, I'll try that if **roelforg**'s idea doesn't fix it.



Okay, that's good, but what about an unpassworded network? What do I change in the second link? And wouldn't I need to manually add in each connection this way?


IIRC you just follow the last one and skip the wireless-key line

SideNotes:
All my networking is done with wires.
I hate Unity yet i use 11.10, how?
i took the server version and configured an gui on top (and omitted config-apps as they clash, i like manually editing config files). As this is hard to get right (took me 1month) i advise you try ubuntu spin-offs like lubuntu kubuntu xubuntu edubuntu etc.

---

### Post by Kvothe on 2012-04-08
Okay, I tried both of those solutions and I got nothing. Connman is not installed, and it still says that there are no such devices for eth0 and wlan0.

---

### Post by Kvothe on 2012-04-08
To expand on that, this is the output I got from restarting the networking daemon:

```
 * Reconfiguring network interfaces...                                          Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]
```
It sounds like I need to bind eth0 and wlan0 to specific devices. Any ideas?

---

### Post by roelforg on 2012-04-08
A google search surned up: [http://askubuntu.com/questions/11015/need-wired-wireless-atheros-driver-for-ar9285-and-ar8152](http://askubuntu.com/questions/11015/need-wired-wireless-atheros-driver-for-ar9285-and-ar8152)
give it a shot, it ain't gonna hurt to have extra drivers

---

### Post by Kvothe on 2012-04-08
I'm pretty sure the thing is that it really isn't detecting the devices. Downloading more drivers isn't going to fix anything if the devices haven't been bound to an interface.

---

### Post by roelforg on 2012-04-08
In your first post, the lshw output clearly shuws 2 nic's
Don't believe me?
Run
```

sudo lshw -C network

```
it'll show 2 seperate nics

---

### Post by Kvothe on 2012-04-08
Oh, you're right. But they are not claimed by interfaces, it's just the hardware. See the UNCLAIMED bit.

```
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0500000-b057ffff memory:b0c00000-b0c0ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:b0400000-b043ffff ioport:2000(size=128)
```
I still need to bind them to eth0 and wlan0. Do you know how to do that?

Okay, I got the ethernet working somehow, but the wifi is still UNCLAIMED. I don't know what to do. Still looking for help, please.

---

### Post by roelforg on 2012-04-08
> **Kvothe said:**
> Oh, you're right. But they are not claimed by interfaces, it's just the hardware. See the UNCLAIMED bit.

```
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0500000-b057ffff memory:b0c00000-b0c0ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:b0400000-b043ffff ioport:2000(size=128)
```
I still need to bind them to eth0 and wlan0. Do you know how to do that?

Okay, I got the ethernet working somehow, but the wifi is still UNCLAIMED. I don't know what to do. Still looking for help, please.

you don't have to, once a matching kmod is found, udev should take care of it
allow me go explain,
a device is unclaimed as long as there isn't a matching kmod (driver) claiming responsibility (saying: "I'll handle this device") over the device.

You probably followed and installed the driver for ethernet,
now you have to find the wlan driver

---

### Post by Kvothe on 2012-04-08
> **roelforg said:**
> you don't have to, once a matching kmod is found, udev should take care of it
allow me go explain,
a device is unclaimed as long as there isn't a matching kmod (driver) claiming responsibility (saying: "I'll handle this device") over the device.

You probably followed and installed the driver for ethernet,
now you have to find the wlan driver
Finding it is proving to be nearly impossible.

If anyone knows which one I need, please tell me.

---

### Post by wildmanne39 on 2012-04-08
Hi, you do not have the driver installed it is not included with 10.04 you can install it if you have a wireless connection that is working.

The driver is in 11.04 and 11.10
Thanks

---

