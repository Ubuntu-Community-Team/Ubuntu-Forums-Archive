---
title: "The Sharper Image USB Microscope"
date: 2013-09-24
forum: Multimedia Software
---

### Post by cameron5 on 2013-09-24
So I have a USB Microscope that I got for like 50 Cents at a garage sale steal. It works just fine under Windows, however it does not appear to be working under Ubuntu. With the 20+ pages of how-to's that I have discovered (most of them dating until late 2009 when the driver was supposed to be added to the kernel) I have yet to get this device to work. Here is some information, please let me know of what else you would like:

uname -r
```
3.2.0-53-generic
```

lsusb | grep -n Micro
```
5:Bus 001 Device 002: ID 0c45:6270 Microdia PC Camera (SN9C201 + MI0360/MT9V011 or MI0360SOC/MT9V111) U-CAM PC Camera NE878, Whitcom WHC017, ...
```

dmesg | grep -i usb
```
[14817.774902] usb 1-1: USB disconnect, device number 2
[14833.144049] usb 1-1: new high-speed USB device number 4 using ehci_hcd
[14833.343126] input: sn9c20x as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/input/input7
```

modprobe -l | grep -n sn9
```
1738:kernel/drivers/media/video/sn9c102/sn9c102.ko
1760:kernel/drivers/media/video/gspca/gspca_sn9c2028.ko
1761:kernel/drivers/media/video/gspca/gspca_sn9c20x.ko
```

lsmod
```
Module                  Size  Used by
nls_utf8               12493  0 
isofs                  39553  0 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
lib80211_crypt_ccmp    12789  2 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158447  10 bnep,rfcomm
binfmt_misc            17292  1 
ext2                   67987  1 
dm_crypt               22528  1 
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
ipw2200               146210  0 
snd_seq_midi           13132  0 
gspca_sn9c20x          35334  1 
snd_rawmidi            25424  1 snd_seq_midi
libipw                 46732  1 ipw2200
gspca_main             27654  2 gspca_sn9c20x
videodev               86588  2 gspca_main
pcmcia                 39826  0 
joydev                 17393  0 
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 ipw2200,libipw
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211               14040  3 lib80211_crypt_ccmp,ipw2200,libipw
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
psmouse                96744  0 
serio_raw              13027  0 
ppdev                  12849  0 
shpchp                 32265  0 
parport_pc             32114  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
i915                  428021  2 
firewire_ohci          40180  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e100                   36289  0 
drm_kms_helper         45466  1 i915
drm                   197641  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
usb_storage            39646  1
```

lshw
```
cameron-laptop
    description: Portable Computer
    version: 3400365
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=portable uuid=8005073D-D31D-B211-8000-8CD7C2DB02B8
  *-core
       description: Motherboard
       product: M275
       vendor: Gateway
       physical id: 0
       version: Rev 1.0
       serial: 0035510827
     *-firmware
          description: BIOS
          vendor: Gateway
          physical id: 0
          version: 48.04.01
          date: 08/03/2005
          size: 110KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1.50GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.6
          slot: uFCPGA2
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: f
          slot: System board or motherboard
          size: 1280MiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM 1
             size: 1GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:11 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:11 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:10 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:10 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=8192) memory:e0200000-e06fffff memory:54000000-5bffffff
           *-network:0
                description: Wireless interface
                product: PRO/Wireless 2200BG [Calexico2] Network Connection
                vendor: Intel Corporation
                physical id: 4
                bus info: pci@0000:02:04.0
                logical name: eth1
                version: 05
                serial: 00:12:f0:6c:33:51
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.114 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
                resources: irq:10 memory:e0600000-e0600fff
           *-pcmcia:0
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 5
                bus info: pci@0000:02:05.0
                version: ac
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00603020-b0060301f irq:10 memory:5c000000-5c000fff ioport:3c00(size=256) ioport:3800(size=256) memory:58000000-5bffffff memory:68000000-6bffffff
           *-pcmcia:1
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 5.1
                bus info: pci@0000:02:05.1
                version: ac
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b00a07020-b00a0701f irq:10 memory:60000000-60000fff ioport:3400(size=256) ioport:3000(size=256) memory:54000000-57ffffff memory:64000000-67ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C552 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 5.2
                bus info: pci@0000:02:05.2
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
                resources: irq:11 memory:e0604000-e06047ff
           *-network:1
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 83
                serial: 00:e0:b8:6d:79:b6
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:11 memory:e0603000-e0603fff ioport:4000(size=64)
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0
             resources: irq:10 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:50000000-500003ff
           *-disk
                description: ATA Disk
                product: HTS548060M9AT00
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MGBO
                serial: MRLB95L4JV411C
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000003c4
              *-volume:0
                   description: Linux filesystem partition
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /boot
                   version: 1.0
                   serial: 33c1ba2d-af0c-4beb-ae49-0b9ac62c5ec4
                   size: 243MiB
                   capacity: 243MiB
                   capabilities: primary bootable ext2 initialized
                   configuration: filesystem=ext2 modified=2013-09-24 01:45:07 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux LVM Physical Volume partition
                      physical id: 5
                      logical name: /dev/sda5
                      serial: OY6kVU-R7R2-nJHS-PxBk-uHzm-cP1i-tAwyNX
                      size: 55GiB
                      capacity: 55GiB
                      capabilities: multi lvm2
           *-cdrom
                description: DVD reader
                product: UJDA755 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/sr0
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:10 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 14GiB (16GB)
             capabilities: partitioned partitioned:dos
             configuration: signature=0ccea99c
           *-volume
                description: Windows FAT volume
                vendor: SYSLINUX
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/PENDRIVE
                version: FAT32
                serial: 1dde-1433
                size: 14GiB
                capacity: 14GiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
```

I have tried cheese, camorama, guvcview, kamerka, mplayer (yes), and even resorted to trying it with wine. I've tried running all of those as a regular user then as root, then with LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so PROGRAMHERE
The latest posting (2011) I could find was: [http://www.benchadwick.com/2011/04/microdia-usb-0c45627b-in-ubuntu-11-04-natty-narwhal/](http://www.benchadwick.com/2011/04/microdia-usb-0c45627b-in-ubuntu-11-04-natty-narwhal/) however it does not work as the source fails consistently with or without edits.

---

