---
title: "[SOLVED] Mythbuntu 7.10 / PVR-350 / TV-Out for X"
date: 2008-03-12
forum: Mythbuntu
---

### Post by CanMan23 on 2008-03-12
Hi all,
after a couple of days without any progress, I hope some in this forum can point me into the right direction. Here's the story: Was running MythTV on an AOpen XCube (SuSE based) with a PVR-350 card (actually had to mod the cover of the XCube to fit the card in...). Working well for about 2 years. Now decided to have a dedicated backend (new PC with 2 PVR-150) and use the existing XCube as frontend only. Selected Mythbuntu to be run on both systems.
This is how far I got
[LIST]
[*] Backend is working fine.
[*] Frontend is working fine as well except for TV-Out
[/LIST]
To be more specific: TV-Out for watching movies / TV is working.
However I can not get TV-Out for the xserver to work. 
I remember from the old set-up, that there was some trouble with the internal graphics adapter. The xorg.conf had to be different if a monitor was connected or nor. Very clever as I'm I did **not** back-up the original xorg.conf used :(

The error message I'm fighting with (for a long time now) is:
(**WW) ivtv: No matching Device section for instance (BusID PCI:2:0:0) found**
And the screen get's removed from the X config....

I basically followed the instructions in: [https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)
and try to have a dual monitor set-up.

All the details:
**cat /proc/fb**
```
0 cx23415 TV out
```

**xorg.conf -- std. xorg.conf + PVR-350 added manually**
```

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
        Option          "XkbVariant"    "nodeadkeys"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
        Screen          0
EndSection

Section "Monitor"
        Identifier      "Samsung SyncMaster 750p"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Monitor Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Samsung SyncMaster 750p"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1024x768" "800x600"
        EndSubSection
EndSection


####################### PVR-350 TV-OUT PAL CONFIG #######################
Section "Module"
        Load "dbe"
        Load "v4l"
        Load "extmod"
#       Load "type1"    # not available
        Load "freetype"
EndSection

Section "Device"
        Identifier "PVR-350"
        Driver "ivtv"
        Option "fbdev" "/dev/fb0"
        Option "ivtv" "/dev/fb0"
        Option "TVStandard" "PAL"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"
        BusID "PCI:2:0:0"
        Screen 1
EndSection

Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        Mode "720x576"
            DotClock 42.6
            HTimings 720 760 832 944
            VTimings 576 577 580 602
            Flags "-HSync" "-VSync"
        EndMode
EndSection

# Our PVR-350 Driver entry
Section "Screen"
        Identifier "TV Screen"
        Device "PVR-350"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
              Depth 24
              FbBpp 32
              Modes "720x576"
        EndSubsection
EndSection

####################### PVR-350 TV-OUT PAL CONFIG #######################


Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "Monitor Screen"
        Screen 1        "TV Screen" RightOf "Monitor Screen" # You can also use LeftOf
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

**lspci output, as the error message indicates some issue with the BusID**
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
02:00.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:09.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
```
Note: 00:02.0 is the internal graphics card and 02:00.0 is the PVR-350

**/var/log/message (IVTV init parts only)**
```
Mar 12 21:15:38 TVFrontend kernel: [   48.147820] ivtv:  ==================== START INIT IVTV ====================
Mar 12 21:15:38 TVFrontend kernel: [   48.147824] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
Mar 12 21:15:38 TVFrontend kernel: [   48.147888] ivtv0: Autodetected Hauppauge card (cx23415 based)
Mar 12 21:15:38 TVFrontend kernel: [   48.147901] ivtv0 info: base addr: 0xe0000000
Mar 12 21:15:38 TVFrontend kernel: [   48.147902] ivtv0 info: Enabling pci device
Mar 12 21:15:38 TVFrontend kernel: [   48.147921] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Mar 12 21:15:38 TVFrontend kernel: [   48.147928] ivtv0 info: Bus Mastering Enabled.
Mar 12 21:15:38 TVFrontend kernel: [   48.147932] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Mar 12 21:15:38 TVFrontend kernel: [   48.147938] ivtv0 info: 2051 (rev 1) at 02:00.0, irq: 18, latency: 64, memory: 0xe0000000
Mar 12 21:15:38 TVFrontend kernel: [   48.147941] ivtv0 info: attempting ioremap at 0xe0000000 len 0x00800000
Mar 12 21:15:38 TVFrontend kernel: [   48.147963] ivtv0 info: attempting ioremap at 0xe1000000 len 0x00800000
Mar 12 21:15:38 TVFrontend kernel: [   48.147984] ivtv0 info: attempting ioremap at 0xe2000000 len 0x00010000
Mar 12 21:15:38 TVFrontend kernel: [   48.147987] ivtv0 info: Preparing for firmware halt.
Mar 12 21:15:38 TVFrontend kernel: [   48.152458] ivtv0 info: Stopping VDM
Mar 12 21:15:38 TVFrontend kernel: [   48.152460] ivtv0 info: Stopping AO
Mar 12 21:15:38 TVFrontend kernel: [   48.152462] ivtv0 info: pinging (?) APU
Mar 12 21:15:38 TVFrontend kernel: [   48.152464] ivtv0 info: Stopping VPU
Mar 12 21:15:38 TVFrontend kernel: [   48.152465] ivtv0 info: Resetting Hw Blocks
Mar 12 21:15:38 TVFrontend kernel: [   48.152467] ivtv0 info: Stopping SPU
Mar 12 21:15:38 TVFrontend kernel: [   48.160444] ivtv0 info: init Encoder SDRAM pre-charge
Mar 12 21:15:38 TVFrontend kernel: [   48.160448] ivtv0 info: init Encoder SDRAM refresh to 1us
Mar 12 21:15:38 TVFrontend kernel: [   48.160451] ivtv0 info: init Decoder SDRAM pre-charge
Mar 12 21:15:38 TVFrontend kernel: [   48.160453] ivtv0 info: init Decoder SDRAM refresh to 1us
Mar 12 21:15:38 TVFrontend kernel: [   48.160455] ivtv0 info: Sleeping for 600ms (600 recommended)
Mar 12 21:15:38 TVFrontend kernel: [   48.759508] ivtv0 info: Loading encoder image
Mar 12 21:15:38 TVFrontend kernel: [   48.797906] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3626953224 bytes)
Mar 12 21:15:38 TVFrontend kernel: [   48.797910] ivtv0 info: Loading decoder image
Mar 12 21:15:38 TVFrontend kernel: [   48.810121] ivtv0: loaded v4l-cx2341x-dec.fw firmware (3626953232 bytes)
Mar 12 21:15:38 TVFrontend kernel: [   49.023142] ivtv0 info: Getting firmware version..
Mar 12 21:15:38 TVFrontend kernel: [   49.031101] ivtv0: Encoder revision: 0x02050032
Mar 12 21:15:38 TVFrontend kernel: [   49.031103] ivtv0: Recommended firmware version is 0x02060039.
Mar 12 21:15:38 TVFrontend kernel: [   49.039103] ivtv0: Decoder revision: 0x02020023
Mar 12 21:15:38 TVFrontend kernel: [   49.039169] ivtv0 info: activating i2c...
Mar 12 21:15:38 TVFrontend kernel: [   49.039703] ivtv0 info: Active card count: 1.
Mar 12 21:15:38 TVFrontend kernel: [   49.052195] ivtv0 info: Loaded module tveeprom
Mar 12 21:15:38 TVFrontend kernel: [   49.104064] tveeprom 0-0050: Hauppauge model 48139, rev K257, serial# 2952158
Mar 12 21:15:38 TVFrontend kernel: [   49.104067] tveeprom 0-0050: tuner model is Philips FM1216 ME MK3 (idx 57, type 38)
Mar 12 21:15:38 TVFrontend kernel: [   49.104070] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) (eeprom 0x74)
Mar 12 21:15:38 TVFrontend kernel: [   49.104073] tveeprom 0-0050: audio processor is MSP4418 (idx 25)
Mar 12 21:15:38 TVFrontend kernel: [   49.104075] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
Mar 12 21:15:38 TVFrontend kernel: [   49.104078] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
Mar 12 21:15:38 TVFrontend kernel: [   49.104081] ivtv0: Autodetected Hauppauge WinTV PVR-350
Mar 12 21:15:38 TVFrontend kernel: [   49.104083] ivtv0 info: PAL tuner detected
Mar 12 21:15:38 TVFrontend kernel: [   49.131281] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
Mar 12 21:15:38 TVFrontend kernel: [   49.131300] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
Mar 12 21:15:38 TVFrontend kernel: [   49.134448] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Mar 12 21:15:38 TVFrontend kernel: [   49.148090] ivtv0 info: Loaded module tuner
Mar 12 21:15:38 TVFrontend kernel: [   49.197268] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
Mar 12 21:15:38 TVFrontend kernel: [   49.321301] ivtv0 info: Loaded module saa7115
Mar 12 21:15:38 TVFrontend kernel: [   49.370993] saa7127 0-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
Mar 12 21:15:38 TVFrontend kernel: [   49.372918] ivtv0 info: Loaded module saa7127
Mar 12 21:15:38 TVFrontend kernel: [   49.395173] msp3400 0-0040: MSP4418G-B3 found @ 0x80 (ivtv i2c driver #0)
Mar 12 21:15:38 TVFrontend kernel: [   49.395176] msp3400 0-0040: MSP4418G-B3 supports nicam and radio, mode is autodetect and autoselect
Mar 12 21:15:38 TVFrontend kernel: [   49.395249] ivtv0 info: Loaded module msp3400
Mar 12 21:15:38 TVFrontend kernel: [   49.395258] tuner 0-0061: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
Mar 12 21:15:38 TVFrontend kernel: [   49.395263] ivtv0 info: Changing input from 1 to 0
Mar 12 21:15:38 TVFrontend kernel: [   49.398873] ivtv0 info: Mute
Mar 12 21:15:38 TVFrontend kernel: [   49.535360] ivtv0 info: Unmute
Mar 12 21:15:38 TVFrontend kernel: [   49.538971] ivtv0 info: Mute
Mar 12 21:15:38 TVFrontend kernel: [   49.538973] ivtv0 info: v4l2 ioctl: set frequency 6400
Mar 12 21:15:38 TVFrontend kernel: [   49.669704] ivtv0 info: Unmute
Mar 12 21:15:38 TVFrontend kernel: [   49.669754] ivtv0: Registered device video0 for encoder MPEG (4 MB)
Mar 12 21:15:38 TVFrontend kernel: [   49.669757] ivtv0 info: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096kB total)
Mar 12 21:15:38 TVFrontend kernel: [   49.669923] ivtv0: Registered device video32 for encoder YUV (2 MB)
Mar 12 21:15:38 TVFrontend kernel: [   49.669926] ivtv0 info: Allocate DMA encoder YUV stream: 161 x 12960 buffers (2037kB total)
Mar 12 21:15:38 TVFrontend kernel: [   49.670071] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
Mar 12 21:15:38 TVFrontend kernel: [   49.670074] ivtv0 info: Allocate DMA encoder VBI stream: 40 x 26208 buffers (1023kB total)
Mar 12 21:15:38 TVFrontend kernel: [   49.670135] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
Mar 12 21:15:38 TVFrontend kernel: [   49.670138] ivtv0 info: Allocate DMA encoder PCM audio stream: 227 x 4608 buffers (1021kB total)
Mar 12 21:15:38 TVFrontend kernel: [   49.670311] ivtv0: Registered device radio0 for encoder radio
Mar 12 21:15:38 TVFrontend kernel: [   49.670336] ivtv0: Registered device video16 for decoder MPEG (1 MB)
Mar 12 21:15:38 TVFrontend kernel: [   49.670339] ivtv0 info: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1024kB total)
Mar 12 21:15:38 TVFrontend kernel: [   49.670389] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
Mar 12 21:15:38 TVFrontend kernel: [   49.670392] ivtv0 info: Allocate decoder VBI stream: 455 x 2304 buffers (1023kB total)
Mar 12 21:15:38 TVFrontend kernel: [   49.670618] ivtv0: Registered device vbi16 for decoder VOUT
Mar 12 21:15:38 TVFrontend kernel: [   49.670644] ivtv0: Registered device video48 for decoder YUV (1 MB)
Mar 12 21:15:38 TVFrontend kernel: [   49.670647] ivtv0 info: Allocate DMA decoder YUV stream: 20 x 51840 buffers (1012kB total)
Mar 12 21:15:38 TVFrontend kernel: [   49.719994] ivtv0: loaded v4l-cx2341x-init.mpg firmware (3626954456 bytes)
Mar 12 21:15:38 TVFrontend kernel: [   49.825882] ivtv0 info: Switching standard to f.
Mar 12 21:15:38 TVFrontend kernel: [   49.929752] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
Mar 12 21:15:38 TVFrontend kernel: [   49.929772] ivtv:  ====================  END INIT IVTV  ====================
Mar 12 21:15:38 TVFrontend kernel: [   49.929866] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
Mar 12 21:15:38 TVFrontend kernel: [   50.257184] intel8x0_measure_ac97_clock: measured 52750 usecs
Mar 12 21:15:38 TVFrontend kernel: [   50.257187] intel8x0: clocking to 48000
Mar 12 21:15:38 TVFrontend kernel: [   51.239921] lp0: using parport0 (interrupt-driven).
Mar 12 21:15:38 TVFrontend kernel: [   51.315583] ivtv0-fb: Framebuffer at 0xe1510000, mapped to 0xdf990000, size 1665k
Mar 12 21:15:38 TVFrontend kernel: [   51.388304] ivtv0-fb info: ivtvfb_check_var
Mar 12 21:15:38 TVFrontend kernel: [   51.388312] ivtv0-fb info: ivtvfb_check_var - Parameters validated
Mar 12 21:15:38 TVFrontend kernel: [   51.388314] ivtv0-fb: === Validated display mode  ===
Mar 12 21:15:38 TVFrontend kernel: [   51.388317] ivtv0-fb: Display size 720x576 (720x576 Virtual) @ 32bpp
Mar 12 21:15:38 TVFrontend kernel: [   51.388319] ivtv0-fb: Display position 1,1
Mar 12 21:15:38 TVFrontend kernel: [   51.388321] ivtv0-fb: Display filter : on
Mar 12 21:15:38 TVFrontend kernel: [   51.388322] ivtv0-fb: Color space : RGB
Mar 12 21:15:38 TVFrontend kernel: [   51.388324] ivtv0-fb info: ivtvfb_get_fix
Mar 12 21:15:38 TVFrontend kernel: [   51.389410] ivtv0-fb info: ivtvfb_set_par
Mar 12 21:15:38 TVFrontend kernel: [   51.389413] ivtv0-fb info: ivtvfb_set_var
Mar 12 21:15:38 TVFrontend kernel: [   51.419473] ivtv0-fb: === Display mode change ===
Mar 12 21:15:38 TVFrontend kernel: [   51.419476] ivtv0-fb: Display size 720x576 (720x576 Virtual) @ 32bpp
Mar 12 21:15:38 TVFrontend kernel: [   51.419478] ivtv0-fb: Display position 1,1
Mar 12 21:15:38 TVFrontend kernel: [   51.419479] ivtv0-fb: Display filter : on
Mar 12 21:15:38 TVFrontend kernel: [   51.419481] ivtv0-fb: Color space : RGB
Mar 12 21:15:38 TVFrontend kernel: [   51.419483] ivtv0-fb info: ivtvfb_get_fix
Mar 12 21:15:38 TVFrontend kernel: [   51.419484] ivtv0-fb info: Set blanking mode : 0
Mar 12 21:15:38 TVFrontend kernel: [   51.427444] ivtv0-fb: Running in compatibility mode. Display resize & mode change disabled
Mar 12 21:15:38 TVFrontend kernel: [   51.427447] ivtv0-fb: Framebuffer registered on ivtv card id 0

```

**And finally the Xorg.0.log**
```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux TVFrontend 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 12 21:47:11 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Monitor Screen" (0)
(**) |   |-->Monitor "Samsung SyncMaster 750p"
(**) |   |-->Device "Intel Corporation 82852/855GM Integrated Graphics Device"
(**) |-->Screen "TV Screen" (1)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "PVR-350"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3580 card 8086,3580 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 8086,3584 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 8086,3585 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:01:0: chip 8086,3581 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,3582 card 8086,3582 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3582 card 8086,3582 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,24c2 rev 03 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,24c2 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,24c2 rev 03 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card a0a0,053f rev 03 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev 83 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24cc card 0000,0000 rev 03 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24ca card 8086,24c2 rev 03 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 8086,24c2 rev 03 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card a0a0,053b rev 03 class 04,01,00 hdr 00
(II) PCI: 02:00:0: chip 4444,0803 card 0070,4000 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:07:0: chip 10ec,8169 card a0a0,0542 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:09:0: chip 11c1,5811 card 0001,0001 rev 61 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/27, 0xe6000000/19, I/O @ 0xe300/3
(--) PCI: (0:2:1) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0x20000000/27, 0x28000000/19
(--) PCI: (2:0:0) unknown vendor (0x4444) unknown chipset (0x0803) rev 1, Mem @ 0xe0000000/26
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xd7ffffff to 0xcfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xe5000000 - 0xe5000fff (0x1000) MX[B]
        [1] -1  0       0xe5001000 - 0xe50010ff (0x100) MX[B]
        [2] -1  0       0xe6082000 - 0xe60820ff (0x100) MX[B]
        [3] -1  0       0xe6081000 - 0xe60811ff (0x200) MX[B]
        [4] -1  0       0x28080000 - 0x280803ff (0x400) MX[B]
        [5] -1  0       0xe6080000 - 0xe60803ff (0x400) MX[B]
        [6] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [7] -1  0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [8] -1  0       0xe6000000 - 0xe607ffff (0x80000) MX[B](B)
        [9] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [10] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [11] -1 0       0x0000e600 - 0x0000e63f (0x40) IX[B]
        [12] -1 0       0x0000e500 - 0x0000e5ff (0x100) IX[B]
        [13] -1 0       0x00005000 - 0x0000501f (0x20) IX[B]
        [14] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [15] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [16] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [19] -1 0       0x0000e200 - 0x0000e21f (0x20) IX[B]
        [20] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [22] -1 0       0x0000e300 - 0x0000e307 (0x8) IX[B](B)
(II) Inactive PCI resource ranges:
        [0] -1  0       0x28000000 - 0x2807ffff (0x80000) MX[B](B)
        [1] -1  0       0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe5000000 - 0xe5000fff (0x1000) MX[B]
        [1] -1  0       0xe5001000 - 0xe50010ff (0x100) MX[B]
        [2] -1  0       0xe6082000 - 0xe60820ff (0x100) MX[B]
        [3] -1  0       0xe6081000 - 0xe60811ff (0x200) MX[B]
        [4] -1  0       0x28080000 - 0x280803ff (0x400) MX[B]
        [5] -1  0       0xe6080000 - 0xe60803ff (0x400) MX[B]
        [6] -1  0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [7] -1  0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [8] -1  0       0xe6000000 - 0xe607ffff (0x80000) MX[B](B)
        [9] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [10] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [11] -1 0       0x0000e600 - 0x0000e63f (0x40) IX[B]
        [12] -1 0       0x0000e500 - 0x0000e5ff (0x100) IX[B]
        [13] -1 0       0x00005000 - 0x0000501f (0x20) IX[B]
        [14] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [15] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [16] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [19] -1 0       0x0000e200 - 0x0000e21f (0x20) IX[B]
        [20] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [21] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [22] -1 0       0x0000e300 - 0x0000e307 (0x8) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
        [0] -1  0       0x28000000 - 0x2807ffff (0x80000) MX[B](B)
        [1] -1  0       0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x27ffffff (0x27f00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x27ffffff (0x27f00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe5000000 - 0xe5000fff (0x1000) MX[B]
        [5] -1  0       0xe5001000 - 0xe50010ff (0x100) MX[B]
        [6] -1  0       0xe6082000 - 0xe60820ff (0x100) MX[B]
        [7] -1  0       0xe6081000 - 0xe60811ff (0x200) MX[B]
        [8] -1  0       0x28080000 - 0x280803ff (0x400) MX[B]
        [9] -1  0       0xe6080000 - 0xe60803ff (0x400) MX[B]
        [10] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xe6000000 - 0xe607ffff (0x80000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] -1 0       0x28000000 - 0x2807ffff (0x80000) MX[B](B)
        [15] -1 0       0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [19] -1 0       0x0000e600 - 0x0000e63f (0x40) IX[B]
        [20] -1 0       0x0000e500 - 0x0000e5ff (0x100) IX[B]
        [21] -1 0       0x00005000 - 0x0000501f (0x20) IX[B]
        [22] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [25] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [27] -1 0       0x0000e200 - 0x0000e21f (0x20) IX[B]
        [28] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [29] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [30] -1 0       0x0000e300 - 0x0000e307 (0x8) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.1.1
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.3.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 2.1.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "ivtv"
(II) Loading /usr/lib/xorg/modules/drivers//ivtv_drv.so
(II) Module ivtv: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) v4l driver for Video4Linux
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33
(II) IVTV: driver for ivtv framebuffer: PVR-350
(II) Primary Device is: PCI 00:02:0
(--) Chipset 852GM/855GM found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x27ffffff (0x27f00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe5000000 - 0xe5000fff (0x1000) MX[B]
        [5] -1  0       0xe5001000 - 0xe50010ff (0x100) MX[B]
        [6] -1  0       0xe6082000 - 0xe60820ff (0x100) MX[B]
        [7] -1  0       0xe6081000 - 0xe60811ff (0x200) MX[B]
        [8] -1  0       0x28080000 - 0x280803ff (0x400) MX[B]
        [9] -1  0       0xe6080000 - 0xe60803ff (0x400) MX[B]
        [10] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xe6000000 - 0xe607ffff (0x80000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] -1 0       0x28000000 - 0x2807ffff (0x80000) MX[B](B)
        [15] -1 0       0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [19] -1 0       0x0000e600 - 0x0000e63f (0x40) IX[B]
        [20] -1 0       0x0000e500 - 0x0000e5ff (0x100) IX[B]
        [21] -1 0       0x00005000 - 0x0000501f (0x20) IX[B]
        [22] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [25] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [27] -1 0       0x0000e200 - 0x0000e21f (0x20) IX[B]
        [28] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [29] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [30] -1 0       0x0000e300 - 0x0000e307 (0x8) IX[B](B)
(WW) ivtv: No matching Device section for instance (BusID PCI:2:0:0) found
(--) Chipset PVR-350 found
(II) IVTV(1): using /dev/fb0
(EE) Screen 1 deleted because of no matching config section.
(II) UnloadModule: "ivtv"
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x27ffffff (0x27f00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe5000000 - 0xe5000fff (0x1000) MX[B]
        [5] -1  0       0xe5001000 - 0xe50010ff (0x100) MX[B]
        [6] -1  0       0xe6082000 - 0xe60820ff (0x100) MX[B]
        [7] -1  0       0xe6081000 - 0xe60811ff (0x200) MX[B]
        [8] -1  0       0x28080000 - 0x280803ff (0x400) MX[B]
        [9] -1  0       0xe6080000 - 0xe60803ff (0x400) MX[B]
        [10] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [11] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [12] -1 0       0xe6000000 - 0xe607ffff (0x80000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] -1 0       0x28000000 - 0x2807ffff (0x80000) MX[B](B)
        [15] -1 0       0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
        [16] 1  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [17] 1  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [18] 1  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [22] -1 0       0x0000e600 - 0x0000e63f (0x40) IX[B]
        [23] -1 0       0x0000e500 - 0x0000e5ff (0x100) IX[B]
        [24] -1 0       0x00005000 - 0x0000501f (0x20) IX[B]
        [25] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [27] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [28] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [30] -1 0       0x0000e200 - 0x0000e21f (0x20) IX[B]
        [31] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [32] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [33] -1 0       0x0000e300 - 0x0000e307 (0x8) IX[B](B)
        [34] 1  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [35] 1  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 855GME
(--) intel(0): Chipset: "852GM/855GM"
(--) intel(0): Linear framebuffer at 0xD8000000
(--) intel(0): IO registers at addr 0xE6000000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
        for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) intel(0): Output VGA using monitor section Samsung SyncMaster 750p
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 32576 kB
(II) intel(0): VESA VBE OEM: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)852GM/852GME/855GM/855GME Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(EE) intel(0): detecting sil164
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(EE) intel(0): Unable to read from DVOI2C_E Slave 236.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(EE) intel(0): ivch: Unable to read register 0x00 from DVOI2C_B:04.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): detecting tfp410
(EE) intel(0): Unable to read from DVOI2C_E Slave 112.
(EE) intel(0): tfp410 not detected got VID FFFFFFFF: from DVOI2C_E Slave 112.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x960" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1280x800" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x768" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1152x864" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) intel(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.1   65.14  1024 1048 1184 1344  768 771 777 806 (48.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output LVDS using initial mode 1024x768
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 32636 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(++) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x70008 (PIPEACONF) changed from 0x80000000 to 0x00000000
(WW) intel(0): PIPEACONF before: enabled, single-wide
(WW) intel(0): PIPEACONF after: disabled, single-wide
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 1   0       0xe6000000 - 0xe607ffff (0x80000) MS[B]
        [1] 1   0       0xd8000000 - 0xdfffffff (0x8000000) MS[B]
        [2] -1  0       0x00100000 - 0x27ffffff (0x27f00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xe5000000 - 0xe5000fff (0x1000) MX[B]
        [7] -1  0       0xe5001000 - 0xe50010ff (0x100) MX[B]
        [8] -1  0       0xe6082000 - 0xe60820ff (0x100) MX[B]
        [9] -1  0       0xe6081000 - 0xe60811ff (0x200) MX[B]
        [10] -1 0       0x28080000 - 0x280803ff (0x400) MX[B]
        [11] -1 0       0xe6080000 - 0xe60803ff (0x400) MX[B]
        [12] -1 0       0xd0000000 - 0xcfffffff (0x0) MX[B]O
        [13] -1 0       0xe0000000 - 0xe3ffffff (0x4000000) MX[B](B)
        [14] -1 0       0xe6000000 - 0xe607ffff (0x80000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [16] -1 0       0x28000000 - 0x2807ffff (0x80000) MX[B](B)
        [17] -1 0       0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
        [18] 1  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [19] 1  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [20] 1  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [21] 1  0       0x0000e300 - 0x0000e307 (0x8) IS[B]
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [23] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [24] -1 0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [25] -1 0       0x0000e600 - 0x0000e63f (0x40) IX[B]
        [26] -1 0       0x0000e500 - 0x0000e5ff (0x100) IX[B]
        [27] -1 0       0x00005000 - 0x0000501f (0x20) IX[B]
        [28] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [31] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [32] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [33] -1 0       0x0000e200 - 0x0000e21f (0x20) IX[B]
        [34] -1 0       0x0000e100 - 0x0000e11f (0x20) IX[B]
        [35] -1 0       0x0000e000 - 0x0000e01f (0x20) IX[B]
        [36] -1 0       0x0000e300 - 0x0000e307 (0x8) IX[B](B)
        [37] 1  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [38] 1  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 104448 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 417788 kB available
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers and
               large DRI memory manager reservation:
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
        (Cannot allocate memory)
(II) intel(0): Allocating 5112 scanlines for pixmap cache
(II) intel(0): Success.
(II) intel(0): Memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00030000-0x01827fff: front buffer (24544 kB)
(II) intel(0): 0x01828000-0x01837fff: xaa scratch (64 kB)
(II) intel(0): 0x01fdf000:            end of stolen memory
(II) intel(0): 0x01fdf000-0x01fdffff: Core cursor (4 kB, 0x        14c52000 physical)
(II) intel(0): 0x01fe0000-0x01fe3fff: ARGB cursor (16 kB, 0x        14c8c000 physical)
(II) intel(0): 0x01fe4000-0x01fe4fff: Core cursor (4 kB, 0x        14c55000 physical)
(II) intel(0): 0x01fe5000-0x01fe8fff: ARGB cursor (16 kB, 0x        14c90000 physical)
(II) intel(0): 0x01fe9000-0x01fe9fff: overlay registers (4 kB, 0x        14c5f000 physical)
(II) intel(0): 0x02000000-0x023fffff: back buffer (4096 kB)
(II) intel(0): 0x02400000-0x027fffff: depth buffer (4096 kB)
(II) intel(0): 0x02800000-0x047fffff: DRI memory manager (32768 kB)
(II) intel(0): 0x04800000-0x067fffff: textures (32768 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): front buffer is not tiled
(II) intel(0): back buffer is tiled
(II) intel(0): depth buffer is tiled
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): [drm] loaded kernel module for "i915" driver
(II) intel(0): [drm] DRM interface version 1.3
(II) intel(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) intel(0): [drm] added 8192 byte SAREA at 0xdfcd5000
(II) intel(0): [drm] mapped SAREA 0xdfcd5000 to 0xb7b2f000
(II) intel(0): [drm] framebuffer handle = 0xd8030000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): Unable to use TTM-based memory manager with DRM version 1.6
(II) intel(0): [drm] Registers = 0xe6000000
(II) intel(0): [drm] ring buffer = 0xd8000000
(II) intel(0): [drm] init sarea width,height = 1024 x 1024 (pitch 1024)
(II) intel(0): [drm] Mapping front buffer
(II) intel(0): [drm] Front Buffer = 0x2b006000
(II) intel(0): [drm] Back Buffer = 0xda000000
(II) intel(0): [drm] Depth Buffer = 0xda400000
(II) intel(0): [drm] textures = 0xdc800000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd8000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                26 256x256 slots
                11 512x512 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01fdf000 (pgoffset 8159)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01fe0000 (pgoffset 8160)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01fe4000 (pgoffset 8164)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01fe5000 (pgoffset 8165)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x01fe9000 (pgoffset 8169)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x02400000 (pgoffset 9216)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x04800000 (pgoffset 18432)
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(**) Option "dpms"
(**) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [DRI] installation complete
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): direct rendering: Enabled
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) intel(0): Option "UseFBDev" is not used
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(EE) AIGLX error: dlopen of /usr/lib/dri/i915_dri.so failed (/usr/lib/dri/i915_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) intel(0): Setting screen physical size to 260 x 195
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbVariant" "nodeadkeys"
(**) Generic Keyboard: XkbVariant: "nodeadkeys"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x800" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.1   65.14  1024 1048 1184 1344  768 771 777 806 (48.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x800" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.1   65.14  1024 1048 1184 1344  768 771 777 806 (48.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) intel(0): Output VGA disconnected
(II) intel(0): EDID for output VGA
(II) intel(0): Output LVDS connected
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID for output LVDS
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x960" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "1280x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1280x800" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x768" (width too large for virtual size)
(II) intel(0): Not using default mode "1152x864" (width too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1440x900" (width too large for virtual size)
(II) intel(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) intel(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) intel(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) intel(0): Printing probed modes for output LVDS
(II) intel(0): Modeline "1024x768"x60.1   65.14  1024 1048 1184 1344  768 771 777 806 (48.5 kHz)
(II) intel(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) intel(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) intel(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
  
```

While trying to resolve the X via TV-Out I have already tried a lot of things. They all did not work.
[LIST]
[*]Started with a single monitor xorg.conf, as normally only the TV is connected
[*]Ran into multiple problems, mainly complains about low resolution (automatically a fail safe xorg.conf overwrites my custom one for TV-Out)
[*]There is no difference if BusID "PCI:2:0:0" or BusID "2:0:0" is used - some resources mention a difference
[/LIST]

Any suggestion / help would be great. Many thanks in advance.

---

### Post by CanMan23 on 2008-03-15
Found the issue myself -- to long hours of installing / testing and not paying attention :)

Issue was a mismatch in the the resolution. For references the working xorg.conf (**PAL Version**) is shown below.

Please note that another major difference is that I reverted to a ONE SCREEN approach. So the xorg.conf below is:
All output to one screen - X, TV, Recordings ... whatever

```
# My xorg.conf für PVR-350 TV-Out....
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

# Specific modules needed *this is important.*
Section "Module"
        Load "dbe"
        Load "v4l"
        Load "extmod"
        Load "type1"
        Load "freetype"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier "PVR350"
        # the driver we installed - in Gutsy, this is NOT "ivtvdev".
        Driver "ivtv"
        # frame buffer we found above
        Option "fbdev" "/dev/fb0"
        Option "ivtv" "/dev/fb0"
        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        #not needed? Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:2:0:0"
        Screen 0
EndSection

#TV-Settings (PAL)
Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        Mode "720x576"
            DotClock 42.6
            HTimings 720 760 832 944
            VTimings 576 577 580 602
            Flags "-HSync" "-VSync"
        EndMode
EndSection
#for pal users more settings: http://www.mythtv.org/wiki/index.php/XV_on_PVR-350#PAL

# Our PVR-350 Driver entry
Section "Screen"
        Identifier "SCART"
        Device "PVR350"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
              Depth 24
              FbBpp 32
              Modes "720x576"
        EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "SCART"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Group   0
        Mode    0666 # Not specifically needed as far as I know.
                     # I think it's specific to my computer's hardware
                     # That said all my ubuntu boxes have this line.
EndSection
```

---

