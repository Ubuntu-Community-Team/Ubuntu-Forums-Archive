---
title: "lubuntu can't connect to wireless networks"
date: 2013-07-20
forum: Networking &amp; Wireless
---

### Post by JJK96 on 2013-07-20
this morning i tried to setup an ad-hoc network on my lenovo thinkpad r60e laptop. It worked, but after disconnecting and reconnecting to my wifi network called "korpershoek" it says connecting, but after a while it says "you are now disconnected".

I of course checked that the password was correct and the wifi network was on.

I googled for some hours, tried some fixes, none worked.

I tried booting from lubuntu live usb, still same problem (in live cd !!!) very strange.
reinstalled lubuntu (so i'm on clean lubuntu now) still same problem.

here is the output of lspci | grep -i network, lsmod, lshw, ifconfig, iwconfig, iwlist scan. if you need any more info just tell me.



```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

lsmod:

Module                  Size  Used by
nls_iso8859_1          12617  1 
usb_storage            47684  1 
bnep                   17669  2 
rfcomm                 37420  12 
joydev                 17097  0 
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
arc4                   12543  2 
i915                  535507  2 
thinkpad_acpi          69384  0 
iwl3945                63619  0 
iwlegacy               87575  1 iwl3945
mac80211              526519  2 iwl3945,iwlegacy
snd_hda_codec_analog    75266  1 
coretemp               13131  0 
nvram                  13986  1 thinkpad_acpi
snd_hda_intel          38307  1 
pcmcia                 39544  0 
snd_hda_codec         117580  2 snd_hda_intel,snd_hda_codec_analog
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         47545  1 i915
snd_rawmidi            25114  1 snd_seq_midi
snd_hwdep              13272  1 snd_hda_codec
cfg80211              436177  3 iwl3945,iwlegacy,mac80211
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm                   228750  3 i915,drm_kms_helper
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
yenta_socket           27095  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
pcmcia_rsrc            18191  1 yenta_socket
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
psmouse                81038  0 
btusb                  17986  0 
microcode              18286  0 
bluetooth             202069  22 bnep,btusb,rfcomm
snd_timer              24411  2 snd_pcm,snd_seq
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
lpc_ich                16925  0 
serio_raw              13031  0 
i2c_algo_bit           13197  1 i915
snd                    56485  12 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device,snd_hda_codec_analog
soundcore              12600  1 snd
mac_hid                13037  0 
video                  18894  1 i915
lp                     13299  0 
parport                40753  1 lp
tg3                   143666  0 
ptp                    18189  1 tg3
pps_core               13736  1 ptp

lshw:

user-thinkpad4
    description: Notebook
    product: 0657A9G ()
    vendor: LENOVO
    version: ThinkPad R60e
    serial: L3BF507
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: administrator_password=disabled boot=normal chassis=notebook cpus=2 family=ThinkPad R60e frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=E7C4AE80-4819-11CB-A4BB-F928BCEA3C4E
  *-core
       description: Motherboard
       product: 0657A9G
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: 1ZCSX6BJ18W
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7EETB5WW (2.05 )
          date: 10/13/2006
          size: 144KiB
          capacity: 1984KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          slot: None
          size: 1667MHz
          capacity: 1667MHz
          width: 64 bits
          clock: 167MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
          configuration: id=1
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back unified
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
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous
             physical id: 0
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR2 Synchronous [empty]
             physical id: 1
             slot: DIMM 2
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.15.6
          serial: 0000-06F6-0000-0000-0000-0000
          size: 1GHz
          capacity: 1GHz
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
          product: Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub
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
             product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:ee100000-ee17ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:ee200000-ee23ffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:ee180000-ee1fffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:44 memory:ee240000-ee243fff
        *-pci:0
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:c000(size=4096) memory:ee000000-ee0fffff ioport:20000000(size=2097152)
           *-network
                description: Ethernet interface
                product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 21
                serial: 00:16:d3:31:ce:24
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=5751m-v3.56 latency=0 link=no multicast=yes port=twisted pair
                resources: irq:46 memory:ee000000-ee00ffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:2000(size=8192) memory:ec000000-edffffff ioport:e4000000(size=1048576)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 02
                serial: 00:18:de:9e:93:63
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.8.0-19-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
                resources: irq:45 memory:edf00000-edf00fff
        *-pci:2
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=8192) memory:e8000000-e9ffffff ioport:e4100000(size=1048576)
        *-pci:3
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:6000(size=8192) memory:ea000000-ebffffff ioport:e4200000(size=1048576)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1880(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:ee444000-ee4443ff
        *-pci:4
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:8000(size=16384) memory:e4300000-e7ffffff ioport:e0000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 0
                bus info: pci@0000:15:00.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:16 memory:e4300000-e4300fff ioport:8000(size=256) ioport:8400(size=256) memory:e0000000-e3ffffff memory:24000000-27ffffff
        *-isa
             description: ISA bridge
             product: 82801GBM (ICH7-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:18b0(size=16)
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:18e0(size=32)
     *-scsi:0
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: HTS541060G9SA00
             vendor: Hitachi
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: MB3I
             serial: MPBCLGXMG5HEAV
             size: 55GiB (60GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000c6846
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: f76d31a0-2059-4c8f-bbb4-8c79634d5a9b
                size: 55GiB
                capacity: 55GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2013-07-20 12:50:22 filesystem=ext4 lastmountpoint=/target modified=2013-07-20 13:00:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2013-07-20 13:00:16 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 501MiB
                capacity: 501MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 501MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM UJ-850
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: RB01
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
     *-scsi:2
          physical id: 4
          bus info: usb@1:5
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: U3 Titanium
             vendor: SanDisk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             version: 7.01
             serial: u
             size: 3835MiB (4022MB)
             capabilities: removable
             configuration: sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdb
                size: 3835MiB (4022MB)
                capabilities: partitioned partitioned:dos
                configuration: signature=000c4419
              *-volume
                   description: Windows FAT volume
                   vendor: SYSLINUX
                   physical id: 1
                   logical name: /dev/sdb1
                   logical name: /media/user/SliTaz core-4in1
                   logical name: /mnt
                   version: FAT32
                   serial: 0294-c9f6
                   size: 3832MiB
                   capacity: 3834MiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,relatime,uid=1000,gid=1000,fmask=0022,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro state=mounted
        *-cdrom
             description: SCSI CD-ROM
             product: U3 Titanium
             vendor: SanDisk
             physical id: 0.0.1
             bus info: scsi@2:0.0.1
             logical name: /dev/cdrom1
             logical name: /dev/sr1
             version: 7.01
             serial: u
             capabilities: removable audio
             configuration: status=ready
           *-medium
                physical id: 0
                logical name: /dev/cdrom1

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:16:d3:31:ce:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45872 (45.8 KB)  TX bytes:45872 (45.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:9e:93:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig:

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

iwlist scan:
          
wlan0     Scan completed :
          Cell 01 - Address: 00:01:E3:AE:58:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Korpershoek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006c14dc2a48
                    Extra: Last beacon: 3440ms ago
                    IE: Unknown: 000B4B6F7270657273686F656B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD180050F204104A00011010440001021057000100103C000101
          Cell 02 - Address: D2:A0:C1:C1:14:B7
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Korpershoek"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006c1444dd6b
                    Extra: Last beacon: 9912ms ago
                    IE: Unknown: 000B4B6F7270657273686F656B
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
                    IE: Unknown: DD920050F204104A000110104400010210570001001041000100103B0001031047001013D9643297A4452DBB7FEBCA26B97631102100075369656D656E73102300057378373632102400001042001130303A30313A45333A41453A35383A41301054000800060050F2040001101100194769676173657420574C414E2041636365737320506F696E74100800020086103C000101
          Cell 03 - Address: 00:1E:E5:84:EB:BA
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Meuleman"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004ecbfc2db8
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00084D65756C656D616E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080400000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD710050F204104A0001101044000102103B00010310470010001EE584EBB8001EE584EBB80400E8001021000C4C696E6B73797320496E632E102300075752543136304E1024000776312E30322E33104200033030311054000800060050F2040001101100075752543136304E100800020088
                    IE: Unknown: DD090010180201F4010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C331C181AFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406080400000000000000000000000000000000000000
```


hope you can help me.

JJK

---

### Post by wildmanne39 on 2013-07-20
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2013-07-20
If you want to access the internet you need to set it as infrastructure.

---

### Post by jjk2 on 2013-08-01
thank you, 

here is an update to the matter, i fixed this at first by doing this:

add the line below to /etc/modprobe.d/alsa-base.conf

options snd-hda-intel model=thinkpad index=0

and then run:

sudo alsa force-reload

this fixed the sound at first, but after a reboot it was broken again. and the above fix didn't work any more.

any help is appreciated.

---

### Post by jjk2 on 2013-08-04
bump, I really want this fixed, what is a laptop without sound? :(

i can provide any info you need

---

