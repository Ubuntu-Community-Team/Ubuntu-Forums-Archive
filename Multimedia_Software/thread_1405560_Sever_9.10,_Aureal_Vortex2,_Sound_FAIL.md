---
title: "Sever 9.10, Aureal Vortex2, Sound FAIL"
date: 2010-02-12
forum: Multimedia Software
---

### Post by HuckBerry on 2010-02-12
Just recently installed server 9.10 to use for various purposes (network auth, file server, etc) and one of the things on the tail end of the Todo list was to set up a network sound server. 

To my surprise however it seems I have no sound capability. So I ran though the usual troubleshooting, here's the output:
lspci:
       ```
00:0f.0 Multimedia audio controller: Aureal Semiconductor Vortex 2 (rev fe)
```lshw:
        ```
*-multimedia:1
             description: Multimedia audio controller
             product: Vortex 2
             vendor: Aureal Semiconductor
             physical id: f
             bus info: pci@0000:00:0f.0
             version: fe
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=au8830 latency=64 maxlatency=12 mingnt=4
             resources: irq:3 memory:f4000000-f403ffff ioport:1838(size=8) ioport:1830(size=8)
```yet aplay -l reports:
           ```
aplay: device_list:223: no soundcards found...
```There is a driver associated and it is loaded in the kernel. Alsa even lists it when it reloads, So... I'm new to alsa since sound generally just works on desktop versions, however I am well adjusted with the terminal so feel free to ask for whatever output you need.

---

### Post by HuckBerry on 2010-02-12
Did some further investigations, turns out that both my Ethernet card and my Audio card were sharing and IRQ, so I put the server down and shifted the audio card to IRQ 11, as shown by the output of cat /proc/interrupts
 ```
          CPU0       
  0:       7995    XT-PIC-XT        timer
  1:          4    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:        144    XT-PIC-XT        eth0
  6:          3    XT-PIC-XT        floppy
  7:          0    XT-PIC-XT        parport0
  8:          0    XT-PIC-XT        rtc0
  9:         48    XT-PIC-XT        acpi, uhci_hcd:usb1
 11:          0    XT-PIC-XT        au8830
 14:       3606    XT-PIC-XT        ata_piix
 15:          0    XT-PIC-XT        ata_piix
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          1   Machine check polls
ERR:          0
MIS:          0
```I also made sure that EVERYTHING was unmuted and turned up to 75% in alsamixer. (I will of course go back and re-mute everything once I start getting sound out of the speakers)

Here is the output of a test incase anyone spots something useful
```

mplayer /test.wma
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /test.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: XXXX
 author: XXXX
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16002->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
[pulse] working around probably broken pause functionality,
        see http://www.pulseaudio.org/ticket/440
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  29.8 (29.8) of 228.0 (03:48.0)  2.4% 
Exiting... (Quit)

```

Yet still no sound....

---

### Post by HuckBerry on 2010-02-12
OK, so all I needed to do after fixing the IRQ issue was sudo the mplayer... 

So obviously the average user doesn't have privileges required to access the soundcard. So this is no longer a multimedia thread, but incase anyone is interested on how to give avg. users access you would do this

```

sudo cp /etc/groups /etc/groups.old
sudo sed s/audio:x:29:pulse/audio:x:29:pulse,me/ /etc/group 

```to do it, replacing 'me' with your username


To anyone else who is having issues, visit these threads for good info:
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)
(and a few others)

---

### Post by xpacker on 2010-02-28
Huckberry--

Thanks for posting all this, but I'm such a newbie that I'm not sure if it applies to me.  I'm resurrecting an ancient desktop for a friend to use.  I've loaded wattOS on it, which is working fine except for no sound.

I also have an Aureal Vortex2.  I tried installing a backports module for alsa -- no luck.

What exactly does your fix do?  How would I know if I should do the same?  Are there any risks involved?

Thanks!

---

### Post by HuckBerry on 2010-02-28
> **xpacker said:**
> Huckberry--
 
What exactly does your fix do? How would I know if I should do the same? Are there any risks involved?
 
Thanks!
 
Risks, no. not that I'm aware of. I have cut myself pretty bad pulling PCI cards out, just be careful, OK?
 
As far as what my fix does, it depends on which fix you are refering to as there are actually two things I did.
 
The first was change IRQ of the sound card by moving the PCI to a differrent slot.
 
The second was give users the proper permissions to use the sound card. 
 
To determine which fix you need, please post the output from the following three commands
```

sudo cat /proc/interrupts
sudo lshw
sudo aplay -l

``` 
 
**note: I am assuming that WattOS is debian based or at least close enough that standard debian commands will apply. I am willing to do some reseach if not, but it would be a great learning experience for you to attempt to also.

---

### Post by xpacker on 2010-02-28
Thanks for your quick response, Huckberry.  Here's the output of the three commands (separated by "======="):

           CPU0       
  0:     125236    XT-PIC-XT        timer
  1:        280    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          1    XT-PIC-XT        au8830
  4:          3    XT-PIC-XT      
  8:          0    XT-PIC-XT        rtc0
  9:          0    XT-PIC-XT        ohci_hcd:usb2, uhci_hcd:usb4
 10:          0    XT-PIC-XT        ehci_hcd:usb1
 11:       2534    XT-PIC-XT        ohci_hcd:usb3, eth0
 12:      13890    XT-PIC-XT        i8042
 14:      13494    XT-PIC-XT        ata_piix
 15:       6295    XT-PIC-XT        ata_piix
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          2   Machine check polls
ERR:          0
MIS:          0

======================================================

OUTPUT OF LSHW


peg-desktop
    description: Computer
    product: XPSR450
    vendor: Dell Computer Corporation
    version: MT
    width: 32 bits
    capabilities: smbios-2.1 dmi-2.1
    configuration: uuid=6A3BEC6A-900A-11D2-A511-0800093DBCE8
  *-core
       description: Motherboard
       product: SE440BX
       vendor: Intel Corporation
       physical id: 0
       version: AA696089-408
       serial: 00028498124648C900Y1
     *-firmware
          description: BIOS
          vendor: Intel Corp.
          physical id: 0
          version: 4S4EB0X1.10A.0035.P13 (09/21/99)
          size: 1MiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi
     *-cpu
          description: CPU
          product: Pentium II (Deschutes)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.5.2
          slot: J4J1
          size: 450MHz
          capacity: 450MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr up
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: None
             size: 32KiB
             capacity: 32KiB
             capabilities: non-burst internal write-back
        *-cache:1
             description: L2 cache
             physical id: a
             slot: None
             size: 512KiB
             capacity: 512KiB
             capabilities: external write-back
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 256MiB
          capacity: 768MiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: J6J1
             size: 128MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous [empty]
             physical id: 1
             slot: J6J2
        *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: J7J1
             size: 128MiB
             width: 32 bits
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel latency=64
          resources: irq:0 memory:f8000000-fbffffff(prefetchable)
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
             resources: memory:f5000000-f5ffffff memory:fc000000-fcffffff(prefetchable)
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV4 [RIVA TNT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 04
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-1.0 bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:f5000000-f5ffffff memory:fc000000-fcffffff(prefetchable)
        *-isa
             description: ISA bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@0000:00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@0000:00:07.1
             logical name: scsi0
             logical name: scsi1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated
             configuration: driver=ata_piix latency=64
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:10a0(size=16)
           *-disk
                description: ATA Disk
                product: IC35L020AVER07-0
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: ER2O
                serial: SVPTVMF2342
                size: 18GiB (20GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=743d1854
              *-volume:0
                   description: Linux swap volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 1
                   serial: ce9f1233-387e-4057-a837-6bb3a07a2e04
                   size: 486MiB
                   capacity: 486MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
              *-volume:1
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: ce0b4f00-9a64-45f8-8a68-d7b34a829350
                   size: 8103MiB
                   capacity: 8103MiB
                   capabilities: primary bootable journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-02-24 22:51:20 filesystem=ext3 modified=2010-02-24 23:13:22 mount.fstype=ext3 mount.options=rw,relatime,errors=remount-ro,data=writeback mounted=2010-02-28 21:00:38 state=mounted
              *-volume:2
                   description: EXT3 volume
                   vendor: Linux
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   logical name: /home
                   version: 1.0
                   serial: 9c1126ab-9f3a-47d9-b38f-d8ca1b8c8dd3
                   size: 10GiB
                   capacity: 10GiB
                   capabilities: primary journaled extended_attributes large_files recover ext3 ext2 initialized
                   configuration: created=2010-02-24 22:51:43 filesystem=ext3 modified=2010-02-28 21:00:41 mount.fstype=ext3 mount.options=rw,relatime,errors=continue,data=writeback mounted=2010-02-28 21:00:41 state=mounted
           *-cdrom
                description: CD-R/CD-RW writer
                product: CD-Writer+ 8100
                vendor: HP
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.0g
                capabilities: removable audio cd-r cd-rw
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@0000:00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: driver=uhci_hcd latency=64
             resources: irq:9 ioport:1080(size=32)
        *-bridge
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@0000:00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: driver=piix4_smbus latency=0
             resources: irq:9
        *-network
             description: Ethernet interface
             product: 3c905B 100BaseTX [Cyclone]
             vendor: 3Com Corporation
             physical id: d
             bus info: pci@0000:00:0d.0
             logical name: eth0
             version: 24
             serial: 00:50:04:05:52:de
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=71.207.180.6 latency=80 link=yes maxlatency=10 mingnt=10 multicast=yes port=MII speed=100MB/s
             resources: irq:11 ioport:1000(size=128) memory:f4043000-f404307f memory:10000000-1001ffff(prefetchable)
        *-multimedia:0 UNCLAIMED
             description: Multimedia video controller
             product: ZR36120
             vendor: Zoran Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=64 maxlatency=16 mingnt=2
             resources: memory:f4040000-f4040fff
        *-multimedia:1
             description: Multimedia audio controller
             product: Vortex 2
             vendor: Aureal Semiconductor
             physical id: f
             bus info: pci@0000:00:0f.0
             version: fe
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=au8830 latency=64 maxlatency=12 mingnt=4
             resources: irq:3 memory:f4000000-f403ffff ioport:10b8(size=8) ioport:10b0(size=8)
        *-usb:1
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
             resources: irq:9 memory:f4041000-f4041fff
        *-usb:2
             description: USB Controller
             product: USB
             vendor: NEC Corporation
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 43
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci_hcd latency=64 maxlatency=42 mingnt=1
             resources: irq:11 memory:f4042000-f4042fff
        *-usb:3
             description: USB Controller
             product: USB 2.0
             vendor: NEC Corporation
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ehci_hcd latency=132 maxlatency=34 mingnt=16
             resources: irq:10 memory:f4043400-f40434ff

=========================================================================

OUTPUT OF APLAY


**** List of PLAYBACK Hardware Devices ****
card 0: au8830 [Aureal Vortex au8830], device 0: AU88x0 ADB [adb]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: au8830 [Aureal Vortex au8830], device 1: AU88x0 SPDIF [spdif]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: au8830 [Aureal Vortex au8830], device 2: AU88x0 A3D [a3d]
  Subdevices: 16/16
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
card 0: au8830 [Aureal Vortex au8830], device 3: AU88x0 WT [wt]
  Subdevices: 64/64
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
  Subdevice #32: subdevice #32
  Subdevice #33: subdevice #33
  Subdevice #34: subdevice #34
  Subdevice #35: subdevice #35
  Subdevice #36: subdevice #36
  Subdevice #37: subdevice #37
  Subdevice #38: subdevice #38
  Subdevice #39: subdevice #39
  Subdevice #40: subdevice #40
  Subdevice #41: subdevice #41
  Subdevice #42: subdevice #42
  Subdevice #43: subdevice #43
  Subdevice #44: subdevice #44
  Subdevice #45: subdevice #45
  Subdevice #46: subdevice #46
  Subdevice #47: subdevice #47
  Subdevice #48: subdevice #48
  Subdevice #49: subdevice #49
  Subdevice #50: subdevice #50
  Subdevice #51: subdevice #51
  Subdevice #52: subdevice #52
  Subdevice #53: subdevice #53
  Subdevice #54: subdevice #54
  Subdevice #55: subdevice #55
  Subdevice #56: subdevice #56
  Subdevice #57: subdevice #57
  Subdevice #58: subdevice #58
  Subdevice #59: subdevice #59
  Subdevice #60: subdevice #60
  Subdevice #61: subdevice #61
  Subdevice #62: subdevice #62
  Subdevice #63: subdevice #63

---

### Post by xpacker on 2010-02-28
Oh yes, about wattOS: it's an Ubuntu-based OS, using LXDE instead of Gnome.  It's working well on this old desktop, very fast and lightweight.  The only thing that's not working for me out of the box is the audio.

[http://www.planetwatt.com/](http://www.planetwatt.com/)

---

### Post by HuckBerry on 2010-03-01
Well it looks like everything is in order as far as hardware. The irq is not being shared, the driver is loaded, and aplay recognises it. So next is software.
 
```

sudo alsamixer

```
 
run that and turn the volume up for master and PCM to about 75%. 
Left&right control the device
up&down adjust volume for both channels
q&e / z&c control volume for one channel at a time
esc quits.
 
Then double check that your media player is set to use that sound card, as there is another one listed in your output (product: ZR36120 / vendor: Zoran Corporation) 
 
Try this code
```

$ sudo aplay -L
default:CARD=au8830
    Aureal Vortex au8830, adb
    Default Audio Device
front:CARD=au8830,DEV=0
    Aureal Vortex au8830, adb
    Front speakers
surround40:CARD=au8830,DEV=0
    Aureal Vortex au8830, adb
    4.0 Surround output to Front and Rear speakers
iec958:CARD=au8830,DEV=0
    Aureal Vortex au8830, spdif
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)$
$ aplay -D front
^CAborted by signal Interrupt...

```
 
you can replace "front" with any of the devices from the "-L" output. If you dont see any errors when it runs, then it is working. Hit CTRL+C to stop playback. If all that works and you don't get sound, you may have the speakers in the wrong jack or the card may be dead.
 
Hope that helps.

---

### Post by xpacker on 2010-03-01
Thanks so much, Huckberry.  It turns out the old speakers were completely dead.  I switched them with a different set, and all is well.

If you hadn't mentioned the word "dead," I'd never have figured it out.  I was convinced there was an esoteric software problem.  I appreciate your checking it all out -- I really had no idea how to check for it myself.

Sorry it turned out so mundane, but my gratitude is just as complete.

---

### Post by HuckBerry on 2010-03-02
No problem, this thread is now a wonderful step-by-step guide on how to troubleshoot audio issues in linux. But do keep in mind the golden rule of troubleshooting: narrow the domain of failure by replacing as much as possible with proven working components. (eg. swap the speakers first, then the soundcard, then the config) Remember all those jokes from the 90's about  plugging  the computer in before calling tech support?

---

### Post by xpacker on 2010-03-02
Heh heh heh.  It runs totally counter to my mind's first thought, "This must be the most difficult, complicated problem imaginable."

But at least I had it plugged in.....

---

