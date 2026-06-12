---
title: "intel 965 chipset video scrambled"
date: 2013-04-14
forum: Multimedia Software
---

### Post by angstrom79 on 2013-04-14
Hi Im new to linux and I'm running a fresh install ubuntu, currently 11.10 (I've tried 12.04 & 12.10 as well with no success and also mint 13 and 14 ) and the video get's scrambled after a while, some times takes 5 minutes others more than 30. This never happens while booting from a live cd. I've searched everywhere for similar issues but so far nothing... I've tried unity, mate, cinnamon and gnome 3 desktops same thing with all...

I'm running an old toshiba l300 , intel 965 chipset with onboard graphics card... 


I' m really trying to move to linux permanently but this is driving me mad... I've tried xorg drivers and intel drivers both with no success.  

What can I do or try more? 

Any help?

---

### Post by mörgæs on 2013-04-15
Hi, welcome to the fora.

Please run **sudo lshw > lshw.txt** and post lshw.txt in CODE tags.

---

### Post by tgalati4 on 2013-04-15
Look in your BIOS and bump up your video RAM from 8MB to 64 or 128MB.  The live CD uses a lower resolution and smaller graphics footprint so it will boot.

Open a terminal (Control-Alt-F1). Look for errors in:

```
less /var/log/Xorg.0.log
```

---

### Post by angstrom79 on 2013-04-16
[SIZE=2][FONT=arial]Thanks [/FONT][/SIZE][COLOR=#000000]for your replies [/COLOR]mörgæs[COLOR=#000000] and tgalati4.

@ [/COLOR][COLOR=#000000]tgalati4 [/COLOR][COLOR=#000000]The bios doesn't have an option to change de gpu memory
[/COLOR][SIZE=4][SIZE=2]Here are the logs requested.[/SIZE][B]

lshw.txt
[/B][/SIZE]
```

hugo
    description: Computer
    version: PSLB0E-07Y01LPT
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal cpus=1 family=Type1Family sku=123456789 uuid=4543F7C0-72CC-11DD-A70E-001E335E8228
  *-core
       description: Motherboard
       product: Base Board Product Name
       vendor: Intel Corp.
       physical id: 0
       version: Base Board Version
       serial: Base Board Serial Number
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: INSYDE
          physical id: 0
          version: 1.50
          date: 07/10/2008
          size: 1MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  T2410  @ 2.00GHz
          vendor: Intel Corp.
          physical id: e
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          slot: CPU
          size: 800MHz
          capacity: 4096MHz
          width: 64 bits
          clock: 533MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=1
        *-cache:0
             description: L2 cache
             physical id: f
             slot: Unknown
             size: 1MiB
             capacity: 1MiB
             capabilities: asynchronous internal write-back unified
        *-cache:1
             description: L1 cache
             physical id: 11
             slot: Unknown
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back data
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
     *-cache
          description: L1 cache
          physical id: 10
          slot: Unknown
          size: 32KiB
          capacity: 32KiB
          capabilities: asynchronous internal write-back instruction
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: M4 70T5663QZ3-CE6
             vendor: Samsung
             physical id: 0
             serial: 0x48B1D892
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 533 MHz (1.9 ns)
             product: M4 70T2953EZ3-CE6
             vendor: Samsung
             physical id: 1
             serial: 0x550C532B
             slot: DIMM2
             size: 1GiB
             width: 64 bits
             clock: 533MHz (1.9ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:45 memory:d3100000-d31fffff memory:c0000000-cfffffff ioport:6110(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:d3200000-d32fffff
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:60c0(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:60a0(size=32)
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:18 memory:d6404c00-d6404fff
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
             configuration: driver=HDA Intel latency=0
             resources: irq:47 memory:d6400000-d6403fff
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
             configuration: driver=pcieport
             resources: irq:40 ioport:4000(size=8192) memory:d5400000-d63fffff ioport:d0000000(size=17825792)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:1e:33:5e:82:28
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:43 ioport:4000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff
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
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:d4300000-d53fffff ioport:d1100000(size=16777216)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 02
                serial: 00:1f:3c:9f:04:5b
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic firmware=15.32.2.9 ip=192.168.1.68 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
                resources: irq:46 memory:d4300000-d4300fff
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:2000(size=4096) memory:d3300000-d42fffff ioport:d2100000(size=16777216)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:6080(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:6060(size=32)
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
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:6040(size=32)
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
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:d6404800-d6404bff
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
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:60e0(size=16)
           *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-L632H
                vendor: TSSTcorp
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/Disc
                version: AC01
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/Disc
                   configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list emulated
             configuration: driver=ahci latency=0
             resources: irq:44 ioport:60f8(size=8) ioport:611c(size=4) ioport:60f0(size=8) ioport:6118(size=4) ioport:6020(size=32) memory:d6404000-d64047ff
           *-disk
                description: ATA Disk
                product: WDC WD2500BEVS-2
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXE508E03489
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=af7e29e2
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: b0156b17-61b2-c74b-b7e8-4c99e691f6f5
                   size: 1498MiB
                   capacity: 1500MiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-03-30 21:56:03 filesystem=ntfs label=WinRE state=clean
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@2:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: fce0c077-9372-9845-a135-793341db8b71
                   size: 108GiB
                   capacity: 108GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2012-03-30 21:56:05 filesystem=ntfs label=Vista modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:2
                   description: Windows NTFS volume
                   physical id: 3
                   bus info: scsi@2:0.0.0,3
                   logical name: /dev/sda3
                   version: 3.1
                   serial: 5a723677-c478-1247-ba5a-97406c9bbd31
                   size: 115GiB
                   capacity: 115GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2012-03-30 21:56:11 filesystem=ntfs label=Data state=clean
              *-volume:3
                   description: Extended partition
                   physical id: 4
                   bus info: scsi@2:0.0.0,4
                   logical name: /dev/sda4
                   size: 8090MiB
                   capacity: 8090MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 2000MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      capacity: 6089MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,user_xattr,acl,barrier=1,data=ordered state=mounted
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:d6405000-d64050ff ioport:6000(size=32)





```
[B]
[SIZE=4]Xorg.0.log[/SIZE][/B]

```

[    18.168] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    18.168] X Protocol Version 11, Revision 0
[    18.168] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    18.168] Current Operating System: Linux hugo 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[    18.168] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=9fe58a9d-059c-4e49-96a3-24046900ad8c ro crashkernel=384M-2G:64M,2G-:128M quiet splash vt.handoff=7
[    18.168] Build Date: 29 September 2011  12:48:48AM
[    18.168] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    18.168] Current version of pixman: 0.22.2
[    18.168]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    18.168] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    18.168] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 16 14:44:59 2013
[    18.196] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    18.196] (==) No Layout section.  Using the first Screen section.
[    18.196] (==) No screen section available. Using defaults.
[    18.196] (**) |-->Screen "Default Screen Section" (0)
[    18.196] (**) |   |-->Monitor "<default monitor>"
[    18.196] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    18.196] (==) Automatically adding devices
[    18.196] (==) Automatically enabling devices
[    18.197] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    18.197]     Entry deleted from font path.
[    18.197] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    18.197]     Entry deleted from font path.
[    18.197] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    18.197]     Entry deleted from font path.
[    18.197] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    18.197]     Entry deleted from font path.
[    18.197] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    18.197]     Entry deleted from font path.
[    18.197] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    18.197] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    18.197] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    18.197] (II) Loader magic: 0x823ada0
[    18.197] (II) Module ABI versions:
[    18.197]     X.Org ANSI C Emulation: 0.4
[    18.197]     X.Org Video Driver: 10.0
[    18.197]     X.Org XInput driver : 12.3
[    18.197]     X.Org Server Extension : 5.0
[    18.198] (--) PCI:*(0:0:2:0) 8086:2a02:1179:ff64 rev 3, Mem @ 0xd3100000/1048576, 0xc0000000/268435456, I/O @ 0x00006110/8
[    18.198] (--) PCI: (0:0:2:1) 8086:2a03:1179:ff64 rev 3, Mem @ 0xd3200000/1048576
[    18.198] (II) Open ACPI successful (/var/run/acpid.socket)
[    18.198] (II) LoadModule: "extmod"
[    18.217] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    18.217] (II) Module extmod: vendor="X.Org Foundation"
[    18.217]     compiled for 1.10.4, module version = 1.0.0
[    18.217]     Module class: X.Org Server Extension
[    18.217]     ABI class: X.Org Server Extension, version 5.0
[    18.217] (II) Loading extension MIT-SCREEN-SAVER
[    18.217] (II) Loading extension XFree86-VidModeExtension
[    18.217] (II) Loading extension XFree86-DGA
[    18.218] (II) Loading extension DPMS
[    18.218] (II) Loading extension XVideo
[    18.218] (II) Loading extension XVideo-MotionCompensation
[    18.218] (II) Loading extension X-Resource
[    18.218] (II) LoadModule: "dbe"
[    18.218] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    18.218] (II) Module dbe: vendor="X.Org Foundation"
[    18.218]     compiled for 1.10.4, module version = 1.0.0
[    18.218]     Module class: X.Org Server Extension
[    18.218]     ABI class: X.Org Server Extension, version 5.0
[    18.218] (II) Loading extension DOUBLE-BUFFER
[    18.218] (II) LoadModule: "glx"
[    18.219] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    18.219] (II) Module glx: vendor="X.Org Foundation"
[    18.219]     compiled for 1.10.4, module version = 1.0.0
[    18.219]     ABI class: X.Org Server Extension, version 5.0
[    18.219] (==) AIGLX enabled
[    18.219] (II) Loading extension GLX
[    18.219] (II) LoadModule: "record"
[    18.219] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    18.219] (II) Module record: vendor="X.Org Foundation"
[    18.219]     compiled for 1.10.4, module version = 1.13.0
[    18.219]     Module class: X.Org Server Extension
[    18.219]     ABI class: X.Org Server Extension, version 5.0
[    18.219] (II) Loading extension RECORD
[    18.219] (II) LoadModule: "dri"
[    18.220] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    18.220] (II) Module dri: vendor="X.Org Foundation"
[    18.220]     compiled for 1.10.4, module version = 1.0.0
[    18.220]     ABI class: X.Org Server Extension, version 5.0
[    18.220] (II) Loading extension XFree86-DRI
[    18.220] (II) LoadModule: "dri2"
[    18.220] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.220] (II) Module dri2: vendor="X.Org Foundation"
[    18.220]     compiled for 1.10.4, module version = 1.2.0
[    18.221]     ABI class: X.Org Server Extension, version 5.0
[    18.221] (II) Loading extension DRI2
[    18.221] (==) Matched intel as autoconfigured driver 0
[    18.221] (==) Matched vesa as autoconfigured driver 1
[    18.221] (==) Matched fbdev as autoconfigured driver 2
[    18.221] (==) Assigned the driver to the xf86ConfigLayout
[    18.221] (II) LoadModule: "intel"
[    18.221] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.221] (II) Module intel: vendor="X.Org Foundation"
[    18.221]     compiled for 1.10.4, module version = 2.15.901
[    18.221]     Module class: X.Org Video Driver
[    18.221]     ABI class: X.Org Video Driver, version 10.0
[    18.221] (II) LoadModule: "vesa"
[    18.221] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    18.222] (II) Module vesa: vendor="X.Org Foundation"
[    18.222]     compiled for 1.10.2, module version = 2.3.0
[    18.222]     Module class: X.Org Video Driver
[    18.222]     ABI class: X.Org Video Driver, version 10.0
[    18.222] (II) LoadModule: "fbdev"
[    18.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    18.222] (II) Module fbdev: vendor="X.Org Foundation"
[    18.222]     compiled for 1.10.0, module version = 0.4.2
[    18.222]     ABI class: X.Org Video Driver, version 10.0
[    18.222] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[    18.222] (II) VESA: driver for VESA chipsets: vesa
[    18.222] (II) FBDEV: driver for framebuffer: fbdev
[    18.222] (++) using VT number 7


[    18.225] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    18.225] (WW) Falling back to old probe method for vesa
[    18.225] (WW) Falling back to old probe method for fbdev
[    18.225] (II) Loading sub module "fbdevhw"
[    18.225] (II) LoadModule: "fbdevhw"
[    18.225] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    18.225] (II) Module fbdevhw: vendor="X.Org Foundation"
[    18.225]     compiled for 1.10.4, module version = 0.0.2
[    18.225]     ABI class: X.Org Video Driver, version 10.0
[    18.226] drmOpenDevice: node name is /dev/dri/card0
[    18.226] drmOpenDevice: open result is 12, (OK)
[    18.226] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    18.226] drmOpenDevice: node name is /dev/dri/card0
[    18.226] drmOpenDevice: open result is 12, (OK)
[    18.226] drmOpenByBusid: drmOpenMinor returns 12
[    18.226] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    18.226] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    18.226] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    18.226] (==) intel(0): RGB weight 888
[    18.226] (==) intel(0): Default visual is TrueColor
[    18.226] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[    18.226] (--) intel(0): Chipset: "965GM"
[    18.226] (**) intel(0): Relaxed fencing enabled
[    18.226] (**) intel(0): Wait on SwapBuffers? enabled
[    18.226] (**) intel(0): Triple buffering? enabled
[    18.226] (**) intel(0): Framebuffer tiled
[    18.226] (**) intel(0): Pixmaps tiled
[    18.226] (**) intel(0): 3D buffers tiled
[    18.226] (**) intel(0): SwapBuffers wait enabled
[    18.226] (==) intel(0): video overlay key set to 0x101fe
[    18.226] (II) intel(0): Output LVDS1 has no monitor section
[    18.226] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    18.244] (II) intel(0): Output VGA1 has no monitor section
[    18.557] (II) intel(0): Output TV1 has no monitor section
[    18.557] (II) intel(0): EDID for output LVDS1
[    18.557] (II) intel(0): Manufacturer: AUO  Model: 8174  Serial#: 0
[    18.557] (II) intel(0): Year: 2006  Week: 1
[    18.557] (II) intel(0): EDID Version: 1.3
[    18.557] (II) intel(0): Digital Display Input
[    18.557] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    18.557] (II) intel(0): Gamma: 2.20
[    18.557] (II) intel(0): No DPMS capabilities specified
[    18.557] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    18.557] (II) intel(0): First detailed timing is preferred mode
[    18.557] (II) intel(0): redX: 0.590 redY: 0.345   greenX: 0.315 greenY: 0.555
[    18.557] (II) intel(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    18.557] (II) intel(0): Manufacturer's mask: 0
[    18.557] (II) intel(0): Supported detailed timing:
[    18.557] (II) intel(0): clock: 71.1 MHz   Image Size:  331 x 207 mm
[    18.557] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[    18.557] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[    18.557] (II) intel(0): Unknown vendor-specific block f
[    18.557] (II) intel(0):  AUO
[    18.557] (II) intel(0):  B154EW08 V1
[    18.557] (II) intel(0): EDID (in hex):
[    18.557] (II) intel(0):     00ffffffffffff0006af748100000000
[    18.557] (II) intel(0):     01100103802115780a1cf59758508e27
[    18.558] (II) intel(0):     27505400000001010101010101010101
[    18.558] (II) intel(0):     010101010101c71b00a0502017303020
[    18.558] (II) intel(0):     36004bcf100000180000000f00000000
[    18.558] (II) intel(0):     00000000000000000020000000fe0041
[    18.558] (II) intel(0):     554f0a202020202020202020000000fe
[    18.558] (II) intel(0):     004231353445573038205631200a0043
[    18.558] (II) intel(0): EDID vendor "AUO", prod id 33140
[    18.558] (II) intel(0): Printing DDC gathered Modelines:
[    18.558] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    18.558] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    18.558] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    18.558] (II) intel(0): Printing probed modes for output LVDS1
[    18.558] (II) intel(0): Modeline "1280x800"x60.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    18.558] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.558] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.558] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.558] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.584] (II) intel(0): EDID for output VGA1
[    18.881] (II) intel(0): EDID for output TV1
[    18.881] (II) intel(0): Output LVDS1 connected
[    18.881] (II) intel(0): Output VGA1 disconnected
[    18.881] (II) intel(0): Output TV1 disconnected
[    18.881] (II) intel(0): Using exact sizes for initial modes
[    18.881] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    18.881] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    18.881] (II) intel(0): Kernel page flipping support detected, enabling
[    18.881] (**) intel(0): Display dimensions: (330, 210) mm
[    18.881] (**) intel(0): DPI set to (98, 96)
[    18.881] (II) Loading sub module "fb"
[    18.881] (II) LoadModule: "fb"
[    18.882] (II) Loading /usr/lib/xorg/modules/libfb.so
[    18.882] (II) Module fb: vendor="X.Org Foundation"
[    18.882]     compiled for 1.10.4, module version = 1.0.0
[    18.882]     ABI class: X.Org ANSI C Emulation, version 0.4
[    18.882] (II) Loading sub module "dri2"
[    18.882] (II) LoadModule: "dri2"
[    18.882] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    18.882] (II) Module dri2: vendor="X.Org Foundation"
[    18.882]     compiled for 1.10.4, module version = 1.2.0
[    18.882]     ABI class: X.Org Server Extension, version 5.0
[    18.882] (II) UnloadModule: "vesa"
[    18.882] (II) Unloading vesa
[    18.882] (II) UnloadModule: "fbdev"
[    18.882] (II) Unloading fbdev
[    18.882] (II) UnloadModule: "fbdevhw"
[    18.882] (II) Unloading fbdevhw
[    18.882] (==) Depth 24 pixmap format is 32 bpp
[    18.883] (II) intel(0): [DRI2] Setup complete
[    18.883] (II) intel(0): [DRI2]   DRI driver: i965
[    18.883] (II) intel(0): Allocated new frame buffer 1280x800 stride 5120, tiled
[    18.898] (II) UXA(0): Driver registered support for the following operations:
[    18.898] (II)         solid
[    18.898] (II)         copy
[    18.898] (II)         composite (RENDER acceleration)
[    18.898] (II)         put_image
[    18.898] (II)         get_image
[    18.898] (==) intel(0): Backing store disabled
[    18.898] (==) intel(0): Silken mouse enabled
[    18.898] (II) intel(0): Initializing HW Cursor
[    18.924] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    18.937] (==) intel(0): DPMS enabled
[    18.937] (==) intel(0): Intel XvMC decoder enabled
[    18.937] (II) intel(0): Set up textured video
[    18.937] (II) intel(0): Set up overlay video
[    18.937] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[    18.937] (II) intel(0): direct rendering: DRI2 Enabled
[    18.937] (==) intel(0): hotplug detection: "enabled"
[    18.937] (--) RandR disabled
[    18.937] (II) Initializing built-in extension Generic Event Extension
[    18.937] (II) Initializing built-in extension SHAPE
[    18.937] (II) Initializing built-in extension MIT-SHM
[    18.937] (II) Initializing built-in extension XInputExtension
[    18.937] (II) Initializing built-in extension XTEST
[    18.937] (II) Initializing built-in extension BIG-REQUESTS
[    18.937] (II) Initializing built-in extension SYNC
[    18.937] (II) Initializing built-in extension XKEYBOARD
[    18.937] (II) Initializing built-in extension XC-MISC
[    18.937] (II) Initializing built-in extension SECURITY
[    18.937] (II) Initializing built-in extension XINERAMA
[    18.937] (II) Initializing built-in extension XFIXES
[    18.938] (II) Initializing built-in extension RENDER
[    18.938] (II) Initializing built-in extension RANDR
[    18.938] (II) Initializing built-in extension COMPOSITE
[    18.938] (II) Initializing built-in extension DAMAGE
[    18.938] (II) Initializing built-in extension GESTURE
[    18.950] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[    18.954] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    18.954] (II) AIGLX: enabled GLX_INTEL_swap_event
[    18.954] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    18.954] (II) AIGLX: enabled GLX_SGI_make_current_read
[    18.954] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    18.954] (II) AIGLX: Loaded and initialized i965
[    18.954] (II) GLX: Initialized DRI2 GL provider for screen 0
[    18.955] (II) intel(0): Setting screen physical size to 338 x 211
[    18.974] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.985] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    18.985] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.985] (II) LoadModule: "evdev"
[    18.986] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.987] (II) Module evdev: vendor="X.Org Foundation"
[    18.987]     compiled for 1.10.2, module version = 2.6.0
[    18.987]     Module class: X.Org XInput Driver
[    18.987]     ABI class: X.Org XInput driver, version 12.3
[    18.987] (II) Using input driver 'evdev' for 'Power Button'
[    18.987] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.987] (**) Power Button: always reports core events
[    18.987] (**) Power Button: Device: "/dev/input/event2"
[    18.987] (--) Power Button: Found keys
[    18.987] (II) Power Button: Configuring as keyboard
[    18.987] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    18.987] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.987] (**) Option "xkb_rules" "evdev"
[    18.987] (**) Option "xkb_model" "pc105"
[    18.987] (**) Option "xkb_layout" "pt"
[    18.990] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[    18.991] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    18.991] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.991] (II) Using input driver 'evdev' for 'Video Bus'
[    18.991] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.991] (**) Video Bus: always reports core events
[    18.991] (**) Video Bus: Device: "/dev/input/event5"
[    18.991] (--) Video Bus: Found keys
[    18.991] (II) Video Bus: Configuring as keyboard
[    18.992] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    18.992] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    18.992] (**) Option "xkb_rules" "evdev"
[    18.992] (**) Option "xkb_model" "pc105"
[    18.992] (**) Option "xkb_layout" "pt"
[    18.995] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.995] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.995] (II) Using input driver 'evdev' for 'Power Button'
[    18.995] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.995] (**) Power Button: always reports core events
[    18.995] (**) Power Button: Device: "/dev/input/event0"
[    18.995] (--) Power Button: Found keys
[    18.995] (II) Power Button: Configuring as keyboard
[    18.995] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.995] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.995] (**) Option "xkb_rules" "evdev"
[    18.995] (**) Option "xkb_model" "pc105"
[    18.995] (**) Option "xkb_layout" "pt"
[    18.996] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    18.996] (II) No input driver/identifier specified (ignoring)
[    18.999] (II) config/udev: Adding input device CNF7051 (/dev/input/event4)
[    18.999] (**) CNF7051: Applying InputClass "evdev keyboard catchall"
[    18.999] (II) Using input driver 'evdev' for 'CNF7051'
[    18.999] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.999] (**) CNF7051: always reports core events
[    18.999] (**) CNF7051: Device: "/dev/input/event4"
[    18.999] (--) CNF7051: Found keys
[    18.999] (II) CNF7051: Configuring as keyboard
[    18.999] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input4/event4"
[    18.999] (II) XINPUT: Adding extended input device "CNF7051" (type: KEYBOARD)
[    18.999] (**) Option "xkb_rules" "evdev"
[    18.999] (**) Option "xkb_model" "pc105"
[    18.999] (**) Option "xkb_layout" "pt"
[    19.000] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    19.000] (II) No input driver/identifier specified (ignoring)
[    19.001] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    19.001] (II) No input driver/identifier specified (ignoring)
[    19.008] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    19.008] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    19.008] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    19.008] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    19.008] (**) AT Translated Set 2 keyboard: always reports core events
[    19.008] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    19.008] (--) AT Translated Set 2 keyboard: Found keys
[    19.008] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    19.008] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    19.008] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    19.008] (**) Option "xkb_rules" "evdev"
[    19.008] (**) Option "xkb_model" "pc105"
[    19.008] (**) Option "xkb_layout" "pt"
[    19.009] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    19.009] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    19.009] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    19.009] (II) LoadModule: "synaptics"
[    19.009] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.009] (II) Module synaptics: vendor="X.Org Foundation"
[    19.009]     compiled for 1.10.4, module version = 1.4.1
[    19.009]     Module class: X.Org XInput Driver
[    19.009]     ABI class: X.Org XInput driver, version 12.3
[    19.009] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    19.009] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    19.009] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.009] (**) Option "Device" "/dev/input/event8"
[    19.010] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    19.010] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    19.010] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    19.010] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    19.010] (--) SynPS/2 Synaptics TouchPad: buttons: left right scroll-buttons
[    19.012] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.012] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    19.016] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    19.016] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    19.016] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    19.016] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    19.016] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    19.016] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    19.016] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    19.016] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    19.016] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    19.016] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    19.016] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    19.016] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    19.016] (II) No input driver/identifier specified (ignoring)
[    20.344] (II) intel(0): EDID vendor "AUO", prod id 33140
[    20.344] (II) intel(0): Printing DDC gathered Modelines:
[    20.344] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    21.178] (II) intel(0): EDID vendor "AUO", prod id 33140
[    21.178] (II) intel(0): Printing DDC gathered Modelines:
[    21.178] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    21.911] (II) intel(0): EDID vendor "AUO", prod id 33140
[    21.911] (II) intel(0): Printing DDC gathered Modelines:
[    21.911] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    23.536] (II) intel(0): EDID vendor "AUO", prod id 33140
[    23.536] (II) intel(0): Printing DDC gathered Modelines:
[    23.536] (II) intel(0): Modeline "1280x800"x0.0   71.11  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.4 kHz)
[    26.051] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm





```

---

### Post by tgalati4 on 2013-04-16
I have a similar graphics chip on this Acer laptop:

        *-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:43 memory:fc000000-fc0fffff memory:d0000000-dfffffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fc100000-fc1fffff

And we are both using the i915 (Intel 915 Series) device driver:

lsmod:  video                  19391  2 i915,acer_wmi


I'm running Linux Mint 14 Mate 64-bit (based on 12.10) and it works fine.

Perhaps you have a hardware problem.  Can you boot a live DVD and set the resolution to 1280 x 800?

---

### Post by xinawesome on 2013-04-19
> **angstrom79 said:**
> Hi Im new to linux and I'm running a fresh install ubuntu, currently 11.10 (I've tried 12.04 & 12.10 as well with no success and also mint 13 and 14 ) and the video get's scrambled after a while, some times takes 5 minutes others more than 30. This never happens while booting from a live cd. I've searched everywhere for similar issues but so far nothing... I've tried unity, mate, cinnamon and gnome 3 desktops same thing with all...

I'm running an old toshiba l300 , intel 965 chipset with onboard graphics card... 


I' m really trying to move to linux permanently but this is driving me mad... I've tried xorg drivers and intel drivers both with no success.  

What can I do or try more? 

Any help?

Hi, I've had the same problem on my Toshiba m800 laptop with the same chipset. I've tried a lot of distros like you did without success. However I'm currently using a version of mint with no problem. I think mine is the mint 2013 [COLOR=#555555][FONT=Arial]LMDE. You should check that out. \

[/FONT][/COLOR]

---

### Post by angstrom79 on 2013-07-08
Ok so it was hardware related eventually the laptop failed completely to boot even under windows, I've now replaced it for a new one... 

Thanks for all the help.

---

