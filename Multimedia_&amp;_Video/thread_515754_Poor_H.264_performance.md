---
title: "Poor H.264 performance"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by Zorael on 2007-08-02
I can't seem to play videos encoded in H.264 and equavilent "CPU-demanding" codecs satisfactorily. Granted, my computer isn't top-notch, but I don't remember experiencing this in Windows. So I've likely done something wrong.

The video file I keep as a benchmark launches in all of the five players I have installed; Totem, mplayer, VLC, gxine and xine (same as gxine?). It's in a Matroska container, H.264 according to Totem, 640x480 and 24fps.

In Totem the framerate is roughly cut in half (guesstimation) by frameskipping, when there's a lot of movement. The sound keeps up nicely. CPU load is at about 20-40%.

In mplayer the framerate is good, with the "occasional" chug that makes sound loopy metallic-ish for the duration of the chug. I avoid mplayer, on the other hand, since with some other videos I've watched, from time to time (~5x over 40 minutes), sound dies on me for 10-15 seconds. If I rewind 15 seconds, chances are it'll have restored itself when I get to the point where it went wrong. It works, but it's an annoyance. CPU load is at about 30-50%.

VLC is sort of a blend between the two. The framerate is at the level of Totem along with decent sound, but the audio dies from time to time. CPU hovers at 20-40%, but drops down to 0-5% at times.

gxine and xine play it best, but ends up freezing some way into the video. Sometimes it's only temporary (takes a couple of seconds for it to get a grip), sometimes Gnome stops listening to keyboard input, so I end up being unable to switch to a console to restart GDM. Meaning a forced shutdown.


```
familjen@svart:~$ uname -r
2.6.20-16-generic

familjen@svart:~$ sudo lshw
Password:
svart                     
    description: Mini Tower Computer
    product: Dimension 8200
    vendor: Dell Computer Corporation
    serial: 1V69F0J
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: administrator_password=enabled boot=normal chassis=mini-tower power-on_password=enabled uuid=44454C4C-5600-1036-8039-B1C04F46304A
  *-core
       description: Motherboard
       product: Dimension 8200
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Dell Computer Corporation
          physical id: 0
          version: A05 (04/18/2002)
          size: 64KB
          capacity: 448KB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb agp ls120boot biosbootspecification netboot
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.20GHz
          vendor: Intel Corp.
          physical id: 400
          bus info: cpu@0
          version: 15.2.4
          slot: Microprocessor
          size: 2200MHz
          capacity: 2400MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 700
             size: 8KB
             capacity: 8KB
             capabilities: internal write-back data
        *-cache:1
             description: L2 cache
             physical id: 701
             size: 512KB
             capacity: 512KB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 512MB
          capacity: 2GB
        *-bank:0
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
             physical id: 0
             slot: RIMM1
             size: 256MB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns)
             physical id: 1
             slot: RIMM2
             size: 256MB
             width: 16 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns) [empty]
             physical id: 2
             slot: RIMM3
             clock: 400MHz (2.5ns)
        *-bank:3
             description: RIMM RDRAM RAMBUS 400 MHz (2.5 ns) [empty]
             physical id: 3
             slot: RIMM4
             clock: 400MHz (2.5ns)
     *-pci
          description: Host bridge
          product: 82850 850 (Tehama) Chipset Host Bridge (MCH)
          vendor: Intel Corporation
          physical id: e0000000
          bus info: pci@00:00.0
          logical name: /dev/fb0
          version: 04
          width: 32 bits
          clock: 33MHz
          capabilities: fb
          configuration: depth=32 frequency=75.69Hz mode=1024x768 visual=truecolor xres=1024 yres=768
          resources: iomemory:e0000000-e7ffffff
        *-pci:0
             description: PCI bridge
             product: 82850 850 (Tehama) Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV25 [GeForce4 Ti 4600]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: a3
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5
                resources: iomemory:fc000000-fcffffff iomemory:f0000000-f7ffffff iomemory:eff80000-efffffff irq:19
        *-pci:1
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-multimedia
                description: Multimedia audio controller
                product: CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator]
                vendor: Cirrus Logic
                physical id: 7
                bus info: pci@02:07.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=Sound Fusion CS46xx latency=64 maxlatency=24 mingnt=4
                resources: iomemory:fe2ff000-fe2fffff iomemory:fe100000-fe1fffff irq:19
           *-communication UNCLAIMED
                description: Communication controller
                product: HSF 56k Data/Fax/Voice/Spkp Modem
                vendor: Conexant
                physical id: 8
                bus info: pci@02:08.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
                resources: iomemory:fe2e0000-fe2effff ioport:ecf8-ecff irq:10
           *-network
                description: Ethernet interface
                product: 21x4x DEC-Tulip compatible 10/100 Ethernet
                vendor: Davicom Semiconductor, Inc.
                physical id: 9
                bus info: pci@02:09.0
                logical name: eth0
                version: 31
                serial: 00:08:a1:21:52:d1
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=dmfe driverversion=1.36.4 ip=192.168.0.5 latency=64 maxlatency=40 mingnt=20 multicast=yes
                resources: ioport:e800-e8ff iomemory:fe2fec00-fe2fecff irq:16
           *-firewire
                description: FireWire (IEEE 1394)
                product: TSB12LV26 IEEE-1394 Controller (Link)
                vendor: Texas Instruments
                physical id: a
                bus info: pci@02:0a.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=3
                resources: iomemory:fe2fe000-fe2fe7ff iomemory:fe2f8000-fe2fbfff irq:17
        *-isa
             description: ISA bridge
             product: 82801BA ISA Bridge (LPC)
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801BA IDE U100
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master emulated scsi-host
             configuration: driver=ata_piix latency=0
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ffa0-ffaf
           *-disk
                description: SCSI Disk
                product: WDC WD1200JB-75C
                vendor: ATA
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 16.0
                serial: WD-WMA8C1935322
                size: 111GB
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5
              *-volume:0
                   description: Hidden FAT16 partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   capacity: 31MB
                   capabilities: primary hidden
              *-volume:1
                   description: Linux filesystem partition
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   capacity: 62MB
                   capabilities: primary
              *-volume:2
                   description: Extended partition
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   size: 111GB
                   capacity: 111GB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      capacity: 107GB
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 3914MB
                      capabilities: nofs
           *-cdrom:0
                description: SCSI CD-ROM
                product: CD-ROM GCR-8481B
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.06
                capabilities: removable audio
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/scd0
           *-cdrom:1
                description: DVD reader
                product: DVD+RW-D01
                vendor: PHILIPS
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                version: 1.41
                serial: 5PHILIPS DVD+RW-D01      1.41011214RICCA2204085
                capabilities: removable audio cd-r cd-rw dvd
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
        *-usb:0
             description: USB Controller
             product: 82801BA/BAM USB (Hub #1)
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@00:1f.2
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff80-ff9f irq:17
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
              *-usb
                   description: Mouse
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 41.01
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12.0MB/s
        *-serial UNCLAIMED
             description: SMBus
             product: 82801BA/BAM SMBus
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@00:1f.3
             version: 04
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:dcd0-dcdf irq:10
        *-usb:1
             description: USB Controller
             product: 82801BA/BAM USB (Hub #2)
             vendor: Intel Corporation
             physical id: 1f.4
             bus info: pci@00:1f.4
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: ioport:ff60-ff7f irq:18
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.20-16-generic uhci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s

familjen@svart:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3)
02:07.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
02:08.0 Communication controller: Conexant HSF 56k Data/Fax/Voice/Spkp Modem (rev 01)
02:09.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)

familjen@svart:~$ xine-check
Please be patient, this script may take a while to run...
[ good ] you're using Linux, doing specific tests
[ good ] looks like you have a /proc filesystem mounted.
[ good ] You seem to have a reasonable kernel version (2.6.20-16-generic)
[ good ] intel compatible processor, checking MTRR support
[ hint ] you have MTRR support but it's unused.
         It seems like your X server didn't set any MTRR ranges for the
         graphics card. Maybe upgrading your X server helps...
         You don't have a PCI graphics card, do you? AFAIK, MTRR only
         helps with AGP cards.
         press <enter> to continue...

[ hint ] multiple xine executables found
         I have found multiple xine executables on your machine:
         /usr/bin/xine
         /usr/X11R6/bin/xine
         xine is the main player as installed by the xine-ui package.
         You should probably uninstall the instances you don't use...
         press <enter> to continue...

[ good ] /usr/bin/xine is in your PATH
[ good ] found /usr/bin/xine-config in your PATH
[ good ] plugin directory /usr/lib/xine/plugins/1.1.4 exists.
[ good ] found unknown plugin: xineplug_flac.so
[ good ] found input plugins
[ good ] found demux plugins
[ good ] found decoder plugins
[ good ] found video_out plugins
[ good ] found audio_out plugins
[ good ] skin directory /usr/share/xine/skins exists.
[ good ] found logo in /usr/share/xine/skins
[ good ] I even found some skins.
[ good ] /dev/cdrom points to /dev/scd1
[ good ] /dev/dvd points to /dev/scd1
[ hint ] Your DVD drive seems not to be attached via ATAPI.
         This might be due to the use of an ide-scsi emulation.
         If you really have a SCSI DVD drive, your SCSI controller is likely
         to do perfect DMA, so there's no reason to worry about this.
         However, if you're using ide-scsi, there is a chance that DMA is
         disabled for the DVD drive. Moreover, I don't know how to enable
         DMA in that case, so you probably have to live with some performance
         loss. (FIXME: check for /proc/ide, provide solution)
         press <enter> to continue...

[ good ] found xvinfo: X-Video Extension version 2.2
[ good ] your Xv extension supports YV12 overlays (improves MPEG performance)
[ good ] your Xv extension supports YUY2 overlays
[ good ] Xv ports:  YUY2 YV12 UYVY I420 YUY2 YV12 UYVY I420

xorg.conf:
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 85.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV25 [GeForce4 Ti 4600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV25 [GeForce4 Ti 4600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "true"
    Option         "AddARGBGLXVisuals" "true"
    Option         "RenderAccel" "true"
    Option         "DisableGLXRootClipping" "true"
    Option         "NoLogo" "true"
    Option	   "RandRRotation" "on" 
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Probably a bunch of stuff in that output is irrelevant. ;)

Again, this is a 640x480 video; I can't imagine how performance would be with a 1280x960 one.


Any ideas? Any help would be greatly appreciated.

---

### Post by stmiller on 2007-08-02
Hm, your machine should have no problem playing this back. Could be the container. I just saw this:

[http://forum.videolan.org/viewtopic.php?f=7&t=38225](http://forum.videolan.org/viewtopic.php?f=7&t=38225)

---

### Post by Zorael on 2007-08-02
Would that account for the issues I experience in the other players?

---

### Post by Zorael on 2007-08-05
Okay, sound issues were fixed by switching audio output device to OSS. Not the solution I'd have preferred, but at least I *can* watch my video files in *some* players. The main issue (video performance under some players) remains.

I'm still on the lookout for a less workaround-ish way of dealing with this though, so... shameless bumpity bump.

---

### Post by -::Bas::- on 2007-08-21
I had that same problem, though even having a faster machine (Athlon X2 3800+, 2GB ram, and more cool crap). In Wondiws that problem doensn't exist.

Somewhere on this forum I found that enabling XVideo in VLC, should fix this problem. And it actually does!

Findthe setting through:
Settings ->
Preferences ->
Video->
Output Modules ->
Xvideo.

That's it.

Still freezes while scrolling through the film, but simple beginning till end playback is fixed now.

---

