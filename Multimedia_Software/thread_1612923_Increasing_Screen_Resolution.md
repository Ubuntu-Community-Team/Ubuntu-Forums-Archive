---
title: "Increasing Screen Resolution"
date: 2010-11-03
forum: Multimedia Software
---

### Post by chome4 on 2010-11-03
Using Jaunty. Will upgrade at a later date but for now how can I get a resolution of 1280x1024 when the highest is currently 1280x800?

---

### Post by vcrpex on 2010-11-03
sudo gedit /etc/X11/xorg.conf 

and set the monitor display to a bigger resolution like the following:

Section "Monitor"
Identifier "Configured Monitor"
	DisplaySize     1920 1080
        HorizSync       30-70
        VertRefresh     60-75
EndSection

the sync n vert is for your own monitor specs. please adjust accordingly.

---

### Post by chome4 on 2010-11-05
My xorg.conf reads:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection



If I enter 'DisplaySize 1280x1024' what's the worst that can happen? I can make a copy of the file for safekeeping but how could I restore it if for some reason the screen stays blank?

---

### Post by vcrpex on 2010-11-13
you can put as you suggested. As the worst that it can happen is that it will appear smaller.  The Displaysize is just to extend limit to what you can stretch in your screen resolution. I have tried this on jaunty, karmic and maverick. Somehow everytime I install the nvidia drivers, my screen will shrink to 640 by 480 and below. Using this, I can change my screen resolution upwards.

---

### Post by chome4 on 2010-11-17
No change, I'm afraid. My xorg.conf now reads:

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
DisplaySize 1920 1080
HorizSync 30-70
VertRefresh 60-75
EndSection

My max is still 1280x800 (16:10) with a refresh rate of 60Hz 

The particular PC I'm working on is an Advent laptop T2080

---

### Post by tommcd on 2010-11-18
You can try using **xrandr** to add undetected screen resolutions. See this tutorial on xrandr:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by chome4 on 2010-11-19
Thanks for the link. It didn't solve the problem but I'll have an upgraded Ubuntu soon.

What's strange is that under Vista, the resolution had a greater range of numbers to choose from - so the problem isn't with the hardware.

Very strange.

Thanks again.

---

### Post by naviathan on 2010-11-19
Are you running the appropriate driver for your video card?  If so, is everything working properly?  Have you checked that DRM is functioning (this is typically a sign of whether the video driver is working or not).
 
```
 glxinfo | grep rendering 
```

---

### Post by tommcd on 2010-11-20
> **chome4 said:**
> Thanks for the link. It didn't solve the problem but I'll have an upgraded Ubuntu soon.

Can you be more specific here? What is the output when you run **xrandr** in the terminal?

---

### Post by chome4 on 2010-11-20
[FONT=monospace]glxinfo | grep rendering returns:

get fences failed: -1
param: 6, val: 0
direct rendering: Yes

===================================================================

xrandr returns:

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV disconnected (normal left inverted right x axis y axis)
[/FONT]

---

### Post by tommcd on 2010-11-21
So what exactly did you try before concluding that xrandr did not work? Did you try anything at all?
What happens if you run:
```
xrandr --newmode 1280x1024
```
or
```
xrandr --addmode 1280x1024
```
You may need to add  
Then run:
```
xrandr --output LVDS --mode 1280x1024
```
Please read the tutorial on xrandr that I linked to, and try to use xrandr as per those examples in the tutorial. 
when you reply, try to provide as much info as possible instead of just "*It didn't solve the problem*". I have never hard to use xrandr myself, so I am not sure what the expected outputs would be from using it.

---

### Post by chome4 on 2010-11-22
I did try and enter "1280x1024", which is within the 'max' level, but it says 'not available.

---

### Post by tommcd on 2010-11-22
> **chome4 said:**
> I did try and enter "1280x1024", which is within the 'max' level, but it says 'not available.
As per the tutorial I linked to, first use **gtf** or **cvt** to create a modeline for 1280x1024 like this:
```

tom[data]$ cvt 1280 1024 60
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```
Then try to add the mode with xrandr like this:
```

xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

```
Note: Use the output that you get from cvt , not what I have posted here. Do not include the line that starts with the #.
Then use the --addmode option to try to add the mode as discussed in the xrandr tutorial. 
Post the output of those commands here if you can.
If this does not work then I am pretty much out of ideas here.

---

### Post by chome4 on 2010-11-29
When I type 'xrandr' I get:
 
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0x100)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
===============================================================================

cvt 1280 1024 60 for me, gives:

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
===============================================================================
I type:
xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

And get: 

xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
[I][COLOR=Red]X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  27[/COLOR][/I]
  Current serial number in output stream:  27

What am I doing wrong?

---

### Post by tommcd on 2010-11-29
> **chome4 said:**
> 
What am I doing wrong?
Well, I am not sure. I have never had to use xrandr myself. I have only read about it.
What happens if you run:
```
xrandr --addmode 1280x1024
```
or:
```
xrandr --newmode 1280x1024
```
or:
```
xrandr --output LVDS1 --mode 1280x1024
``` You will have to try different options with xrandr as per the tutorial I linked to earlier.

What video card do you have?

You could also try backing up your xorg.conf. Then add the horizontal sync and vertical refresh rates for your monitor, as well as the modeline generated by cvt or gtf to the Monitor section of your xorg.conf. Try something like this:
```

Section "Monitor"
Identifier "Configured Monitor"
VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync
EndSection

``` 
But replace those refresh rates with the refresh rates for your monitor. And use your output from cvt or gtf to generate the modeline.

---

### Post by chome4 on 2010-12-01
My problem is with adding a modeline.

xrandr --newmode <Mode``Line> gives: 

bash: syntax error near unexpected token `newline'

Another instruction says input: xrandr -newmode <Modeline> and I get:
bash: syntax error near unexpected token `newline'

According to the specs, the video is: Intel 943GML (up to 128MB shared)

Advent Laptop T2080 8115

---

### Post by tommcd on 2010-12-01
Are you still using Jaunty 9.04? Ubuntu 9.04 reached end of life in October:
[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)
If so, then perhaps the best thing would be to do a clean install of Ubuntu 10.10. I don't know what else to suggest at this point.

---

### Post by Yellow Pasque on 2010-12-01
Can you pastebin your /var/log/Xorg.0.log ? Thanks.

---

### Post by chome4 on 2010-12-01
sudo gedit /etc/X11/xorg.conf I get an empty file!

This is a new install of 10.10

---

### Post by Yellow Pasque on 2010-12-01
You should have no xorg.conf. Post /var/log/Xorg.0.log if you;re still having issues.

---

### Post by chome4 on 2010-12-01
Here it is....

[    23.773] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    23.773] X Protocol Version 11, Revision 0
[    23.773] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    23.773] Current Operating System: Linux Brightwell 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686
[    23.773] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=adfcb546-c7d3-4047-abf9-a0dbd4cc951d ro quiet splash
[    23.773] Build Date: 16 September 2010  05:39:22PM
[    23.773] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    23.773] Current version of pixman: 0.18.4
[    23.773] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    23.773] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.773] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec  2 00:32:53 2010
[    24.005] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.175] (==) No Layout section.  Using the first Screen section.
[    24.259] (==) No screen section available. Using defaults.
[    24.259] (**) |-->Screen "Default Screen Section" (0)
[    24.259] (**) |   |-->Monitor "<default monitor>"
[    24.260] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    24.260] (==) Automatically adding devices
[    24.260] (==) Automatically enabling devices
[    24.468] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.468] 	Entry deleted from font path.
[    24.656] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    24.656] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.656] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.656] (II) Loader magic: 0x81f8e00
[    24.656] (II) Module ABI versions:
[    24.656] 	X.Org ANSI C Emulation: 0.4
[    24.656] 	X.Org Video Driver: 8.0
[    24.656] 	X.Org XInput driver : 11.0
[    24.656] 	X.Org Server Extension : 4.0
[    24.657] (--) PCI:*(0:0:2:0) 8086:27a2:1584:9916 rev 3, Mem @ 0xb0080000/524288, 0xc0000000/268435456, 0xb0040000/262144, I/O @ 0x00001800/8
[    24.657] (--) PCI: (0:0:2:1) 8086:27a6:1584:9916 rev 3, Mem @ 0xb0100000/524288
[    24.657] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.657] (II) LoadModule: "extmod"
[    24.704] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.744] (II) Module extmod: vendor="X.Org Foundation"
[    24.744] 	compiled for 1.9.0, module version = 1.0.0
[    24.744] 	Module class: X.Org Server Extension
[    24.744] 	ABI class: X.Org Server Extension, version 4.0
[    24.744] (II) Loading extension MIT-SCREEN-SAVER
[    24.744] (II) Loading extension XFree86-VidModeExtension
[    24.744] (II) Loading extension XFree86-DGA
[    24.744] (II) Loading extension DPMS
[    24.744] (II) Loading extension XVideo
[    24.744] (II) Loading extension XVideo-MotionCompensation
[    24.744] (II) Loading extension X-Resource
[    24.744] (II) LoadModule: "dbe"
[    24.744] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.769] (II) Module dbe: vendor="X.Org Foundation"
[    24.769] 	compiled for 1.9.0, module version = 1.0.0
[    24.769] 	Module class: X.Org Server Extension
[    24.769] 	ABI class: X.Org Server Extension, version 4.0
[    24.769] (II) Loading extension DOUBLE-BUFFER
[    24.769] (II) LoadModule: "glx"
[    24.770] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.783] (II) Module glx: vendor="X.Org Foundation"
[    24.783] 	compiled for 1.9.0, module version = 1.0.0
[    24.783] 	ABI class: X.Org Server Extension, version 4.0
[    24.784] (==) AIGLX enabled
[    24.784] (II) Loading extension GLX
[    24.784] (II) LoadModule: "record"
[    24.784] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    24.785] (II) Module record: vendor="X.Org Foundation"
[    24.785] 	compiled for 1.9.0, module version = 1.13.0
[    24.785] 	Module class: X.Org Server Extension
[    24.785] 	ABI class: X.Org Server Extension, version 4.0
[    24.785] (II) Loading extension RECORD
[    24.785] (II) LoadModule: "dri"
[    24.785] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    24.786] (II) Module dri: vendor="X.Org Foundation"
[    24.786] 	compiled for 1.9.0, module version = 1.0.0
[    24.786] 	ABI class: X.Org Server Extension, version 4.0
[    24.786] (II) Loading extension XFree86-DRI
[    24.786] (II) LoadModule: "dri2"
[    24.786] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    24.787] (II) Module dri2: vendor="X.Org Foundation"
[    24.787] 	compiled for 1.9.0, module version = 1.2.0
[    24.787] 	ABI class: X.Org Server Extension, version 4.0
[    24.787] (II) Loading extension DRI2
[    24.787] (==) Matched intel as autoconfigured driver 0
[    24.787] (==) Matched vesa as autoconfigured driver 1
[    24.787] (==) Matched fbdev as autoconfigured driver 2
[    24.787] (==) Assigned the driver to the xf86ConfigLayout
[    24.787] (II) LoadModule: "intel"
[    24.811] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    24.839] (II) Module intel: vendor="X.Org Foundation"
[    24.839] 	compiled for 1.9.0, module version = 2.12.0
[    24.839] 	Module class: X.Org Video Driver
[    24.839] 	ABI class: X.Org Video Driver, version 8.0
[    24.839] (II) LoadModule: "vesa"
[    24.840] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    24.850] (II) Module vesa: vendor="X.Org Foundation"
[    24.850] 	compiled for 1.8.99.905, module version = 2.3.0
[    24.850] 	Module class: X.Org Video Driver
[    24.850] 	ABI class: X.Org Video Driver, version 8.0
[    24.850] (II) LoadModule: "fbdev"
[    24.850] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    24.859] (II) Module fbdev: vendor="X.Org Foundation"
[    24.859] 	compiled for 1.8.99.905, module version = 0.4.2
[    24.859] 	ABI class: X.Org Video Driver, version 8.0
[    24.859] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    24.860] (II) VESA: driver for VESA chipsets: vesa
[    24.860] (II) FBDEV: driver for framebuffer: fbdev
[    24.860] (++) using VT number 7

[    24.860] (WW) Falling back to old probe method for vesa
[    24.860] (WW) Falling back to old probe method for fbdev
[    24.860] (II) Loading sub module "fbdevhw"
[    24.860] (II) LoadModule: "fbdevhw"
[    24.861] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    24.875] (II) Module fbdevhw: vendor="X.Org Foundation"
[    24.875] 	compiled for 1.9.0, module version = 0.0.2
[    24.875] 	ABI class: X.Org Video Driver, version 8.0
[    24.878] drmOpenDevice: node name is /dev/dri/card0
[    24.878] drmOpenDevice: open result is 9, (OK)
[    24.878] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    24.878] drmOpenDevice: node name is /dev/dri/card0
[    24.878] drmOpenDevice: open result is 9, (OK)
[    24.878] drmOpenByBusid: drmOpenMinor returns 9
[    24.878] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    24.878] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    24.878] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    24.878] (==) intel(0): RGB weight 888
[    24.878] (==) intel(0): Default visual is TrueColor
[    24.878] (II) intel(0): Integrated Graphics Chipset: Intel(R) 945GM
[    24.878] (--) intel(0): Chipset: "945GM"
[    24.878] (==) intel(0): video overlay key set to 0x101fe
[    24.917] (II) intel(0): Output VGA1 has no monitor section
[    24.917] (II) intel(0): Output LVDS1 has no monitor section
[    24.917] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    25.253] (II) intel(0): Output TV1 has no monitor section
[    25.309] (II) intel(0): EDID for output VGA1
[    25.309] (II) intel(0): EDID for output LVDS1
[    25.309] (II) intel(0): Manufacturer: CPT  Model: 140a  Serial#: 0
[    25.309] (II) intel(0): Year: 2007  Week: 20
[    25.309] (II) intel(0): EDID Version: 1.3
[    25.309] (II) intel(0): Digital Display Input
[    25.309] (II) intel(0): Max Image Size [cm]: horiz.: 33  vert.: 21
[    25.309] (II) intel(0): Gamma: 2.20
[    25.309] (II) intel(0): No DPMS capabilities specified
[    25.309] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.309] (II) intel(0): First detailed timing is preferred mode
[    25.309] (II) intel(0): redX: 0.613 redY: 0.336   greenX: 0.311 greenY: 0.563
[    25.309] (II) intel(0): blueX: 0.152 blueY: 0.131   whiteX: 0.315 whiteY: 0.329
[    25.309] (II) intel(0): Manufacturer's mask: 0
[    25.309] (II) intel(0): Supported detailed timing:
[    25.309] (II) intel(0): clock: 68.9 MHz   Image Size:  331 x 207 mm
[    25.309] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1408 h_border: 0
[    25.309] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 816 v_border: 0
[    25.309] (II) intel(0): Unknown vendor-specific block f
[    25.309] (II) intel(0):  FD1630154WB4
[    25.309] (II) intel(0):  -@PY}©Èÿ
[    25.309] (II) intel(0): EDID (in hex):
[    25.309] (II) intel(0): 	00ffffffffffff000e140a1400000000
[    25.309] (II) intel(0): 	14110103802115780a092d9d564f9027
[    25.309] (II) intel(0): 	21505400000001010101010101010101
[    25.309] (II) intel(0): 	010101010101ea1a0080502010303020
[    25.309] (II) intel(0): 	36004bcf100000190000000f00000000
[    25.309] (II) intel(0): 	0000000000206e050f00000000fe0046
[    25.309] (II) intel(0): 	443136333031353457423420000000fe
[    25.309] (II) intel(0): 	002d4050597da9c8ff01012020200077
[    25.310] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    25.310] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    25.310] (II) intel(0): Printing probed modes for output LVDS1
[    25.310] (II) intel(0): Modeline "1280x800"x60.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[    25.310] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.310] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.310] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.310] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.644] (II) intel(0): EDID for output TV1
[    25.644] (II) intel(0): Output VGA1 disconnected
[    25.644] (II) intel(0): Output LVDS1 connected
[    25.644] (II) intel(0): Output TV1 disconnected
[    25.644] (II) intel(0): Using exact sizes for initial modes
[    25.644] (II) intel(0): Output LVDS1 using initial mode 1280x800
[    25.644] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.644] (II) intel(0): Kernel page flipping support detected, but forcibly disabled.
[    25.644] (==) intel(0): DPI set to (96, 96)
[    25.644] (II) Loading sub module "fb"
[    25.644] (II) LoadModule: "fb"
[    25.644] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.708] (II) Module fb: vendor="X.Org Foundation"
[    25.708] 	compiled for 1.9.0, module version = 1.0.0
[    25.708] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    25.708] (II) UnloadModule: "vesa"
[    25.708] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.708] (II) UnloadModule: "fbdev"
[    25.708] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.708] (II) UnloadModule: "fbdevhw"
[    25.708] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    25.708] (==) Depth 24 pixmap format is 32 bpp
[    25.708] (II) intel(0): [DRI2] Setup complete
[    25.708] (II) intel(0): [DRI2]   DRI driver: i915
[    25.708] (**) intel(0): Tiling enabled
[    25.708] (**) intel(0): SwapBuffers wait enabled
[    25.708] (==) intel(0): VideoRam: 262144 KB
[    25.708] (II) intel(0): Allocated new frame buffer 1280x800 stride 8192, tiled
[    25.822] (II) UXA(0): Driver registered support for the following operations:
[    25.822] (II)         solid
[    25.822] (II)         copy
[    25.822] (II)         composite (RENDER acceleration)
[    25.822] (II)         put_image
[    25.822] (II)         get_image
[    25.822] (==) intel(0): Backing store disabled
[    25.822] (==) intel(0): Silken mouse enabled
[    25.825] (II) intel(0): Initializing HW Cursor
[    25.868] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    25.869] (==) intel(0): DPMS enabled
[    25.869] (==) intel(0): Intel XvMC decoder disabled
[    25.869] (II) intel(0): Set up textured video
[    25.869] (II) intel(0): Set up overlay video
[    25.869] (II) intel(0): direct rendering: DRI2 Enabled
[    25.869] (--) RandR disabled
[    25.869] (II) Initializing built-in extension Generic Event Extension
[    25.869] (II) Initializing built-in extension SHAPE
[    25.869] (II) Initializing built-in extension MIT-SHM
[    25.869] (II) Initializing built-in extension XInputExtension
[    25.869] (II) Initializing built-in extension XTEST
[    25.869] (II) Initializing built-in extension BIG-REQUESTS
[    25.869] (II) Initializing built-in extension SYNC
[    25.869] (II) Initializing built-in extension XKEYBOARD
[    25.869] (II) Initializing built-in extension XC-MISC
[    25.870] (II) Initializing built-in extension SECURITY
[    25.870] (II) Initializing built-in extension XINERAMA
[    25.870] (II) Initializing built-in extension XFIXES
[    25.870] (II) Initializing built-in extension RENDER
[    25.870] (II) Initializing built-in extension RANDR
[    25.870] (II) Initializing built-in extension COMPOSITE
[    25.870] (II) Initializing built-in extension DAMAGE
[    25.870] (II) Initializing built-in extension GESTURE
[    26.499] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    26.499] (II) AIGLX: enabled GLX_INTEL_swap_event
[    26.499] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    26.499] (II) AIGLX: enabled GLX_SGI_make_current_read
[    26.499] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    26.499] (II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
[    26.499] (II) GLX: Initialized DRI2 GL provider for screen 0
[    26.500] (II) intel(0): Setting screen physical size to 338 x 211
[    26.776] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.801] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    26.801] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.801] (II) LoadModule: "evdev"
[    26.802] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.854] (II) Module evdev: vendor="X.Org Foundation"
[    26.854] 	compiled for 1.9.0, module version = 2.3.2
[    26.854] 	Module class: X.Org XInput Driver
[    26.854] 	ABI class: X.Org XInput driver, version 11.0
[    26.854] (**) Power Button: always reports core events
[    26.854] (**) Power Button: Device: "/dev/input/event3"
[    26.856] (II) Power Button: Found keys
[    26.856] (II) Power Button: Configuring as keyboard
[    26.856] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.856] (**) Option "xkb_rules" "evdev"
[    26.856] (**) Option "xkb_model" "evdev"
[    26.856] (**) Option "xkb_layout" "gb"
[    26.859] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[    26.861] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    26.861] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.861] (**) Video Bus: always reports core events
[    26.861] (**) Video Bus: Device: "/dev/input/event5"
[    26.868] (II) Video Bus: Found keys
[    26.868] (II) Video Bus: Configuring as keyboard
[    26.868] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.868] (**) Option "xkb_rules" "evdev"
[    26.868] (**) Option "xkb_model" "evdev"
[    26.868] (**) Option "xkb_layout" "gb"
[    26.871] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.871] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.871] (**) Power Button: always reports core events
[    26.871] (**) Power Button: Device: "/dev/input/event1"
[    26.885] (II) Power Button: Found keys
[    26.885] (II) Power Button: Configuring as keyboard
[    26.885] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.885] (**) Option "xkb_rules" "evdev"
[    26.885] (**) Option "xkb_model" "evdev"
[    26.885] (**) Option "xkb_layout" "gb"
[    26.886] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    26.886] (II) No input driver/identifier specified (ignoring)
[    26.886] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    26.886] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    26.886] (**) Sleep Button: always reports core events
[    26.886] (**) Sleep Button: Device: "/dev/input/event2"
[    26.897] (II) Sleep Button: Found keys
[    26.897] (II) Sleep Button: Configuring as keyboard
[    26.897] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    26.897] (**) Option "xkb_rules" "evdev"
[    26.897] (**) Option "xkb_model" "evdev"
[    26.897] (**) Option "xkb_layout" "gb"
[    26.904] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    26.904] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.904] (**) AT Translated Set 2 keyboard: always reports core events
[    26.904] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    26.916] (II) AT Translated Set 2 keyboard: Found keys
[    26.916] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.916] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.916] (**) Option "xkb_rules" "evdev"
[    26.916] (**) Option "xkb_model" "evdev"
[    26.916] (**) Option "xkb_layout" "gb"
[    26.917] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[    26.917] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    26.917] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    26.917] (II) LoadModule: "synaptics"
[    26.917] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    26.975] (II) Module synaptics: vendor="X.Org Foundation"
[    26.980] 	compiled for 1.9.0, module version = 1.2.2
[    26.980] 	Module class: X.Org XInput Driver
[    26.980] 	ABI class: X.Org XInput driver, version 11.0
[    26.980] (II) Synaptics touchpad driver version 1.2.2
[    26.980] (**) Option "Device" "/dev/input/event6"
[    27.021] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[    27.021] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[    27.021] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.021] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    27.021] (II) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    27.053] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    27.053] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.069] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    27.069] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.069] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[    27.069] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.069] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.101] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    27.101] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    27.101] (II) No input driver/identifier specified (ignoring)
[    31.329] (II) intel(0): EDID vendor "CPT", prod id 5130
[    31.329] (II) intel(0): Printing DDC gathered Modelines:
[    31.329] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[    31.781] (II) intel(0): EDID vendor "CPT", prod id 5130
[    31.888] (II) intel(0): Printing DDC gathered Modelines:
[    31.888] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[    32.420] (II) intel(0): EDID vendor "CPT", prod id 5130
[    32.420] (II) intel(0): Printing DDC gathered Modelines:
[    32.420] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[    32.796] (II) intel(0): EDID vendor "CPT", prod id 5130
[    32.796] (II) intel(0): Printing DDC gathered Modelines:
[    32.796] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[    43.169] (II) intel(0): EDID vendor "CPT", prod id 5130
[    43.169] (II) intel(0): Printing DDC gathered Modelines:
[    43.169] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[    43.636] (II) intel(0): EDID vendor "CPT", prod id 5130
[    43.636] (II) intel(0): Printing DDC gathered Modelines:
[    43.636] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[   126.108] (II) intel(0): EDID vendor "CPT", prod id 5130
[   126.108] (II) intel(0): Printing DDC gathered Modelines:
[   126.108] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)
[  1000.909] (II) intel(0): EDID vendor "CPT", prod id 5130
[  1000.909] (II) intel(0): Printing DDC gathered Modelines:
[  1000.909] (II) intel(0): Modeline "1280x800"x0.0   68.90  1280 1328 1360 1408  800 803 809 816 -hsync -vsync (48.9 kHz)

---

