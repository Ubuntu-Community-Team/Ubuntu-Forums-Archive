---
title: "Matrox Marvel G450 TVOUT problem"
date: 2006-09-15
forum: Multimedia &amp; Video
---

### Post by hammer30 on 2006-09-15
Hi all,

i use Ubuntu 6.06 with custum kernel 2.6.17.11. In a new kernel i compieled all needed drivers for tv out as follows some "how to"

I tried to install Matrox Tvout driver:

1) i wrote a script "matroxTVOut" in /etc/init.d/ :

#!/bin/sh

. /lib/lsb/init-functions
. /etc/default/rcS

MATROXSET=/usr/bin/matroxset
FBSET=/usr/sbin/fbset
FBDEV=/dev/fb0
FBDEV2=/dev/fb1

# test to ensure that the proper tools are present
echo "Testing for matrox set"
test -f $MATROXSET || exit 0
echo "Testing for fbset"
test -f $FBSET || exit 0
echo "Testing for fbdev"
test -c $FBDEV || exit 0
echo "everything seems to be present"

case "$1" in
        start)
                log_begin_msg "Initializing Matrox TV out..."
                $MATROXSET -f $FBDEV -m 0
                $MATROXSET -f $FBDEV -m 3
                $MATROXSET -f $FBDEV -o 1 2
                $FBSET -fb $FBDEV -xres 800 -yres 600
                $FBSET -fb $FBDEV -left 54 -right 26 -lower 32 -upper 80 -hslen 40
                log_end_msg $?
                ;;
        stop)
                log_begin_msg "Stopping Matrox TV out..."
                $MATROXSET -f $FBDEV -m 0
                $MATROXSET -f $FBDEV2 -m 0
                $MATROXSET -f $FBDEV -m 1
                $FBSET -fb $FBDEV -left 0 -right 0 -lower 0 -upper 0
                log_end_msg $?
                ;;
        *)
                log_success_msg "Usage: matroxTVOut {start|stop}"
                exit 1
                ;;
esac

2) i added previous script to all "rc's "



3) i added raws to /etc/modules :

# needed for doing TVOut
mga
i2c-matroxfb
matroxfb_crtc2
matroxfb_maven

3) i edited "xorg.conf" :

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
        Identifier      "Matrox Graphics, Inc. MGA G400 AGP"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Option          "hw cursor" "off"
        Option          "UseFBDev" "on"
EndSection

Section "Monitor"
	Identifier	"L1750SQ"
	Option		"DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA G400 AGP"
        Monitor         "L1750SQ"
        DefaultDepth    16
        DefaultFbBPP    16
        SubSection "Display"
                Depth 16
                Modes "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


  After all, i restarted my system and saw strange screen om my TV - something like 9 same small screens in a one screen.

 Did i forget to add something to my files?
 Does anybody that's wrong? :)

---

### Post by hammer30 on 2006-09-15
i can't post full xorg0.log because it too long, but at the end of the log you could see some errors
:


	
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(--) MGA(0): Chipset: "mgag400" (G450)
(**) MGA(0): Depth 24, (--) framebuffer bpp 32
(==) MGA(0): RGB weight 888
(**) MGA(0): Option "OldDmaInit" "True"
(==) MGA(0): Using AGP 1x mode
(--) MGA(0): Linear framebuffer at 0xE4000000
(--) MGA(0): MMIO registers at 0xE6000000
(--) MGA(0): Pseudo-DMA transfer window at 0xE7000000
(==) MGA(0): BIOS at 0xC0000
(--) MGA(0): Video BIOS info block at offset 0x07CC0
(--) MGA(0): VideoRAM: 32768 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) MGA(0): I2C bus "DDC P1" initialized.
(II) MGA(0): I2C device "DDC P1:ddc2" registered at address 0xA0.
(II) MGA(0): I2C device "DDC P1:ddc2" removed.
(II) MGA(0): I2C Monitor info: 0x81f9f30
(II) MGA(0): Manufacturer: GSM  Model: 43e8  Serial#: 99954
(II) MGA(0): Year: 2005  Week: 4
(II) MGA(0): EDID Version: 1.3
(II) MGA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) MGA(0): Sync:  Separate  Composite  SyncOnGreen
(II) MGA(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) MGA(0): Gamma: 2.20
(II) MGA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) MGA(0): First detailed timing is preferred mode
(II) MGA(0): redX: 0.641 redY: 0.342   greenX: 0.292 greenY: 0.611
(II) MGA(0): blueX: 0.147 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) MGA(0): Supported VESA Video Modes:
(II) MGA(0): 720x400@70Hz
(II) MGA(0): 640x480@60Hz
(II) MGA(0): 640x480@75Hz
(II) MGA(0): 800x600@60Hz
(II) MGA(0): 800x600@75Hz
(II) MGA(0): 832x624@75Hz
(II) MGA(0): 1024x768@60Hz
(II) MGA(0): 1024x768@75Hz
(II) MGA(0): 1280x1024@75Hz
(II) MGA(0): 1152x870@75Hz
(II) MGA(0): Manufacturer's mask: 0
(II) MGA(0): Supported Future Video Modes:
(II) MGA(0): #0: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) MGA(0): #1: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) MGA(0): #2: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) MGA(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) MGA(0): Supported additional Video Mode:
(II) MGA(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) MGA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) MGA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) MGA(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 140 MHz
(II) MGA(0): Monitor name: L1750SQ
(II) MGA(0): Monitor name: 
(II) MGA(0): end of I2C Monitor info
(==) MGA(0): Using gamma correction (1.0, 1.0, 1.0)
(==) MGA(0): Min pixel clock is 12 MHz
(--) MGA(0): Max pixel clock is 600 MHz
(II) MGA(0): L1750SQ: Using default hsync range of 30.00-83.00 kHz
(II) MGA(0): L1750SQ: Using default vrefresh range of 56.00-75.00 Hz
(II) MGA(0): Clock range:  12.00 to 600.00 MHz
(II) MGA(0): Not using default mode "640x350" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x175" (vrefresh out of range)
(II) MGA(0): Not using default mode "640x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x200" (vrefresh out of range)
(II) MGA(0): Not using default mode "720x400" (vrefresh out of range)
(II) MGA(0): Not using default mode "360x200" (vrefresh out of range)
(II) MGA(0): Not using default mode "640x480" (vrefresh out of range)
(II) MGA(0): Not using default mode "320x240" (vrefresh out of range)
(II) MGA(0): Not using default mode "800x600" (vrefresh out of range)
(II) MGA(0): Not using default mode "400x300" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "512x384" (vrefresh out of range)
(WW) (1280x960,L1750SQ) mode clock 148.5MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1280x960" (hsync out of range)
(II) MGA(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,L1750SQ) mode clock 157.5MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1280x1024" (hsync out of range)
(II) MGA(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,L1750SQ) mode clock 162MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,L1750SQ) mode clock 175.5MHz exceeds DDC maximum 140MHz
(WW) (1600x1200,L1750SQ) mode clock 189MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,L1750SQ) mode clock 202.5MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,L1750SQ) mode clock 229.5MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1600x1200" (hsync out of range)
(II) MGA(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,L1750SQ) mode clock 204.8MHz exceeds DDC maximum 140MHz
(WW) (1792x1344,L1750SQ) mode clock 261MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1792x1344" (hsync out of range)
(II) MGA(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,L1750SQ) mode clock 218.3MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1856x1392" (hsync out of range)
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,L1750SQ) mode clock 288MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1856x1392" (hsync out of range)
(WW) (928x696,L1750SQ) mode clock 144MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,L1750SQ) mode clock 234MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1920x1440" (hsync out of range)
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,L1750SQ) mode clock 297MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,L1750SQ) mode clock 148.5MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(II) MGA(0): Not using default mode "1152x768" (vrefresh out of range)
(II) MGA(0): Not using default mode "576x384" (vrefresh out of range)
(II) MGA(0): Not using default mode "1152x864" (vrefresh out of range)
(II) MGA(0): Not using default mode "576x432" (vrefresh out of range)
(WW) (1400x1050,L1750SQ) mode clock 151MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,L1750SQ) mode clock 155.8MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,L1750SQ) mode clock 184MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1400x1050" (hsync out of range)
(II) MGA(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,L1750SQ) mode clock 147.14MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,L1750SQ) mode clock 146.25MHz exceeds DDC maximum 140MHz
(WW) (1680x1050,L1750SQ) mode clock 214.51MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1680x1050" (hsync out of range)
(II) MGA(0): Not using default mode "840x525" (hsync out of range)
(WW) (1920x1200,L1750SQ) mode clock 193.16MHz exceeds DDC maximum 140MHz
(WW) (1920x1200,L1750SQ) mode clock 230MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1920x1200" (hsync out of range)
(II) MGA(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,L1750SQ) mode clock 341.35MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1920x1440" (hsync out of range)
(WW) (960x720,L1750SQ) mode clock 170.675MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,L1750SQ) mode clock 266.95MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "2048x1536" (hsync out of range)
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,L1750SQ) mode clock 340.48MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,L1750SQ) mode clock 170.24MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,L1750SQ) mode clock 388.04MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "2048x1536" (hsync out of range)
(WW) (1024x768,L1750SQ) mode clock 194.02MHz exceeds DDC maximum 140MHz
(II) MGA(0): Not using default mode "1024x768" (hsync out of range)
(II) MGA(0): Not using mode "720x400" (no mode of this name)
(II) MGA(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) MGA(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) MGA(0): Not using default mode "1440x900" (width too large for virtual size)
(--) MGA(0): Has SDRAM
(--) MGA(0): Virtual size is 1280x1024 (pitch 1280)
(**) MGA(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 Hz
(II) MGA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) MGA(0): *Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) MGA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) MGA(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) MGA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) MGA(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) MGA(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) MGA(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) MGA(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 801 804 828
(**) MGA(0):  Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) MGA(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) MGA(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) MGA(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 769 772 795
(**) MGA(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) MGA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) MGA(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) MGA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) MGA(0):  Default mode "896x672": 102.4 MHz, 83.7 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "896x672"  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync
(**) MGA(0):  Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "960x600"   96.58  960 1024 1128 1296  600 600 602 621 doublescan
(**) MGA(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) MGA(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) MGA(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) MGA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) MGA(0):  Default mode "800x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) MGA(0): Modeline "800x600"   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) MGA(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) MGA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) MGA(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "800x600"   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync
(**) MGA(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) MGA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) MGA(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) MGA(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) MGA(0):  Default mode "840x525": 73.1 MHz, 65.3 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "840x525"   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync
(**) MGA(0):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (D)
(II) MGA(0): Modeline "700x525"   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync
(**) MGA(0):  Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (D)
(II) MGA(0): Modeline "700x525"   75.50  700 732 828 980  525 525 527 550 doublescan +hsync +vsync
(**) MGA(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) MGA(0):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "640x512"   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync
(**) MGA(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) MGA(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) MGA(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) MGA(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) MGA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) MGA(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) MGA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) MGA(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) MGA(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) MGA(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) MGA(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) MGA(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) MGA(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (D)
(II) MGA(0): Modeline "512x384"   39.40  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) MGA(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) MGA(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) MGA(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) MGA(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) MGA(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) MGA(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) MGA(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) MGA(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) MGA(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) MGA(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) MGA(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) MGA(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) MGA(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) MGA(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) MGA(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) MGA(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) MGA(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) MGA(0): Modeline "320x240"   15.75  320 332 352 416  240 244 245 260 doublescan -hsync -vsync
(**) MGA(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) MGA(0): Modeline "320x240"   12.60  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(--) MGA(0): Display dimensions: (340, 270) mm
(--) MGA(0): DPI set to (95, 96)
(II) MGA(0): YDstOrg is set to 0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe7000000 - 0xe77fffff (0x800000) MX[B]
	[1] 0	0	0xe6000000 - 0xe6003fff (0x4000) MX[B]
	[2] 0	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe9200000 - 0xe920ffff (0x10000) MX[B]
	[8] -1	0	0xe9000000 - 0xe90fffff (0x100000) MX[B]
	[9] -1	0	0xe9210000 - 0xe9210fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe7000000 - 0xe77fffff (0x800000) MX[B](B)
	[12] -1	0	0xe6000000 - 0xe6003fff (0x4000) MX[B](B)
	[13] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[20] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d03f (0x40) IX[B]
	[25] 0	0	0xe60203b0 - 0xe60203bb (0xc) IS[B](OprU)
	[26] 0	0	0xe60203c0 - 0xe60203df (0x20) IS[B](OprU)
(II) MGA(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(--) MGA(0): 16 DWORD fifo
(==) MGA(0): Default visual is TrueColor
(II) MGA(0): [drm] bpp: 32 depth: 24
(II) MGA(0): [drm] Sarea 2200+664: 2864
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenByBusid: drmOpenMinor returns 6
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) MGA(0): [drm] DRM interface version 1.2
(II) MGA(0): [drm] created "mga" driver at busid "pci:0000:01:00.0"
(II) MGA(0): [drm] added 8192 byte SAREA at 0xe8bfc000
(II) MGA(0): [drm] mapped SAREA 0xe8bfc000 to 0xb50bc000
(II) MGA(0): [drm] framebuffer handle = 0xe4000000
(II) MGA(0): [drm] added 1 reserved context for kernel
(II) MGA(0): [agp] Mode 0x1f000201 [AGP 0x1106/0x3128; Card 0x102b/0x0525]
(II) MGA(0): [agp] 12288 kB allocated with handle 0x00000001
(II) MGA(0): [agp] WARP microcode handle = 0xe0000000
(II) MGA(0): [agp] Primary DMA handle = 0xe0008000
(II) MGA(0): [agp] DMA buffers handle = 0xe0108000
(II) MGA(0): [drm] Added 128 65536 byte DMA buffers
(II) MGA(0): [agp] agpTexture handle = 0xe0908000
(II) MGA(0): [agp] agpTexture size: 2816 kb
(II) MGA(0): [drm] Registers handle = 0xe6000000
(II) MGA(0): [drm] Status handle = 0xeac75000
(II) MGA(0): [dri] visual configs initialized
(II) MGA(0): Memory manager initialized to (0,0) (1280,2047)
(II) MGA(0): Largest offscreen area available: 1280 x 1023
(II) MGA(0): Reserved back buffer at offset 0xa00000
(II) MGA(0): Reserved depth buffer at offset 0xf00000
(II) MGA(0): Reserved 12288 kb for textures at offset 0x1400000
(II) MGA(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid filled trapezoids
	8x8 mono pattern filled rectangles
	8x8 mono pattern filled trapezoids
	Indirect CPU to Screen color expansion
	Screen to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		9 256x256 slots
(==) MGA(0): Backing store disabled
(==) MGA(0): Silken mouse enabled
(**) Option "dpms"
(**) MGA(0): DPMS enabled
(II) MGA(0): Using overlay video
(II) MGA(0): X context handle = 0x1
(II) MGA(0): [drm] installed DRM signal handler
(II) MGA(0): [DRI] installation complete
(II) MGA(0): [drm] Mapped 128 DMA buffers
(II) MGA(0): [drm] dma control initialized, using IRQ 11
(II) MGA(0): Direct rendering enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /etc/X11/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

