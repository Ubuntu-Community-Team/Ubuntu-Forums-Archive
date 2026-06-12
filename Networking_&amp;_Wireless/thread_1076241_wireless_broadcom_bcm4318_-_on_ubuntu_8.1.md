---
title: "wireless broadcom bcm4318 - on ubuntu 8.1"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by possumboy on 2009-02-21
Okay I really cant figure this out, im a n00b which doesnt help but i've followed all tutorials. But I'm out of luck.

My brother bought a Dell inspiron 2200 a few years back.
And has just got a new laptop and installed ubuntu on this one.
the laptop came with a broadcom BCM4318 [AirForce One 54g] 802.11 wireless LAN controller.

I have been totally unable to connect to the wireless.
I have installed ndiswrapper, and have installed the drivers.
when i typed ndiswrapper -l into the terminal i recieve:

[I]possumboy@possumboy-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)[/I]

I think this terminal info should be useful.

[I]possumboy@possumboy-laptop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.


possumboy@possumboy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)



possumboy@possumboy-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
usb_storage            81728  1 
libusual               27156  1 usb_storage
ipv6                  263972  10 
af_packet              25728  2 
i915                   38144  2 
drm                    86056  3 i915
rfkill_input           12672  0 
binfmt_misc            16904  1 
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
cpufreq_ondemand       14988  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ndiswrapper           196124  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
dcdbas                 15008  0 
b43                   131356  0 
rfkill                 17176  2 rfkill_input,b43
mac80211              216820  1 b43
evdev                  17696  11 
cfg80211               32392  1 mac80211
led_class              12164  1 b43
input_polldev          11912  1 b43
video                  25104  0 
output                 11008  1 video
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                45200  0 
serio_raw              13444  0 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy          10884  0 
pcspkr                 10624  0 
battery                18436  0 
button                 14224  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
ac                     12292  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
ata_generic            12932  0 
pata_acpi              12160  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
e100                   41356  0 
mii                    13440  1 e100
ssb                    40580  1 b43
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  6 usb_storage,libusual,ndiswrapper,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 



root@possumboy-laptop:/home/possumboy# lshw
possumboy-laptop          
    description: Portable Computer
    product: Inspiron 2200
    vendor: Dell Inc.
    serial: 9C4BX1J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=portable uuid=44454C4C-4300-1034-8042-B9C04F58314A
  *-core
       description: Motherboard
       product: 0U6962
       vendor: Dell Inc.
       physical id: 0
       serial: .9C4BX1J.CN4864358N0168.
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A05 (06/21/2005)
          size: 64KiB
          capacity: 512KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.50GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 6.13.8
          slot: Microprocessor
          size: 1500MHz
          capacity: 1800MHz
          width: 32 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KiB
             capacity: 8KiB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 1MiB
             capacity: 1MiB
             clock: 66MHz (15.0ns)
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MiB
        *-bank:0
             description: Chip DDR Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: System Board Memory
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR Synchronous 333 MHz (3.0 ns)
             vendor: 4000000000000000
             physical id: 1
             serial: 7B16069F
             slot: DIMM_B
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
     *-pci
          description: Host bridge
          product: Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile 915GM/GMS/910GML Express Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: d3
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master cap_list
           *-pcmcia
                description: CardBus bridge
                product: PCI1510 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192 module=yenta_socket
           *-network:0
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64 module=ssb
           *-network:1
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 03
                serial: 00:12:3f:f7:c0:29
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
        *-multimedia
             description: Multimedia audio controller
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1e.2
             bus info: pci@0000:00:1e.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=0 module=snd_intel8x0
        *-communication UNCLAIMED
             description: Modem
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1e.3
             bus info: pci@0000:00:1e.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-isa
             description: ISA bridge
             product: 82801FBM (ICH6M) LPC Interface Bridge
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
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: SAMSUNG MP0603H
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: UD20
                serial: S03ZJ10Y968453
                size: 55GiB (60GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=d0f4738c
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1.0
                   serial: a8d8ba82-4cae-4da4-a9f4-507c923fa13b
                   size: 2651MiB
                   capacity: 2651MiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-25 23:39:14 filesystem=ext3 modified=2009-02-19 22:39:00 mounted=2009-02-19 22:39:00 state=clean
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 53GiB
                   capacity: 53GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 1451MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sda6
                      logical name: /
                      logical name: /dev/.static/dev
                      capacity: 50GiB
                      configuration: mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux swap / Solaris partition
                      physical id: 7
                      logical name: /dev/sda7
                      capacity: 1451MiB
                      capabilities: nofs
           *-cdrom
                description: DVD writer
                product: DVD+-RW AD-5540A
                vendor: Optiarc
                physical id: 0.1.0
                bus info: scsi@0:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 103C
                serial: [Optiarc DVD+-RW AD-5540A103C Mar07,2007
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-serial UNCLAIMED
             description: SMBus
             product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:3
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             size: 983MiB (1030MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=5bfba3b3
           *-volume
                description: Windows FAT volume
                vendor: MSDOS5.0
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/THIS ONE!
                version: FAT16
                serial: 0007-e64c
                size: 982MiB
                capacity: 982MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-battery
       product: DELL4C7SIM
       vendor: SMP
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 45000mWh
       configuration: voltage=9.6V
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:3a:b9:cc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 7a:ba:16:c6:c3:c7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


root@possumboy-laptop:/home/possumboy# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:f7:c0:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15040 (15.0 KB)  TX bytes:15040 (15.0 KB)
possumboy@possumboy-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
[/I]



That last one made it fairly clear that the network is down... but how do i turn it on?!?
sudo ifconfig wlan0 up returns
SIOCSIFFLAGS: No such file or directory

My wireless router is configered for channel 11, and i have changed the channel to 11 with iwconfig wlan0 channel 11

But still hovering over the little picture of two computers returns "No network connection".
clicking it shows "enable networking" and "enable wireless" as selected.
I'm just very stuck =[ any help would be very much appreciated.

---

### Post by kevdog on 2009-02-21
Why dont we take a different approach and try the b43/openfwwf driver instead of ndiswrapper.  Its a newer driver.

Here are the instructions:
[http://linuxfans.betaserver.org/](http://linuxfans.betaserver.org/)

---

### Post by kingocounty on 2009-02-24
This worked for me and I've tried everything else!  Thank you!!!

---

### Post by kevdog on 2009-02-25
Awesome -- glad it worked out for you -- chalk down another happy broadcom opensource user!  Just be careful if you ever upgrade kernels (which happens with automatic updates from time to time), you will need to repeat this process!

---

### Post by kingocounty on 2009-02-25
Thanks for the tip; I've got this page bookmarked!

---

### Post by drjimm on 2009-02-27
> **kevdog said:**
> Why dont we take a different approach and try the b43/openfwwf driver instead of ndiswrapper.  Its a newer driver.

Here are the instructions:
[http://linuxfans.betaserver.org/](http://linuxfans.betaserver.org/)

Kev -
I was SO optimistic, followed your instructions precisely, but in step 1: no flex, step 2: no git, and no other things, just GIGO as far as I am concerned,

I am trying to configure a new Toshiba L305-S5924 notebook to take to a handicapped friend in Long Beach - I'm in Louisiana.  I really wanted to install 8.04.2, but when it loads all I get is garbage on the screen, so gave up and installed 8.1.  It wouldn't connect to my wireless router, but somewhere, someone gave me one line of code that installed a driver that connected immediately.  WELL, I was so determined to make 8.04.2 work that I deleted 8.1 and now I'm trying to make it work again.  Like so many others, I'm really frustrated because I'm running 8.04 on 2 machines, and the discs I've burned from the .iso file work perfectly on my XP notebook and Vista desktop.  The forums have been no help until I stumbled on your instructions.  I've been using computers since 1981 and even done some programming, so I'm comfortable with code, but this is driving me bananas.  Sorry to be so verbose, but perhaps you or someone you know can help - preferably with 8.04.2, but I will settle for 8.1.
Many thanks -
Dr Jim Metcalf
Natchitoches, Louisisna
318-352-2647
[email]drjimm@cp-tel.net[/email]

---

### Post by kingocounty on 2009-03-03
Just to follow up on this, I notice that I'm getting moderate packet loss (average 40%) and slow connections using this driver.  I've ruled out the router and my hardware as the cause (reinstalled Windoze, great connection) so I guess there are still some bugs with the driver.  If anyone has any other suggestions as to what to try, I'm all ears!

---

### Post by kingocounty on 2009-03-04
Just to update this, I thought I'd try installing Kubuntu 64 for kicks as I have an AMD64 processor and my wireless was working great; no packet loss and fast steady connections!  I then just installed the Ubuntu 64 bit OS and am back to crappy speeds and average 40% packet loss.  I don't know what the difference is between the two kernels but maybe this will point someone smarter than me in the right direction!

---

