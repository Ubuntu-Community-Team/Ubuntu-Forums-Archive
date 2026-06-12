---
title: "Broadcom Wireless (im a complete noob to linux and need help)"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by Crackmonkey91 on 2009-07-02
well im tring to get my wireless up and runing but i just dont know how i have gone to other threads like [http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+install](http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+install) but I have a problem write from the start guy or girls says to make a directory but i dont even know how to do that im so confused i just want to get it up and running can some one please go step by step including how to make a directory?????  :?::?:](*,)

---

### Post by Ayuthia on 2009-07-02
If you have a Broadcom 4311, 4312, 4321, 4322, or 4328 card, you should just go to System->Administration->Hardware Drivers and activate the Broadcom STA option.  That way you don't have to download or create anything.

Hope that helps.

---

### Post by t0mppa on 2009-07-02
EDIT: Ah, Ayuthia beat me to it.

---

### Post by Crackmonkey91 on 2009-07-03
i have 4318 card type

---

### Post by rmhartman on 2009-07-03
> **Ayuthia said:**
> If you have a Broadcom 4311, 4312, 4321, 4322, or 4328 card, you should just go to System->Administration->Hardware Drivers and activate the Broadcom STA option.  That way you don't have to download or create anything.

Hope that helps.

When I go there it says "this driver is activated but not currently in use".

How do I get it to *use* the darned thing!

(Broadcom 4328)

---

### Post by rmhartman on 2009-07-03
> **Crackmonkey91 said:**
> well im tring to get my wireless up and runing but i just dont know how i have gone to other threads like [http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+install](http://ubuntuforums.org/showthread.php?t=896713&highlight=broadcom+install) but I have a problem write from the start guy or girls says to make a directory but i dont even know how to do that im so confused i just want to get it up and running can some one please go step by step including how to make a directory?????  :?::?:](*,)

Nobody actually answered your question.  In the thread you reference they have blocks that are labeled "code".  The first such block says "mkdir wdriver".  "mkdir" is the command to _m_a_k_e a _dir_ectory.

But ... where/how do you type this?  For that you need to fire up a terminal window.  This is, IIRC, on the "Accessories" menu.  

Forgive me if I get it wrong ... I am typing on a Dell Vostro 1310 which has a Broadcom wireless adapter that I still can't get working under Ubuntu so to read the forums I have to boot under XP and can't double-check the ubuntu menu structure.  Look around, it's there somewhere.  The icon looks a lot like a little black square.  Maybe a monitor with a black screen.

Hope this helps.

---

### Post by superprash2003 on 2009-07-03
you may need a wired connection for this as it may require to download some packages.. and also try rebooting after your done

---

### Post by rmhartman on 2009-07-03
> **superprash2003 said:**
> you may need a wired connection for this as it may require to download some packages.. and also try rebooting after your done

Ok, so when I have a wired connection, what packages do I need to download?  Tell me how I get it from "active but not used" to being used please.

---

### Post by superprash2003 on 2009-07-04
deactivate it.. get a working wired connection with internet access. and activate it again , it should automatically download the necessary packages.. and remember to reboot

---

### Post by bidbrooken on 2009-07-04
damn this forum software- keeps killing my message text - guess the developers can't be bothered checking to see if they can execute stuff - just assume they can - what is it they say about assume

anyhow

I have the same problem as [rmhartman]("http://ubuntuforums.org/member.php?u=462704") so would also like the answer...

---

### Post by rmhartman on 2009-07-04
> **superprash2003 said:**
> deactivate it.. get a working wired connection with internet access. and activate it again , it should automatically download the necessary packages.. and remember to reboot

Ok.  To be explicit, my plan is:
deactivate
shut down
plug in wired
boot up
activate
wait while it downloads what it needs
reboot

Sound good?  Am I missing something?

I will let you know how it goes ...

---

### Post by bidbrooken on 2009-07-04
Tried tihs and it didn't work for me - here's hoping

---

### Post by t0mppa on 2009-07-05
Nice case of thread hijacking, original poster got totally ignored, which is the reason for the "one thread, one problem" rule of the thumb.

[QUOTE=Crackmonkey91]i have 4318 card type [/QUOTE]

Ok, then the STA driver will not support it and thus you have to use either b43 or ndiswrapper. B43 should be the default Broadcom driver though, so why don't you run **lshw -c network** and **dmesg | grep -e Broadcom -e b43** from a terminal and post back with the output, which will likely point us towards what the issue is.

[QUOTE=bidbrooken]damn this forum software- keeps killing my message text - guess the developers can't be bothered checking to see if they can execute stuff - just assume they can - what is it they say about assume[/QUOTE]

It's a vbulletin board, so the admins here are only maintaining it, not actively developing the code behind it. And on top of that, since there doesn't seem to be any posts towards this in the [feedback]("http://ubuntuforums.org/forumdisplay.php?f=48") subforum, everyone who's run into it has just done what you have, ie. been frustrated, but not bothered to actually tell anyone what went wrong to find out what's causing that. There are tens of thousands of new posts daily, the admins can't read every single one looking for trouble.

[QUOTE=bidbrooken]Tried tihs and it didn't work for me - here's hoping[/QUOTE]

Can always try compiling it manually, in which case you'll actually get output about what went wrong, if there was trouble. [Here]("http://linuxfans.betaserver.org/index.php?option=com_content&view=article&id=48:guide-to-compiling-and-using-the-broadcom-sta-module&catid=34:guides&Itemid=61")'s a guide for doing that.

---

### Post by bidbrooken on 2009-07-05
ok point taken

Heres my output from the commands - since I have the same problems

Just to clarify
On boot I have no broadcom - either eth0 or 1
If I go into hardware drivers and activate both start fine
If I reboot - start the process again
Activation choice not being preserved

lshw -c network
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 03
       serial: 00:1c:26:94:5b:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.91.9 ip=10.10.9.203 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:9d:19:21
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.10.9.202 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e6:e9:22:00:42:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


AND

dmesg | grep -e Broadcom -e b4
[    3.504049] usb usb4: configuration #1 chosen from 1 choice
[    5.443378] input: Broadcom Corp as /devices/pci0000:00/0000:00:13.3/usb5/5-2/5-2.2/5-2.2:1.0/input/input6
[    5.469108] generic-usb 0003:0A5C:4502.0002: input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:13.3-2.2/input0
[    5.664516] input: Broadcom Corp as /devices/pci0000:00/0000:00:13.3/usb5/5-2/5-2.3/5-2.3:1.0/input/input7
[    5.693112] generic-usb 0003:0A5C:4503.0003: input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:13.3-2.3/input0
[  223.904318] input: Broadcom Corp as /devices/pci0000:00/0000:00:13.3/usb5/5-2/5-2.2/5-2.2:1.0/input/input12
[  223.938209] generic-usb 0003:0A5C:4502.0004: input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:13.3-2.2/input0
[  224.146718] input: Broadcom Corp as /devices/pci0000:00/0000:00:13.3/usb5/5-2/5-2.3/5-2.3:1.0/input/input13
[  224.191415] generic-usb 0003:0A5C:4503.0005: input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:13.3-2.3/input0
[  770.018872] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.91.9
[  770.079823] b44 0000:03:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  770.141649] b44.c:v2.0
[  770.163151] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:9d:19:21
[  770.247843] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.91.9
[  778.804203] b44: eth0: Link is up at 100 Mbps, full duplex.
[  778.804211] b44: eth0: Flow control is off for TX and off for RX.

---

### Post by rmhartman on 2009-07-05
That seems to have done it.  Thank you.

I wonder why it had to be de-activated before it would work though ...

---

### Post by jpyanowski on 2009-07-05
> **rmhartman said:**
> When I go there it says "this driver is activated but not currently in use".

How do I get it to *use* the darned thing!

(Broadcom 4328)

Thank you for this info. I seemed to have forgotten about the drivers on this install. Wireless is working great now. \\:D/

---

### Post by t0mppa on 2009-07-05
> **rmhartman said:**
> That seems to have done it.  Thank you.

I wonder why it had to be de-activated before it would work though ...

It needed to download packets to get activated and if you enabled it without a working internet connection, then it couldn't do that, but still considered itself activated as it did the other stuff. And since you can't turn on something that thinks it's already on, you instead had to shut it down first and then re-activate it.

[QUOTE=bidbrooken]Just to clarify
On boot I have no broadcom - either eth0 or 1
If I go into hardware drivers and activate both start fine
If I reboot - start the process again
Activation choice not being preserved
[/QUOTE]

Ok, run lshw after a boot before doing anything to see in what state the interface is before you do the activation. For instance the ssb module sometimes hogs up the wireless even when it's not supposed to and that needs a small workaround to fix permanently.

---

### Post by bidbrooken on 2009-07-06
this is lshw - did a full not just -c network

sudo lshw
dw1                       
    description: Portable Computer
    product: Inspiron 1721
    vendor: Dell Inc.
    serial: 2S2R63J
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=portable uuid=44454C4C-5300-1032-8052-B2C04F36334A
  *-core
       description: Motherboard
       product: 0UK441
       vendor: Dell Inc.
       physical id: 0
       serial: .2S2R63J.CN4864379E2265.
       slot: &#65533;&#65533;@
     *-firmware
          description: BIOS
          vendor: Dell Inc.
          physical id: 0
          version: A07 (04/21/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-66
          vendor: Advanced Micro Devices [AMD]
          physical id: 400
          bus info: cpu@0
          slot: Microprocessor
          size: 2300MHz
          capacity: 2300MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 128KiB
             capacity: 128KiB
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
          size: 4GiB
        *-bank:0
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 16HTF25664HY-80EE1
             vendor: 2C00000000000000
             physical id: 0
             serial: D220DAC8
             slot: DIMM_A
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR Synchronous 667 MHz (1.5 ns)
             product: 16HTF25664HY-80EE1
             vendor: 2C00000000000000
             physical id: 1
             serial: D220DA2D
             slot: DIMM_B
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci:0
          description: Host bridge
          product: RS690 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (Internal gfx)
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=64
        *-pci:1
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 1)
             vendor: ATI Technologies Inc
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
           *-network UNCLAIMED
                description: Network controller
                product: BCM4328 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
        *-pci:2
             description: PCI bridge
             product: RS690 PCI to PCI Bridge (PCI Express Port 3)
             vendor: ATI Technologies Inc
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver
        *-storage
             description: SATA controller
             product: SB600 Non-Raid-5 SATA
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: scsi0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci
           *-disk
                description: ATA Disk
                product: SAMSUNG HM250JI
                physical id: 0.0.0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: HS10
                serial: S133JD0P912593
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00000080
              *-volume:0
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   logical name: /
                   version: 1.0
                   serial: f980c524-fd38-4981-a445-f50f43b749af
                   size: 223GiB
                   capacity: 223GiB
                   capabilities: primary bootable journaled extended_attributes large_files ext3 ext2 initialized
                   configuration: created=2009-07-04 03:06:02 filesystem=ext3 modified=2009-07-06 06:27:26 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2009-07-05 22:54:51 state=mounted
              *-volume:1
                   description: Extended partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   size: 9703MiB
                   capacity: 9703MiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 9703MiB
                      capabilities: nofs
        *-usb:0
             description: USB Controller
             product: SB600 USB (OHCI0)
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:1
             description: USB Controller
             product: SB600 USB (OHCI1)
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:2
             description: USB Controller
             product: SB600 USB (OHCI2)
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:3
             description: USB Controller
             product: SB600 USB (OHCI3)
             vendor: ATI Technologies Inc
             physical id: 13.3
             bus info: pci@0000:00:13.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:4
             description: USB Controller
             product: SB600 USB (OHCI4)
             vendor: ATI Technologies Inc
             physical id: 13.4
             bus info: pci@0000:00:13.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64
        *-usb:5
             description: USB Controller
             product: SB600 USB Controller (EHCI)
             vendor: ATI Technologies Inc
             physical id: 13.5
             bus info: pci@0000:00:13.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd
        *-serial
             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 14
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4
        *-ide
             description: IDE interface
             product: SB600 IDE
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master emulated
             configuration: driver=pata_atiixp latency=64
           *-cdrom
                description: DVD writer
                product: DVD+-RW DS-8W1P
                vendor: PBDS
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: BD1B
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=open
        *-multimedia
             description: Audio device
             product: SBx00 Azalia (Intel HDA)
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: SB600 PCI to LPC Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
           *-network UNCLAIMED
                description: Ethernet controller
                product: BCM4401-B0 100Base-TX
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 1
                bus info: pci@0000:03:01.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.1
                bus info: pci@0000:03:01.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64 module=sdhci_pci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 1.2
                bus info: pci@0000:03:01.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 1.3
                bus info: pci@0000:03:01.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
     *-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             product: 4000BEV External
             vendor: WD
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdb
             version: 1.05
             serial: WD-WXN908NZ3924
             size: 372GiB (400GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=4 signature=5b6ac646
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@6:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/My Passport
                version: 3.1
                serial: 2eb843dd-3923-0345-ae1e-67342bf2dcdb
                size: 293GiB
                capacity: 293GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=512 created=2008-12-02 15:52:30 filesystem=ntfs label=My Passport mount.fstype=fuseblk mount.options=rw,nosuid,nodev,user_id=0,group_id=0,allow_other state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@6:0.0.0,2
                logical name: /dev/sdb2
                size: 79GiB
                capacity: 79GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: W95 FAT32 partition
                   physical id: 5
                   logical name: /dev/sdb5
                   logical name: /media/PS3
                   capacity: 79GiB
                   configuration: mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
  *-battery
       product: DELL UW28079
       vendor: Sanyo
       physical id: 1
       slot: Sys. Battery Bay
       capacity: 78000mWh
       configuration: voltage=11.1V
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 72:5c:1a:e1:5c:f8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by t0mppa on 2009-07-06
A full lshw is too much info for merely fixing wireless, although it does show you have a few other interfaces (display, memory stick bus host, picture card controller) that don't get associated with any drivers either. The other two you might be able to live without depending on your needs, but the display driver is kind of important. :)

Of course, with an ATI x1200, you won't be getting much out of Jaunty (9.04), since Jaunty upgraded to XServer 1.6, which doesn't support the older ATI drivers and ATI updated their newer drivers to only support the mid/high end cards. There are open source drivers available, which are good for 2D, but 3D performance will be rather crappy. Anyway, you can get more information about that from the [Hardware & Laptop subforum]("http://ubuntuforums.org/forumdisplay.php?f=332").

As for your wireless & wired, they're both listed as unclaimed, meaning no driver is getting associated with them and that being the reason they're not working. I'm not sure why, since enabling them once should do it for good. Maybe you should take a look at your blacklisting files (in /etc/modprobe.d/) and see if they're all blacklisted there.

Anyway, try running **sudo modprobe wl b44 ssb** from a fresh boot without touching the Hardware Drivers yet to see if that fixes the situation. If it does, you can add the line into your /etc/rc.local before the *exit 0* line, so it will be run every time you boot your machine.

---

### Post by bidbrooken on 2009-07-06
ok tried your modprobe command and turned the box over and it is working

Thanks

no idea what you did but the prop device is now working properly

---

### Post by t0mppa on 2009-07-06
Modprobing is simply how Linux loads up driver modules for the kernel to use. So, the command I posted just told the system: "load up and start using these 3 modules", which it did and then realized they're drivers for the wired & wireless device, associated the two with each other and that was all.

The odd thing is why they didn't get loaded in the first place, but if it works after reboots now, guess that's not too big of an issue.

---

