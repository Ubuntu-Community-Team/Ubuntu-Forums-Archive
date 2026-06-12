---
title: "No sound°!!!"
date: 2009-05-23
forum: Multimedia Software
---

### Post by juapo2 on 2009-05-23
Hi,

I am new to Ubuntu..I took the decision and I erased WinXp and installed Ubuntu 9.04 =D

But i am facing a problem, I couldnt get my mic to work and i followed this guide: [http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html](http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html)
It didn't work, and when i rebooted computer, i didn't have sound!!!!!!!!!!!!!!!!!!!

I was like OMG!!!! Well, I dont know what to do, i restored the esd.conf to default and still nothing, can any of you guys help me please?

Sound card integrated. 

Also tried this
[SIZE=2]aplay -l[/SIZE]
[SIZE=2]
And told me no sound card detected...

Regards,
Richi, PHP Developer
[/SIZE]

---

### Post by khelben1979 on 2009-05-23
Have you checked all your settings with [Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") (see wiki link).

```
sudo apt-get install alsamixergui
```
to install it with root permissions.

Also make sure to keep an eye on mute/unmute to see if it can fix anything.

---

### Post by juapo2 on 2009-05-23
HI,

First, thanks for reply.

It is not muted

I did wht you told me and I opened the gui, but what do i do there? =S

Regards,
Richi, PHP Developer

---

### Post by khelben1979 on 2009-05-23
Move all the bars at the top in AlsamixerGUI to see if it changes anything.

[Alsaconf]("http://man-wiki.net/index.php/8:alsaconf") is a program you can use to change your settings for the soundcard/soundchip. I'm not sure if it comes with Ubuntu, but it is part of [the ALSA project]("http://www.alsa-project.org/main/index.php/Main_Page").

One other thing: if you're using external speakers, you should check your cables if they sit correctly. Are you?

---

### Post by juapo2 on 2009-05-23
Hi,

Not working still. Double checked with headphones, external speakers, internal and still same.

--Richi

---

### Post by ALIENDUDE5300 on 2009-05-23
Run sudo lshw and post the output here inside of code tags so that we can see more information about you system hardware. That may help us determine what drivers you would need.

EDIT: Also, if you JUST got Ubuntu, it may be easier to simply reinstall the operating system... you claim that you had no sound from your microphone? You can check if your microphone is muted by right clicking on the volume icon and then choosing "Open Volume Control". Your microphone may be called something such as "Front Mic" or "Line In". Unmute these and drag the bars near the top to see if that works. You might also want to try running sudo /etc/init.d/alsa-utils restart after restoring your esd.conf file

---

### Post by juapo2 on 2009-05-23
Hi,

Thanks for being this helpful guys =)

I have already put up a lot of things to my Ubuntu, so I would like to leave the reinstall as last resource..

Here is the output of the command you told me:
```
richi@richi-lap-ubuntu:~$ sudo lshw
[sudo] password for richi: 
richi-lap-ubuntu          
    description: Notebook
    product: Satellite M35
    vendor: TOSHIBA
    version: PSM30U-0QKJ1H
    serial: Z3017454P
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: administrator_password=disabled boot=normal chassis=notebook frontpanel_password=unknown keyboard_password=unknown power-on_password=enabled uuid=37DE7580-FB46-19B9-8031-CB51A3017454
  *-core
       description: Motherboard
       product: Portable PC
       vendor: TOSHIBA
       physical id: 0
       version: Version A0
       serial: $$T03YU49L
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: Version 1.30 (10/17/2003)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia upgrade shadowing vesa escd cdboot bootselect pcmciaboot edd int13floppy720 int5printscreen int9keyboard int17printer acpi usb agp biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1400MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: uFC-PGA Socket
          size: 600MHz
          capacity: 1400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up bts est tm2 cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: CPU Internal
             size: 64KiB
             capacity: 64KiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: CPU Internal
             size: 1MiB
             capacity: 1MiB
             clock: 1GHz (1.0ns)
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 81
          slot: System board or motherboard
          size: 512MiB
          capacity: 2GiB
        *-bank:0
             description: SODIMM SDRAM Synchronous
             physical id: 0
             slot: DIMM 0
             size: 256MiB
             width: 64 bits
        *-bank:1
             description: SODIMM SDRAM Synchronous
             physical id: 1
             slot: DIMM 1
             size: 256MiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: 82855PM Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 21
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82855PM Processor to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 21
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-display
                description: VGA compatible controller
                product: NV34M [GeForce FX Go5200 64M]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 bus_master cap_list
                configuration: driver=nvidia latency=64 maxlatency=1 mingnt=5 module=nvidia
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
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
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
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
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:1
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci bus_master
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
                vendor: Texas Instruments
                physical id: 7
                bus info: pci@0000:02:07.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-network:0
                description: Ethernet interface
                product: 82801DB PRO/100 VE (MOB) Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth0
                version: 83
                serial: 00:08:0d:6e:19:cd
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
           *-network:1
                description: Wireless interface
                product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
                vendor: Intel Corporation
                physical id: a
                bus info: pci@0000:02:0a.0
                logical name: eth1
                version: 04
                serial: 00:04:23:90:2a:f5
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 ip=192.168.1.64 latency=64 link=yes maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=IEEE 802.11b
           *-pcmcia
                description: CardBus bridge
                product: ToPIC100 PCI to Cardbus Bridge with ZV Support
                vendor: Toshiba America Info Systems
                physical id: b
                bus info: pci@0000:02:0b.0
                version: 33
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=0 maxlatency=5 mingnt=128 module=yenta_socket
           *-system UNCLAIMED
                description: System peripheral
                product: SD TypA Controller
                vendor: Toshiba America Info Systems
                physical id: d
                bus info: pci@0000:02:0d.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm cap_list
                configuration: latency=0
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
           *-disk
                description: ATA Disk
                product: IC25N020ATMR04-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: MO1O
                serial: MRG108K1CDA8VH
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=9b149b14
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: 9913b838-a16e-41fb-aa79-878d1eb93b5b
                   size: 17GiB
                   capacity: 17GiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2009-05-16 12:40:33 filesystem=ext3 modified=2009-05-23 17:43:52 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-05-23 17:43:52 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 839MiB
                   capacity: 839MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 839MiB
                      capabilities: nofs
           *-cdrom
                description: DVD reader
                product: UJDA750 DVD/CDRW
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.51
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi2
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: Windows FAT volume
             vendor: MSDOS5.0
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sdb
             logical name: /media/RICHI
             version: FAT32
             serial: 44a2-3f42
             size: 15GiB
             capacity: 15GiB
             capabilities: fat initialized
             configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush signature=de8e7bb0 state=mounted
  *-battery
       description: Lithium Ion Battery
       product: LP644E
       vendor: TOSHIBA
       physical id: 1
       version: 03/10/23
       serial: 2100020684
       slot: 1st Battery
       configuration: voltage=10.8V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8e:56:a8:9a:b7:92
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Here is a screenshot when I click on the volume preferences..

Regards,
Richi

---

### Post by juapo2 on 2009-05-24
Bump,

I really need this fix, can any1 please give me a solution?? :]

--Richi

---

### Post by khelben1979 on 2009-05-25
You can do this the hard way or the easy way.

The hard way would be to get the Alsa source packages, configure them up, compile and install them using an Ubuntu Alsa script which can be found on this forum.

The easiest way is that you make backup on all your important files and do a complete reinstall of Ubuntu.

From what I can see, there is no easy quick fix, but you can always wait some more to see if someone else has anything to say about this problem. Patience is good in this situation, I think.

---

### Post by linux_tech on 2009-05-25
You may also try reinstalling alsa packages ```
sudo apt-get install linux-sound-base alsa-base alsa-utils
``` 


reboot test sound again

---

### Post by dragos_iliescu_2005 on 2009-05-25
Take a look here:
[http://ubuntuforums.org/showthread.php?p=6589810]("Take a look here: http://ubuntuforums.org/showthread.php?p=6589810 It work for me on a Compaq 6715.")
It work for me on a Compaq 6715.

---

### Post by juapo2 on 2009-05-27
Hii,

THANKS EVERY1 YOU GUYS ARE THE SH!T!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!11

THANKS FOR THE HELP AGAIN, I REALLY APPRECIATED IT.

BEST REGARDS,
Richi

---

