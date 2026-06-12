---
title: "Belkin adapter sees networks but wont connect"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by ceegee on 2010-09-22
hi guys my internet on my desktop is a mess.

I am using the Belkin wireless g usb adapter f5d7050 v1000 or at least that is what ubuntu says when I lsusb.

```
ceegee@Valar1:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 019: ID 050d:7050 Belkin Components F5D7050 ver 1000 WiFi
Bus 001 Device 016: ID 0718:0648 Imation Corp. 
Bus 001 Device 011: ID 0c0b:0336 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 010: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 001 Device 008: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 007: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ceegee@Valar1:~$ 
```It shows me networks even asks for the wpa when necessary, but wont connect. I have tried multiple networks and checked if they were both broadcasting on G mode. 

The device shows up with lshw command, and it reconizes it as a wireless but I dont see the driver.

```
ceegee@Valar1:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:11:50:46:b8:62
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
ceegee@Valar1:~$ 
```I cant seem to install the xp drivers to see if that is the problem.

ndiswrapper gives me an "error 2" when i get to the "make install" command.

```
ceegee@Valar1:~/Desktop$ cd ndiswrapper-1.8
ceegee@Valar1:~/Desktop/ndiswrapper-1.8$ make uninstall
make: Warning: File `version' has modification time 4.4e+07 s in the future
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
/bin/rm: cannot remove `/sbin/loadndisdriver': Permission denied
make: *** [uninstall] Error 1
ceegee@Valar1:~/Desktop/ndiswrapper-1.8$ su
Password: 
root@Valar1:/home/ceegee/Desktop/ndiswrapper-1.8# make uninstall
make: Warning: File `version' has modification time 4.4e+07 s in the future
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /lib/modules/2.6.32-24-generic/kernel/ubuntu/ndiswrapper
/bin/rm: cannot remove `/lib/modules/2.6.32-24-generic/kernel/ubuntu/ndiswrapper': Is a directory
removing /lib/modules/2.6.32-24-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
make: warning:  Clock skew detected.  Your build may be incomplete.
root@Valar1:/home/ceegee/Desktop/ndiswrapper-1.8# make
make: Warning: File `version' has modification time 4.4e+07 s in the future
make -C driver
make[1]: Entering directory `/home/ceegee/Desktop/ndiswrapper-1.8/driver'
make[1]: Warning: File `/lib/modules/2.6.32-24-generic/build/.config' has modification time 1.9e+08 s in the future
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/ceegee/Desktop/ndiswrapper-1.8/driver \
        DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
make[2]: Warning: File `/usr/src/linux-headers-2.6.32-24-generic/arch/x86/Makefile_32.cpu' has modification time 1.9e+08 s in the future
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ceegee/Desktop/ndiswrapper-1.8/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/ceegee/Desktop/ndiswrapper-1.8/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ceegee/Desktop/ndiswrapper-1.8/driver'
make: *** [all] Error 2
root@Valar1:/home/ceegee/Desktop/ndiswrapper-1.8# make install
make: Warning: File `version' has modification time 4.4e+07 s in the future
make -C driver install
make[1]: Entering directory `/home/ceegee/Desktop/ndiswrapper-1.8/driver'
make[1]: Warning: File `/lib/modules/2.6.32-24-generic/build/.config' has modification time 1.9e+08 s in the future
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/ceegee/Desktop/ndiswrapper-1.8/driver \
        DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
make[2]: Warning: File `/usr/src/linux-headers-2.6.32-24-generic/arch/x86/Makefile_32.cpu' has modification time 1.9e+08 s in the future
scripts/Makefile.build:49: *** CFLAGS was changed in "/home/ceegee/Desktop/ndiswrapper-1.8/driver/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [_module_/home/ceegee/Desktop/ndiswrapper-1.8/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ceegee/Desktop/ndiswrapper-1.8/driver'
make: *** [install] Error 2
root@Valar1:/home/ceegee/Desktop/ndiswrapper-1.8# ndiswrapper -i RT2500~4.inf
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
apt-get install ndiswrapper-common
root@Valar1:/home/ceegee/Desktop/ndiswrapper-1.8# 
```The computer has no other internet access. the router is 3 floors down. I seem to have the same problem if I plug it into my laptop.

I just moved to ubuntu a few weeks ago, Im not a native to any linux distros. or programing languange. 

Any help would be appreciated- I don't want to have to move back to vista cause I cant get internet. 

I have been trying to follow t[his]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") guide.



Here is the entire specs for my comp
```
    vendor: Shuttle Inc
    width: 32 bits
    capabilities: smbios-2.2 dmi-2.2 smp
    configuration: boot=normal chassis=desktop uuid=1297F541-FFFF-FFFF-FFFF-FFFFFFFFFFFF
  *-core
       description: Motherboard
       product: FN41UV10
       vendor: Shuttle Inc
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (08/27/2004)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-cpu
          description: CPU
          product: AMD Athlon(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.6.2
          slot: Socket A
          size: 1050MHz
          capacity: 2GHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow up cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: External Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: synchronous external write-back
     *-memory
          description: System Memory
          physical id: 16
          slot: System board or motherboard
          size: 512MiB
          capacity: 1GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: A0
        *-bank:1
             description: DIMM
             physical id: 1
             slot: A1
             size: 512MiB
     *-pci
          description: Host bridge
          product: nForce2 IGP2
          vendor: nVidia Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-nvidia
          resources: irq:0 memory:e8000000-ebffffff(prefetchable)
        *-memory:0 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 1
             vendor: nVidia Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:1 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 4
             vendor: nVidia Corporation
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:2 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 3
             vendor: nVidia Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:3 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 2
             vendor: nVidia Corporation
             physical id: 0.4
             bus info: pci@0000:00:00.4
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-memory:4 UNCLAIMED
             description: RAM memory
             product: nForce2 Memory Controller 5
             vendor: nVidia Corporation
             physical id: 0.5
             bus info: pci@0000:00:00.5
             version: a2
             width: 32 bits
             clock: 66MHz (15.2ns)
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: MCP2A ISA bridge
             vendor: nVidia Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: isa ht bus_master cap_list
             configuration: latency=0
        *-serial
             description: SMBus
             product: MCP2A SMBus
             vendor: nVidia Corporation
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm cap_list
             configuration: driver=nForce2_smbus latency=0 maxlatency=1 mingnt=3
             resources: irq:10 ioport:e400(size=32)
        *-usb:0
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:20 memory:ee003000-ee003fff
        *-usb:1
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:ee004000-ee004fff
        *-usb:2
             description: USB Controller
             product: MCP2A USB Controller
             vendor: nVidia Corporation
             physical id: 2.2
             bus info: pci@0000:00:02.2
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: debug pm bus_master cap_list
             configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
             resources: irq:21 memory:ee005000-ee0050ff
        *-bridge
             description: Ethernet interface
             product: MCP2A Ethernet Controller
             vendor: nVidia Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: a3
             serial: 00:30:1b:b6:80:8c
             capacity: 100000000
             width: 32 bits
             clock: 66MHz
             capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
             resources: irq:20 memory:ee000000-ee000fff ioport:eb00(size=8)
        *-multimedia
             description: Multimedia audio controller
             product: MCP2S AC'97 Audio Controller
             vendor: nVidia Corporation
             physical id: 6
             bus info: pci@0000:00:06.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2
             resources: irq:21 ioport:e000(size=256) ioport:e100(size=128) memory:ee001000-ee001fff
        *-pci:0
             description: PCI bridge
             product: MCP2A PCI Bridge
             vendor: nVidia Corporation
             physical id: 8
             bus info: pci@0000:00:08.0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:c000(size=4096) memory:ed000000-edffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 46
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=32 maxlatency=32
                resources: irq:16 memory:ed000000-ed0007ff ioport:c000(size=128)
        *-ide:0
             description: IDE interface
             product: MCP2A IDE
             vendor: nVidia Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: scsi2
             logical name: scsi3
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
           *-disk
                description: ATA Disk
                product: WDC WD2500AAJB-0
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sdb
                version: 01.0
                serial: WD-WCAV2D563671
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00076660
              *-volume:0
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sdb1
                   logical name: /
                   version: 1.0
                   serial: 6fb7226d-32ca-479d-9853-1087fee2bee4
                   size: 231GiB
                   capacity: 231GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2004-08-27 04:03:56 filesystem=ext4 lastmountpoint=/&#65533;OW#&#65533;&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1492;\&#65533;&#65533;g &#65533;&#65533;g/&#65533;&#65533;\&#65533;&#65533;!&#65533;&#65533;]M&#65533;&#65533;]M&#1984;&#65533;&#65533;&#65533;\&#1968;\&#1933;j modified=2004-08-26 20:03:46 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered mounted=2004-08-26 20:07:44 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sdb2
                   size: 1455MiB
                   capacity: 1455MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 1455MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD Writer 530r
                vendor: HP
                physical id: 0.1.0
                bus info: scsi@3:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: VPS8
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-ide:1
             description: IDE interface
             product: nForce2 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: b
             bus info: pci@0000:00:0b.0
             logical name: scsi0
             version: a3
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:22 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:e900(size=16) ioport:ea00(size=128)
           *-disk
                description: ATA Disk
                product: WDC WD2500YD-01N
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WMANK1705404
                size: 233GiB (251GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0004da3a
              *-volume:0
                   description: Windows FAT volume
                   vendor: mkdosfs
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 83a4-2353
                   size: 122GiB
                   capacity: 122GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=DarkValar
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 111GiB
                   capacity: 111GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1455MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 108GiB
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1455MiB
                      capabilities: nofs
        *-pci:1
             description: PCI bridge
             product: nForce2 AGP
             vendor: nVidia Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: a2
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: ioport:d000(size=4096) memory:ec000000-ecffffff memory:d8000000-e7ffffff(prefetchable)
           *-display:0
                description: VGA compatible controller
                product: RV280 [Radeon 9200 SE]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: agp agp-3.0 pm bus_master cap_list rom
                configuration: driver=radeon latency=32 mingnt=8
                resources: irq:19 memory:d8000000-dfffffff(prefetchable) ioport:d000(size=256) memory:ec030000-ec03ffff memory:ec000000-ec01ffff(prefetchable)
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV280 [Radeon 9200 SE] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:02:00.1
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8
                resources: memory:e0000000-e7ffffff(prefetchable) memory:ec020000-ec02ffff
     *-scsi:0
          physical id: 1
          bus info: usb@1:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdc
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: signature=182c6fd4
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdc1
                logical name: /media/Kara
                version: 3.1
                serial: a8b85a16-ee08-9340-adc0-61749504264e
                size: 799GiB
                capacity: 800GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-11-25 05:03:48 filesystem=ntfs label=Kara mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@4:0.0.0,2
                logical name: /dev/sdc2
                logical name: /media/Siigrune
                version: 3.1
                serial: 30505e6a-8276-e648-acb4-5135c840c333
                size: 79GiB
                capacity: 80GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-11-25 03:28:49 filesystem=ntfs label=Siigrune mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@4:0.0.0,3
                logical name: /dev/sdc3
                logical name: /media/Svava
                version: 3.1
                serial: 84d64de5-f93d-2a4f-b675-151e3efc2385
                size: 51GiB
                capacity: 51GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2009-11-25 02:21:07 filesystem=ntfs label=Svava mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
     *-scsi:1
          physical id: 2
          bus info: usb@1:7
          logical name: scsi7
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/sdd
             size: 1911MiB (2003MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=c3072e18
           *-volume
                description: Windows FAT volume
                vendor: mkdosfs
                physical id: 1
                bus info: scsi@7:0.0.0,1
                logical name: /dev/sdd1
                logical name: /media/Cassandra
                version: FAT32
                serial: 853d-48c1
                size: 1907MiB
                capacity: 1907MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat label=Cassandra mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush,errors=remount-ro state=mounted
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:11:50:46:b8:62
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
root@Valar1:/home/ceegee# 
root@Valar1:/home/ceegee# 
```

---

### Post by ceegee on 2010-09-22
I just tried to see if ndiswrapper is installed. 

it tells me it is not, but when I run sudo apt-get.. it tells me the lattest ndiswrapper is installed. 

```
ceegee@Valar1:~$ ndiswrapper -l
The program 'ndiswrapper' is currently not installed.  You can install it by typing:
sudo apt-get install ndiswrapper-common
ceegee@Valar1:~$ sudo apt-get install ndiswrapper-common
[sudo] password for ceegee: 
Sorry, try again.
[sudo] password for ceegee: 
Sorry, try again.
[sudo] password for ceegee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ceegee@Valar1:~$ 




```

---

### Post by ceegee on 2010-09-22
I got ndiswrapper installed with this guide

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

But I cant get the sys files or inf files out of the exe.

its the rt2500usb driver for xp. ive tried unshield, cabextract, and the archive manager, all of them say unable to open the file. 

can anyone help? 

i got the file from the ralink website 
[http://driverscollection.com/?H=RT2500USB&By=Ralink](http://driverscollection.com/?H=RT2500USB&By=Ralink)

---

