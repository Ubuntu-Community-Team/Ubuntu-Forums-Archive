---
title: "Wireless problem Broadcom BCM4318 on Ubuntu 9.10"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by Ellinor on 2009-12-02
Hi everybody,

Thanks for accepting me into your lovely community. I recently installed Ubuntu 9.10 on my PC and cannot connect to my wireless network. 
I gave it a few tries, first using ndiswrapper, then b43-fwcutter, but to no avail. 

Below please find my details, as well as the output I get from various Terminal commands (I apologize in advance if some of the things I'm posting here are superfluous- they sound like Greek to me, but could be helpful to someone who is an expert?), including lsmod, ndiswrapper -l, blacklist, uname, iwconfig, ifconfig, lshw, lspci, etc. If I understand correctly, it recognizes my card and the drivers I have installed, but still says network is DISABLED. I've tried activating the driver from the 'Hardware Drivers' option, but a message pops up saying 'you are offline- disconnected'. No wireless networks that I can detect from clicking onto the network signal on my upper right hand corner.


System: AMD Athlon(tm) 64 X2 Dual Core Processor
OS: DUal Boot Windows Vista32-bit/UBuntu 9.10 (computer came pre-installed with just Vista)
Cannot try with cable as I'm on the third floor...
Cannot ping, says network is unreachable
ISP: BT
Country: UK
Network card: Broadcomm 4318 Air Force One 8211g (see below for more info from Terminal).


lsmod gives me:

Module                  Size  Used by
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
ndiswrapper           185404  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
ppdev                   6688  0 
lp                      8964  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
arc4                    1660  2 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
psmouse                56180  0 
b43                   122136  0 
serio_raw               5280  0 
i2c_nforce2             6784  0 
mac80211              181236  1 b43
snd_rawmidi            22208  1 snd_seq_midi
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
cfg80211               93052  2 b43,mac80211
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
led_class               4096  1 b43
k8temp                  4188  0 
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usbhid                 38208  0 
usb_storage            52544  1 
ssb                    35300  1 b43
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 


ndiswrapper -l gives me:
Module                  Size  Used by
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
ndiswrapper           185404  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
ppdev                   6688  0 
lp                      8964  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
arc4                    1660  2 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
psmouse                56180  0 
b43                   122136  0 
serio_raw               5280  0 
i2c_nforce2             6784  0 
mac80211              181236  1 b43
snd_rawmidi            22208  1 snd_seq_midi
parport_pc             31940  1 
parport                35340  3 ppdev,lp,parport_pc
cfg80211               93052  2 b43,mac80211
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
led_class               4096  1 b43
k8temp                  4188  0 
x_tables               16544  1 ip_tables
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
usbhid                 38208  0 
usb_storage            52544  1 
ssb                    35300  1 b43
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
sky2                   46560  0 
Ellinor:~/Desktop$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl6 : driver installed
    device (14E4:4318) present (alternate driver: ssb)

cat /etc/modprobe.d/blacklist gives me:

blacklist bcm43xx
blacklist bcmwl5


uname -r  gives me:
2.6.31-14-generic

iwconfig gives:
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci gives me:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6100 nForce 405] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)

lsusb gives:
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bc2:3300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lshw gives:

description: Desktop Computer
    product: Aspire T180
    vendor: Acer
    version: R01-B4
    serial: **********************
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=0019210C-DB1F-2007-0521-055816000000
  *-core
       description: Motherboard
       product: EM61SM/EM61PM
       vendor: Acer
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: R01-B4 (04/27/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.11.1
          slot: Socket M2
          size: 1GHz
          capacity: 3GHz
          width: 64 bits
          clock: 201MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: d
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: f
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-cpu:1
          description: CPU
          vendor: AMD
          physical id: 7
          bus info: cpu@1
          version: 15.11.1
          slot: Socket M2
          size: 1GHz
          capacity: 3GHz
          clock: 201MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: e
             slot: Internal Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 10
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back
     *-memory:0
          description: System Memory
          physical id: 22
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: DIMM
             product: None
             vendor: None
             physical id: 0
             serial: None
             slot: A0
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 1
             serial: None
             slot: A1
             width: 64 bits
        *-bank:2
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 2
             serial: None
             slot: A2
             width: 64 bits
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
             width: 64 bits
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:00.0
          version: a1
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP61 LPC Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial
          description: SMBus
          product: MCP61 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:5 ioport:fc00(size=64) ioport:1c00(size=64) ioport:f400(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP61 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:fe02f000-fe02ffff
     *-usb:1
          description: USB Controller
          product: MCP61 USB Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a3
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:fe02e000-fe02e0ff
     *-pci:0
          description: PCI bridge
          product: MCP61 PCI bridge
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
          resources: ioport:c000(size=4096) memory:fd800000-fd8fffff memory:fdf00000-fdffffff(prefetchable)
        *-network
             description: Network controller
             product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
             vendor: Broadcom Corporation
             physical id: 5
             bus info: pci@0000:01:05.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=b43-pci-bridge latency=64
             resources: irq:16 memory:fd8fc000-fd8fdfff
        *-firewire
             description: FireWire (IEEE 1394)
             product: TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
             vendor: Texas Instruments
             physical id: 9
             bus info: pci@0000:01:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2
             resources: irq:19 memory:fd8ff000-fd8ff7ff memory:fd8f8000-fd8fbfff
     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:20 memory:fe028000-fe02bfff
     *-ide:0
          description: IDE interface
          product: MCP61 IDE
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:06.0
          logical name: scsi2
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16)
        *-cdrom
             description: DVD writer
             product: DVD-RW_GSA-H41N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: RA00
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
     *-ide:1
          description: IDE interface
          product: MCP61 SATA Controller
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          logical name: scsi0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm msi ht bus_master cap_list emulated
          configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:dc00(size=16) memory:fe02d000-fe02dfff
        *-disk
             description: ATA Disk
             product: Hitachi HDS72161
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: P22O
             serial: ***********
             size: 153GiB (164GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=da5c6fa5
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: *********
                size: 6996MiB
                capacity: 6997MiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2007-05-18 15:45:36 filesystem=ntfs label=PQSERVICE state=clean
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                version: 3.1
                serial: *************************
                size: 71GiB
                capacity: 71GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2006-12-26 12:21:04 filesystem=ntfs label=ACER state=clean
           *-volume:2
                description: Windows NTFS volume
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                version: 3.1
                serial: ****************************
                size: 49GiB
                capacity: 49GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2007-05-18 15:53:34 filesystem=ntfs label=DATA state=clean
           *-volume:3
                description: Extended partition
                physical id: 4
                bus info: scsi@0:0.0.0,4
                logical name: /dev/sda4
                size: 25GiB
                capacity: 25GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 24GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 1137MiB
                   capabilities: nofs
     *-pci:1
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:24 ioport:b000(size=4096) memory:fde00000-fdefffff ioport:fdd00000(size=1048576)
     *-pci:2
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:25 ioport:a000(size=4096) memory:fdc00000-fdcfffff ioport:fdb00000(size=1048576)
        *-network
             description: Ethernet interface
             product: 88E8056 PCI-E Gigabit Ethernet Controller
             vendor: Marvell Technology Group Ltd.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: eth0
             version: 12
             serial: 00:19:21:0c:db:1f
             capacity: 1GB/s
             width: 64 bits
             clock: 33MHz
             capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
             resources: irq:27 memory:fdcfc000-fdcfffff ioport:ac00(size=256) memory:fdb00000-fdb1ffff(prefetchable)
     *-pci:3
          description: PCI bridge
          product: MCP61 PCI Express bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
          resources: irq:26 ioport:9000(size=4096) memory:fda00000-fdafffff ioport:fd900000(size=1048576)
     *-display UNCLAIMED
          description: VGA compatible controller
          product: C61 [GeForce 6100 nForce 405]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list
          configuration: latency=0
          resources: memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:20000000-2001ffff(prefetchable)
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
     *-scsi:0
          physical id: e
          bus info: usb@1:3
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: Desktop
             vendor: Seagate
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             version: 0130
             serial: *********
             size: 931GiB (1TB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=00ed4eab
           *-volume
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/Expansion Drive
                version: 3.1
                serial: *************************
                size: 931GiB
                capacity: 931GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2009-05-06 06:15:02 filesystem=ntfs label=Expansion Drive mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
     *-scsi:1
          physical id: f
          bus info: usb@2:8
          logical name: scsi5
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@5:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@5:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@5:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@5:0.0.3
             logical name: /dev/sdf
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:86:a6:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

lshw -class network gives:

description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:16 memory:fd8fc000-fd8fdfff
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:19:21:0c:db:1f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fdcfc000-fdcfffff ioport:ac00(size=256) memory:fdb00000-fdb1ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:86:a6:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:19:21:0c:db:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


route -n gives:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


Thank you in advance for reading this! I hope someone can help me! 
xx
-Ellie

---

### Post by Ulysses361 on 2009-12-03
Hi,

Please first connect your network card to the wireless router using an ethernet cable (also known as a LAN cable).

In order to gather essential troubleshooting information about your wireless card, please follow this procedure:

Step 1: Open Terminal from "Applications->Accessories->Terminal"

Step 2: Please copy-paste the following command into the Linux Terminal. The command STARTS with the word sudo and ENDS with the word restart. So please copy-paste the ENTIRE command below from Firefox into a Terminal, press <enter>, then enter password when sudo asks for password, then press enter again.

sudo lshw -C network; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -C usb; uname -a; dmesg | grep ound; dmesg | grep b43; dmesg | grep iwl; iwconfig; sudo /etc/init.d/networking restart

Step 3: Please post results (copy/paste terminal output) on this thread

Step 4: Please also specify the exact model and make of your PC (if known) on this thread

Regards,

Mark

---

### Post by Ellinor on 2009-12-03
Hi Ulysses361,
Thank you for your fast reply!

As my computer is on the third floor of my house, a cable cannot reach all the way there...

Here is what I get from the command you specified:
(note: does this mean it can't find the firmware I would need for this b43 program? It did not ask me to include anything like this on installation)...

*-network               
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:16 memory:fd8fc000-fd8fdfff
  *-network
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 12
       serial: 00:19:21:0c:db:1f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:27 memory:fdcfc000-fdcfffff ioport:ac00(size=256) memory:fdb00000-fdb1ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:17:3f:86:a6:de
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
00:0d.0 VGA compatible controller [0300]: nVidia Corporation C61 [GeForce 6100 nForce 405] [10de:03d1] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
01:09.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
03:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bc2:3300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux Ellinor 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] found SMP MP-table at [c00f3c90] f3c90
[    0.177411] ACPI: No dock devices found.
[    0.290626] pnp: PnP ACPI: found 15 devices
[    0.580070] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.580120] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.580178] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.580237] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.580301] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.580368] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.939525] isapnp: No Plug & Play device found
[    0.956127] hub 1-0:1.0: USB hub found
[    1.014088] hub 2-0:1.0: USB hub found
[    1.015257] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.017190] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 3600+ processors (2 cpu cores) (version 2.20.00)
[    1.017662] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.419990] usb-storage: device found at 2
[    1.464050] ssb: Sonics Silicon Backplane found on PCI device 0000:01:05.0
[    2.862712] usb-storage: device found at 3
[   10.073184] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   10.920571] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.920578] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.277209] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.277215] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[    1.398319] b43-pci-bridge 0000:01:05.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[    1.398328] b43-pci-bridge 0000:01:05.0: setting latency timer to 64
[   10.073184] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   10.637043] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   10.915962] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   10.920571] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   10.920578] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   10.920581] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   11.261369] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   11.266915] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   11.277209] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.277215] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.277219] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 * Reconfiguring network interfaces...

---

### Post by Ulysses361 on 2009-12-03
Hi,

The error "b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found" means that b43-fwcutter is not installed yet on your pc. And that means that the Broadcom firmware for your wireless card is not loaded or installed yet.

Please proceed with the following commands:

sudo aptitude update
sudo aptitude install b43-fwcutter

b43-fwcutter exists in the Ubuntu repositories, but you will need a working wired Internet connection in Ubuntu in order to locate it and install it.

The only way to do that - in your case - is to connect the pc to the wireless router using a LAN cable, instead of using wireless.

Or alternatively, if you want wireless to work out-of-the-box, you should download and install Linux Mint 8 instead, which you can get here:

[http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php)

Regards,

Mark

---

### Post by Ellinor on 2009-12-03
Hi Mark,

Thanks for the valuable information.

Theoretically, I can use my Vista wireless connection to download b43-fwcutter on my usb stick and transfer it to my Ubuntu desktop? Unless I am talking nonsense. If not, would I use the same commands to install it from there? Thank you again, you are wonderfully helpful!

Ellie

---

### Post by Ulysses361 on 2009-12-03
Sorry, but it will not work that way. Best thing to do, is download and install Linux Mint 8 instead. First test wireless during the LiveCD session in Linux Mint 8. If wireless works, then install Linux Mint 8.

---

### Post by lion77 on 2009-12-05
Hi Ulysses361,

I have the same problem, I have the radio turned OFF.. I try turne it ON by acerhk, but don't work..
Help me, please...

I send you my command results:

danilo@danilo-laptop:~$** sudo lshw -C network; sudo iwlist scanning; cat /etc/network/interfaces; cat /etc/lsb-release; lspci -nn; lsusb; sudo lshw -C usb; uname -a; dmesg | grep ound; dmesg | grep b43; dmesg | grep iwl; iwconfig; sudo /etc/init.d/networking restart**

  [COLOR=Navy]*-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:89:e4:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=23.215.38.254 latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:58000000-5801ffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e2000000-e2001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0e:9b:b6:44:52
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

auto lo
iface lo inet loopback

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 760/M760 Host [1039:0760] (rev 03)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SG86C202 [1039:0002]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] [1039:0963] (rev 25)
00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
00:02.6 Modem [0703]: Silicon Integrated Systems [SiS] AC'97 Modem Controller [1039:7013] (rev a0)
00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 91)
00:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter [1039:6330]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux danilo-laptop 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686 GNU/Linux
[    0.000000] found SMP MP-table at [c00f7fd0] f7fd0
[    0.106306] ACPI: No dock devices found.
[    0.120881] pnp: PnP ACPI: found 8 devices
[    1.245803] isapnp: No Plug & Play device found
[    1.260155] hub 1-0:1.0: USB hub found
[    1.316117] hub 2-0:1.0: USB hub found
[    1.372110] hub 3-0:1.0: USB hub found
[    1.376540] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.378627] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 2800+ processors (1 cpu cores) (version 2.20.00)
[    1.379049] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.016121] ssb: Sonics Silicon Backplane found on PCI device 0000:00:0b.0
[    2.044233] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[    2.049760] 0000:00:04.0: Using transceiver found at address 13 as default
[   17.140425] lp: driver loaded but no devices found
[   17.382407] yenta_cardbus 0000:00:06.0: CardBus bridge found [1025:0083]
[   17.600963] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    1.941939] b43-pci-bridge 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.600963] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   42.516044] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   42.523071] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   42.551956] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   42.562988] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   42.894873] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   42.988434] Registered led device: b43-phy0::tx
[   42.988461] Registered led device: b43-phy0::rx
[   42.988489] Registered led device: b43-phy0::radio
[   42.988545] b43-phy0: Radio hardware status changed to DISABLED
[   42.988710] b43-phy0: Radio turned on by software
[   42.988713] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth0=eth0.
[/COLOR]

Thanks for your interest

Danilo

---

### Post by uncaspi on 2009-12-05
Ellinor if you don't see the network icon try to clean up /etc/network/interfaces file and delete all lines except auto lo and iface lo inet loopback

Se if this helps. Make a backup of the file before editing it.

---

### Post by uncaspi on 2009-12-05
I forgot to say you have to reboot.

---

### Post by lion77 on 2009-12-07
RESOLVED. I have an Acer Aspire 3000 with Ubuntu 9.10.
I realized that the button to turn on wi-fi was not pressed. :)

However before you press the button I installed the drivers for the Broadcom 4318 from System -> Hardware Drivers and then I downloaded the form acerhk (serving to enable the LED wi-fi) I installed and compiled (but are not sure this is necessary).
Then press the button for the wireless, everything worked.

Thanks to all.
Danilo

---

### Post by mikey.duhhh on 2009-12-07
Yesterday, I installed 9.10 on an old laptop for a friend and the wireless Broadcom 4306 wasn't working either.  I then did a search for 4306 and turned up a page I haven't been able to find today that pointed me to tar.gz file with two directories inside.  I placed them in /lib/firmaware and rebooted.  Still didn't work, so I ran update after connecting to a cable (147 updates) and rebooted.  It worked on an open network. And it confirmed that it was using b43legacy.  If you can locate that tar.gz and send it to the firmware directory, you be in the same exact spot I'm in.

I don't like that seahorse (authorization and keyring) takes over and insists on a password before I can connect to the wireless network which won't connect.  I wonder if I can just delete seahorse altogether.
 

Now I can't get the sucker to connect to WPA2 in a coffee shop.

I am about to scream with frustration.

---

