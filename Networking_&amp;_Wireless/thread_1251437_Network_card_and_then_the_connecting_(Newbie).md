---
title: "Network card and then the connecting (Newbie)"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by BirgersBurger on 2009-08-27
Hello, just installed Ubuntu on my stationary for the first time.


Internet won't just start tho! 

I filled the information like Gateway, Adress, Netmask and DNS Server.
I did some guides from internet, and I think it didn't find my network card or something like that..

**How do I know what network card I have by the way?**

Like I said I have been trying a few guides, and none of them were working, so I guess this forum is the last hope for my computers network!

Thanks for any help I can get.

[SIZE=5][COLOR=Lime]**PROBLEM SOLVED**[/COLOR][/SIZE]

**Solution:**

Go into the BIOS settings in the Peripheral Devices section and checking
VIA-3043 onchip lan. In this case it was DISABLED, I changed it to _ENABLED_!



Huge thanks to  [SIZE=6]bkratz [/SIZE]for actively helping me under theese hours!
:guitar:

---

### Post by bkratz on 2009-08-27
> **BirgersBurger said:**
> Hello, just installed Ubuntu on my stationary for the first time.


Internet won't just start tho! 

I filled the information like Gateway, Adress, Netmask and DNS Server.
I did some guides from internet, and I think it didn't find my network card or something like that..
**How do I know what network card I have by the way?**
Like I said I have been trying a few guides, and none of them were working, so I guess this forum is the last hope for my computers network!
Thanks for any help I can get.


lspci or lsusb, depending on whether it is pci card or usb dongle.
[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by BirgersBurger on 2009-08-27
when writing

ispci

in terminal, i got the following message:

bash: ispci: command not found

the same for isusb


And by the way, it's a built-in network card.

---

### Post by BirgersBurger on 2009-08-27
Oh, I should add that this is WIRED, not WIRELESS!


Thanks for any help!

---

### Post by bkratz on 2009-08-27
> **BirgersBurger said:**
> when writing

ispci

in terminal, i got the following message:

bash: ispci: command not found

the same for isusb


And by the way, it's a built-in network card.

No, that lspci (l as in long)

---

### Post by BirgersBurger on 2009-08-27
Oh...!

I guess this is the network card? : VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge




Or can it be this ? : VIA Technologies, Inc. VT8237/VX700 PCI Bridge




Assuming this is the network card, what is my next step?

---

### Post by bkratz on 2009-08-27
> **BirgersBurger said:**
> Oh...!

I guess this is the network card? : VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
Or can it be this ? : VIA Technologies, Inc. VT8237/VX700 PCI Bridge
Assuming this is the network card, what is my next step?

Nether is these is related to the network-- I googled each and they are not related.

Just post the output of lspci to this forum and someone here will be able to find it for you.


Please look at this   [http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681) it is very helpful. I probably should have said to do number 6 which is
 $ sudo lshw -C network

---

### Post by BirgersBurger on 2009-08-27
this is the result from sudo lshw -c network


> *-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 9e:55:4f:b7:83:c2
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes 
multicast=yes


And this is the result from lshw

```
WARNING: you should run this program as super-user.
makrill                   
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1508MiB
     *-cpu
          product: AMD Athlon(tm) XP 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.10.0
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AP [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: cap_list
                configuration: latency=32 mingnt=8
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:55:4f:b7:83:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
@Makrill:~$ 

```



What are the next step?

---

### Post by bkratz on 2009-08-27
Sorry, but I still don't see the wireless network controller--I probably had you do the wrong thing.

Can You post the outputs for lsusb and lspci so we can all see them?

I just reread it and it clearly states wired network! Just post lspci.

---

### Post by BirgersBurger on 2009-08-27
> **bkratz said:**
> Sorry, but I still don't see the wireless network controller--I probably had you do the wrong thing.

Can You post the outputs for lsusb and lspci so we can all see them?



I'm _not_ on a Wireless network

---

### Post by BirgersBurger on 2009-08-27
Result:

> @Makrill:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
@Makrill:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
@Makrill:~$ 




Hope this helps

---

### Post by bkratz on 2009-08-27
It was lspci.

Sorry they are right next to each other.  Maybe I should sleep awhile!

---

### Post by BirgersBurger on 2009-08-27
Okay, what can we do with this information? And what exactly is the name of my network card?

---

### Post by bkratz on 2009-08-27
Sorry I know more about wireless!  I am searching in google right now for an education.  I will PM you as soon as I know what I am doing!




Here seems to be a good source of info.

[http://gaarai.com/2009/01/22/how-to-find-hardware-devices-in-ubuntu-with-lshw/](http://gaarai.com/2009/01/22/how-to-find-hardware-devices-in-ubuntu-with-lshw/)


What we wanted was    sudo lshw    which apparently stands for (hardware)!  It is probably a long list but you should be able to decode it!

---

### Post by BirgersBurger on 2009-08-28
Result from sudo lshw and [Edit] two more tests at the bottom.

At the bottom of the first command is the Network-part. If I understand this right, the name my network card is pan0.

What's the next step?

```
@Makrill:~$ sudo lshw
[sudo] password for : 
makrill                   
    description: Desktop Computer
    product: KM400-8235
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: KM400-8235
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (05/21/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm) XP 3000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.10.0
          slot: Socket A
          size: 2171MHz
          capacity: 3GHz
          width: 32 bits
          clock: 167MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1536MiB
          capacity: 3GiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: A0
             size: 1GiB
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: A2
     *-pci
          description: Host bridge
          product: VT8378 [KM400/A] Chipset Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display:0 UNCLAIMED
                description: VGA compatible controller
                product: RV350 AP [Radeon 9600]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list
                configuration: latency=32 mingnt=8
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV350 AP [Radeon 9600] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8235 ISA Bridge
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 11.1
             bus info: pci@0000:00:11.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=32
           *-disk
                description: ATA Disk
                product: Maxtor 6Y080L0
                vendor: Maxtor
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: YAR4
                serial: Y23JRRSE
                size: 76GiB (81GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0ca80ca7
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: f55e251e-90dd-4349-848e-1f9a62e84d6e
                   size: 73GiB
                   capacity: 73GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-08-27 23:14:36 filesystem=ext3 modified=2009-08-28 01:57:04 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-08-28 05:05:31 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 3223MiB
                   capacity: 3223MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 3223MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD_RW ND-3550A
                vendor: _NEC
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.05
                serial: [_NEC    DVD_RW ND-3550A 1.0505093000
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: **********
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
@Makrill:~$ 
```



**ifconfig -a** command

> caroline@Makrill:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1120 (1.1 KB)  TX bytes:1120 (1.1 KB)

pan0      Link encap:Ethernet  HWaddr 0e:3d:cd:de:f2:a7  
          inet6 addr: fe80::c3d:cdff:fede:f2a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:12661 (12.6 KB)

pan0:avahi Link encap:Ethernet  HWaddr 0e:3d:cd:de:f2:a7  
          inet addr:169.254.11.125  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

@Makrill:~$ 
@Makrill:~$ 

**lspci -v** command

> @Makrill:~$ lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
	Subsystem: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: e8000000-e80fffff
	Prefetchable memory behind bridge: c0000000-dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at e000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at e100 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
	Subsystem: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
	Flags: bus master, medium devsel, latency 32, IRQ 10
	I/O ports at e200 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20)
	Subsystem: VIA Technologies, Inc. USB 2.0
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at e8100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
	Subsystem: VIA Technologies, Inc. VT8235 ISA Bridge
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: i2c-viapro, via-ircc

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
	Flags: bus master, medium devsel, latency 32, IRQ 11
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at e300 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
	Subsystem: EPoX Computer Co., Ltd. Device 3005
	Flags: medium devsel, IRQ 10
	I/O ports at e400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
	Subsystem: Connect Components Ltd Device 2002
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at d000 [size=256]
	Memory at e8020000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e8000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
	Subsystem: Connect Components Ltd Device 2003
	Flags: 66MHz, medium devsel
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Memory at e8030000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

@Makrill:~$ 


---

### Post by BirgersBurger on 2009-08-28
When opening Network Tool, i can see two different Network devices.


The first one (that is selected) : Loopback interface (lo) , this device is not valid I think, 


The second one : Unknown Interface (pan0) 

This must be the right one, since my networks card name is pan0.

 It has some strange ip on it tho..

"Protocol IPv6"
"IP Adress fe80::c3d:cdff:fede:f2a7" 
"Netmask 64"
"Scope Link"

However, I can select pan0, but when closing and opening Network Tools again, the (lo) will be selected again. Seems I gotta get rid of the (lo).



Thanks for any help !

---

### Post by bkratz on 2009-08-28
This link is for your motherboard-- [http://hardware4linux.info/system/2686/](http://hardware4linux.info/system/2686/)

This sublink is for you controller--http://hardware4linux.info/component/20455/

Pan0 is one of the names usually taken (at least from what I've seen) for a wireless interface
-- I just don't see anything in the list that gives any indication of the network controller from the links listed ID 1106 VT6102 etc.
Still looking

---

### Post by BirgersBurger on 2009-08-28
Okay, this is not telling me anything due the lack of advanced computer knowledge.

I hope that you find something more about this.


And I wonder if there's any way to deactivate the (lo) device, and let the (pan0) be the only one to choose?

---

### Post by BirgersBurger on 2009-08-28
[SIZE=5][COLOR=Lime]**PROBLEM SOLVED**[/COLOR][/SIZE]

**Solution:**

Go into the BIOS settings in the Peripheral Devices section and checking
VIA-3043 onchip lan. In this case it was DISABLED, I changed it to _ENABLED_!



Huge thanks to  [SIZE=6]bkratz [/SIZE]for actively helping me under theese hours!

:guitar:

---

