---
title: "Wired connection not working"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by TheSamurai07 on 2009-06-16
I have Ubuntu 9.04 (fresh install), and I can't get the wired networking to work.

NIC: ADMTek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
The router I have is the BEFW11S4

I'm not sure, I tried manually setting the IP/Gateway etc. And it still wasn't working.

The card was working fine in Windows XP.

---

### Post by Amilo1718 on 2009-06-16
what do you get with?

```
sudo lshw
```

---

### Post by TheSamurai07 on 2009-06-16
Sorry for the late reply; just did another clean-install of Ubuntu 9.04 because I did some stuff. So, now it's completely just fresh.

```

    description: Desktop Computer
    product: VT8363
    vendor: VIA Technologies, Inc.
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: 8363-686A
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Award Software International, Inc.
          physical id: 0
          version: 6.00 PG (02/09/2001)
          size: 128KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.4.2
          slot: Socket A
          size: 1200MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 256KiB
     *-cache
          description: L2 cache
          physical id: b
          slot: External Cache
          size: 256KiB
          capacity: 256KiB
          capabilities: synchronous external write-back
     *-memory
          description: Flash Memory
          physical id: 1f
          slot: System board or motherboard
          size: 256MiB
          capacity: 512MiB
        *-bank:0
             description: DIMM
             physical id: 0
             slot: BANK_0
             size: 256MiB
        *-bank:1
             description: DIMM [empty]
             physical id: 1
             slot: BANK_1
        *-bank:2
             description: DIMM [empty]
             physical id: 2
             slot: BANK_2
        *-bank:3
             description: DIMM [empty]
             physical id: 3
             slot: BANK_3
     *-pci
          description: Host bridge
          product: VT8363/8365 [KT133/KM133]
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-via module=via_agp
        *-pci
             description: PCI bridge
             product: VT8363/8365 [KT133/KM133 AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci pm bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV18 [GeForce4 MX 4000]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: c1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: isa pm bus_master cap_list
             configuration: driver=parport_pc latency=0 module=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_via latency=64
           *-disk
                description: ATA Disk
                product: WDC WD200BB-18DE
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 05.0
                serial: WD-WMAD21906852
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=743f743f
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 6555060c-ec48-4e85-b19d-2c450a5bd0e9
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-06-15 13:41:50 filesystem=ext3 modified=2009-06-15 13:58:53 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-06-15 13:42:10 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 713MiB
                   capacity: 713MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 713MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: DVD-ROM 16X
                vendor: BENQ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TANE
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 16
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@0000:00:07.4
             version: 40
             width: 32 bits
             clock: 33MHz
             capabilities: bridge pm cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@0000:00:07.5
             version: 50
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-network
             description: Ethernet interface
             product: NC100 Network Everywhere Fast Ethernet 10/100
             vendor: ADMtek
             physical id: a
             bus info: pci@0000:00:0a.0
             logical name: eth0
             version: 11
             serial: 00:4c:69:6e:75:79
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=32 maxlatency=128 mingnt=64 module=tulip multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6e:f1:47:bb:59:8e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by TheSamurai07 on 2009-06-16
In System > Aministration > Network Tools for my ethernet device eth0

It shows in devices

IPv6 | fe80::24c:69ff:fe6e:7579 | 64 | | Link
IPv4 | 0.0.0.0 | 0.0.0.0 | | |

---

### Post by Amilo1718 on 2009-06-16
I'd disable ipv6

---

### Post by TheSamurai07 on 2009-06-16
How do you do that with Ubuntu 9.04?

---

### Post by Amilo1718 on 2009-06-16
[here]("http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html")

---

### Post by TheSamurai07 on 2009-06-16
Theres no aliases in Ubuntu 9.04

---

### Post by Amilo1718 on 2009-06-16
[have you searched this forum]("http://ubuntuforums.org/showthread.php?t=1065469") ?

:o

---

### Post by jhannah on 2009-06-17
What do you get when running the below command?

```
sudo ethtool eth0
```

Provided link detected reports yes, I don't think it is a driver issue. If it does report yes, try running tcpdump on the interface in one terminal while manually running dhclient on the interface in another and see if it is actually receiving a DHCP lease or any traffic for that matter.

Start up tcpdump with the below:
```
sudo tcpdump -vvxXns0 -i eth0
```Then, in another terminal, try to get a new DHCP lease:
```
sudo dhclient eth0
```You could also try to manually assign the IP/DNS information again and see if you can reach anything on your network. If not, I would be interested to see what the ARP table and routing table look like. Provided running dhclient manually doesn't get you an IP and DNS info that works, please post the results of the below commands (after manually configuring the IP/DNS info):

```
ifconfig eth0
arp -na
netstat -nr
cat /etc/resolv.conf

```Let me know if any of that helps.

---

