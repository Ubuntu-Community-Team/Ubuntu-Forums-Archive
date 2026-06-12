---
title: "Still no sound in Hardy Heron"
date: 2008-04-29
forum: Multimedia Software
---

### Post by mmasroorali on 2008-04-29
Previously I was using the beta version and was hoping that things will improve as soon as the stable version is released. However, things are all the same. Here is the debug information:

	   1. Sound is not muted in Master, set at 100%.
	   
	   2. Excerpt from the output of lspci
	      00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 
           
           3. Output of ls -l /dev/dsp
              crw-rw----+ 1 root audio 14, 3 2008-04-29 09:36 /dev/dsp

	   4. Output of ls -l /dev/snd
              total 0
	      crw-rw----+ 1 root audio 116,  0 2008-04-29 09:36 controlC0
	      crw-rw----+ 1 root audio 116,  4 2008-04-29 09:36 hwC0D0
	      crw-rw----+ 1 root audio 116, 24 2008-04-29 09:38 pcmC0D0c
	      crw-rw----+ 1 root audio 116, 16 2008-04-29 12:17 pcmC0D0p
	      crw-rw----+ 1 root audio 116, 28 2008-04-29 09:36 pcmC0D4c
	      crw-rw----+ 1 root audio 116,  1 2008-04-29 09:36 seq
	      crw-rw----+ 1 root audio 116, 33 2008-04-29 09:36 timer

           5. In alsamixer none of the Playback devices are muted.

	   6. Output of aplay -l
	      **** List of PLAYBACK Hardware Devices ****
	      card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
	        Subdevices: 1/1  Subdevice #0: subdevice #0

	   7. Use audio devices is checked for the user.

Feeling frustrated. Previously one kind subscriber suggested changing the sound channel. Do you know how that can be done?

---

### Post by litmos95 on 2008-04-29
There are tons of similar issues here, have you tried this one

```

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

```
and then reboot.

---

### Post by mmasroorali on 2008-04-29
I tried the above. But it did not work. 

Wondering whether the speakers are okay? Yes, I hear the system beeps.

And when Windows XP was installed in this computer, the sound was fine.

---

### Post by rjmdomingo2003 on 2008-04-29
Try installing linux-386 from synaptic, then, reboot. See if it works.

---

### Post by litmos95 on 2008-04-29
> **mmasroorali said:**
> 
 Yes, I hear the system beeps.

Well system beeps come from the speaker on mainboard, it doesn't confirm that ubuntu recognized your sound card.
Do you see your sound card in 
```

sudo lshw

```?

---

### Post by mmasroorali on 2008-04-29
I did, no luck.

---

### Post by mmasroorali on 2008-04-29
Output of lshw

masroor-desktop
    description: Desktop Computer
    product: HP dx2700 MT(RC737AV)
    vendor: Hewlett-Packard
    version: HP Desktop
    serial: SGH7190G9S
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=A50B1B0C-EE00-DC11-ABAF-676047490AE4
  *-core
       description: Motherboard
       product: 0A78h
       vendor: Hewlett-Packard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: V1.08 (02/02/2007)
          size: 128KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification netboot
     *-cpu:0
          description: CPU
          product: Intel(R) Pentium(R) D CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          slot: Socket 775
          size: 3GHz
          capacity: 3066MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc pebs bts sync_rdtsc pni monitor ds_cpl est cid cx16 xtpr lahf_lm cpufreq
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: b
             slot: External Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: synchronous external write-back
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
     *-memory
          description: System Memory
          physical id: 1b
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: None
             vendor: C100000000000000
             physical id: 0
             serial: None
             slot: A0
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: None
             vendor: 7F7F7F7F7F510000
             physical id: 1
             serial: None
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:2
             description: DIMM Synchronous 533 MHz (1.9 ns)
             product: None
             vendor: C100000000000000
             physical id: 2
             serial: None
             slot: A2
             size: 256MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:3
             description: DIMM [empty]
             product: None
             vendor: None
             physical id: 3
             serial: None
             slot: A3
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 15.6.5
          serial: 0000-0F65-0000-0000-0000-0000
          size: 18EHz
          capabilities: ht
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
     *-pci
          description: Host bridge
          product: 82Q963/Q965 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display UNCLAIMED
             description: VGA compatible controller
             product: 82Q963/Q965 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-network
                description: Ethernet interface
                product: RTL-8110SC/8169SC Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 7
                bus info: pci@0000:01:07.0
                logical name: eth0
                version: 10
                serial: 00:1a:4b:b6:2a:07
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=172.20.237.232 latency=64 link=yes maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
        *-isa
             description: ISA bridge
             product: 82801HB/HR (ICH8/R) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide:0
             description: IDE interface
             product: 82801H (ICH8 Family) 4 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-disk
                description: ATA Disk
                product: WDC WD800JD-60LS
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 10.0
                serial: WD-WMAM9NP59818
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=b233b233
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 03e409aa-a310-44f7-a08d-067ce1153c9e
                   size: 15GiB
                   capacity: 15GiB
                   capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-04-28 10:20:30 filesystem=ext3 modified=2008-04-29 14:06:09 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2008-04-29 13:38:16 state=mounted
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /usr
                   version: 1.0
                   serial: 708086fc-82d3-4fbb-adbf-cd78bdb66bd1
                   size: 30GiB
                   capacity: 30GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-04-28 10:20:36 filesystem=ext3 modified=2008-04-29 14:06:58 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-04-29 14:06:58 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: c7efba6a-1da8-4df4-bb11-4e6fd1d6168a
                   size: 1953MiB
                   capacity: 1953MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:3
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 4
                   bus info: scsi@0:0.0.0,4
                   logical name: /dev/sda4
                   logical name: /home
                   version: 1.0
                   serial: bcd81b20-2c3f-4b3d-99fc-da7ca1d46628
                   size: 26GiB
                   capacity: 26GiB
                   capabilities: primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-03-11 23:26:00 filesystem=ext3 modified=2008-04-29 14:06:58 mount.fstype=ext3 mount.options=rw,relatime,data=ordered mounted=2008-04-29 14:06:58 state=mounted
           *-cdrom
                description: DVD reader
                product: CDW/DVD TS-H493A
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/dvd1
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: CD06
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5 status=open
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
        *-ide:1
             description: IDE interface
             product: 82801H (ICH8 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             logical name: scsi2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix
           *-cdrom
                description: DVD-RAM writer
                product: DRW-2014L1T
                vendor: ASUS
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=open

---

### Post by chickpea on 2008-05-01
Hi, mmasroorali.
I'm not sure this one could help you, but just try it. It won't at least waste your time so much:KS

in a terminal window:
```
alsamixer
```

Scroll right in the alsamixer settings window with arrow key, you'll end up to <External>. Then press m key to turn it off.
When I installed ubuntu 8.04 on my NEC laptop no sound could be heard. And this setting solved my problem.

---

