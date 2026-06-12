---
title: "HOWTO: Get X Running on pvr-350 Tv-Out"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by trubblemaker on 2006-12-06
I've posted a how to on the wiki, get X Running on pvr-350:
[ Fiesty Howto ](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out)
[  Edgy Howto ]("https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out?action=show")

 I believe that all good wiki's need a forum so you can post questions on this forum...

---

### Post by superm1 on 2006-12-06
Trubblemaker, 

This looks great, and i'm glad to see it on the wiki.  A minor note, since it's an edgy howto - be sure to link to the edgy version of the Ivtv hwoto.  There are some minor differences with how dapper and edgy have to handle ivtv.

---

### Post by superm1 on 2006-12-06
Also, I've linked you into the IVTV Howto for edgy :)

---

### Post by trubblemaker on 2006-12-06
added both links (dapper and edgy).  Thanks for the tip.

---

### Post by dawson64 on 2006-12-07
I used superm1's howto. Here are the notes i took on the order i did things.  It's not totally clear when to go from one page to another...
> 
Install SSH
Install XFS utilities
Setup NTP
Update source list & apply updates

Install Myth TV, x server, fonts, mysql...

CREATE SESSION FOR AUTOMATIC MYTHTV LOGIN

CREATE MYTHTV SCRIPT & SET TO BE EXECUTEABLE

RUN GDMSETUP & CONFIGURE

COPY MYSQL.TXT TO ~/.MYTHTV

RUNNING IVTV SETUP
- install firmware
*** Didn't copy v4l to ivtv firmware (/lib/firmware) yet as firmware fix (from bottom of how to - need to copy enc & dec?)

RUN MYTHTV SETUP
CONTINUE ON TO BACKEND/FRONTEND SETUP - 
- FILL THE DATABASE
- Restart backend

Change X to startup mythtv

Setup PVR per trublemaker's how to



My v4l probelm  (module failed to load) could have been i typed in v4{one} which is wrong. Doh!  

Now i'm back to a fb0 error. Could the FB change by moving the card? (0000:00:0d.0 = 0.13) I'm not able to come up with a fb using either method. Did i miss something? Do i need to initialize it?
> 
***warnings about all the font paths***
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
compiled for 7.1.1, module version = 0.1.1
ABI class: X.Org Video Driver, version 1.0
(--) Chipset PVR-350 found
(EE) open /dev/fb0: No such device
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found  


I ran which i believe initializes things and i think it is going further now but i don't believe this is right.
modprobe ivtv-fb 


Here's my "error"... from Xorg.0.log. as a result.  This causes other errors.

> 
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/X11R6/bin/X(AddScreen+0x1ee) [0x806dd6e]
3: /usr/X11R6/bin/X(InitOutput+0x21e) [0x809f76e]
4: /usr/X11R6/bin/X(main+0x276) [0x806e506]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dc38cc]
6: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 4. Server aborting


---

### Post by trubblemaker on 2006-12-07
lets see the output of ```
lspci 
```again.  Might have changed if you moved the cards location since last install;

---

### Post by jpneely on 2006-12-07
I need to try this

---

### Post by dawson64 on 2006-12-07
```

@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
00:0d.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)

```

---

### Post by dawson64 on 2006-12-07
Here are some other items for debug...

dmesg IVTV section
```

[42949526.970000] ivtv:  ==================== START INIT IVTV ====================
[42949526.970000] ivtv:  version 0.7.0 (tagged release) loading
[42949526.970000] ivtv:  Linux version: 2.6.17-10-server SMP mod_unload 686 REGPARM gcc-4.1
[42949526.970000] ivtv:  In case of problems please include the debug info between
[42949526.970000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[42949526.970000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[42949526.970000] ivtv0: Autodetected Hauppauge WinTV PVR-350 card (cx23415 based)
[42949526.980000] PCI: Enabling device 0000:00:0d.0 (0014 -> 0016)
[42949526.980000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 16 (level, low) -> IRQ 185
[42949526.980000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[42949527.020000] tveeprom 1-0050: Hauppauge model 48132, rev K268, serial# 8618453
[42949527.020000] tveeprom 1-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[42949527.020000] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[42949527.020000] tveeprom 1-0050: audio processor is MSP4448 (idx 27)
[42949527.020000] tveeprom 1-0050: decoder processor is SAA7115 (idx 19)
[42949527.020000] tveeprom 1-0050: has radio, has IR remote
[42949527.100000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[42949527.250000] tda9887 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[42949527.300000] saa7115 1-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[42949527.470000] saa7127 1-0044: saa7129 found @ 0x88 (ivtv i2c driver #0)
[42949527.500000] msp3400 1-0040: MSP4448G-B3 found @ 0x80 (ivtv i2c driver #0)
[42949527.500000] msp3400 1-0040: MSP4448G-B3 supports radio, mode is autodetect and autoselect
[42949527.650000] ts: Compaq touchscreen protocol output
[42949528.280000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[42949528.330000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[42949528.400000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[42949528.630000] ivtv0: Encoder revision: 0x02050032
[42949528.640000] ivtv0: Decoder revision: 0x02020023
[42949528.640000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[42949528.640000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[42949528.640000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[42949528.640000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[42949528.640000] ivtv0: Create encoder radio stream
[42949528.640000] ivtv0: Allocate DMA decoder MPEG stream: 16 x 65536 buffers (1024KB total)
[42949528.640000] ivtv0: Allocate DMA decoder VBI stream: 512 x 2048 buffers (1024KB total)
[42949528.640000] ivtv0: Create decoder VOUT stream
[42949528.640000] ivtv0: Allocate DMA decoder YUV stream: 24 x 43200 buffers (1024KB total)
[42949528.700000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[42949528.810000] tuner 1-0061: type set to 47 (LG NTSC (TAPE series))
[42949528.840000] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[42949528.840000] ivtv:  ====================  END INIT IVTV  ====================

```

here is my current xorg.conf (cut out some extra stuff [kb, mouse, etc])
```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
#       FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
#       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load "dbe"
        Load "v4l"
        Load "extmod"
        Load "type1"
        Load "freetype"
EndSection

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed.
        Driver "ivtvdev"

        Option "fbdev" "/dev/fb0"  # frame buffer we found above
        # Option "ivtv" "/dev/fb1" # for pal users I believe

        # below settings are optional I believe I've seen lots of people with them commented out.
        Option "TVStandard" "NTSC-M" # sorry pal don't know your settings
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        BusID "PCI:0:13:0" # busis we found with lspci converted as shown above

Screen 0
EndSection

Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        DisplaySize 183 122
        Mode "720x480"
        DotClock 34.564
        HTimings 720 752 840 928
        VTimings 480 484 488 504
        Flags "-HSync" "-VSync"
        EndMode

#       Identifier      "Generic Monitor"
#       Option          "DPMS"
#       HorizSync       28-51
#       VertRefresh     43-60
EndSection

Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
        Depth 24
        FbBpp 32
        Modes "720x480"
EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

The latest error message from Xorg.0.log after a reboot
> 
(II) v4l driver for Video4Linux
(II) IVTVDEV_TST: driver for framebuffer: PVR-350
(II) Primary Device is: PCI 00:0d:0
(--) Chipset PVR-350 found
(EE) open /dev/fb0: No such device
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found


---

### Post by majoridiot on 2006-12-07
your lspci shows: 00:0d.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)

but xorg.conf says: BusID "PCI:0:13:0" # busis we found with lspci converted as shown above

should be: BusID "PCI:0:0d:0"

---

### Post by trubblemaker on 2006-12-08
no he's write, you either convert to decimal "PCI:0:13:0" or add hex prefix "PCI:0x0:0x0d:0x0", as xorg.conf only understands decimal.

> EE) open /dev/fb0: No such device
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.


this accoding to xorg means you where all good to go but had no matching config, this means the driver is loading find, but it'd didn't match the settings with the hardware.  Try using the hex addressing maybe that's what I did differently.

---

### Post by majoridiot on 2006-12-08
> **trubblemaker said:**
> ...as xorg.conf only understands decimal.

that's news to me but good to know. :)

---

### Post by dawson64 on 2006-12-08
I tried both & I'm not sure if that is better or worse.
using "PCI:0x0:0x0d:0x0" & "PCI:0:0d:0", I get:

> (II) v4l driver for Video4Linux
(II) IVTVDEV_TST: driver for framebuffer: PVR-350
(II) Primary Device is: PCI 00:0d:0
(WW) ivtvdev: No matching Device section for instance (BusID PCI:0:13:0) found
(EE) No devices detected.

Fatal server error:
no screens found

---

### Post by trubblemaker on 2006-12-08
ok so the howto i read is wrong it only understands hex, I'll fix the howto. You're definately better, it's found the device but somehow can't see the Device section for it.

---

### Post by majoridiot on 2006-12-08
BusID "PCI:0:13:0" is correct...

it couldn't find the framebuffer before.  is this NTSC or PAL?

---

### Post by trubblemaker on 2006-12-08
majoridiot you seem to know what your doing, but i got to say that the, I think he's farther check the [error]("http://xorg.freedesktop.org/wiki/FAQErrorMessages?highlight=%28error%29#head-93b1e0b56f76546d61364f789045e9c745b6cfd4")

I think he's closer, maybe looking at the 
/var/log/Xorg.0.log

will get us closer?

He's now getting the buffer detected but it's complaining it can't find the correct config.  maybe he's on pal and not ntsc?

---

### Post by majoridiot on 2006-12-08
'zactly what i'm thinking, trubble... with BusID "PCI:0:13:0" everything
seems ok until it looks for the framebuffer fb0.  i'm thinking it's PAL
and it should be fb1?

if so, a simple change.  if not, then we definitley need to see at least
a complete xorg.conf and Xorg.0.log.

---

### Post by dawson64 on 2006-12-08
I'm not sure of the difference of NTSC & PAL.  I believe I want NTSC (I'm in the USA).

How would I know what I'm setup for?

Thanks for your help!

Here is xorg.conf
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
#       FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
#       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed.
        Driver "ivtvdev"

        Option "fbdev" "/dev/fb0"  # frame buffer we found above
        Option "ivtv" "/dev/fb0" # for pal users I believe

        # below settings are optional I believe I've seen lots of people with them commented out.
        Option "TVStandard" "NTSC-M" # sorry pal don't know your settings
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        BusID "PCI:0:13:0" # busis we found with lspci converted as shown above

Screen 0
EndSection

Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        DisplaySize 183 122
        Mode "720x480"
        DotClock 34.564
        HTimings 720 752 840 928
        VTimings 480 484 488 504
        Flags "-HSync" "-VSync"
        EndMode

#       Identifier      "Generic Monitor"
#       Option          "DPMS"
#       HorizSync       28-51
#       VertRefresh     43-60
EndSection

Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
        Depth 24
        FbBpp 32
        Modes "720x480"
EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV Screen"

        # there is another way to get rid of keyboard and mouse, but you can leave them as is
        # this setup will run fine as is, without keyboard and mouse plugged in.
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666 # not needed I think it's specific to my computer, but all my computers have it.
EndSection

```

Here is Xorg.0.log
```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ubuntu 2.6.17-10-server #2 SMP Fri Oct 13 18:47:26 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  8 17:35:57 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "TV Screen" (0)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "Hauppauge PVR 350 iTVC15 Framebuffer"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/TTF/,
        /usr/share/fonts/X11/OTF,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/CID/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.0
        X.Org XInput driver : 0.6
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3099 card 1043,807f rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b099 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:05:0: chip 13f6,0111 card 1043,80e2 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:07:0: chip 104c,8026 card 1043,808d rev 00 class 0c,00,10 hdr 00
(II) PCI: 00:09:0: chip 1106,3038 card 1043,8080 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:09:1: chip 1106,3038 card 1043,8080 rev 50 class 0c,03,00 hdr 80
(II) PCI: 00:09:2: chip 1106,3104 card 1043,8080 rev 51 class 0c,03,20 hdr 80
(II) PCI: 00:0c:0: chip 1186,1300 card 1186,1301 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0d:0: chip 4444,0803 card 0070,4000 rev 01 class 04,00,00 hdr 00
(II) PCI: 00:11:0: chip 1106,3147 card 1043,808c rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1043,808c rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:2: chip 1106,3038 card 1043,808c rev 23 class 0c,03,00 hdr 00
(II) PCI: 00:11:3: chip 1106,3038 card 1043,808c rev 23 class 0c,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0000 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:13:0) unknown vendor (0x4444) unknown chipset (0x0803) rev 1, Mem @ 0xdc000000/26
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe1ffffff to 0xdfffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xda000000 - 0xda0000ff (0x100) MX[B]
        [1] -1  0       0xda800000 - 0xda8000ff (0x100) MX[B]
        [2] -1  0       0xdb000000 - 0xdb003fff (0x4000) MX[B]
        [3] -1  0       0xdb800000 - 0xdb8007ff (0x800) MX[B]
        [4] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [5] -1  0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [6] -1  0       0x0000a800 - 0x0000a81f (0x20) IX[B]
        [7] -1  0       0x0000b000 - 0x0000b01f (0x20) IX[B]
        [8] -1  0       0x0000b400 - 0x0000b40f (0x10) IX[B]
        [9] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [10] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [11] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [12] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xda000000 - 0xda0000ff (0x100) MX[B]
        [1] -1  0       0xda800000 - 0xda8000ff (0x100) MX[B]
        [2] -1  0       0xdb000000 - 0xdb003fff (0x4000) MX[B]
        [3] -1  0       0xdb800000 - 0xdb8007ff (0x800) MX[B]
        [4] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [5] -1  0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [6] -1  0       0x0000a800 - 0x0000a81f (0x20) IX[B]
        [7] -1  0       0x0000b000 - 0x0000b01f (0x20) IX[B]
        [8] -1  0       0x0000b400 - 0x0000b40f (0x10) IX[B]
        [9] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [10] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [11] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [12] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xda000000 - 0xda0000ff (0x100) MX[B]
        [5] -1  0       0xda800000 - 0xda8000ff (0x100) MX[B]
        [6] -1  0       0xdb000000 - 0xdb003fff (0x4000) MX[B]
        [7] -1  0       0xdb800000 - 0xdb8007ff (0x800) MX[B]
        [8] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [9] -1  0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x0000a800 - 0x0000a81f (0x20) IX[B]
        [13] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[B]
        [14] -1 0       0x0000b400 - 0x0000b40f (0x10) IX[B]
        [15] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [16] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [17] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.1
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.1.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "ivtvdev"
(II) Loading /usr/lib/xorg/modules/drivers/ivtvdev_drv.o
(II) Module ivtv: vendor="The XFree86 Project"
        compiled for 4.3.0, module version = 0.10.6
        ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) v4l driver for Video4Linux
(II) IVTVDEV_TST: driver for framebuffer: PVR-350
(II) Primary Device is: PCI 00:0d:0
(WW) ivtvdev: No matching Device section for instance (BusID PCI:0:13:0) found
(EE) No devices detected.

Fatal server error:
no screens found

```

---

### Post by dawson64 on 2006-12-08
From all of my research I have found that I should convert the hex to decimal.  IVTV driver's how to even says this.
[http://ivtvdriver.org/index.php/Howto:XDriver](http://ivtvdriver.org/index.php/Howto:XDriver)

NTSC

> **majoridiot said:**
> BusID "PCI:0:13:0" is correct...

it couldn't find the framebuffer before.  is this NTSC or PAL?

---

### Post by dawson64 on 2006-12-08
If i run:     sudo modprobe ivtv-fb  
& run:        cat /proc/fb
I get:        0 cx23415 TV out
& then gdm restart

Xorg.0.log goes further (using BusID "PCI:0:13:0"):
```
(II) Primary Device is: PCI 00:0d:0
(--) Chipset PVR-350 found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xda000000 - 0xda0000ff (0x100) MX[B]
        [5] -1  0       0xda800000 - 0xda8000ff (0x100) MX[B]
        [6] -1  0       0xdb000000 - 0xdb003fff (0x4000) MX[B]
        [7] -1  0       0xdb800000 - 0xdb8007ff (0x800) MX[B]
        [8] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [9] -1  0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x0000a800 - 0x0000a81f (0x20) IX[B]
        [13] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[B]
        [14] -1 0       0x0000b400 - 0x0000b40f (0x10) IX[B]
        [15] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [16] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [17] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) IVTVDEV_TST(0)using default device
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xda000000 - 0xda0000ff (0x100) MX[B]
        [5] -1  0       0xda800000 - 0xda8000ff (0x100) MX[B]
        [6] -1  0       0xdb000000 - 0xdb003fff (0x4000) MX[B]
        [7] -1  0       0xdb800000 - 0xdb8007ff (0x800) MX[B]
        [8] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [9] -1  0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [10] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [11] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [12] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000a800 - 0x0000a81f (0x20) IX[B]
        [16] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[B]
        [17] -1 0       0x0000b400 - 0x0000b40f (0x10) IX[B]
        [18] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [19] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [20] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [21] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [22] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [23] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(EE) IVTVDEV_TST(0)Framebuffer id from dev /dev/fb0is 0
(EE) IVTVDEV_TST(0)open /dev/video48 returned  9
(EE) IVTVDEV_TST(0)get_fb returned  0 fbid 0
(**) IVTVDEV_TST(0)Depth 24, (**) framebuffer bpp 32
(==) IVTVDEV_TST(0)RGB weight 888
(==) IVTVDEV_TST(0)Default visual is TrueColor
(==) IVTVDEV_TST(0)Using gamma correction (1.0, 1.0, 1.0)
(II) IVTVDEV_TST(0)Hardware: cx23415 TV out (vidmem: 1665k)
(**) IVTVDEV_TST(0)Option "ivtv" "/dev/fb0"
(II) IVTVDEV_TST(0)Checking Modes against framebuffer device...
(II) IVTVDEV_TST(0)     mode "720x480" ok
(II) IVTVDEV_TST(0)Checking Modes against monitor...
(--) IVTVDEV_TST(0)Virtual size is 720x480 (pitch 720)
(**) IVTVDEV_TST(0) Mode "720x480": 34.6 MHz (scaled from 0.0 MHz), 37.2 kHz, 73.9 Hz
(II) IVTVDEV_TST(0)Modeline "720x480"   34.56  720 752 840 928  480 484 488 504 -hsync -vsync
(**) IVTVDEV_TST(0)Display dimensions: (183, 122) mm
(**) IVTVDEV_TST(0)DPI set to (99, 99)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(**) IVTVDEV_TST(0)Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xdc000000 - 0xdfffffff (0x4000000) MX[B]
        [1] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [2] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [3] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [4] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [5] -1  0       0xda000000 - 0xda0000ff (0x100) MX[B]
        [6] -1  0       0xda800000 - 0xda8000ff (0x100) MX[B]
        [7] -1  0       0xdb000000 - 0xdb003fff (0x4000) MX[B]
        [8] -1  0       0xdb800000 - 0xdb8007ff (0x800) MX[B]
        [9] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [10] -1 0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [11] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [12] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [13] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000a800 - 0x0000a81f (0x20) IX[B]
        [17] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[B]
        [18] -1 0       0x0000b400 - 0x0000b40f (0x10) IX[B]
        [19] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [20] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [21] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [22] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [23] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [24] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
        bitsPerPixel=32, depth=24, defaultVisual=TrueColor
        mask: ff0000,ff00,ff, offset: 16,8,0

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/X11R6/bin/X(AddScreen+0x1ee) [0x806dd6e]
3: /usr/X11R6/bin/X(InitOutput+0x21e) [0x809f76e]
4: /usr/X11R6/bin/X(main+0x276) [0x806e506]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d638cc]
6: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 4.  Server aborting

```

---

### Post by majoridiot on 2006-12-09
try changing:

```
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed.
        Driver "ivtvdev"

        Option "fbdev" "/dev/fb0"  # frame buffer we found above
        # Option "ivtv" "/dev/fb1" # for pal users I believe

        # below settings are optional I believe I've seen lots of people with them commented out.
        Option "TVStandard" "NTSC-M" # sorry pal don't know your settings
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        BusID "PCI:0:0d:0" # busis we found with lspci converted as shown above

Screen 0
EndSection
```

to:

```
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"  
        Option "ivtv" "/dev/fb0" 
        Option "TVStandard" "NTSC-M" 
        Option "VideoOverlay" "on"
        Option "XVideo" "1"
        BusID "PCI:0:13:0" 
        Screen 0
EndSection
```

i've read where some apps like mythtv work fine with fbdev, but x needs ivtv or (maybe?) both fbdev and ivtv options defined.

any failures, post a fresh Xorg.0.log so we can keep tracking it. ;)

---

### Post by trubblemaker on 2006-12-09
I got a guess it's the fonts try:
```
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
#       FontPath        "/usr/share/X11/fonts/cyrillic"
#        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
#        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
#       FontPath        "/usr/share/fonts/X11/Type1"
#        FontPath        "/usr/share/fonts/X11/100dpi"
#        FontPath        "/usr/share/fonts/X11/75dpi"
#        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
EndSection
```
who needs all the fonts?

try it out couldn't hurt

---

### Post by trubblemaker on 2006-12-09
if your in the states your on ntsc I"m 99% positive.

---

### Post by dawson64 on 2006-12-09
Still no go.  I rebooted and still get the same thing.  I have tried fbdev, ivtv and both.

What does ```
sudo modprobe ivtv-fb 
```
do differently?  It seems to get past this point that I've been stuck at (see my last post).

Nothing really new in Xorg.0.log
```
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xda000000 - 0xda0000ff (0x100) MX[B]
        [5] -1  0       0xda800000 - 0xda8000ff (0x100) MX[B]
        [6] -1  0       0xdb000000 - 0xdb003fff (0x4000) MX[B]
        [7] -1  0       0xdb800000 - 0xdb8007ff (0x800) MX[B]
        [8] -1  0       0xe0000000 - 0xdfffffff (0x0) MX[B]O
        [9] -1  0       0xdc000000 - 0xdfffffff (0x4000000) MX[B](B)
        [10] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [11] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [12] -1 0       0x0000a800 - 0x0000a81f (0x20) IX[B]
        [13] -1 0       0x0000b000 - 0x0000b01f (0x20) IX[B]
        [14] -1 0       0x0000b400 - 0x0000b40f (0x10) IX[B]
        [15] -1 0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [16] -1 0       0x0000d000 - 0x0000d01f (0x20) IX[B]
        [17] -1 0       0x0000d400 - 0x0000d41f (0x20) IX[B]
        [18] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers/v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.1
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
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
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.1.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "ivtvdev"
(II) Loading /usr/lib/xorg/modules/drivers/ivtvdev_drv.o
(II) Module ivtv: vendor="The XFree86 Project"
        compiled for 4.3.0, module version = 0.10.6
        ABI class: XFree86 Video Driver, version 0.6
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) v4l driver for Video4Linux
(II) Primary Device is: PCI 00:0d:0
(--) Chipset PVR-350 found
(EE) open /dev/fb0: No such device
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found

```

> **majoridiot said:**
> try changing:


i've read where some apps like mythtv work fine with fbdev, but x needs ivtv or (maybe?) both fbdev and ivtv options defined.

any failures, post a fresh Xorg.0.log so we can keep tracking it. ;)

---

### Post by trubblemaker on 2006-12-09
try:

```
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"  
        #Option "ivtv" "/dev/fb0" 
        #Option "TVStandard" "NTSC-M" 
        #Option "VideoOverlay" "on"
        #Option "XVideo" "1"
        BusID "PCI:0:13:0" 
        Screen 0
EndSection
```

---

### Post by dawson64 on 2006-12-09
Get the same thing:
```
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) v4l driver for Video4Linux
(II) IVTVDEV_TST: driver for framebuffer: PVR-350
(II) Primary Device is: PCI 00:0d:0
(--) Chipset PVR-350 found
(EE) open /dev/fb0: No such device
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found


```


> **trubblemaker said:**
> try:

```
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"  
        #Option "ivtv" "/dev/fb0" 
        #Option "TVStandard" "NTSC-M" 
        #Option "VideoOverlay" "on"
        #Option "XVideo" "1"
        BusID "PCI:0:13:0" 
        Screen 0
EndSection
```

---

### Post by trubblemaker on 2006-12-09
does this give you any different output or is it the exact same?

```
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"  
        #Option "ivtv" "/dev/fb0" 
        #Option "TVStandard" "NTSC-M" 
        #Option "VideoOverlay" "on"
        #Option "XVideo" "1"
        BusID "PCI:0:0xd:0" 
        Screen 0
EndSection
```

---

### Post by dawson64 on 2006-12-09
Exact same.

```
(II) v4l driver for Video4Linux
(II) IVTVDEV_TST: driver for framebuffer: PVR-350
(II) Primary Device is: PCI 00:0d:0
(--) Chipset PVR-350 found
(EE) open /dev/fb0: No such device
(EE) Screen 0 deleted because of no matching config section.
(II) UnloadModule: "ivtvdev"
(EE) Device(s) detected, but none match those in the config file.

Fatal server error:
no screens found

```

> **trubblemaker said:**
> does this give you any different output or is it the exact same?

```
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"  
        #Option "ivtv" "/dev/fb0" 
        #Option "TVStandard" "NTSC-M" 
        #Option "VideoOverlay" "on"
        #Option "XVideo" "1"
        BusID "PCI:0:0xd:0" 
        Screen 0
EndSection
```

---

### Post by trubblemaker on 2006-12-09
I'm off to right a final.  Might be worth while checking out the mail archives on [http://ivtvdriver.org/](http://ivtvdriver.org/) , or maybe posting to there mailing list.

---

### Post by dawson64 on 2006-12-09
GOT IT :-)

I had started checking out ivtvdriver.org...

Here is what I did: 
```
uname -r
2.6.17-10-server
```
So I downloaded the latest stable release from here [http://ivtvdriver.org/index.php/Download](http://ivtvdriver.org/index.php/Download)

Then basically followed the instructions from here:
[http://www.mythtv.org/wiki/index.php/IVTV_Install](http://www.mythtv.org/wiki/index.php/IVTV_Install)

to update the modules i ran ```
sudo depmod -ae

```

to do the module configurations i ran (install wasn't working for me)
```
sudo sh -c 'echo ivtv >>/etc/modules'
sudo sh -c 'echo ivtv-fb >>/etc/modules'

```

Rebooted & I'm running :-)
> **trubblemaker said:**
> I'm off to right a final.  Might be worth while checking out the mail archives on [http://ivtvdriver.org/](http://ivtvdriver.org/) , or maybe posting to there mailing list.

---

### Post by trubblemaker on 2006-12-09
I said hell ya! So glad to hear you finally up and running, so what do you think the big change was. Sounds like it was a IVTV setup thing and not related to the xorg.conf.  is that what you would say? anything that you think I should add to the howto?

---

### Post by dawson64 on 2006-12-09
I think it was this...
I did do a modprobe ivtv-fb before hand.

```

sudo sh -c 'echo ivtv >>/etc/modules'
sudo sh -c 'echo ivtv-fb >>/etc/modules'
```

I'll confirm.  I tried getting the 320GB drive going again and somehow messed something up.  I was able to install to the 320GB now & am just about done...


> **trubblemaker said:**
> I said hell ya! So glad to hear you finally up and running, so what do you think the big change was. Sounds like it was a IVTV setup thing and not related to the xorg.conf.  is that what you would say? anything that you think I should add to the howto?

---

### Post by dawson64 on 2006-12-09
It was more that that I think.:-k   I tried just adding to the modules and still no go.  

So i followed all the steps in this as best i could:
[http://www.mythtv.org/wiki/index.php/IVTV_Install](http://www.mythtv.org/wiki/index.php/IVTV_Install)

I'm not sure if something is wrong in xorg.conf or what
```
Section "Files"
        FontPath "/usr/share/fonts/X11/misc"
        # FontPath "/usr/share/X11/fonts/cyrillic"
        FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath "/usr/share/fonts/X11/Type1"
        FontPath "/usr/share/fonts/X11/100dpi"
        FontPath "/usr/share/fonts/X11/75dpi"
        FontPath "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        # FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load "dbe"
        Load "v4l"
        Load "extmod"
        Load "type1"
        Load "freetype"
EndSection


Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"
        Option "ivtv" "/dev/fb0"
        Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"
        BusID "PCI:0:13:0"
        Screen 0
EndSection

#Section "Device"
#       Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed.
#       Driver "ivtvdev"

#       Option "fbdev" "/dev/fb0" # frame buffer we found above
#       Option "ivtv" "/dev/fb0" # for pal users I believe

        # below settings are optional I believe I've seen lots of people with t$
#       Option "TVStandard" "NTSC-M" # sorry pal don't know your settings
#       Option "VideoOverlay" "on"
#       Option "XVideo" "1"

#       BusID "PCI:0:13:0" # busis we found with lspci converted as shown above

#       Screen 0
#EndSection

Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        DisplaySize 183 122
        Mode "720x480"
        DotClock 34.564
        HTimings 720 752 840 928
        VTimings 480 484 488 504
        Flags "-HSync" "-VSync"
EndMode

EndSection

Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
        Depth 24
        FbBpp 32
        Modes "720x480"
        EndSubsection
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


#Section "Device"
#       Identifier      "Generic Video Card"
#       Driver          "vesa"
#       BusID           "PCI:1:0:0"
#EndSection

#Section "Monitor"
#       Identifier      "Generic Monitor"
#       Option          "DPMS"
#       HorizSync       28-51
#       VertRefresh     43-60
#EndSection


Section "ServerLayout"
        Identifier "Default Layout"
        Screen "TV Screen"
        InputDevice "Generic Keyboard"
        InputDevice "Configured Mouse"
EndSection

#Section "ServerLayout"
#       Identifier      "Default Layout"
#       Screen          "Default Screen"
#       InputDevice     "Generic Keyboard"
#       InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
#EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by dawson64 on 2006-12-09
Trubblemaker 

I'm back up and running again after a few hours worth of work.  The changes on your how to are good now!  I didn't have to do anything from the ivtv driver site or use the mythtv wiki.

I had installed that driver you added.  I think that was one part.  

The other part was adding both ivtv and ivtv-fb to the list of startup modules.  I would add that to your howto since the ivtv-fb isn't in superm1's IVTV how to.  :D 

> **trubblemaker said:**
> I said hell ya! So glad to hear you finally up and running, so what do you think the big change was. Sounds like it was a IVTV setup thing and not related to the xorg.conf.  is that what you would say? anything that you think I should add to the howto?

---

### Post by majoridiot on 2006-12-09
glad ya got is going! :D

---

### Post by Yoooder on 2007-01-18
Hey, thanks for the how-to!  It took a couple stabs to get it working but I now have X running on my TV.  Here's a question though... somewhere along the lines in my first attempt I had things working where my Desktop and the MythTV UI were showing on my PC's monitor, while whenever I switched to watch TV it showed on my TV.

I hate to admit it but I don't know what I did to have that effect, do you know how I can get it back that way?  Also, my ideal config would be to have MythTV run entirely on my TV (never on my monitor) and all else run solely on my monitor.  Any idea if this would be possible?

Thanks again!

---

### Post by trubblemaker on 2007-01-18
If you want to setup the TV play back with X on the monitor then you just have to switch you xorg.conf to the backup you made at the begging of the tutorial.  

At the completion of the tutorial all should run on the TV.  I'm not sure where your at right (what is playing on what) now so I don't know how to help you.  Tell me more and I'll try and help out.

---

### Post by Yoooder on 2007-01-18
> **trubblemaker said:**
> If you want to setup the TV play back with X on the monitor then you just have to switch you xorg.conf to the backup you made at the begging of the tutorial.  

At the completion of the tutorial all should run on the TV.  I'm not sure where your at right (what is playing on what) now so I don't know how to help you.  Tell me more and I'll try and help out.

Appologies for being vague, after I wrote that I realized how little info I had included.

I'm using a PVR-350 and (as stated) have a modified xorg.conf that utilizes my TV as a monitor.  I placed this config aside and restored the original xorg.conf.  What I noticed is this:  If I boot to the default xorg.conf then my TV responds by going gray (versus it's "no-signal" blue).  However--even though MythTV is set to output on the video-out it will still show my TV on my pc monitor.

If I use the xorg.conf that your tutorial describes, restart X, replace the modified xorg.conf with the original and again restart X THEN MythTV will output it's TV feed to my TV (the GUI remains on my monitor).

---

### Post by trubblemaker on 2007-01-18
are you rebooting or restarting X?  because their are some driver's that need to be initialized you do need to reboot, to swap between them.  try rebooting instead of restarting.  (If you are using a stripped down kernel it will be faster than you think. mine only takes ~15- 20 seconds)

let me know how it goes.

obviously to swap all outputs onto the monitor you just need to change the mythtv setting.


I definiately think something isn't initializing as if you change the xorg.conf and the setup doesn't work, ie can't initialize the tv as a monitor, you should actually get two blank screens and a whole lot of electronic paper weights.  So, I would definately say your restarting of X isn't re-initializing the xorg.conf.  Remember that if you do get lots of blank screens you can use the <alt>+ <F[N]> keys to get a terminal running most days.  Failing that a boot disk will help out.

---

### Post by jarodl on 2007-02-23
Hi,

This is my first post on an Ubuntu forum, so hopefully this is the correct place.

I have a question about using the TV-out on the PVR-350 (I believe it is the same question as Yoooder):

Can I have MythTV (including the menu system, not just the video) run solely on the TV out of the PVR-350, and have everything else run on my monitor?  Since I am using hardware endoding and decoding, I should have plenty of horsepower left in my computer to use it for other stuff, i.e. if my wife is using MythTV on the TV, I should be able to surf the net on my monitor at the same time.

I have a PVR-150 and a PVR-350, and Ubuntu Edgy Eft.

From what I can understand in the Xorg.conf from the HowTO, it looks like it will switch all output to the PVR-350 output, and the monitor will be blank.  Is this correct?

---

### Post by trubblemaker on 2007-02-27
your options are:

playback on TV, everything else on the monitor,
Everything on the monitor,
Everything on the TV.

Their may be an option where you setup a "dual" monitor, one is your tv, and the other your monitor, I haven't ever done this, but the setup for to use the tv, is a perfectly valid x setup and should theoretically work just fine if that is all that is required to setup dual monitors.  be aware that any TV remote commands will be interpreted as keystrokes on your keyboard, so you can't actually do both at the same time, but as long as you cooperated it would be ok.

ie ("honey, i'm going to change the channel can you click on myth for me")

Here's an [ubuntu forum for dual monitors]("http://ubuntuforums.org/showthread.php?t=221174")

.....


all that said, if you do have a pvr 350, why not spend $200-$300 on an old pentuim 3 and make two boxes?  (a dedicated myth box and a computer for you to use.)  Mine uses a pentuim 3 and it's all good.  Or just ask friends for any old parts and make one out of them.... Usually people do have an old garage sale ready computer they'd give to you for $100...   just a suggestion.

---

### Post by jarodl on 2007-03-02
That's definitely an option, and I think I will try that out.  There's just no reason why I shouldn't be able to run MythTV on my main PC (except for software limitations).  Currently that's what I do in Windows.  I run GB-PVR on Windows XP Home.  It works great.  To enable the PVR-350 TV output, all I had to do was open the configuration utility and select that option.  It not only passes the video to the output, but the whole menu system is output to the TV as well.  The GB-PVR software is freeware (not open source).  It is maintained by one person who goes by the handle 'sub'.  The software was about 10 time easier to set up than MythTV, and it works really well.  I don't understand how a freeware program (GB-PVR) maintained by one person can be superior in many ways to an open source program (MythTV).  Sorry for the rant; it just seems like MythTV should be further along than it is.

Of course, having two computers running instead of one eats up more electricity as well.  That's probably the only disadvantage to having a dedicated PVR.

Don't get me wrong, I am a big fan of open source and Linux.  Also, I haven't actually had a chance to use MythTV yet, I am just finishing installing it, so I guess we'll see how it stacks up to GB-PVR for functionality.

---

### Post by trubblemaker on 2007-03-02
well I understand that their maybe easier programs to install, especially if one person is on it.  I think you will find that mythtv's complication in installation is warranted through its massive functionality.  I believe it to be better than tivo.... my opinion..

---

### Post by nation on 2007-03-11
I have a bit of a different question on this topic - I'm not sure if anyone here might know how to help.

I'm running Dapper with a PVR-350, and I have X-out working great.  My xorg.conf is basically a carbon-copy of the one in the guide, with the exception that I load the i2c module (I think I saw somewhere that I needed it).

My problem is that Xorg seems to be seriously loading down my system doing refreshes.  I can basically open a console, start top, then hit the space bar repeatedly and watch the processor usage for Xorg go up to 80%, just from the console refresh!  This doesn't seem to be a problem for MythTV playback (except for some lag at times I think), but it is a problem when playing DVDs.

Does anyone know if there is something I can do to try to relieve this problem?  My processor is a 3.0 GHz Celeron with 2 GB of RAM, so I would think it wouldn't be that causing the issue.  My IVTV build should be up-to-date since I redid the whole install more or less this morning.

---

### Post by trubblemaker on 2007-03-11
are you playing back to the tv? make sure you've enabled the hardware decoding in the mythtv settings, the guide tells you how.  Also remember that dvd does take some work.... I'll have to think about it and get back to you.

---

### Post by nation on 2007-03-11
Yeah, the slowdown only occurs when playing back to the TV.  No playback is going to the video card.  When I do play just to the video card and monitor, the slow down isn't there.

The hardware decoding setting in MythTV is checked.

---

### Post by trubblemaker on 2007-03-14
K gave it some more thought, I don't know where your at with this issue, but you could try playing something with mplayer instead of myth to try and pin down if it's myth 'causeing the issue or just xorg.  I'd also snoop around the forum looking at dvd specific issues.  Let me know what you come up with, if it's myth related I'd like to know

low probability suggestion:
If you have an extra dvd drive you could swap it out to see if something about the driver is messing with x

---

### Post by trubblemaker on 2007-03-14
uh oh bad news: [http://www.mythtv.org/wiki/index.php/Talk:MythDVD](http://www.mythtv.org/wiki/index.php/Talk:MythDVD) apparently the issue is wide spread has to do with the frame buffer not quite up to the task of DVD payback.

Read the "does" section
[http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350#Does](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350#Does)

---

### Post by nation on 2007-03-14
Hmmm.  Well, that first link has an update claiming that updating the X Driver did the trick.  I think I have the newest version though (for Dapper, anyway).  I tried installing the one your guide lists from hellion.org.uk and that crashed the X server.  I downloaded one from ivtvdriver.org and tried copying that over my current ivtvdev_drv.o and that also crashed the X server.  Trying to compile from source got me nowhere since I can't seem to find the X.org source directory (if it exists), and it sounds like I shouldn't have to do that anyway...

If it helps, trying the ivtvdriver.org driver gets a bunch of missing symbols.

---

### Post by trubblemaker on 2007-03-14
yeah it does say that you "can do it now" doesn't say that you can do it with minimal CPU usage.  I advise against swapping out the frame buffer driver, I've had many a  headaches because of them,  

I wish you luck in finding an answer and would love to hear it if you find one.

I'm using a p3 for my myth box so I wouldn't dream of using myth for DVD's.  If you find a solution I'll try it on my machine for a real stress test.

---

### Post by nation on 2007-03-14
Yeah, I'll post something if I ever figure it out.  Thanks for the help!

---

### Post by Vincentoo on 2007-03-21
Hello,

I made an installation of MythTV on an old PC (in Ubuntu Edgy) with an Hauppauge PVR-350. Everything was installed fine (I followed the fabulous Ubuntu community guide) so far but I have issues with outputting to the TV.
The test:
```
/sbin/rmmod saa7127
/sbin/modprobe saa7127 test_image=1
```
never worked for me.
I am using apparently ivtv 0.7.0... and displaying on a PAL TV.

Would it be possible to get some advises on things I could try, because I already made 2 re-installs and really start thinking this is never going to work :( :( :( 

Vincentoo

---

### Post by trubblemaker on 2007-03-21
Hmmm, that's kind of a rough test to fail, as it's the hardware test.  That means that the  hardware driver isn't setup correctly.

The area of your problem is the IVTV driver.  

does your installation [pass the ivtv installation test?]("https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out#head-6614110f27426b52757180f04baa7b31aece0787")

If it does great we can look at other issues, if it doesn't then we'll start looking their.

---

### Post by Vincentoo on 2007-03-21
Hello,

First thanks for the answer :-)

I just ran - again - the ivtv test commands.
The movie recording works juste fine (ok, my movie displays garbage on the screen, normal since I did not yet connect my TV cable).

As far as the initialization is concerned, it gives the following result:
```
vincent@mythome:~$ dmesg |grep Initialized
[17179591.384000] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0

```

And finally, the /dev/video0 device is there too.
(as well as a video16, video24, video32, video4 8 )

Regards,

Vincentoo

---

### Post by trubblemaker on 2007-03-22
Things to think about:  The guide was written for 0.8 you are running 0.7  I have noticed that in the different versions of IVTV that their interface to commands **REALLY REALLY CHANGES** we could try and charge ahead and see what happens without doing the test and everything might work, you could try and look up other commands for IVTV 0.7 frame buffer module to see if that is the k.  

Here's a test that might help. Turn off the computer but plug the cables into the tv. (with the TV on) now turn on the computer and see if you get any changes onscreen.  It may help to hint that yes, it's working we just don't have the correct test command....


Scrap that according to [a bug report ]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90981")and [a post]("http://ubuntuforums.org/showthread.php?p=2337024#post2337024"), I've seen forget the test the module was not shipped by default in fiesty.  You need to compile it before you can use it.  [Here's some vague instructions]("http://ubuntuforums.org/showpost.php?p=2307589&postcount=3") on how to do that I will attempt to find better ones and change the wiki.

---

### Post by superm1 on 2007-03-22
> **trubblemaker said:**
> Things to think about:  The guide was written for 0.8 you are running 0.7  I have noticed that in the different versions of IVTV that their interface to commands **REALLY REALLY CHANGES** we could try and charge ahead and see what happens without doing the test and everything might work, you could try and look up other commands for IVTV 0.7 frame buffer module to see if that is the k.  

Here's a test that might help. Turn off the computer but plug the cables into the tv. (with the TV on) now turn on the computer and see if you get any changes onscreen.  It may help to hint that yes, it's working we just don't have the correct test command....


Scrap that according to [a bug report ]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/90981")and [a post]("http://ubuntuforums.org/showthread.php?p=2337024#post2337024"), I've seen forget the test the module was not shipped by default in fiesty.  You need to compile it before you can use it.  [Here's some vague instructions]("http://ubuntuforums.org/showpost.php?p=2307589&postcount=3") on how to do that I will attempt to find better ones and change the wiki.
Following up on trubblemaker's post -
This Saturday a new feisty kernel is going to be released including the module.  If you can hold off until then, you won't have to compile.
The kernel is going to be 2.6.20-13.

---

### Post by Vincentoo on 2007-03-24
Hello,

So you suggest that I switch to Festy? Or only its new kernel?

I configured Xorg and the framebuffer today; I definitvly see some flickering on the screen when I start something like gdm.
I also see some error messages in the X log:
> X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux mythome 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 24 11:36:47 2007
(==) Using config file: "/etc/X11/xorg.conf"
[B](EE) IVTVDEV_TST(0)Framebuffer id from dev /dev/fb0is 0
(EE) IVTVDEV_TST(0)open /dev/video48 returned  7
(EE) IVTVDEV_TST(0)get_fb returned  0 fbid 0
[/B]        bitsPerPixel=32, depth=24, defaultVisual=TrueColor
        mask: ff0000,ff00,ff, offset: 16,8,0
Init Video
Here I am with fPtr 0x81f95c0
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1/, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.


Does it ring a bell to you?

Vincentoo

---

### Post by trubblemaker on 2007-03-24
Yeah I do suggest upgrading to the newest kernel coming out today, and it will make your life significantly easier as we can rule out driver issues quickly.  also can you please post your /etc/X11/xorg.conf file after the upgrade, I'll try looking for error in it.

---

### Post by Vincentoo on 2007-03-25
Hello,

Sorry, but how do I retrieve/install this new kernel? Do I have to upgrade the complete distribution?
If so, then, how...

Thanks in advance

Vincentoo

---

### Post by superm1 on 2007-03-25
> **Vincentoo said:**
> Hello,

Sorry, but how do I retrieve/install this new kernel? Do I have to upgrade the complete distribution?
If so, then, how...

Thanks in advance

Vincentoo
I'm still waiting on it to trickle down the mirrors (hasn't hit mine yet).  Probably the same case for you.  Once it does:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Will get it.

---

### Post by Vincentoo on 2007-03-25
Hello again,

I guess I still miss something...
My apt sources.list is still basic and I guess I won't see this new kernel... Or?
```
deb http://archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://dl.ivtvdriver.org/ubuntu edgy firmware

```

Shall I add something?

Vincentoo

---

### Post by Vincentoo on 2007-03-30
Hello,

Small update on my previous problem...
I moved to feisty beta and retrieved kernel 2.6.20-13-generic #2
Unfortunately I have been fighting with my wireless USB dongle (Linksys WUSB54GC) since compilation of the driver did not work anymore with this new kernel (had to slightly modify the code).

Finally it is working and I can now move my PC next the TV in order to restart my tests on TV output
:-) :-)

Vincentoo

---

### Post by Vincentoo on 2007-03-31
Hello,

So the results is the almost same... :-(
When I run the saa7127 test_image=1 command, I some black/blue/red stripes moving along on the TV (not horizontal bars, but //).
Of course, if I try to run X, I get nothing...

A few details:
Linux mythome 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

```
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  ==================== START INIT IVTV ====================
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  version 0.10.1 (tagged release) loading
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  Linux version: 2.6.20-13-generic SMP mod_unload 586
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  In case of problems please include the debug info between
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv0: Autodetected Hauppauge card (cx23415 based)
Mar 31 13:54:11 mythome kernel: [   25.300000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Mar 31 13:54:11 mythome kernel: [   25.300000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Mar 31 13:54:11 mythome kernel: [   25.300000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Mar 31 13:54:11 mythome kernel: [   25.936000] rtusb init ====>
Mar 31 13:54:11 mythome kernel: [   26.288000] idVendor = 0x13b1, idProduct = 0x20
Mar 31 13:54:11 mythome kernel: [   26.288000] usbcore: registered new interface driver rt73
Mar 31 13:54:11 mythome kernel: [   26.340000] rt73 driver version - 1.0.3.6
Mar 31 13:54:11 mythome kernel: [   26.376000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
Mar 31 13:54:11 mythome kernel: [   27.004000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
Mar 31 13:54:11 mythome kernel: [   27.228000] ivtv0: Encoder revision: 0x02050032
Mar 31 13:54:11 mythome kernel: [   27.228000] ivtv0: Recommended firmware version is 0x02060039.
Mar 31 13:54:11 mythome kernel: [   27.236000] ivtv0: Decoder revision: 0x02020023
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: Hauppauge model 48134, rev J347, serial# 7013635
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: tuner model is LG TP18PSB01D (idx 47, type 28)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: TV standards PAL(B/G) (eeprom 0x04)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: audio processor is MSP4418 (idx 25)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: decoder processor is SAA7115 (idx 19)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter
Mar 31 13:54:11 mythome kernel: [   27.324000] ivtv0: Autodetected Hauppauge WinTV PVR-350
Mar 31 13:54:11 mythome kernel: [   27.380000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.504000] saa7115 1-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.768000] saa7127 1-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.832000] msp3400 1-0040: MSP4418G-A2 found @ 0x80 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.832000] msp3400 1-0040: MSP4418G-A2 supports nicam and radio, mode is autodetect and autoselect
Mar 31 13:54:11 mythome kernel: [   27.836000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
Mar 31 13:54:11 mythome kernel: [   27.836000] ivtv0: Registered device video32 for encoder YUV (2 MB)
Mar 31 13:54:11 mythome kernel: [   27.836000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.844000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.844000] ivtv0: Registered device radio0 for encoder radio
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device video16 for decoder MPEG (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device vbi16 for decoder VOUT
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device video48 for decoder YUV (1 MB)
Mar 31 13:54:11 mythome kernel: [   28.076000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
Mar 31 13:54:11 mythome kernel: [   28.184000] tuner 1-0061: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
Mar 31 13:54:11 mythome kernel: [   28.692000] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
Mar 31 13:54:11 mythome kernel: [   28.692000] ivtv:  ====================  END INIT IVTV  ====================

```

My Xorg.cong
> Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

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
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "latin9"
        Option          "XkbOptions"    "lv3:ralt_switch"
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

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"
        BusID "PCI:00:08:00"
EndSection

Section "Monitor"
  Identifier "PAL Monitor"
  HorizSync 30-68
  VertRefresh 50-120
  Mode "720x576"
    DotClock 42.6
    HTimings 720 760 832 944
    VTimings 576 577 580 602
    Flags "-HSync" "-VSync"
  EndMode
EndSection

Section "Screen"
        Identifier "TV"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "PAL Monitor"
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
        Screen          "TV"
#       InputDevice     "Generic Keyboard"
#       InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection


What else can I do now?

Regards,

Vincentoo

---

### Post by superm1 on 2007-03-31
> **Vincentoo said:**
> Hello,

So the results is the almost same... :-(
When I run the saa7127 test_image=1 command, I some black/blue/red stripes moving along on the TV (not horizontal bars, but //).
Of course, if I try to run X, I get nothing...

A few details:
Linux mythome 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

```
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  ==================== START INIT IVTV ====================
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  version 0.10.1 (tagged release) loading
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  Linux version: 2.6.20-13-generic SMP mod_unload 586
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  In case of problems please include the debug info between
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
Mar 31 13:54:11 mythome kernel: [   25.296000] ivtv0: Autodetected Hauppauge card (cx23415 based)
Mar 31 13:54:11 mythome kernel: [   25.300000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
Mar 31 13:54:11 mythome kernel: [   25.300000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
Mar 31 13:54:11 mythome kernel: [   25.300000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
Mar 31 13:54:11 mythome kernel: [   25.936000] rtusb init ====>
Mar 31 13:54:11 mythome kernel: [   26.288000] idVendor = 0x13b1, idProduct = 0x20
Mar 31 13:54:11 mythome kernel: [   26.288000] usbcore: registered new interface driver rt73
Mar 31 13:54:11 mythome kernel: [   26.340000] rt73 driver version - 1.0.3.6
Mar 31 13:54:11 mythome kernel: [   26.376000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
Mar 31 13:54:11 mythome kernel: [   27.004000] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
Mar 31 13:54:11 mythome kernel: [   27.228000] ivtv0: Encoder revision: 0x02050032
Mar 31 13:54:11 mythome kernel: [   27.228000] ivtv0: Recommended firmware version is 0x02060039.
Mar 31 13:54:11 mythome kernel: [   27.236000] ivtv0: Decoder revision: 0x02020023
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: Hauppauge model 48134, rev J347, serial# 7013635
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: tuner model is LG TP18PSB01D (idx 47, type 28)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: TV standards PAL(B/G) (eeprom 0x04)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: audio processor is MSP4418 (idx 25)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: decoder processor is SAA7115 (idx 19)
Mar 31 13:54:11 mythome kernel: [   27.324000] tveeprom 1-0050: has radio, has IR receiver, has no IR transmitter
Mar 31 13:54:11 mythome kernel: [   27.324000] ivtv0: Autodetected Hauppauge WinTV PVR-350
Mar 31 13:54:11 mythome kernel: [   27.380000] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.504000] saa7115 1-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.768000] saa7127 1-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.832000] msp3400 1-0040: MSP4418G-A2 found @ 0x80 (ivtv i2c driver #0)
Mar 31 13:54:11 mythome kernel: [   27.832000] msp3400 1-0040: MSP4418G-A2 supports nicam and radio, mode is autodetect and autoselect
Mar 31 13:54:11 mythome kernel: [   27.836000] ivtv0: Registered device video0 for encoder MPEG (4 MB)
Mar 31 13:54:11 mythome kernel: [   27.836000] ivtv0: Registered device video32 for encoder YUV (2 MB)
Mar 31 13:54:11 mythome kernel: [   27.836000] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.844000] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.844000] ivtv0: Registered device radio0 for encoder radio
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device video16 for decoder MPEG (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device vbi16 for decoder VOUT
Mar 31 13:54:11 mythome kernel: [   27.848000] ivtv0: Registered device video48 for decoder YUV (1 MB)
Mar 31 13:54:11 mythome kernel: [   28.076000] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
Mar 31 13:54:11 mythome kernel: [   28.184000] tuner 1-0061: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
Mar 31 13:54:11 mythome kernel: [   28.692000] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
Mar 31 13:54:11 mythome kernel: [   28.692000] ivtv:  ====================  END INIT IVTV  ====================

```My Xorg.cong


What else can I do now?

Regards,

Vincentoo
Hi Vincentoo,

I'm assuming that you are running those test commands in something such as VT1 or the like?  

If not, that is where you need to start.  Hit ctrl-alt-f1, and login to the session right there.
Issue a command to stop gdm
```
sudo /etc/init.d/gdm stop
```

When you rmmod the module, you should see a message in 'dmesg' about it being unloaded.  Be sure this is there, or at least verify you don't see it on the list in lsmod.

When you modprobe it, just the same should happen. A message should appear in dmesg and/or the module should now be in lsmod.  

If you are following all of these things, are you using a PAL TV with a NTSC card or vice-versa?  Having lines moving horizontally sounds like its the wrong TV standard.

Lastly, are you sure this card is fully functional?  In my experiences, linux has been much more forgiving about bad hardware than windows.  Short example, I know of someone with a gateway laptop.  Their sound card appears to be bad because on a fresh install of windows, the drivers from *gateways website* for the sound card cause it to blue screen.  As in you install the driver, and in the process you get a blue screen before it gets close to completion.  I told the person to let me try a live disk with it.  I grabbed a feisty disk, booted it up, and showed them desktop effects out of the box on their intel card, and all this fully functional hardware.  Sound worked no trouble whatsoever.

---

### Post by Vincentoo on 2007-04-03
> Hi Vincentoo,

I'm assuming that you are running those test commands in something such as VT1 or the like?  

To be exact, I am connected to the PC via SSH over WIFI.

> 
If not, that is where you need to start.  Hit ctrl-alt-f1, and login to the session right there.
Issue a command to stop gdm
```
sudo /etc/init.d/gdm stop
```

When you rmmod the module, you should see a message in 'dmesg' about it being unloaded.  Be sure this is there, or at least verify you don't see it on the list in lsmod.

When you modprobe it, just the same should happen. A message should appear in dmesg and/or the module should now be in lsmod.  

If you are following all of these things, are you using a PAL TV with a NTSC card or vice-versa?  Having lines moving horizontally sounds like its the wrong TV standard.


I am in Belgium, so PAL TV.
The problem with the test of saa7127 test_image=1 
is that there is no argument to specify the TV standard. So I can imagine that by default it is using the wrong format.

> 
Lastly, are you sure this card is fully functional?  In my experiences, linux has been much more forgiving about bad hardware than windows.  Short example, I know of someone with a gateway laptop.  Their sound card appears to be bad because on a fresh install of windows, the drivers from *gateways website* for the sound card cause it to blue screen.  As in you install the driver, and in the process you get a blue screen before it gets close to completion.  I told the person to let me try a live disk with it.  I grabbed a feisty disk, booted it up, and showed them desktop effects out of the box on their intel card, and all this fully functional hardware.  Sound worked no trouble whatsoever.

The PVR-350 was functional, but barely used.
I have another one (was planning to have 2 for PiP) so I can try to switch it, but I don't think it is going to change anything.

Vincentoo

---

### Post by superm1 on 2007-04-05
> **Vincentoo said:**
> To be exact, I am connected to the PC via SSH over WIFI.



I am in Belgium, so PAL TV.
The problem with the test of saa7127 test_image=1 
is that there is no argument to specify the TV standard. So I can imagine that by default it is using the wrong format.



The PVR-350 was functional, but barely used.
I have another one (was planning to have 2 for PiP) so I can try to switch it, but I don't think it is going to change anything.

Vincentoo
I'm parched for ideas now.  I looked into finding a way to change the output format of saa7127, but I didn't have any luck finding one.  Perhaps anyone else can chime in here with suggestions?

---

### Post by Vincentoo on 2007-04-16
Hello,

Update...
After trying on another PC/other PVR350 card, I had the same issue: the test_image=1 test does not display a thing on my tv. Strange is that, the strange display stuff I got in the past, I could reproduce only on one of my TV SCART entry (my TV has 2 SCARTs entries, and one composite), using the composite cables (and not the S-VIDEO).

Another thing, using 2x PVR-350, on the latest Feisty kernel (-14 I think it was), none of them was inited correctly (Decoder mailbox error thingy, -19). Could only use one...

I am now re-installing my machine with _:-(_indows to try out the PVR350 with WinTV and potentially with other SageTV to see if I can have it working there, to confirm that the cards are working well.

Vincentoo

---

### Post by trubblemaker on 2007-04-16
sorry had my Head stuck in some books,(Graduating University and have been studying hard) I'm pretty sure you can change your coding standard with direct command line arguments to IVTV.  I've seen this done before some of the links on the bottom will help you with that....  but that being said, I don't know what standard (pal or ntsc) is default and if that is your issue.  We need to find you some pal settings, 

Here's some logic I got for you.

**IF** you get a change in behavior now (on your tv( when inserting the 

"saa7127 test_image=1", 

great we now your card works, and cable send a signal, like you said it's PAL standard and the test image may not be setup for that.

So I would suggest trudging on with x-testing and hoping that we can find the correct standard for pal users.  For [that the IVTV page for PAL users using running X ]("http://ivtv.writeme.ch/tiki-index.php?page=TvOutPal")  might be of help.

they show the specific setting to change to PAL on boot 

adding enteries to your alias file like:
```

options ivtv ivtv_debug=1 ivtv_pal=1 tuner=5 

```
among other things, hope that this helps,

if you do go back to windows I would really suggest using some other software other than wintv scheduler, it sucks,

If I was the person that wrote that software I'd be embarrassed it limits you to taping 8 shows, is counter intuitive and restrictive.  All wintv scheduler, really is a interface to windows scheduler,  I did find some software on sourceforge a while ago that promised to be way better, but that's when I found out about mythtv and dropped windows....

(there is a hack to get around 8 shows with "wintv scheduler" you simply edit "window scheduler" manually to contain more entries.   It's not hard ones you see how they, setup recording, it's easy)

Sorry I haven't been around wish I'd seen this post sooner....

---

### Post by Crakie on 2007-04-21
I am having the same problem as Vincentoo. Independently from this thread, I was reading [this]("http://ivtv.writeme.ch/tiki-print.php?page=TvOutHowto") and more specifically [this]("http://ivtv.writeme.ch/tiki-index.php?page=TvOutPal") which you were reading as well, trubblemaker, weren't you? ;) Well, I can confirm adding lines like 'options ivtv ivtv_debug=1 ivtv_pal=1 tuner=5' to the alias file is a step towards the right solution, but it does not solve the problem entirely. That is, for a few minutes, I got TV-out from the Hauppauge 350 working with MythTV while playing around with the suggestions in the Howtos I linked above. Two things were wrong though: 1) no sound and 2) no overlay (channel info, tv guide, menu etc not visible when appropriate key pressed). One thing was really great: the picture quality!!!

So I played around some more and I never got to that point again. From what I can recall I added something *like* this to aliases in /etc/modprobe.d:

alias char-major-81-0 ivtv
alias /dev/v4l ivtv
options ivtv ivtv_debug=1 ivtv_pal=1 tuner=5
options tuner pal=1
options saa7127 enable_output=1 output_select=0 pal=1

and then running depmod -a and update-modules (and also rebooting sometimes)

I emphasize *like* because I do remember leaving out some lines with respect to the Howto from the links given above. I cannot remember which ones exactly. I also remember getting all kinds of different error messages when running dmesg | grep ivtv or dmesg | grep saa7127, also when MythTV could use the Tv-out of the Hauppauge.  For every combination of lines left out, the error message was usually different I got things with 'warning' in it (which is never good) and also things with 'ivtv_debug unknown', indicating the syntax is wrong.

As you may have deduced from the above, I am not a very seasoned Linux user. I basically had no idea what I was doing. My preliminary conclusion is that saa7127 indeed needs to be told to use pal. I just dont know how. I'd appreciate any help to resolve this, because I'd really like to enjoy the picture quality of the Hauppauge TV-out.

---

### Post by trubblemaker on 2007-04-21
you might try posting to the [ivtv userlist]("http://ivtvdriver.org/mailman/listinfo/ivtv-users")  real answers and users that have the card working.

Due to the rapid development of the driver, settings have really changed, but you might be able to get the newest settings for the tuner.  I can't help you more until my finals are over but I'll see what I can do then....

actually I've posted your question to the user-list for you and will check on it periodically for you.

---

### Post by Crakie on 2007-04-22
Thanks, trubblemaker. I think I saw your post and I added one of my own. If you can find the time to read it, it contains some updates (I played around some more with some settings, now I have TV-out but a terminal 'on top' of it and still no sound). Let's hope we get something useful out of it. Good luck on the exams! [-o<

---

### Post by Vincentoo on 2007-04-23
Hello,

Indeed, thanks for the answers too.
I did not manage to get the Hauppauge TV out working, even using WinTV (I only switched to Windows because I wanted to check if I could output to TV using the "supported"/default software :) :) ); so I reached a point where I suspect:
[LIST]
[*]My 2 Hauppauge PVR-350 to be broken
[*]My TV to be picky about input video sources
[/LIST]
In any case, I will re-do the Feisty installation in the coming weeks and try out your tricks; I am also looking at find a VGA -> S-Video/SCART adapter if it turns out that these cards are really broken.

Vincentoo

---

### Post by trubblemaker on 2007-04-23
Warning just saw a post about  video4linux, it apparently it messes up the video capture for some reason.

You need to build the saa7127 module from source.  There's a
howto at this link:
 [http://www.gossamer-threads.com/lists/ivtv/users/35059](http://www.gossamer-threads.com/lists/ivtv/users/35059)

it's written for RedHat but most of instructions can be translated to Ubnuntu

you will need to run these instructions instead to be able to build Modules on Ubuntu:
```
sudo apt-get install build-essential          # install's make among other things
sudo apt-get install linux-headers-`uname -r`  #needed so you can  build kernel modules

```

that takes should take care of the rpm for source code needed(refered to in the howto)  from their most instructions will be the same....

---

### Post by Vincentoo on 2007-07-02
Hi

Long time without a bump! :p

To say that I managed to have MythTV working on my PVR-350 using the TV-out function of the card. I found by hazard a new cable for the card (providing a SCART interface instead of the S-Video + WHITE/RED/YELLOW cables). I tried it and I got some output from the saa7127 test_image. "Some output" because the ouput is 1) unstable 2) weird (due to the fact that it is in NTSC instead of PAL?).
However, the framebuffer worked, as well as the X-Driver.
The video quality is indeed very good!

All this using:
- Ubuntu Feisty (latest updates, not latest kernel).
- Recompiled ivtv module (1.0.3).

Regards,

Vincentoo

---

### Post by BenFranske on 2007-07-16
The ivtvdev_drv driver is no longer available on the hellion.org.uk site. It looks like the driver is now available in a Debian package instead. It hasn't made its way into Ubuntu Feisty but you can download the xserver-xorg-video-ivtv package from the Debian repository and install it with dpkg.

---

### Post by LostShootingStar on 2007-07-24
Im having a lot of trouble with this. i had MythTV working perfectly in Edgy, but trying to install it (from scratch) on Feisty is not working....or at least the PVR-350 TV out is not working anyway.

I can get as far as getting my consol onto my TV, but Xorg fails. here are the errors.

```


(II) LoadModule: "ivtvdev"
(II) Loading /usr/lib/xorg/modules/drivers//ivtvdev_drv.so
(II) Module ivtv: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.10.6
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2
(EE) module ABI minor version (2) is newer than the server's version (1)
(II) UnloadModule: "ivtvdev"
(II) Unloading /usr/lib/xorg/modules/drivers//ivtvdev_drv.so
**(EE) Failed to load module "ivtvdev" (module requirement mismatch, 0)**


```

and a little later in the log file:

```


(EE) No devices detected.

Fatal server error:
no screens found


```


Here is my xorg.conf

```

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"




        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
        Load            "dbe"
        Load            "v4l"
        Load            "type1"
        Load            "freetype"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
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

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection


Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"



        # the driver we installed.

        Driver "ivtvdev"
  
      # frame buffer we found above
        Option "ivtv" "/dev/fb0"
        Option "fbdev" "/dev/fb0"
     
        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:0:08:0"           

        Screen 0

EndSection

Section "Device"
        Identifier      "nVidia Corporation NV17 [GeForce4 MX 440]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "eView 17f"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        DisplaySize 183 122
        Mode "720x480"
        DotClock 34.564
        HTimings 720 752 840 928
        VTimings 480 484 488 504
        Flags "-HSync" "-VSync"
        EndMode


        # for pal users:
        #Section "Monitor"
        #       Identifier  "TV"
        #       HorizSync  30-68
        #       VertRefresh 50-120
        #       Mode "720x576"
        #       D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
        #       DotClock 41.476
        #       HTimings 720 752 840 928
        #       VTimings 576 580 584 600
        #       Flags    "-HSync" "-VSync"
        #       EndMode
        #EndSection
        #for pal users more settings: http://www.mythtv.org/wiki/index.php/XV_on_PVR-350#PAL 

        # Sorry SECAM users I don't have the codes for that but I did see them on the web
        # So seek and you will find.  There are some resources at the bottom of this 
        # webpage to help out.

EndSection

# Our PVR-350 Driver entry
Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
              Depth 24
              FbBpp 32
              Modes "720x480"
        EndSubsection
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 440]"
        Monitor         "eView 17f"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "800x600"      "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "TV Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

EndSection

Section "DRI"
        Mode    0666
EndSection


```

I think it has something to do with:
```
(EE) module ABI minor version (2) is newer than the server's version (1)
```

but my mind is so fried from working on this, i just cant think clearly anymore


EDIT: Took an hour break and got it working.

the problem is that i was extracting ivtvdev_drv.so from : [http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtv_0.10.6-2_i386.deb](http://www.hellion.org.uk/ivtv/debian/xserver-xorg-video-ivtv_0.10.6-2_i386.deb)

I swapped the .so file with an archived one ([http://www.hellion.org.uk/ivtv/debian/archive/ivtvdev_drv.so~i386](http://www.hellion.org.uk/ivtv/debian/archive/ivtvdev_drv.so~i386)) and it works fine.

now i just have to figure out why i only have 13 channels...

---

### Post by Chuckels550 on 2007-07-31
Are you sure that everything is working?  I have Feisty Fawn and the ivtvdev_drv.so now provided through Hellion.org.uk causes errors that won't allow me to run the sound through the soundcard.  

I have audio for Live TV or any of the TV Mythtv functions, but running anything through an optical drive means no sound because I cannot cable through the soundcard - the sound is straight out of the WinPVR 350 to the TV.  

If you do a dmesg, you have to view the whole result to see the errors causing the problem near the end of your read out.  Don't grep just the IVTV stuff.

Update - my IVTV (WinPVR 350 TV Out) issue turned out to be an audio issue involving my configuration of ALSA, soundcard and MythTV.  I now cable the TV Tuner audio from the audio out to the soundcard audio in and then from the sound card audio out to the TV audio in.  It works currently for everthing except MythDVD.  For some reason I haven't been able to configure the playback sound for MythDVD ripped DVDs that preserve the AC3 audio.

---

### Post by LostShootingStar on 2007-07-31
> **Chuckels550 said:**
> Are you sure that everything is working?  I have Feisty Fawn and the ivtvdev_drv.so now provided through Hellion.org.uk causes errors that won't allow me to run the sound through the soundcard.  

I have audio for Live TV or any of the TV Mythtv functions, but running anything through an optical drive means no sound because I cannot cable through the soundcard - the sound is straight out of the WinPVR 350 to the TV.  

If you do a dmesg, you have to view the whole result to see the errors causing the problem near the end of your read out.  Don't grep just the IVTV stuff.

I actually have the same problem, but dont use the DVD drive in my myth box, so i dont notice it..

I think it has something to do with the MythTV option that tells the sound to go ONLY to the PVR-350, i forget the actual wordage they use...

---

### Post by Nimda1000 on 2007-12-22
> **LostShootingStar said:**
> 
now i just have to figure out why i only have 13 channels...

This one is easy, I had same thing.

You must select the proper channel frequency table in your Video Source Setup in Myth TV Settings.  North America uses US-Cable for Cable Service or US-Broadcast For Antenna.

Delete all 13 channels then you can re-add all the channels by either doing a channel scan or pull them down from your listings provider.

Hope this helps.

---

### Post by mckemie on 2008-01-28
I've been using the wiki document to try to get video out of my 350 S-Video connector.  I've never had Myth working, so I may be under some misconceptions as to how things are supposed to work.  Anyway, after trying several flavors of Myth, Mythbuntu has finally given me some small successes.
I seem to have installed the deb video driver package and now I'm stuck on the "cat /proc/fb" part.  I have /proc/fb, but it is empty.  How do I get a frame buffer device?

Update:  More thorough reading of the document reveals the answer.  Now, I'm on to getting X configured to use the TVout.  Perhaps more questions later.

---

### Post by krazyj on 2008-03-05
Hi all,
Can anyone post a WORKING xorg.conf for:

Fiesty w/ Mythbuntu
Dual Monitors (LCD + TV)
PVR-350

?

I cant get it to work and I think a working example would be all I need.

THANKS!

---

### Post by Crakie on 2008-03-06
Here you go. It's actually a triple monitor setup, with 2 monitors connected to the graphics card and the tv connected to the Hauppauge 350. Details like the BusID will vary of course. Also note that this gives me three separate X-screens.

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "v41"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "alt-intl"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "BenQ FP91G+"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "PHILIPS 109P4"
    HorizSync       30.0 - 111.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT-0: 1280x1024 +0+0; CRT-0: 800x600 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "metamodes" "CRT-1: 1280x1024 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Monitor"
        Identifier  "PALTV"
        HorizSync  30-68
        VertRefresh 50-120
        Mode "720x576"
          DotClock 42.6
          HTimings 720 760 832 944
          VTimings 576 577 580 602
          Flags    "-HSync" "-VSync"
        EndMode
 EndSection

Section "Device"
        Identifier "HauppaugePVR"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"
        BusID  "7:5:0"
EndSection

Section "Screen"
  Identifier "Screen2"
  Device "HauppaugePVR"
  Monitor "PALTV"
  DefaultDepth 24
  DefaultFbbpp 32
  Subsection "Display"
    Depth 24
    FbBpp 32
  EndSubsection
EndSection
```

---

### Post by boca raton on 2008-05-04
I am using a PVR 350 on Mythbuntu 8.04.

I am using the 350 tv output for TV and a monitor to set up the pc. I have tv output showing on the TV but I can not get x to the TV.  It's a PIII 1.2 Ghz box with about 350 Meg of memory.

I've tried most of the recommendations in this thread, religiously I might add, with no success. (not to say I havn't missed something in my observance!)  

There appear to be differences in the solutions to this as myth and Ubuntu have progressed thru their versions.  Does 8.04 need to be 'massaged' as with previous examples in this thread or am I just not using the configuration and setup menus in 8.04 correctly?
 
Help is appreciated!

---

### Post by trubblemaker on 2008-05-05
I'm not sure but X might be launched differently on 8.04.

I haven't played with it yet.

Where are you getting to with launching X?  Where is it failing?


Some steps that helped me to see where I was going wrong,

boot into a shell (recovery/safe) mode
start x manually from the terminal.
```
X
```
post the error messages here.

---

### Post by boca raton on 2008-05-05
trubblemaker
Has an Ubuntu Drip
 
Join Date: Oct 2005
Posts: 776
Thanks: 0
Thanked 0 Times in 0 Posts
	
Re: HOWTO: Get X Running on pvr-350 Tv-Out
I'm not sure but X might be launched differently on 8.04.

I haven't played with it yet.

Where are you getting to with launching X? Where is it failing?


Some steps that helped me to see where I was going wrong,

boot into a shell (recovery/safe) mode
start x manually from the terminal.
Code:

X

post the error messages here.
__________________

I'm not sure what you mean by 'boot into a shell (recovery/safe) mode.'

But I did open a terminal and type x, result was;
bash: x: command not found

So I did Alt/Cntrl/F4.  Surprise (to me), it displayed on the tv.  I logged in, result was;

a rather lengthy bit of verbage..... and;

Encoders:
myth-desktop (1) - Idle

Schedule Conflicts:
Unable to access MythTV Perl API.  Try with -- verbose to find out why.

and back to prompt, at which I enter 'x', result is'
-bash: x: command not found
return to prompt

My current xorg.conf is;

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection


I had tried an xorg.conf
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch" #added this line"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

#Section "Device"
#       Identifier      "Configured Video Device"
#EndSection

#Section "Monitor"
#       Identifier      "Configured Monitor"
#EndSection
#
#Section "Screen"
#       Identifier      "Default Screen"
#       Monitor         "Configured Monitor"
#       Device          "Configured Video Device"
#EndSection
#
#Section "ServerLayout"
#       Identifier      "Default Layout"
#       Screen          "Default Screen"
#EndSection
#
#following added to end of file
Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed - in Gutsy, this is NOT "ivtvdev".
        Driver "ivtv"

        # frame buffer we found above
        Option "fbdev" "/dev/fb0"

        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:1:09:0"

        Screen 0


EndSection

# these settings are generic (for TVs) but are specifically for TV

Section "Monitor"
        Identifier "TV"
        HorizSync 30-68
        VertRefresh 50-120
        DisplaySize 183 122
        Mode "720x480"
        DotClock 34.564
        HTimings 720 752 840 928
        VTimings 480 484 488 504
        Flags "-HSync" "-VSync"
        EndMode


        # for pal users:
        #Section "Monitor"
        #       Identifier  "TV"
        #       HorizSync  30-68

       #       VertRefresh 50-120
        #       Mode "720x576"
        #       D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
        #       DotClock 41.476
        #       HTimings 720 752 840 928
        #       VTimings 576 580 584 600
        #       Flags    "-HSync" "-VSync"
        #       EndMode
        #EndSection
        #for pal users more settings: [http://www.mythtv.org/wiki/index.php/XV_on_PVR-350#PAL](http://www.mythtv.org/wiki/index.php/XV_on_PVR-350#PAL)

        # Sorry SECAM users I don't have the codes for that but I did see them on the web
        # So seek and you will find.  There are some resources at the bottom of this
        # webpage to help out.

EndSection

# Our PVR-350 Driver entry
Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
              Depth 24
              FbBpp 32
              Modes "720x480"
        EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV Screen"

        # There is other ways to get rid of keyboard and mouse, but you can these settings as is.
        # This setup is designed to run without keyboard and mouse plugged in.
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

.....which did not work, on the TV it displayed;
stopping remote control deomon LIRC
and everything froze

Sorry if I'm not giving good info.  But I can take instruction (if it's simple enough) if you care to pursue this further.

thanks for your time!

---

### Post by Crakie on 2008-05-06
I am not surprised the xorg.conf you tried, ended up displaying on the TV only. You are not telling X that there is also a monitor attached (and should be used!). I suggest you model your xorg.conf after the one I posted a few posts up. I am not sure if you understand the structure of it, but I will guide you through it if necessary. Since I am a *bit* lazy ;) I will just give a few pointers now.

* In the "Serverlayout" section (at the top in mine), you define the screens you need, which would be "screen0" and "screen1" (or whatever names you prefer). You also define their relative orientation using LeftOf or RightOf.

* For each screen, there should be a screen, monitor and device section. In the "screen0" section you identify a monitor and a device name, as in for example:

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"

which gives a device section with Identifier "Videocard0" and a monitor section "Monitor0". Again, you are free to choose the names within the "" as long as they match eachother in the different sections.

* For the normal monitor use the sections of the xorg.conf you use now and for the tv, use the one the that failed. Combined, they should work, if you crossreference correctly.

I hope this helps.

---

### Post by tommie74 on 2008-05-06
I am trying to get X running on pvr-350, but so far have no success. I can, with my normal xorg.conf, watch tv-shows on te tv-out of the pvr-350. When I select to watch tv in Mythbuntu the the monitor goes black, and the tv goes from black to showing the tv program. When I hit escape, the tv goes black, and I am back on the monitor watching the mythbuntu gui interface.

But I want this as a standalone tv-box. So I tried to configure xorg.conf according to the wiki so that X also displays on the tv.

I have some abnormalities.

```
pvr@tvpc:~$ cat /var/log/messages |grep "TV out"
pvr@tvpc:~$
```

No output there..

```
pvr@tvpc:~$ lspci | grep "Internext Compression"
00:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
00:09.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
pvr@tvpc:~$
```

Double output there.. I think this might be because my VIA PC2500 motherboard has an mpeg decoder onboard?

Further, when I shutdown my computer first my monitor turns black, and then the ubuntu splash screen with the bar showing progress actually shows on the tv screen before the computer finally shuts down completely.

I tried both bus adresses in the xorg.conf:
0:8:0
0:9:0

But no success so far.

I have PAL coming in from cable.

The xorg.conf I tried was:
```
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

# Almost standard keyboard 
# Note: This setup doesn't require the keyboard to be present

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

# Almost standard mouse pointer
# Note: This setup doesn't require the mouse to be present

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"

        # the driver we installed - in Gutsy, this is NOT "ivtvdev".
        Driver "ivtv" 

        # frame buffer we found above
        Option "fbdev" "/dev/fb0"    
     
        # below settings are optional I've seen lots of people with them commented out.
        # I believe that pal users should just comment below line out.
        #Option "TVStandard" "NTSC-M"
        Option "VideoOverlay" "on"
        Option "XVideo" "1"

        # Not optional setting
        # BusID we found with lspci converted as shown above
        BusID "PCI:0:9:0"           

        Screen 0

EndSection

# these settings are generic (for TVs) but are specifically for TV

#Section "Monitor"
#        Identifier "TV"
#        HorizSync 30-68
#        VertRefresh 50-120
#        DisplaySize 183 122
#        Mode "720x480"
#        DotClock 34.564
#        HTimings 720 752 840 928
#        VTimings 480 484 488 504
#        Flags "-HSync" "-VSync"
#        EndMode


        # for pal users:
        Section "Monitor"
               Identifier  "TV"
               HorizSync  30-68
               VertRefresh 50-120
               Mode "720x576"
               D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
               DotClock 41.476
               HTimings 720 752 840 928
               VTimings 576 580 584 600
               Flags    "-HSync" "-VSync"
               EndMode
        EndSection
        #for pal users more settings: http://www.mythtv.org/wiki/index.php/XV_on_PVR-350#PAL 

        # Sorry SECAM users I don't have the codes for that but I did see them on the web
        # So seek and you will find.  There are some resources at the bottom of this 
        # webpage to help out.

#EndSection


# Our PVR-350 Driver entry
Section "Screen"
        Identifier "TV Screen"
        Device "Hauppauge PVR 350 iTVC15 Framebuffer"
        Monitor "TV"
        DefaultDepth 24
        DefaultFbbpp 32
        Subsection "Display"
              Depth 24
              FbBpp 32
              Modes "720x480"
        EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "TV Screen"

        # There is other ways to get rid of keyboard and mouse, but you can these settings as is.
        # This setup is designed to run without keyboard and mouse plugged in.
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

#Section "DRI"
#        Mode    0666 # Not specifically needed as far as I know. 
#                     # I think it's specific to my computer's hardware
#                     # That said all my ubuntu boxes have this line.

EndSection
```

Anybody an idea what to do?

PS, when I shutdown the computer, first my monitor turns black, and then I can actually see the ubuntu splash on the tv before the computer shuts down totally.

---

### Post by boca raton on 2008-05-06
I followed crakie's suggestions for xorg.conf, modified for ntsc and my installation.

But I still get results exactly like tommie74.  (Except I get a single "Internext Compression" response as opposed to his 2 responses)

My goal is like tommie74, to see ALL of the desktop, menus and tv out on the tv set thru the PVR-350 tv output.  That is, no PC monitor connected.

So, common symptoms, perhaps a common solution?  

Any ideas?   :)

Below is my xorg.conf file;

#test xorg.conf file
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
                         #pc monitor
    Screen      1  "Screen1" RightOf "Screen0"
                         #tv
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
 Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
EndSection

Section "Monitor"
        Identifier  "TV"
        HorizSync  30-68
        VertRefresh 50-120
      Mode "720x480"
           DotClock 34.564
           HTimings 720 752 840 928
           VTimings 480 484 488 504
           Flags    "-HSync" "-VSync"
        EndMode
EndSection

Section "Device"
        Identifier "HauppaugePVR"
        Driver "ivtvdev"
        Option "fbdev" "/dev/fb0"
        Option "VideoOverlay" "on"
        Option "TVStandard" "NTSC-M"
        Option "XVideo" "1"
        BusID  "1:9:0"
EndSection

Section "Screen"
  Identifier "Screen1"
  Device "HauppaugePVR"
 Monitor "TV"
  DefaultDepth 24
  DefaultFbbpp 32
  Subsection "Display"
    Depth 24
    FbBpp 32
  EndSubsection
EndSection

---

### Post by tommie74 on 2008-05-07
Well Boca,
I think I found a sollution that is rather rigorous, but in the end might be easier. I have decided to go for Mythdora5 which comes with a gui for pvr 350 tvout. In the mythdora forum I read minor problems getting this to run, so I will give it a try. Will let you know the results.

---

### Post by Crakie on 2008-05-07
Hmmm. I reviewed your xorg.conf, Boca, and it seems to be ok. Perhaps you can post the output of /var/log/xorg.0.log when you boot with this xorg.conf

Yours, Tommie74, lacks a second entry for a screen in the ServerLayout section (and maybe more, but I stopped right there ;)).

Incidentally, I also have that odd phenomenon of changing screens. When I boot, the kernel messages fly by on the tv with the monitor black. When the splash pops up, it shows on the monitor with the tv black. Then I login and I get two X screens as desired. When I shutdown, the reverse happens - so to speak.

---

### Post by trubblemaker on 2008-05-07
boca raton:  What I meant was boot into a shell.  (Recovery Mode is I think the option... if you use grub, the one below what you normally choose) 
I can't remeber the boot option for doing that.  
Also The command is 'X' not 'x'.  This will give you verbose output from Xorg as to why your failing.  Unfortunately when I was trying to debug Ubuntu kept fainling and automatically failing over to my Monitor that I had installed.  This was problematic as it over wrote my xorg.0.log making it impossible for me to tell why it failed.

Booting into a shell and Manually starting X solved that issue and displayed the reasons why to the screen.  That was very helpful for debugging and showed me that I was missing only a 'S'

I also got the same behavoiur with the screen shutting down on the TV that is how I knew that I could get X on the TV.


boca raton: if you are wanting both X and play back on your TV you will have to re-change your xorg.conf back to the original configuration, the xorg.conf that Crakie pointed to you is a setup for dual monitors.

---

### Post by tommie74 on 2008-05-07
I have tried Mythdora, but that was no succes either. Then I learned that Mythbuntu 8.04 also has the option to choose for pvr 350 during installation. I am used to working on Xubuntu so, Mythbuntu is easier to manouvre for me. Back again, but with a bit of experience.

In Mythdore I had running both X and the video output on the tv. But, I was missing the sound. In 7.10 Mythbuntu I had the video output on the tv with sound, the rest on the monitor. The 8.04 Mythbuntu and the Mythdora seem to have problems with the xmltv data I am used to grab, it isn't accepted anymore by mythfilldatabase.

So far my update. This was the xorg.conf that in Mythdora gave me both video and X on the tv, I thought it might be of use. I had to tweak it a littel though to get it running. I changed "fb1" to "/dev/fb" I had to put a # in front of display size.

```
# XFree86 4 configuration created by pyxf86config

Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Module"
Load "dbe"
Load "extmod"
Load "freetype"
Load "type1"
EndSection

Section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "Monitor"
Identifier "PAL Monitor"
HorizSync 30-68
VertRefresh 50-120

Mode "720x576"
# DisplaySize 182 121
# Could also be 183 122
# D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
DotClock 41.476
HTimings 720 752 840 928
VTimings 576 580 584 600
Flags "-HSync" "-VSync"
EndMode
EndSection

Section "Device"
Identifier "Hauppauge PVR 350 iTVC15 Framebuffer"
Driver "ivtv"
Option "fbdev" "/dev/fb"
Option "VideoOverlay" "on"
Option "XVideo" "1"
BusID "PCI:0:9:0"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Hauppauge PVR 350 iTVC15 Framebuffer"
Monitor "PAL Monitor"
DefaultDepth 24
DefaultFbbpp 32
Subsection "Display"
Depth 24
FbBpp 32
Modes "720x576"
EndSubsection
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection
```

Then this xorg.conf got it running. No sound though.

On the Mythdora website it says that pvr 350 users should during installation add the ivtv_xdriver and video4linux packages when willing to use tv-out. I only installed the ivtv_xdriver later, and not the video4linux. That might have been the reason for the lack of sound.. not sure though.

Right now, I can't get the listings..

---

### Post by trubblemaker on 2008-05-07
tommie74 I'm not really sure if your post is ontopic ?  Could you please post your need for help on listing on a new thread?

---

### Post by boca raton on 2008-05-07
trubblemaker (like the name)
I think tommie74 and I are trying for the same end result, reference posts 87 and 88.

Thanks for the details regarding boot and starting X manually.  I will try it this evening.

Thanks again!

---

### Post by tommie74 on 2008-05-07
> **trubblemaker said:**
> tommie74 I'm not really sure if your post is ontopic ?  Could you please post your need for help on listing on a new thread?

Sorry about that, the listings is off topic (edit: and is solved now, new version of mythfilldatabase --file needs a little different input), it was just a remark. The rest of the mail is on topic, because I am still trying to get mythbuntu (X) running on the tv-out of a pvr 350.

---

### Post by tommie74 on 2008-05-07
I have put this post also in another thread which is specifically about getting tv-out working in Mythbuntu 8.04. 
[http://ubuntuforums.org/showthread.php?t=780229&page=2](http://ubuntuforums.org/showthread.php?t=780229&page=2)
Correct me if I am wrong, but maybe people should follow the discussion there from now on if they use 8.04, not to mix different versions up?

Anyhow,
I am still trying to get the tv-out of the PVR 350 to work in Mythbuntu 8.04. The goal is to get both the video on the tv-screen using and the X session.

Machinery:
VIA PC2500 mainboard, 1Gig memory, built in video with mpeg decoder
PVR 150
PVR 350
connection to pc via ssh and vnc
TV is PAL, europe.

As a basis I used the following howto from Mythbuntu 7.1:
[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

dmesg gives (selected the parts that seemed interesting):
```
[   33.705897] ivtv:  Start initialization, version 1.1.0
[   33.706129] ivtv0: Initializing card #0
[   33.706139] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   33.757847] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 16 (level, low) -> IRQ 19
[   33.839418] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   33.956056] tveeprom 1-0050: Hauppauge model 26134, rev F1B3, serial# 10200854
[   33.956066] tveeprom 1-0050: tuner model is TCL M2523_3DB_E (idx 113, type 55)
[   33.956074] tveeprom 1-0050: TV standards PAL(B/G) PAL(D/D1/K) (eeprom 0x44)
[   33.956081] tveeprom 1-0050: audio processor is CX25842 (idx 36)
[   33.956087] tveeprom 1-0050: decoder processor is CX25842 (idx 29)
[   33.956093] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   33.956101] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   33.956106] ivtv0: Reopen i2c bus for IR-blaster support
[   35.557466] input: Power Button (FF) as /devices/virtual/input/input3
[   35.573211] ACPI: Power Button (FF) [PWRF]
[   35.573406] input: Power Button (CM) as /devices/virtual/input/input4
[   35.588833] ACPI: Power Button (CM) [PWRB]
[   35.589066] input: Sleep Button (CM) as /devices/virtual/input/input5
[   35.607542] ACPI: Sleep Button (CM) [SLPB]
[   36.284626] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   39.944628] cx25840 1-0044: cx25842-24 found @ 0x88 (ivtv i2c driver #0)
[   40.378764] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   40.538341] tuner-simple 1-0061: type set to 55 (TCL 2002MB)
[   40.538351] tuner 1-0061: type set to TCL 2002MB
[   40.539046] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   40.539077] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   40.539105] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   40.539133] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   40.539139] ivtv0: Initialized card #0: Hauppauge WinTV PVR-150
[   40.539333] ivtv1: Initializing card #1
[   40.539341] ivtv1: Autodetected Hauppauge card (cx23415 based)
[   40.579048] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 20
[   40.586053] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   40.770325] tveeprom 2-0050: Hauppauge model 48134, rev J342, serial# 7067163
[   40.770336] tveeprom 2-0050: tuner model is Temic 4009FR5 (idx 42, type 20)
[   40.770343] tveeprom 2-0050: TV standards PAL(B/G) (eeprom 0x04)
[   40.770350] tveeprom 2-0050: audio processor is MSP4418 (idx 25)
[   40.770356] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   40.770363] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   40.770370] ivtv1: Autodetected Hauppauge WinTV PVR-350
[   41.729721] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   42.224925] parport_pc 00:0a: reported by Plug and Play ACPI
[   42.224979] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   42.314415] usbcore: registered new interface driver libusual
[   42.366508] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #1)
[   42.417590] Initializing USB Mass Storage driver...
[   42.425567] scsi4 : SCSI emulation for USB Mass Storage devices
[   42.433878] usbcore: registered new interface driver usb-storage
[   42.433892] USB Mass Storage support registered.
[   42.434135] usb-storage: device found at 2
[   42.434139] usb-storage: waiting for device to settle before scanning
[   42.989890] saa7127 2-0044: saa7127 found @ 0x88 (ivtv i2c driver #1)
[   43.052963] msp3400 2-0040: MSP4418G-A2 found @ 0x80 (ivtv i2c driver #1)
[   43.052972] msp3400 2-0040: MSP4418G-A2 supports nicam and radio, mode is autodetect and autoselect
[   43.061541] tuner-simple 2-0061: type set to 20 (Temic PAL_BG (4009 FR5) or PAL_I (4069 FR5))
[   43.061552] tuner 2-0061: type set to Temic PAL_BG (4009 
[   43.072625] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   43.072683] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   43.072736] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   43.072784] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   43.072831] ivtv1: Registered device radio1 for encoder radio
[   43.072876] ivtv1: Registered device video17 for decoder MPG (1024 kB)
[   43.072932] ivtv1: Registered device vbi9 for decoder VBI (64 kB)
[   43.072978] ivtv1: Registered device vbi17 for decoder VOUT
[   43.073025] ivtv1: Registered device video49 for decoder YUV (1024 kB)
[   43.073031] ivtv1: Initialized card #1: Hauppauge WinTV PVR-350
[   43.073729] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   43.073745] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 21
[   43.073902] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   43.590830] ivtv:  End initialization

[   63.187448] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   63.385451] ivtv0: Encoder revision: 0x02060039

[  949.839326] saa7127 2-0044: saa7127 found @ 0x88 (ivtv i2c driver #1)
[ 1013.598034] saa7127 2-0044: saa7127 found @ 0x88 (ivtv i2c driver #1)
```

lsmod:
```
$ lsmod | grep ivtvfb
ivtvfb                 16028  1 
ivtv                  140352  2 ivtvfb
```
(It seems that ivtv_fb has been replaced by ivtvfb in Hardy)

/dev/video?
```
pvr@tvpc:~$ ls /dev | grep video
video0
video1
video17
video24
video25
video32
video33
video49
```
Which says I have to Settings &#8594; TV Settings &#8594; Playback there set Use PVR-350 Out, and insert /dev/video17

I have added a line to /etc/modprobe.d
"options ivtvfb osd_compat=1"
for I am using PAL, dont know if ivtvfb supports this though..

I get a nice set of colored vertical bars if I do:
```
pvr@tvpc:~$ sudo rmmod saa7127
pvr@tvpc:~$ sudo modprobe saa7127 test_image=1
```

Watching a show with Mythbuntu black the monitor screen and on the tv with the tv-out gives a black screen with some diagonal white lines. This makes me suspect that PAL is not setup correctly. Previously I had a Mythbuntu 7.1 install that after following the howto until here displayed shows in Mythbuntu perfectly on the tv, not X though. So the howto is not accurate for 8.04 yet.

This is where I get stuck in this howto. 

The next step in the howto involves installing X drivers for ivtv to get the X session to display on the tv too. I don't know wether this is needed in Mythbuntu 8.04 or not, and if such a driver is already availeable. I did have X on the tv with the newest Mythdora. That distribution needs installing two drivers by hand when using the PVR 150, namely the ivtv_xdriver and the video4linux. Maybe this is needed in Mythbuntu too. 

All help is very welcome, I am not a linux crack, so it is kind of hard to crack this nut for me.

---

### Post by boca raton on 2008-05-07
Lest we forget; this is with Mythbuntu 8.04 with a PVR-350.

I restored xorg.conf to original.  Booted into recovery mode (I don't remember using recovery in 3 years with Linux ... hmmmm makes things here seem pretty stable compared to some other os's)  

On the first attempt, the monitor (PC) scrolled much text until it got to '[19.567259] fuse init (API version 7.9) Done.' And it stopped doing anything.  I had the TV off.

Second attempt, I turned on the TV, the monitor scrolled much text to '[42.9 ....]' and then the TV displayed a Recovery Menu.  

Selected 'Root Shell' and text quickly scrolls past on the TV, and it displays a '_'cursor.  Then the monitor displays colored hash with an X for a mouse cursor, and nothing.  

I ALT/CTL/F3 then the monitor displays the previous text, the last line is [42.965043] ivtvfb0: frame buffer @ 0xf1510000, mapped to 0xd9b10000 size 1665k.

I CTL/ALT/F2 (planning on shutting down) and the monitor is a gray screen with a 'X' mouse cursor.  ?

I pull the AC plug to shut down the box.

Does this indicate what is happening?  Is there anything else I can do to get more / better information on what is / is not happening?

Thanks for your time and help!

my Xorg.0.log;

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux myth-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM

        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  8 16:45:40 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
        Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
        Using the first keyboard device.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 2.0
        X.Org XInput driver : 2.0
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7120 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7121 card 8086,4332 rev 03 class 03,00,00 hdr 00
(II) PCI: 00:1e:0: chip 8086,2418 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2410 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2411 card 8086,2411 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2412 card 8086,2412 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2413 card 8086,2413 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:08:0: chip 168c,0013 card 1948,3a02 rev 01 class 02,00,00 hdr 00
(II) PCI: 01:09:0: chip 4444,0803 card 0070,4000 rev 01 class 04,00,00 hdr 00
(II) PCI: 01:0b:0: chip 1274,1371 card 1274,1371 rev 09 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xff800000 - 0xff8fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xeea00000 - 0xf6afffff (0x8100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:1:0) Intel Corporation 82810 (CGC) Chipset Graphics Controller rev 3, Mem @ 0xf8000000/26, 0xffa80000/19
(--) PCI: (1:9:0) unknown vendor (0x4444) unknown chipset (0x0803) rev 1, Mem @ 0xf0000000/26
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
(II) Active PCI resource ranges:
        [0] -1  0       0xff8e0000 - 0xff8effff (0x10000) MX[B]
        [1] -1  0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)

        [2] -1  0       0xffa80000 - 0xffafffff (0x80000) MX[B](B)
        [3] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [4] -1  0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [5] -1  0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [6] -1  0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [7] -1  0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xff8e0000 - 0xff8effff (0x10000) MX[B]
        [1] -1  0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [2] -1  0       0xffa80000 - 0xffafffff (0x80000) MX[B](B)
        [3] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [4] -1  0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [5] -1  0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [6] -1  0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [7] -1  0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
      [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff8e0000 - 0xff8effff (0x10000) MX[B]
        [5] -1  0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [6] -1  0       0xffa80000 - 0xffafffff (0x80000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [9] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [10] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [11] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [12] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [13] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        Module class: X.Org Server Extension
       ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.4.0.90, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.13.0
        Module class: X.Org Server Extension
      ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 2.2.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.4.0, module version = 1.2.3
       Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.4.0, module version = 1.2.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:01:0
(--) Assigning device section with no busID to primary device
(--) Chipset i810 found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff8e0000 - 0xff8effff (0x10000) MX[B]
       [5] -1  0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [6] -1  0       0xffa80000 - 0xffafffff (0x80000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [9] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [10] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [11] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [12] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [13] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff8e0000 - 0xff8effff (0x10000) MX[B]
        [5] -1  0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [6] -1  0       0xffa80000 - 0xffafffff (0x80000) MX[B](B)
        [7] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [8] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [9] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [10] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]

        [11] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [12] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [13] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [14] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [15] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [16] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [17] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [18] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 0.1.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 16/16
(==) intel(0): Depth 16, (==) framebuffer bpp 16
(==) intel(0): RGB weight 565
(==) intel(0): Default visual is TrueColor
(II) Loading sub module "xaa"

(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.2.0
        ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.1.0
        ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 1024 kB
(II) intel(0): VESA VBE OEM: Intel(R) 8xx Chipset Video BIOS
(II) intel(0): VESA VBE OEM Software Rev: 34.41
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(R) 8xx Chipset
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) intel(0): VESA VBE DDC supported
(II) intel(0): VESA VBE DDC Level none
(II) intel(0): VESA VBE DDC transfer in appr. 0 sec.
(II) intel(0): VESA VBE DDC read failed
(--) intel(0): Chipset: "i810"
(--) intel(0): Linear framebuffer at 0xF8000000
(--) intel(0): IO registers at addr 0xFFA80000
(II) intel(0): Kernel reported 81920 total, 1 used
(II) intel(0): I810CheckAvailableMemory: 327676k available
(==) intel(0): Will alloc AGP framebuffer: 24576 kByte
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(II) intel(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) intel(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(WW) intel(0): Unable to estimate virtual size
(II) intel(0): Clock range:   9.50 to 163.00 MHz
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)

(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "640x480" (hsync out of range)
(II) intel(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (hsync out of range)
(II) intel(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (unknown reason)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "832x624" (hsync out of range)
(II) intel(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x768" (hsync out of range)
(II) intel(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1280x800" (hsync out of range)
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x768" (hsync out of range)
(II) intel(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) intel(0): Virtual size is 800x600 (pitch 1024)
(**) intel(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) intel(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) intel(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
       compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(**) intel(0): page flipping disabled
(II) intel(0): XvMC is Disabled: use XvMCSurfaces config option to enable.
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xffa80000 - 0xffafffff (0x80000) MS[B]
        [1] 0   0       0xf8000000 - 0xfbffffff (0x4000000) MS[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xff8e0000 - 0xff8effff (0x10000) MX[B]
        [7] -1  0       0xf0000000 - 0xf3ffffff (0x4000000) MX[B](B)
        [8] -1  0       0xffa80000 - 0xffafffff (0x80000) MX[B](B)
        [9] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [10] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [11] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [12] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [16] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [17] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [18] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [19] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [20] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:01.0
drmOpenByBusid: Searching for BusID pci:0000:00:01.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
(II) [drm] loaded kernel module for "i810" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer handle = 0xf8000000
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(II) intel(0): [drm] Registers = 0xffa80000
(II) intel(0): [agp] dcacheHandle : 0x0
(II) intel(0): [agp] GART: no dcache memory found
(II) intel(0): [agp] Bound backbuffer memory
(II) intel(0): [agp] Bound depthbuffer memory
(II) intel(0): [agp] Bound System Texture Memory
(II) intel(0): [agp] GART: Allocated 4K for mouse cursor image
(II) intel(0): [agp] GART: Allocated 16K for ARGB mouse cursor image
(II) intel(0): Adding 768 scanlines for pixmap caching
(II) intel(0): Allocated Scratch Memory
(II) intel(0): [dri] Buffer map : 149b000
(II) intel(0): [drm] added 256 4096 byte DMA buffers
(II) intel(0): [drm] Init v1.4 interface.
(II) intel(0): [drm] dma control initialized, using IRQ -22
(II) intel(0): [dri] visual configs initialized.
(==) intel(0): Write-combining range (0xf8000000,0x4000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) intel(0): Setting dot clock to 40.0 MHz [ 0x8 0x1 0x30 ] [ 10 3 3 ]
(II) intel(0): chose watermark 0x22007000: (tab.freq 40.0)
(II) intel(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Horizontal and Vertical Lines
        Setting up tile and stipple cache:
                28 128x128 slots
                6 256x256 slots
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): DPMS enabled
(II) intel(0): [DRI] installation complete
(II) intel(0): Direct rendering enabled
(WW) intel(0): Option "UseFBDev" is not used
(==) RandR enabled
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
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:01.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:01.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i810_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded





T

---

### Post by tommie74 on 2008-05-08
> **boca raton said:**
> I am using a PVR 350 on Mythbuntu 8.04.

I am using the 350 tv output for TV and a monitor to set up the pc. I have tv output showing on the TV but I can not get x to the TV.  It's a PIII 1.2 Ghz box with about 350 Meg of memory.

I've tried most of the recommendations in this thread, religiously I might add, with no success. (not to say I havn't missed something in my observance!)  

There appear to be differences in the solutions to this as myth and Ubuntu have progressed thru their versions.  Does 8.04 need to be 'massaged' as with previous examples in this thread or am I just not using the configuration and setup menus in 8.04 correctly?
 
Help is appreciated!

Hello Boca Raton,
what steps did you take to get the tv output to the tv?

---

### Post by Crakie on 2008-05-08
Boca,

As I said, the xorg.conf that you modelled after mine seemed to be ok. I think getting that cursor on tv is a good sign. My first step to go from there would be to read xorg.0.log in /var/log. With a non-functional machine using that xorg.conf, this is tricky though. You could boot with the xorg.conf that seems to be ok, switch off and then use a live CD to get to it. It may also be useful to know the one-but-last bootlog of X is stored in xorg.0.log.old.

I went through this exact phase, except I my case I could boot into recovery mode, shown on the tv (and a black monitor). I twisted my neck reading from the tv and typing commands on the keyboard located at the other side of the room ;)

One other thing. It occurred to me that using KDE was helpful to me. Once I got xorg.conf set up properly, I did not have to do anything to get KDE on the extra screens. As soon as KDE detects an X screen, it will use it to put KDE menus/taskbars/what not on it. Other desktop environments may have to 'encouraged' to do so with some additional editing.

In case you are wondering, I am still using Kubuntu Feisty. I'll upgrade to Hardy as soon as I am done moving... but I expect some trouble setting it up the way I have it now ;)

---

### Post by boca raton on 2008-05-08
> **tommie74 said:**
> Hello Boca Raton,
what steps did you take to get the tv output to the tv?

In the setup menus, utilities/setup > setup > TV settings > playback > on 9 of 9 select 'Use PVR 350 output' 

Then in utilities/setup > setup > appearance > on 'video mode settings' select 'separate video modes for gui and playback  

And during installation of Mythbuntu 8.04, at the choice for 'special' video drivers, I chose the PVR-350.

So far so good.

---

### Post by tommie74 on 2008-05-10
> **boca raton said:**
> In the setup menus, utilities/setup > setup > TV settings > playback > on 9 of 9 select 'Use PVR 350 output' 

Then in utilities/setup > setup > appearance > on 'video mode settings' select 'separate video modes for gui and playback  

And during installation of Mythbuntu 8.04, at the choice for 'special' video drivers, I chose the PVR-350.

So far so good.

Hi Boca,
thx for the answer. As you probably have read in another thread I ran into some hardware trouble. That was just more trouble than I was waiting for. So I skipped the project. Maybe some other time I will try again. I am sure with patience you will get it working. It is possible. 
greetings Thomas.

---

### Post by jswinghammer on 2008-06-28
Hi,

First I'd like to say thanks for the very nice HOW-TO it's gotten me pretty far in this process.

I'm using Mythbuntu and I'm trying to get my PVR-350 to display on the TV instead of a monitor I have connected to it. I was able to find out that it is in on /dev/fb0 and that it's PCI bus id is: 0x04:0x08:0x00. I see a cursor on the screen when X is running and when it's booting and shutting down I'll see messages that look like normal Linux boot text.

I did the test to make the colored lines appear on the screen so I believe the driver is loaded and the card is working properly. My problem is that when X starts it says that it's going to run in low res mode and then eventually loads up the standard display on the monitor. I should be clear to say that at no time does X appear on the TV itself.

My questions are: is there probably something obvious that I missed here or is it a setting in MythTv to get that to work properly?

Thanks for the help, in advance.

Jon

---

### Post by trubblemaker on 2008-06-30
No there isn't some obvioius way to tell, 

What I'd suggest doing is booting into a terminal and start x manually from the command line:
```
x
```
This will let you see why that X is failing and booting into "low res" mode.

Post the output from starting x if you need help.

---

### Post by trubblemaker on 2008-06-30
I don't remeber the exact name off the top of my head, but on boot choose the boot option below your regular kernal It might be called <kernel> (Recovery) .

---

### Post by Crakie on 2008-07-07
[https://help.ubuntu.com/community/WikiGuide/Ubuntu_Hardy_Hauppauge350_X_on_your_TV_OUT]("https://help.ubuntu.com/community/WikiGuide/Ubuntu_Hardy_Hauppauge350_X_on_your_TV_OUT")

I created a wiki for Hardy Heron, as there were minor but important differences with Gutsy. Feel free to add/edit :)

---

### Post by trubblemaker on 2008-07-08
Thanks for adding to the wiki!

---

### Post by dallas8101 on 2008-07-21
Crakie, 
thanks for the Hardy wiki doc.  Unfortunately, I have still not had success, running on 8.04.1.  I have followed the doc and my results so far are that the xorg.conf file is accepted (no longer showing up as xorg.conf.broken after a reboot), I get the Myth TV and "Watch Videos/Recordings" to play on the PVR350 TV Out.  The audio comes out the PVR 350, not the mother board audio. The VLC player audio output comes out the  motherboard but not the PVR350, and the video is on the screen 0 default screen not the TV.  The TV displays a picture of a little mouse with the letter XFCE beneath it. 

 The xorg.0.log shows:
 (++) IVTV(1): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(**) IVTV(1): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Reloading /usr/lib/xorg/modules//libshadow.so
(--) Depth 24 pixmap format is 32 bpp  

I get a line that does not seem correct to me in the xorg log:
(II) IVTV(1): Linked framebuffer 'dev/fb0' to yuv device '/dev/video48'

I would have thought that should be video16.
Later I get:
(II) IVTV(1): Enabling Xv support for PVR350

However, I never get the Myth display on the PVR, only the video.
I am still a bit of a noob, so I do not know what else you might need to be able to help.  
Thanks.

---

### Post by dallas8101 on 2008-07-22
Some additional information from the Xorg.0.log shows a couple of warnings:

(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945G Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945G Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xc0000000, size: 0x7b0000
(II) VESA(0): Splitting WC range: base: 0xc0400000, size: 0x3b0000
(II) VESA(0): Splitting WC range: base: 0xc0600000, size: 0x1b0000
(II) VESA(0): Splitting WC range: base: 0xc0700000, size: 0xb0000
(II) VESA(0): Splitting WC range: base: 0xc0780000, size: 0x30000
(==) VESA(0): Write-combining range (0xc07a0000,0x10000)
(==) VESA(0): Write-combining range (0xc0780000,0x30000)
(==) VESA(0): Write-combining range (0xc0700000,0xb0000)
(==) VESA(0): Write-combining range (0xc0600000,0x1b0000)
(==) VESA(0): Write-combining range (0xc0400000,0x3b0000)
(WW) VESA(0): Failed to set up write-combining range (0xc0000000,0x7b0000)
(II) VESA(0): virtual address = 0xb71d6000,
        physical address = 0xc0000000, size = 8060928
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) IVTV(1): bitsPerPixel=32, depth=24, defaultVisual=TrueColor
        mask: ff0000,ff00,ff, offset: 16,8,0
(II) IVTV(1): Screen init width 720 height 480 virtual 720 480
(==) IVTV(1): Backing store disabled
(II) IVTV(1): DPMS enabled
(II) IVTV(1): Init Video
(II) IVTV(1): Enabling Xv support for PVR350
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) AIGLX: Screen 1 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 1
(WW) Configured Mouse: No Device specified, looking for one...

Some output from dmsg:

[   25.277576] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   25.280344] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.280354] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   25.281009] Attansic(R) L2 Ethernet Network Driver - version 1.0.40.2
[   25.281010] Copyright (c) 2006 Attansic Corporation.
[   25.357595] tveeprom 0-0050: Hauppauge model 48132, rev K168, serial# 7378437
[   25.357599] tveeprom 0-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   25.357601] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   25.357602] tveeprom 0-0050: audio processor is MSP4448 (idx 27)
[   25.357604] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[   25.357605] tveeprom 0-0050: has radio, has IR receiver, has no IR transmitter
[   25.357608] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   25.408783] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   25.408799] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   25.408801] tuner 0-0043: type set to tda9887
[   25.411988] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   25.474957] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   25.703600] saa7127 0-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[   25.720362] msp3400 0-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   25.720366] msp3400 0-0040: MSP4448G-A2 supports radio, mode is autodetect and autoselect
[   25.750185] tuner-simple 0-0061: type set to 47 (LG NTSC (TAPE series))
[   25.750188] tuner 0-0061: type set to LG NTSC (TAPE serie
[   25.760525] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   25.760539] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   25.760552] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   25.760566] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   25.760581] ivtv0: Registered device radio0 for encoder radio
[   25.760594] ivtv0: Registered device video16 for decoder MPG (1024 kB)
[   25.760607] ivtv0: Registered device vbi8 for decoder VBI (64 kB)
[   25.760619] ivtv0: Registered device vbi16 for decoder VOUT
[   25.760635] ivtv0: Registered device video48 for decoder YUV (1024 kB)
[   25.760637] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350

I have not been able to determine if the Xorg log warnings and not being DRI capable indicate my problem or not.

Does anyone have any suggestions?

---

### Post by dallas8101 on 2008-07-22
I found that I could not use the dual display setup in the HowTo.  I had to go to the single output display shown in message 27 and/or 28 of [http://ubuntuforums.org/showthread.php?t=780229&page=3](http://ubuntuforums.org/showthread.php?t=780229&page=3)

I now get everything output to the TV-Out, but the overscan is pretty bad.  I have tried the Appearance settings, and have gotten the Windowed Myth GUI to shrink down to size.  The TV image basically stays at the same dimensions as the Ubuntu OS, too large for the TV screen.  I tried xvidtune, to no avail.  It makes things a little difficult since the OS menu bar and the MCC exit buttons etc are off screen now.

Is there an overscan application for Hauppauge like the nvtv for NVidea?  Any other options?

---

### Post by Crakie on 2008-07-24
Hi dallas8101,

sorry to react so late to your posts. I am subscribed to this thread to be able to react quickly, but I happened to be on holidays. It seems you made progress anyway, although I am not sure how the dual head setup did not work for you. The videocard and the Hauppauge are two different things after all.

I'm afraid I cannot help you either on the overscan issue, as I've been extremely lucky never to have run into it. After a thorough google session, I'd suggest taking it to the ivtv mail lists.

---

