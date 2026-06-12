---
title: "I can't set 1024x768 resolution on Ubuntu 10.04"
date: 2012-03-27
forum: Multimedia Software
---

### Post by Sseo on 2012-03-27
Hi everybody :) Can you please help me to fix this problem ? 

Only options I have in my system-->prefferences-->monitors are 640x480 and 800x600. I'm facing this problem for more then a year(I install Ubuntu, then I spend 3-4 days trying to fix resolution and then quit dissapointed and go back to windows :S). Not sure, but I think the problem is in monitor(I always had problems with resolution, but with old monitor I was able to get 1024x768 after alot of tweaking.)

I must say I'm completely new in linux field(yup, I installed several distros for several times) but I have a zero knowledge when it comes to basic philosophy of Linux in general. But - I'm willing to learn :P

I think I'm good enough with computers to follow your advices. :)(not sure tough)

Motherboard: AsRock P4VM800
Processor: Intel Celeron CPU 2.13GHz
RAM: DDR1 768MB(704 actually, because of integrated graphic chip)
Display: VIA/S3G UniChrome Pro IGP (64MB)
Monitor: Hansol 730ED
I think sound card, network etc are not important...

*I don't know if this is a valuable information or not, but on all newest distros(Ubuntu, Mint, Debian...) I don't have problems with resolution(It gets fixed automaticaly during the setup). But, I can't go for Ubuntu 11.10 because it eats my resources too much :) I know there are Xubuntu and other xfce distros, but I have problems with installing them with Wubi(I opened another thread on this forum regarding that problem, lets focus on my resolution problem :P). 

**The point of the uselles text above - Please help me to get 1024x768 resolution on Ubuntu 10.04 :)

---

### Post by Yellow Pasque on 2012-03-27
Try: [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions)

---

### Post by Sseo on 2012-03-27
Thank you for your answer, and please don't get pissed of with my "noobnes". :)

When I try the first command from your tutorial, I'm getting "xrandr: cannot find output "S-video".

How can I see what is my mode ?

Regards.

---

### Post by Yellow Pasque on 2012-03-27
This will tell you what output name is (it's probably not S-video):
```
xrandr -q
```

For example, mine is VGA-0:
```
xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 8192 x 8192
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+   74.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 disconnected (normal left inverted right x axis y axis)
```

---

### Post by Sseo on 2012-03-27
I'm getting this error:

> $ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18

---

### Post by Sseo on 2012-03-27
*UPDATE - After installing all the updates and restarting the PC I'm not getting this error, so I did all the steps, but after I apply the last one "xrandr --output default --mode 1024x768_60.00" I'm getting the response:

> xrandr: screen cannot be larger than 800x600 (desired size 1024x768)

**And now I have option 1024x768 in system-->preferences-->monitors but when I set the resolution and click on apply I'm getting this pop-up error:

**The selected configuration for displays could not be applied**
could not set the configuration for CRTC 119

TNX for helping me!

---

### Post by qneill on 2012-03-27
For the first error, try using a different name for the mode.

See [http://stackoverflow.com/questions/851704/xrandr-errors-badname-named-color-or-font-does-not-exist](http://stackoverflow.com/questions/851704/xrandr-errors-badname-named-color-or-font-does-not-exist)

For the second, your hardware is probably insufficiently supported by the driver in use.   You might need to install a newer driver.

Post the output of 'hwinfo --gfxcard', it will tell you the driver name and module.

---

### Post by Sseo on 2012-03-27
If I understand well, last link can't help me, because now I have mode in my prefferences-->monitors but I can't apply it.(please correct me if I'm wrong)

---

### Post by Sseo on 2012-03-27
Sorry, it took me some time to see your updated response :) Here is the requested output:

```
26: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1106_3344
  Unique ID: VCu0.6GlZWCUUmi5
  Parent ID: vSkL.S16qDHSKEeD
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "VIA CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]"
  Vendor: pci 0x1106 "VIA Technologies, Inc."
  Device: pci 0x3344 "CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro]"
  SubVendor: pci 0x1849 "ASRock Incorporation"
  SubDevice: pci 0x3344 
  Revision: 0x01
  Memory Range: 0xf0000000-0xf3ffffff (rw,prefetchable)
  Memory Range: 0xfd000000-0xfdffffff (rw,non-prefetchable)
  Memory Range: 0xfeaf0000-0xfeafffff (ro,prefetchable,disabled)
  IRQ: 16 (109372 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001106d00003344sv00001849sd00003344bc03sc00i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #15 (PCI bridge)

Primary display adapter: #26
```

---

### Post by qneill on 2012-03-27
Googling for "CN700/P4M800 X11 support" I see this bug [https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-unichrome/+question/122572](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-unichrome/+question/122572) which suggests you have poorly supported hardware.  This does not mean you can't get 1024x768, in fact I'm fairly confident you'll get it only because 1024x768 has been around since the stone age graphic days.  

You could try your own xorg.conf file (as described above) if you feel confident.  But easier might be to try updating the X11 graphics driver and see if it fixes the problem. To do that though we need to know what driver it is - I'm guessing it is "openchrome" after googling around.  To know for sure, you'll need to poke around in the X11 log file [FONT="Courier New"]/var/log/Xorg.0.log[/FONT] to see what X is thinking.  On my system I can see what driver got loaded with:

```
$ grep -i 'radeon' /var/log/Xorg.0.log | egrep -i 'driver|module'
[ 78147.987] (II) LoadModule: "radeon"
[ 78147.987] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 78148.004] (II) Module radeon: vendor="X.Org Foundation"
[ 78148.005] (II) RADEON: Driver for ATI Radeon chipsets:
[ 78148.015] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 78148.286] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[ 78148.286] (II) RADEON(0): [DRI2]   DRI driver: r600
```
but that's because I know it picked the "radeon" driver.  You could try this:
```
grep -i 'chrome' /var/log/Xorg.0.log | egrep -i 'driver|module'
```
and then if it appears chrome is being loaded, try
```
sudo apt-get update xserver-xorg-video-openchrome
```
If no update happens, or if it doesn't fix the problem, you probably need to create your own xorg.conf file, at which point you'd start with posting [FONT="Courier New"]/var/log/Xorg.0.log[/FONT] to the thread.

---

### Post by Sseo on 2012-03-28
(==) Matched openchrome as autoconfigured driver 0
(II) LoadModule: "openchrome"
(II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
(II) Module openchrome: vendor="http://openchrome.org/"
(II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,

This is the output, so I guess it is Chrome.

But, when I try "sudo apt-get update xserver-xorg-video-openchrome" I'm getting the response:

```
E: The update command takes no arguments
```

Unfortunately, there is no "Xorg.0.log" in the var folder. There are only "dpkg.log", "perf.log" and "pycentral.log".

Once again, thank you very much for your fast and easy to understand advices. You guys are great :)

*Just to add, maybe problem is in monitor and not graphic card, because I can lets say watch movies without lagging.

---

### Post by Sseo on 2012-03-28
Anyone having any thoughts ? :S I tried Xubuntu 11.10 today, but I was pretty dissapointed with a realy bad performances(Working same or even worse than Ubuntu 11.10). Only good thing is that resolution is good. Now I'm trying Ubuntu 9.10, and I have same problems with resolution... I switched to 9.10 hoping to find "Xorg.0.log", and here it is:

Actually I have two of them:

**Xorg.0.log.old:**

```
[   106.677] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   106.678] X Protocol Version 11, Revision 0
[   106.678] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   106.678] Current Operating System: Linux stefan-P4VM800 3.2.0-17-generic-pae #27-Ubuntu SMP Fri Feb 24 15:59:25 UTC 2012 i686
[   106.678] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-17-generic-pae root=UUID=7c588d55-4a12-442b-80a3-688d1b230bae ro quiet splash vt.handoff=7
[   106.678] Build Date: 22 February 2012  03:13:47AM
[   106.678] xorg-server 2:1.11.4-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[   106.678] Current version of pixman: 0.24.4
[   106.678]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   106.678] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   106.678] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 28 11:38:15 2012
[   106.679] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   106.688] (==) No Layout section.  Using the first Screen section.
[   106.688] (==) No screen section available. Using defaults.
[   106.688] (**) |-->Screen "Default Screen Section" (0)
[   106.688] (**) |   |-->Monitor "<default monitor>"
[   106.688] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   106.688] (==) Automatically adding devices
[   106.688] (==) Automatically enabling devices
[   106.689] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   106.689]     Entry deleted from font path.
[   106.689] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   106.689]     Entry deleted from font path.
[   106.689] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   106.689]     Entry deleted from font path.
[   106.689] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   106.689]     Entry deleted from font path.
[   106.689] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   106.689]     Entry deleted from font path.
[   106.689] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[   106.689]     Entry deleted from font path.
[   106.689]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[   106.689] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   106.689] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   106.689] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   106.689] (II) Loader magic: 0x89e5a0
[   106.689] (II) Module ABI versions:
[   106.689]     X.Org ANSI C Emulation: 0.4
[   106.689]     X.Org Video Driver: 11.0
[   106.689]     X.Org XInput driver : 16.0
[   106.689]     X.Org Server Extension : 6.0
[   106.691] (--) PCI:*(0:1:0:0) 1106:3344:1849:3344 rev 1, Mem @ 0xf0000000/67108864, 0xfd000000/16777216, BIOS @ 0x????????/65536
[   106.700] (II) Open ACPI successful (/var/run/acpid.socket)
[   106.700] (II) LoadModule: "extmod"
[   106.701] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   106.701] (II) Module extmod: vendor="X.Org Foundation"
[   106.701]     compiled for 1.11.3, module version = 1.0.0
[   106.701]     Module class: X.Org Server Extension
[   106.701]     ABI class: X.Org Server Extension, version 6.0
[   106.701] (II) Loading extension MIT-SCREEN-SAVER
[   106.701] (II) Loading extension XFree86-VidModeExtension
[   106.701] (II) Loading extension XFree86-DGA
[   106.701] (II) Loading extension DPMS
[   106.701] (II) Loading extension XVideo
[   106.701] (II) Loading extension XVideo-MotionCompensation
[   106.701] (II) Loading extension X-Resource
[   106.701] (II) LoadModule: "dbe"
[   106.702] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   106.702] (II) Module dbe: vendor="X.Org Foundation"
[   106.702]     compiled for 1.11.3, module version = 1.0.0
[   106.702]     Module class: X.Org Server Extension
[   106.702]     ABI class: X.Org Server Extension, version 6.0
[   106.702] (II) Loading extension DOUBLE-BUFFER
[   106.702] (II) LoadModule: "glx"
[   106.703] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   106.703] (II) Module glx: vendor="X.Org Foundation"
[   106.703]     compiled for 1.11.3, module version = 1.0.0
[   106.703]     ABI class: X.Org Server Extension, version 6.0
[   106.703] (==) AIGLX enabled
[   106.703] (II) Loading extension GLX
[   106.710] (II) LoadModule: "record"
[   106.710] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   106.711] (II) Module record: vendor="X.Org Foundation"
[   106.711]     compiled for 1.11.3, module version = 1.13.0
[   106.711]     Module class: X.Org Server Extension
[   106.711]     ABI class: X.Org Server Extension, version 6.0
[   106.711] (II) Loading extension RECORD
[   106.711] (II) LoadModule: "dri"
[   106.711] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   106.712] (II) Module dri: vendor="X.Org Foundation"
[   106.712]     compiled for 1.11.3, module version = 1.0.0
[   106.712]     ABI class: X.Org Server Extension, version 6.0
[   106.712] (II) Loading extension XFree86-DRI
[   106.712] (II) LoadModule: "dri2"
[   106.713] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   106.713] (II) Module dri2: vendor="X.Org Foundation"
[   106.713]     compiled for 1.11.3, module version = 1.2.0
[   106.713]     ABI class: X.Org Server Extension, version 6.0
[   106.713] (II) Loading extension DRI2
[   106.713] (==) Matched openchrome as autoconfigured driver 0
[   106.713] (==) Matched vesa as autoconfigured driver 1
[   106.713] (==) Matched fbdev as autoconfigured driver 2
[   106.713] (==) Assigned the driver to the xf86ConfigLayout
[   106.713] (II) LoadModule: "openchrome"
[   106.714] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[   106.714] (II) Module openchrome: vendor="http://openchrome.org/"
[   106.725]     compiled for 1.11.3, module version = 0.2.904
[   106.725]     Module class: X.Org Video Driver
[   106.725]     ABI class: X.Org Video Driver, version 11.0
[   106.725] (II) LoadModule: "vesa"
[   106.726] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   106.726] (II) Module vesa: vendor="X.Org Foundation"
[   106.727]     compiled for 1.11.3, module version = 2.3.0
[   106.727]     Module class: X.Org Video Driver
[   106.727]     ABI class: X.Org Video Driver, version 11.0
[   106.727] (II) LoadModule: "fbdev"
[   106.727] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   106.728] (II) Module fbdev: vendor="X.Org Foundation"
[   106.728]     compiled for 1.11.3, module version = 0.4.2
[   106.728]     ABI class: X.Org Video Driver, version 11.0
[   106.728] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
    CX700/VX700, K8M890/K8N890, P4M890, P4M900/VN896/CN896, VX800/VX820,
    VX855/VX875, VX900
[   106.728] (II) VESA: driver for VESA chipsets: vesa
[   106.728] (II) FBDEV: driver for framebuffer: fbdev
[   106.728] (++) using VT number 7

[   106.729] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[   106.729] (!!) VIA Technologies does not support this driver in any way.
[   106.729] (!!) For support, please refer to http://www.openchrome.org/.
[   106.729] (!!) (development build, compiled on Tue Feb 14 18:51:55 2012)
[   106.729] (WW) Falling back to old probe method for vesa
[   106.729] (WW) Falling back to old probe method for fbdev
[   106.729] (II) Loading sub module "fbdevhw"
[   106.729] (II) LoadModule: "fbdevhw"
[   106.729] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   106.730] (II) Module fbdevhw: vendor="X.Org Foundation"
[   106.730]     compiled for 1.11.3, module version = 0.0.2
[   106.730]     ABI class: X.Org Video Driver, version 11.0
[   106.730] (II) CHROME(0): VIAPreInit
[   106.730] (II) Loading sub module "vgahw"
[   106.730] (II) LoadModule: "vgahw"
[   106.731] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   106.731] (II) Module vgahw: vendor="X.Org Foundation"
[   106.731]     compiled for 1.11.3, module version = 0.1.0
[   106.731]     ABI class: X.Org Video Driver, version 11.0
[   106.731] (II) CHROME(0): VIAGetRec
[   106.731] (II) CHROME(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   106.731] (==) CHROME(0): Depth 24, (--) framebuffer bpp 32
[   106.731] (==) CHROME(0): RGB weight 888
[   106.731] (==) CHROME(0): Default visual is TrueColor
[   106.731] (--) CHROME(0): Chipset: VM800/P4M800Pro/VN800/CN700
[   106.731] (--) CHROME(0): Chipset revision: 0
[   106.734] (--) CHROME(0): Probed amount of VideoRAM = 65536 kB
[   106.734] (II) CHROME(0): VIASetupDefaultOptions - Setting up default chipset options.
[   106.734] (==) CHROME(0): Shadow framebuffer is disabled.
[   106.734] (==) CHROME(0): Hardware acceleration is enabled.
[   106.734] (==) CHROME(0): Using XAA acceleration architecture.
[   106.734] (==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
[   106.734] (==) CHROME(0): GPU virtual command queue will be enabled.
[   106.734] (==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
[   106.734] (==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
[   106.734] (==) CHROME(0): AGP DMA will be used for 2D acceleration.
[   106.734] (==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
[   106.734] (==) CHROME(0): Will not enable VBE modes.
[   106.734] (==) CHROME(0): VBE VGA register save & restore will not be used
    if VBE modes are enabled.
[   106.734] (==) CHROME(0): Xv Bandwidth check is enabled.
[   106.734] (==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
[   106.734] (==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
[   106.734] (==) CHROME(0): Digital output bus width is 12 bits.
[   106.734] (==) CHROME(0): DVI Center is disabled.
[   106.734] (==) CHROME(0): Panel size is not selected from config file.
[   106.734] (==) CHROME(0): Panel will not be forced.
[   106.734] (==) CHROME(0): TV dotCrawl is disabled.
[   106.734] (==) CHROME(0): TV deflicker is set to 0.
[   106.734] (==) CHROME(0): No default TV type is set.
[   106.734] (==) CHROME(0): No default TV output signal type is set.
[   106.734] (==) CHROME(0): No default TV output port is set.
[   106.734] (II) CHROME(0): VIAMapMMIO
[   106.734] (--) CHROME(0): mapping MMIO @ 0xfd000000 with size 0x9000
[   106.735] (--) CHROME(0): mapping BitBlt MMIO @ 0xfd200000 with size 0x200000
[   106.735] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   106.735] (==) CHROME(0): Will not print VGA registers.
[   106.735] (==) CHROME(0): Will not scan I2C buses.
[   106.735] (II) CHROME(0): ...Finished parsing config file options.
[   106.735] (--) CHROME(0): Detected ASRock P4VM800. Card-Ids (1849|3344)
[   106.735] (II) CHROME(0): Detected MemClk 5
[   106.735] (II) CHROME(0): ViaGetMemoryBandwidth. Memory type: 5
[   106.738] (II) CHROME(0): Detected TV standard: NTSC.
[   106.738] (==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
[   106.738] (II) Loading sub module "i2c"
[   106.738] (II) LoadModule: "i2c"
[   106.738] (II) Module "i2c" already built-in
[   106.738] (II) CHROME(0): ViaI2CInit
[   106.738] (II) CHROME(0): ViaI2CBus1Init
[   106.738] (II) CHROME(0): I2C bus "I2C bus 1" initialized.
[   106.738] (II) CHROME(0): ViaI2cBus2Init
[   106.738] (II) CHROME(0): I2C bus "I2C bus 2" initialized.
[   106.738] (II) CHROME(0): ViaI2CBus3Init
[   106.738] (II) CHROME(0): I2C bus "I2C bus 3" initialized.
[   106.738] (II) Loading sub module "ddc"
[   106.738] (II) LoadModule: "ddc"
[   106.738] (II) Module "ddc" already built-in
[   106.738] (II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
[   106.746] (II) CHROME(0): ViaOutputsDetect
[   106.746] (II) CHROME(0): VIATVDetect
[   106.747] (II) CHROME(0): ViaOutputsSelect
[   106.747] (II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
[   106.747] (II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x00
[   106.747] (II) CHROME(0): ViaOutputsSelect: CRT.
[   106.747] (II) CHROME(0): ViaModesAttach
[   106.747] (II) CHROME(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[   106.747] (II) CHROME(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[   106.747] (II) CHROME(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[   106.747] (WW) CHROME(0): Unable to estimate virtual size
[   106.747] (II) CHROME(0): Clock range:  20.00 to 230.00 MHz
[   106.747] (II) CHROME(0): ViaValidMode: Validating 640x350 (Clock: 31500)
[   106.747] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.747] (II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
[   106.747] (II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[   106.747] (II) CHROME(0): ViaValidMode: Validating 640x400 (Clock: 31500)
[   106.747] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.747] (II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
[   106.747] (II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[   106.747] (II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 35500)
[   106.747] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.752] (II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
[   106.752] (II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[   106.752] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   106.752] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.752] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   106.752] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   106.752] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.752] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   106.752] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   106.752] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   106.752] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.752] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   106.752] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   106.752] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 36000)
[   106.752] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.752] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   106.752] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   106.752] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   106.752] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.752] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   106.752] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   106.752] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[   106.753] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[   106.753] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 56300)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "800x600" (hsync out of range)
[   106.753] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1024x768i (Clock: 44900)
[   106.753] (II) CHROME(0): Not using default mode "1024x768i" (interlace mode not supported)
[   106.753] (II) CHROME(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   106.753] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   106.753] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 94500)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   106.753] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 108000)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   106.753] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 108000)
[   106.753] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.753] (II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
[   106.753] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   106.753] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 148500)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 157500)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 162000)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 175500)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 189000)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 202500)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 229500)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1792x1344 (Clock: 204800)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1792x1344" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   106.754] (II) CHROME(0): ViaValidMode: Validating 1856x1392 (Clock: 218300)
[   106.754] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.754] (II) CHROME(0): Not using default mode "1856x1392" (hsync out of range)
[   106.754] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): ViaValidMode: Validating 832x624 (Clock: 57284)
[   106.755] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.755] (II) CHROME(0): Not using default mode "832x624" (hsync out of range)
[   106.755] (II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 81620)
[   106.755] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.755] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   106.755] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 96770)
[   106.755] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.755] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   106.755] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 104990)
[   106.755] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.755] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   106.755] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 119650)
[   106.755] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.755] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   106.755] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   106.755] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 121500)
[   106.755] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.759] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   106.759] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   106.759] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 143470)
[   106.759] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.759] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   106.759] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   106.759] (II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 72000)
[   106.759] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.759] (II) CHROME(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[   106.759] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   106.759] (II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 84750)
[   106.759] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.760] (II) CHROME(0): Not using default mode "1360x768" (mode clock too high)
[   106.760] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   106.760] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 122000)
[   106.760] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.760] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   106.760] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   106.760] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 145060)
[   106.760] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.760] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   106.760] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   106.760] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 155800)
[   106.760] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.760] (II) CHROME(0): Not using default mode "1400x1050" (horizontal sync too wide)
[   106.760] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   106.760] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 179260)
[   106.760] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.760] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   106.760] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   106.760] (II) CHROME(0): ViaValidMode: Validating 1440x900 (Clock: 106500)
[   106.761] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.761] (II) CHROME(0): Not using default mode "1440x900" (hsync out of range)
[   106.761] (II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[   106.761] (II) CHROME(0): ViaValidMode: Validating 1600x1024 (Clock: 103125)
[   106.761] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.761] (II) CHROME(0): Not using default mode "1600x1024" (hsync out of range)
[   106.761] (II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[   106.761] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 119000)
[   106.761] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.761] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   106.761] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   106.761] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 146250)
[   106.761] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.761] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   106.761] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   106.761] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 174000)
[   106.761] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.761] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   106.761] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   106.761] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 187000)
[   106.761] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.761] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   106.761] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 214750)
[   106.762] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.762] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   106.762] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): ViaValidMode: Validating 1920x1080 (Clock: 138500)
[   106.762] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.762] (II) CHROME(0): Not using default mode "1920x1080" (hsync out of range)
[   106.762] (II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): ViaValidMode: Validating 1920x1200 (Clock: 154000)
[   106.762] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.762] (II) CHROME(0): Not using default mode "1920x1200" (hsync out of range)
[   106.762] (II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
[   106.762] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
[   106.762] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
[   106.762] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   106.762] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
[   106.762] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.762] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   106.762] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.762] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   106.762] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.762] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   106.762] (II) CHROME(0): ViaFirstCRTCModeValid
[   106.763] (--) CHROME(0): Virtual size is 1024x768 (pitch 1024)
[   106.763] (**) CHROME(0): *Default mode "1024x768": 65.0 MHz (scaled from 173160.0 MHz), 48.4 kHz, 60.0 Hz
[   106.763] (II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   106.763] (**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 106560.0 MHz), 37.9 kHz, 60.3 Hz
[   106.763] (II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   106.763] (**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 95904.0 MHz), 35.2 kHz, 56.2 Hz
[   106.763] (II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   106.763] (**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from 67066.2 MHz), 31.5 kHz, 59.9 Hz
[   106.763] (II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   106.763] (==) CHROME(0): DPI set to (96, 96)
[   106.763] (II) Loading sub module "fb"
[   106.763] (II) LoadModule: "fb"
[   106.770] (II) Loading /usr/lib/xorg/modules/libfb.so
[   106.770] (II) Module fb: vendor="X.Org Foundation"
[   106.770]     compiled for 1.11.3, module version = 1.0.0
[   106.770]     ABI class: X.Org ANSI C Emulation, version 0.4
[   106.770] (II) Loading sub module "xaa"
[   106.770] (II) LoadModule: "xaa"
[   106.771] (II) Loading /usr/lib/xorg/modules/libxaa.so
[   106.772] (II) Module xaa: vendor="X.Org Foundation"
[   106.772]     compiled for 1.11.3, module version = 1.2.1
[   106.772]     ABI class: X.Org Video Driver, version 11.0
[   106.772] (II) Loading sub module "ramdac"
[   106.772] (II) LoadModule: "ramdac"
[   106.772] (II) Module "ramdac" already built-in
[   106.772] (II) CHROME(0): VIAUnmapMem
[   106.773] (II) UnloadModule: "vesa"
[   106.773] (II) Unloading vesa
[   106.773] (II) UnloadModule: "fbdev"
[   106.773] (II) Unloading fbdev
[   106.773] (II) UnloadModule: "fbdevhw"
[   106.773] (II) Unloading fbdevhw
[   106.773] (--) Depth 24 pixmap format is 32 bpp
[   106.773] (II) CHROME(0): VIAScreenInit
[   106.773] (II) CHROME(0): VIAMapFB
[   106.773] (--) CHROME(0): mapping framebuffer @ 0xf0000000 with size 0x4000000
[   106.800] (--) CHROME(0): Frame buffer start: 0xb375b000, free start: 0x300000 end: 0x4000000
[   106.800] (II) CHROME(0): VIAMapMMIO
[   106.800] (--) CHROME(0): mapping MMIO @ 0xfd000000 with size 0x9000
[   106.800] (--) CHROME(0): mapping BitBlt MMIO @ 0xfd200000 with size 0x200000
[   106.801] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   106.801] (II) CHROME(0): VIASave
[   106.801] (II) CHROME(0): Primary
[   106.809] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[   106.809] (II) CHROME(0): Crtc...
[   106.809] (II) CHROME(0): TVSave...
[   106.809] (II) CHROME(0): VIAWriteMode
[   106.809] (II) CHROME(0): ViaModeSet
[   106.809] (II) CHROME(0): Name: 1024x768
[   106.809] (II) CHROME(0): Clock: 65000
[   106.809] (II) CHROME(0): VRefresh: 60.003841
[   106.809] (II) CHROME(0): HSync: 48.363094
[   106.809] (II) CHROME(0): HDisplay: 1024
[   106.809] (II) CHROME(0): HSyncStart: 1048
[   106.809] (II) CHROME(0): HSyncEnd: 1184
[   106.809] (II) CHROME(0): HTotal: 1344
[   106.809] (II) CHROME(0): HSkew: 0
[   106.809] (II) CHROME(0): VDisplay: 768
[   106.809] (II) CHROME(0): VSyncStart: 771
[   106.809] (II) CHROME(0): VSyncEnd: 777
[   106.809] (II) CHROME(0): VTotal: 806
[   106.810] (II) CHROME(0): VScan: 0
[   106.810] (II) CHROME(0): Flags: 10
[   106.810] (II) CHROME(0): CrtcHDisplay: 0x400
[   106.810] (II) CHROME(0): CrtcHBlankStart: 0x400
[   106.810] (II) CHROME(0): CrtcHSyncStart: 0x418
[   106.810] (II) CHROME(0): CrtcHSyncEnd: 0x4a0
[   106.810] (II) CHROME(0): CrtcHBlankEnd: 0x540
[   106.810] (II) CHROME(0): CrtcHTotal: 0x540
[   106.810] (II) CHROME(0): CrtcHSkew: 0x0
[   106.810] (II) CHROME(0): CrtcVDisplay: 0x300
[   106.810] (II) CHROME(0): CrtcVBlankStart: 0x300
[   106.810] (II) CHROME(0): CrtcVSyncStart: 0x303
[   106.810] (II) CHROME(0): CrtcVSyncEnd: 0x309
[   106.810] (II) CHROME(0): CrtcVBlankEnd: 0x326
[   106.810] (II) CHROME(0): CrtcVTotal: 0x326
[   106.810] (II) CHROME(0): ViaDisplaySetStreamOnCRT
[   106.810] (II) CHROME(0): ViaDisplayEnableCRT
[   106.810] (II) CHROME(0): ViaModeFirstCRTC
[   106.810] (II) CHROME(0): ViaFirstCRTCSetMode
[   106.810] (II) CHROME(0): Setting up 1024x768
[   106.810] (II) CHROME(0): ViaSetPrimaryFIFO
[   106.810] (II) CHROME(0): ViaSetDotclock to 0x06d06d
[   106.810] (II) CHROME(0): ViaSetUseExternalClock
[   106.810] (II) CHROME(0): ViaDisplayDisableSimultaneous
[   106.810] (II) CHROME(0): VIAAdjustFrame 0x0
[   106.810] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   106.810] (II) CHROME(0): VIAAdjustFrame 0x0
[   106.810] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   106.810] (II) CHROME(0): - Blanked
[   106.810] drmOpenDevice: node name is /dev/dri/card0
[   106.811] drmOpenDevice: open result is 18, (OK)
[   106.811] drmOpenDevice: node name is /dev/dri/card0
[   106.811] drmOpenDevice: open result is 18, (OK)
[   106.811] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   106.811] drmOpenDevice: node name is /dev/dri/card0
[   106.811] drmOpenDevice: open result is 18, (OK)
[   106.811] drmOpenByBusid: drmOpenMinor returns 18
[   106.811] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   106.811] (II) [drm] DRM interface version 1.4
[   106.811] (II) [drm] DRM open master succeeded.
[   106.811] (II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
[   106.814] (II) CHROME(0): [drm] framebuffer handle = 0xf0000000
[   106.814] (II) CHROME(0): [drm] added 1 reserved context for kernel
[   106.814] (II) CHROME(0): X context handle = 0x1
[   106.814] (II) CHROME(0): [drm] installed DRM signal handler
[   106.815] (II) CHROME(0): [dri] visual configs initialized.
[   106.815] (II) CHROME(0): [drm] register handle = 0xfd000000
[   106.815] (II) CHROME(0): [drm] framebuffer handle = 0xf0000000
[   106.815] (II) CHROME(0): [drm] mmio Registers = 0xfd000000
[   106.815] (II) CHROME(0): [dri] mmio mapped.
[   106.815] (II) CHROME(0): - Visuals set up
[   106.815] (II) CHROME(0): VIAInternalScreenInit
[   106.815] (II) CHROME(0): - B & W
[   106.815] (II) CHROME(0): CursorStart: 0x3fc0000
[   106.815] (II) CHROME(0): Frame Buffer From (0,0) To (1024,3072)
[   106.815] (II) CHROME(0): Using 2304 lines for offscreen memory.
[   106.815] (II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
[   106.815]     Screen to screen bit blits
[   106.815]     Solid filled rectangles
[   106.815]     8x8 mono pattern filled rectangles
[   106.815]     8x8 color pattern filled rectangles
[   106.815]     Solid Lines
[   106.815]     Dashed Lines
[   106.815]     Image Writes
[   106.817]     Setting up tile and stipple cache:
[   106.817]         31 128x128 slots
[   106.817]         12 256x256 slots
[   106.817]         4 512x512 slots
[   106.817]         32 8x8 color pattern slots
[   106.818] (==) CHROME(0): Backing store disabled
[   106.818] (II) CHROME(0): - Backing store set up
[   106.818] (II) CHROME(0): - SW cursor set up
[   106.818] (II) CHROME(0): VIAHWCursorInit
[   106.818] (II) CHROME(0): HWCursor ARGB enabled
[   106.818] (II) CHROME(0): - Def Color map set up
[   106.818] (II) CHROME(0): VIALoadPalette: numColors: 256
[   106.818] (II) CHROME(0): VIALoadRgbLut
[   106.818] (II) CHROME(0): - Palette loaded
[   106.818] (==) CHROME(0): DPMS enabled
[   106.818] (II) CHROME(0): - DPMS set up
[   106.818] (II) CHROME(0): - Color maps etc. set up
[   106.819] (II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0314
[   106.819] (II) CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
[   106.819] (II) CHROME(0): [drm] Trying to enable AGP fast writes.
[   106.819] (II) CHROME(0): [drm] drmAgpEnabled succeeded
[   106.958] (II) CHROME(0): [drm] agpAddr = 0xf8000000
[   106.973] (II) CHROME(0): [drm] agpBase = (nil)
[   106.973] (II) CHROME(0): [drm] agpAddr = 0xf8000000
[   106.973] (II) CHROME(0): [drm] agpSize = 0x01e00000
[   106.973] (II) CHROME(0): [drm] agp physical addr = 0x00000000
[   106.973] (II) CHROME(0): [dri] Using AGP.
[   106.973] (II) CHROME(0): [drm] Using 54255584 bytes for DRM memory heap.
[   106.973] (II) CHROME(0): [dri] Frame buffer initialized.
[   106.973] (II) CHROME(0): [DRI] installation complete
[   106.973] (II) CHROME(0): [dri] Kernel data initialized.
[   106.973] (II) CHROME(0): [drm] IRQ handler installed, using IRQ 16.
[   106.974] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[   106.974] (II) CHROME(0): direct rendering enabled
[   106.976] (II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
[   106.976] Fulfilled via DRI at 12587008
[   106.977] (II) CHROME(0): Benchmarking video copy.  Less time is better.
[   106.991] (--) CHROME(0): Timed   libc YUV420 copy... 2298464. Throughput: 550.6 MiB/s.
[   107.002] (--) CHROME(0): Timed kernel YUV420 copy... 2233232. Throughput: 566.7 MiB/s.
[   107.010] (--) CHROME(0): Timed    SSE YUV420 copy... 2534248. Throughput: 499.4 MiB/s.
[   107.018] (--) CHROME(0): Timed    MMX YUV420 copy... 2465832. Throughput: 513.2 MiB/s.
[   107.019] (--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
[   107.026] (--) CHROME(0): Timed   MMX2 YUV420 copy... 2243568. Throughput: 564.1 MiB/s.
[   107.026] Freed 12587008 (pool 2)
[   107.026] (--) CHROME(0): Using kernel YUV42X copy for video.
[   107.026] (II) CHROME(0): [XvMC] Registering chromeXvMC.
[   107.026] (II) CHROME(0): [XvMC] Initialized XvMC extension.
[   107.026] (II) CHROME(0): - Done
[   107.027] (==) RandR enabled
[   107.027] (II) Initializing built-in extension Generic Event Extension
[   107.027] (II) Initializing built-in extension SHAPE
[   107.027] (II) Initializing built-in extension MIT-SHM
[   107.027] (II) Initializing built-in extension XInputExtension
[   107.027] (II) Initializing built-in extension XTEST
[   107.027] (II) Initializing built-in extension BIG-REQUESTS
[   107.027] (II) Initializing built-in extension SYNC
[   107.027] (II) Initializing built-in extension XKEYBOARD
[   107.027] (II) Initializing built-in extension XC-MISC
[   107.027] (II) Initializing built-in extension SECURITY
[   107.027] (II) Initializing built-in extension XINERAMA
[   107.027] (II) Initializing built-in extension XFIXES
[   107.027] (II) Initializing built-in extension RENDER
[   107.027] (II) Initializing built-in extension RANDR
[   107.027] (II) Initializing built-in extension COMPOSITE
[   107.027] (II) Initializing built-in extension DAMAGE
[   107.078] (II) AIGLX: Screen 0 is not DRI2 capable
[   107.078] drmOpenDevice: node name is /dev/dri/card0
[   107.078] drmOpenDevice: open result is 19, (OK)
[   107.078] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   107.078] drmOpenDevice: node name is /dev/dri/card0
[   107.079] drmOpenDevice: open result is 19, (OK)
[   107.079] drmOpenByBusid: drmOpenMinor returns 19
[   107.079] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[   107.079] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   107.082] (EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/unichrome_dri.so failed (/usr/lib/i386-linux-gnu/dri/unichrome_dri.so: cannot open shared object file: No such file or directory)
[   107.082] (EE) AIGLX: reverting to software rendering
[   107.191] (II) AIGLX: Loaded and initialized swrast
[   107.191] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   107.243] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   107.261] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   107.261] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   107.261] (II) LoadModule: "evdev"
[   107.262] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   107.263] (II) Module evdev: vendor="X.Org Foundation"
[   107.266]     compiled for 1.11.3, module version = 2.6.99
[   107.266]     Module class: X.Org XInput Driver
[   107.266]     ABI class: X.Org XInput driver, version 16.0
[   107.266] (II) Using input driver 'evdev' for 'Power Button'
[   107.266] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   107.266] (**) Power Button: always reports core events
[   107.266] (**) evdev: Power Button: Device: "/dev/input/event1"
[   107.266] (--) evdev: Power Button: Vendor 0 Product 0x1
[   107.266] (--) evdev: Power Button: Found keys
[   107.266] (II) evdev: Power Button: Configuring as keyboard
[   107.267] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   107.267] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   107.267] (**) Option "xkb_rules" "evdev"
[   107.267] (**) Option "xkb_model" "pc105"
[   107.267] (**) Option "xkb_layout" "us"
[   107.269] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   107.269] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   107.269] (II) Using input driver 'evdev' for 'Power Button'
[   107.269] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   107.269] (**) Power Button: always reports core events
[   107.273] (**) evdev: Power Button: Device: "/dev/input/event0"
[   107.273] (--) evdev: Power Button: Vendor 0 Product 0x1
[   107.273] (--) evdev: Power Button: Found keys
[   107.273] (II) evdev: Power Button: Configuring as keyboard
[   107.274] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   107.274] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   107.274] (**) Option "xkb_rules" "evdev"
[   107.274] (**) Option "xkb_model" "pc105"
[   107.274] (**) Option "xkb_layout" "us"
[   107.276] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   107.279] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   107.280] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   107.280] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   107.281] (**) AT Translated Set 2 keyboard: always reports core events
[   107.281] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   107.281] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   107.281] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   107.281] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   107.281] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   107.281] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[   107.281] (**) Option "xkb_rules" "evdev"
[   107.281] (**) Option "xkb_model" "pc105"
[   107.281] (**) Option "xkb_layout" "us"
[   107.283] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event3)
[   107.283] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[   107.283] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[   107.283] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   107.283] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[   107.287] (**) evdev: ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
[   107.287] (--) evdev: ImExPS/2 Generic Explorer Mouse: Vendor 0x2 Product 0x6
[   107.287] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[   107.287] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[   107.287] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found relative axes
[   107.287] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[   107.287] (II) evdev: ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[   107.287] (II) evdev: ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[   107.287] (**) evdev: ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[   107.287] (**) evdev: ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   107.288] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[   107.288] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE, id 9)
[   107.288] (II) evdev: ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[   107.289] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[   107.289] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[   107.289] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[   107.289] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[   107.290] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[   107.290] (II) No input driver specified, ignoring this device.
[   107.290] (II) This device may have been added with another device file.
[   119.668] (II) CHROME(0): ViaDisplayEnableCRT
[   276.554] (II) evdev: Power Button: Close
[   276.554] (II) UnloadModule: "evdev"
[   276.554] (II) Unloading evdev
[   276.554] (II) evdev: Power Button: Close
[   276.554] (II) UnloadModule: "evdev"
[   276.554] (II) Unloading evdev
[   276.554] (II) evdev: AT Translated Set 2 keyboard: Close
[   276.554] (II) UnloadModule: "evdev"
[   276.554] (II) Unloading evdev
[   276.555] (II) evdev: ImExPS/2 Generic Explorer Mouse: Close
[   276.555] (II) UnloadModule: "evdev"
[   276.555] (II) Unloading evdev
[   276.562] (II) CHROME(0): ViaDisplayEnableCRT
[   276.562] (II) CHROME(0): VIACloseScreen
[   276.620] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[   276.635] (II) CHROME(0): [drm] Freeing agp memory
[   276.658] (II) CHROME(0): [drm] Releasing agp module
[   276.658] (II) CHROME(0): [drm] removed 1 reserved context for kernel
[   276.658] (II) CHROME(0): [drm] unmapping 8192 bytes of SAREA 0xec7c2000 at 0xb779c000
[   276.660] (II) CHROME(0): [drm] Closed DRM master.
[   276.660] Freed 12587008 (pool 1)
[   276.660] (II) CHROME(0): [drm] IRQ handler uninstalled.
[   276.660] (II) CHROME(0): VIARestore
[   276.668] (II) CHROME(0): ViaDisablePrimaryFIFO
[   276.669] (II) CHROME(0): VIAUnmapMem
[   276.713]  ddxSigGiveUp: Closing log
[   276.713] Server terminated successfully (0). Closing log file.
```

Xorg.0.log:

```
[   276.963] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   276.963] X Protocol Version 11, Revision 0
[   276.963] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[   276.963] Current Operating System: Linux stefan-P4VM800 3.2.0-17-generic-pae #27-Ubuntu SMP Fri Feb 24 15:59:25 UTC 2012 i686
[   276.963] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-17-generic-pae root=UUID=7c588d55-4a12-442b-80a3-688d1b230bae ro quiet splash vt.handoff=7
[   276.964] Build Date: 22 February 2012  03:13:47AM
[   276.964] xorg-server 2:1.11.4-0ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[   276.964] Current version of pixman: 0.24.4
[   276.964]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   276.964] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   276.965] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 28 11:41:05 2012
[   276.965] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   276.966] (==) No Layout section.  Using the first Screen section.
[   276.966] (==) No screen section available. Using defaults.
[   276.966] (**) |-->Screen "Default Screen Section" (0)
[   276.966] (**) |   |-->Monitor "<default monitor>"
[   276.966] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   276.967] (==) Automatically adding devices
[   276.967] (==) Automatically enabling devices
[   276.967] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   276.967]     Entry deleted from font path.
[   276.967] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   276.967]     Entry deleted from font path.
[   276.967] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   276.967]     Entry deleted from font path.
[   276.967] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   276.967]     Entry deleted from font path.
[   276.967] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   276.967]     Entry deleted from font path.
[   276.986] (WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
[   276.986]     Entry deleted from font path.
[   276.986]     (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
[   276.986] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   276.986] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   276.986] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   276.986] (II) Loader magic: 0x5c35a0
[   276.986] (II) Module ABI versions:
[   276.986]     X.Org ANSI C Emulation: 0.4
[   276.986]     X.Org Video Driver: 11.0
[   276.986]     X.Org XInput driver : 16.0
[   276.986]     X.Org Server Extension : 6.0
[   276.988] (--) PCI:*(0:1:0:0) 1106:3344:1849:3344 rev 1, Mem @ 0xf0000000/67108864, 0xfd000000/16777216, BIOS @ 0x????????/65536
[   276.989] (II) Open ACPI successful (/var/run/acpid.socket)
[   276.989] (II) LoadModule: "extmod"
[   276.990] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   276.990] (II) Module extmod: vendor="X.Org Foundation"
[   276.990]     compiled for 1.11.3, module version = 1.0.0
[   276.990]     Module class: X.Org Server Extension
[   276.991]     ABI class: X.Org Server Extension, version 6.0
[   276.991] (II) Loading extension MIT-SCREEN-SAVER
[   276.991] (II) Loading extension XFree86-VidModeExtension
[   276.991] (II) Loading extension XFree86-DGA
[   276.991] (II) Loading extension DPMS
[   276.991] (II) Loading extension XVideo
[   276.991] (II) Loading extension XVideo-MotionCompensation
[   276.991] (II) Loading extension X-Resource
[   276.991] (II) LoadModule: "dbe"
[   276.991] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   277.004] (II) Module dbe: vendor="X.Org Foundation"
[   277.004]     compiled for 1.11.3, module version = 1.0.0
[   277.004]     Module class: X.Org Server Extension
[   277.004]     ABI class: X.Org Server Extension, version 6.0
[   277.004] (II) Loading extension DOUBLE-BUFFER
[   277.004] (II) LoadModule: "glx"
[   277.004] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   277.015] (II) Module glx: vendor="X.Org Foundation"
[   277.015]     compiled for 1.11.3, module version = 1.0.0
[   277.015]     ABI class: X.Org Server Extension, version 6.0
[   277.015] (==) AIGLX enabled
[   277.015] (II) Loading extension GLX
[   277.015] (II) LoadModule: "record"
[   277.016] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   277.016] (II) Module record: vendor="X.Org Foundation"
[   277.016]     compiled for 1.11.3, module version = 1.13.0
[   277.016]     Module class: X.Org Server Extension
[   277.016]     ABI class: X.Org Server Extension, version 6.0
[   277.016] (II) Loading extension RECORD
[   277.016] (II) LoadModule: "dri"
[   277.017] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   277.018] (II) Module dri: vendor="X.Org Foundation"
[   277.018]     compiled for 1.11.3, module version = 1.0.0
[   277.018]     ABI class: X.Org Server Extension, version 6.0
[   277.018] (II) Loading extension XFree86-DRI
[   277.018] (II) LoadModule: "dri2"
[   277.018] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   277.019] (II) Module dri2: vendor="X.Org Foundation"
[   277.019]     compiled for 1.11.3, module version = 1.2.0
[   277.019]     ABI class: X.Org Server Extension, version 6.0
[   277.019] (II) Loading extension DRI2
[   277.019] (==) Matched openchrome as autoconfigured driver 0
[   277.019] (==) Matched vesa as autoconfigured driver 1
[   277.019] (==) Matched fbdev as autoconfigured driver 2
[   277.019] (==) Assigned the driver to the xf86ConfigLayout
[   277.019] (II) LoadModule: "openchrome"
[   277.020] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[   277.025] (II) Module openchrome: vendor="http://openchrome.org/"
[   277.025]     compiled for 1.11.3, module version = 0.2.904
[   277.025]     Module class: X.Org Video Driver
[   277.025]     ABI class: X.Org Video Driver, version 11.0
[   277.025] (II) LoadModule: "vesa"
[   277.026] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   277.027] (II) Module vesa: vendor="X.Org Foundation"
[   277.027]     compiled for 1.11.3, module version = 2.3.0
[   277.027]     Module class: X.Org Video Driver
[   277.027]     ABI class: X.Org Video Driver, version 11.0
[   277.027] (II) LoadModule: "fbdev"
[   277.027] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   277.033] (II) Module fbdev: vendor="X.Org Foundation"
[   277.033]     compiled for 1.11.3, module version = 0.4.2
[   277.033]     ABI class: X.Org Video Driver, version 11.0
[   277.034] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
    CX700/VX700, K8M890/K8N890, P4M890, P4M900/VN896/CN896, VX800/VX820,
    VX855/VX875, VX900
[   277.034] (II) VESA: driver for VESA chipsets: vesa
[   277.034] (II) FBDEV: driver for framebuffer: fbdev
[   277.034] (++) using VT number 7

[   277.034] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[   277.034] (!!) VIA Technologies does not support this driver in any way.
[   277.034] (!!) For support, please refer to http://www.openchrome.org/.
[   277.034] (!!) (development build, compiled on Tue Feb 14 18:51:55 2012)
[   277.034] (WW) Falling back to old probe method for vesa
[   277.034] (WW) Falling back to old probe method for fbdev
[   277.034] (II) Loading sub module "fbdevhw"
[   277.034] (II) LoadModule: "fbdevhw"
[   277.035] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   277.041] (II) Module fbdevhw: vendor="X.Org Foundation"
[   277.041]     compiled for 1.11.3, module version = 0.0.2
[   277.041]     ABI class: X.Org Video Driver, version 11.0
[   277.041] (II) CHROME(0): VIAPreInit
[   277.041] (II) Loading sub module "vgahw"
[   277.041] (II) LoadModule: "vgahw"
[   277.042] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   277.045] (II) Module vgahw: vendor="X.Org Foundation"
[   277.045]     compiled for 1.11.3, module version = 0.1.0
[   277.045]     ABI class: X.Org Video Driver, version 11.0
[   277.045] (II) CHROME(0): VIAGetRec
[   277.045] (II) CHROME(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   277.045] (==) CHROME(0): Depth 24, (--) framebuffer bpp 32
[   277.045] (==) CHROME(0): RGB weight 888
[   277.046] (==) CHROME(0): Default visual is TrueColor
[   277.046] (--) CHROME(0): Chipset: VM800/P4M800Pro/VN800/CN700
[   277.046] (--) CHROME(0): Chipset revision: 0
[   277.046] (--) CHROME(0): Probed amount of VideoRAM = 65536 kB
[   277.046] (II) CHROME(0): VIASetupDefaultOptions - Setting up default chipset options.
[   277.046] (==) CHROME(0): Shadow framebuffer is disabled.
[   277.046] (==) CHROME(0): Hardware acceleration is enabled.
[   277.046] (==) CHROME(0): Using XAA acceleration architecture.
[   277.046] (==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
[   277.046] (==) CHROME(0): GPU virtual command queue will be enabled.
[   277.046] (==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
[   277.046] (==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
[   277.046] (==) CHROME(0): AGP DMA will be used for 2D acceleration.
[   277.046] (==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
[   277.046] (==) CHROME(0): Will not enable VBE modes.
[   277.046] (==) CHROME(0): VBE VGA register save & restore will not be used
    if VBE modes are enabled.
[   277.046] (==) CHROME(0): Xv Bandwidth check is enabled.
[   277.046] (==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
[   277.046] (==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
[   277.046] (==) CHROME(0): Digital output bus width is 12 bits.
[   277.046] (==) CHROME(0): DVI Center is disabled.
[   277.046] (==) CHROME(0): Panel size is not selected from config file.
[   277.046] (==) CHROME(0): Panel will not be forced.
[   277.046] (==) CHROME(0): TV dotCrawl is disabled.
[   277.046] (==) CHROME(0): TV deflicker is set to 0.
[   277.046] (==) CHROME(0): No default TV type is set.
[   277.046] (==) CHROME(0): No default TV output signal type is set.
[   277.046] (==) CHROME(0): No default TV output port is set.
[   277.047] (II) CHROME(0): VIAMapMMIO
[   277.047] (--) CHROME(0): mapping MMIO @ 0xfd000000 with size 0x9000
[   277.047] (--) CHROME(0): mapping BitBlt MMIO @ 0xfd200000 with size 0x200000
[   277.047] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   277.047] (==) CHROME(0): Will not print VGA registers.
[   277.048] (==) CHROME(0): Will not scan I2C buses.
[   277.048] (II) CHROME(0): ...Finished parsing config file options.
[   277.048] (--) CHROME(0): Detected ASRock P4VM800. Card-Ids (1849|3344)
[   277.048] (II) CHROME(0): Detected MemClk 5
[   277.048] (II) CHROME(0): ViaGetMemoryBandwidth. Memory type: 5
[   277.048] (II) CHROME(0): Detected TV standard: NTSC.
[   277.048] (==) CHROME(0): Using gamma correction (1.0, 1.0, 1.0)
[   277.048] (II) Loading sub module "i2c"
[   277.048] (II) LoadModule: "i2c"
[   277.048] (II) Module "i2c" already built-in
[   277.048] (II) CHROME(0): ViaI2CInit
[   277.048] (II) CHROME(0): ViaI2CBus1Init
[   277.048] (II) CHROME(0): I2C bus "I2C bus 1" initialized.
[   277.048] (II) CHROME(0): ViaI2cBus2Init
[   277.048] (II) CHROME(0): I2C bus "I2C bus 2" initialized.
[   277.048] (II) CHROME(0): ViaI2CBus3Init
[   277.048] (II) CHROME(0): I2C bus "I2C bus 3" initialized.
[   277.048] (II) Loading sub module "ddc"
[   277.048] (II) LoadModule: "ddc"
[   277.048] (II) Module "ddc" already built-in
[   277.048] (II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
[   277.051] (II) CHROME(0): ViaOutputsDetect
[   277.051] (II) CHROME(0): VIATVDetect
[   277.052] (II) CHROME(0): ViaOutputsSelect
[   277.052] (II) CHROME(0): ViaOutputsSelect: X Configuration: 0x00
[   277.052] (II) CHROME(0): ViaOutputsSelect: BIOS Initialised register: 0x00
[   277.052] (II) CHROME(0): ViaOutputsSelect: CRT.
[   277.052] (II) CHROME(0): ViaModesAttach
[   277.052] (II) CHROME(0): <default monitor>: Using default hsync range of 31.50-48.00 kHz
[   277.053] (II) CHROME(0): <default monitor>: Using default vrefresh range of 50.00-70.00 Hz
[   277.053] (II) CHROME(0): <default monitor>: Using default maximum pixel clock of 65.00 MHz
[   277.053] (WW) CHROME(0): Unable to estimate virtual size
[   277.053] (II) CHROME(0): Clock range:  20.00 to 230.00 MHz
[   277.053] (II) CHROME(0): ViaValidMode: Validating 640x350 (Clock: 31500)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "640x350" (vrefresh out of range)
[   277.053] (II) CHROME(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
[   277.053] (II) CHROME(0): ViaValidMode: Validating 640x400 (Clock: 31500)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "640x400" (vrefresh out of range)
[   277.053] (II) CHROME(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
[   277.053] (II) CHROME(0): ViaValidMode: Validating 720x400 (Clock: 35500)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "720x400" (vrefresh out of range)
[   277.053] (II) CHROME(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
[   277.053] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   277.053] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   277.053] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   277.053] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 31500)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   277.053] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   277.053] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 36000)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "640x480" (vrefresh out of range)
[   277.053] (II) CHROME(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
[   277.053] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   277.053] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.053] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 50000)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[   277.054] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 49500)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "800x600" (vrefresh out of range)
[   277.054] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 56300)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "800x600" (hsync out of range)
[   277.054] (II) CHROME(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 1024x768i (Clock: 44900)
[   277.054] (II) CHROME(0): Not using default mode "1024x768i" (interlace mode not supported)
[   277.054] (II) CHROME(0): Not using default mode "512x384i" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 75000)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   277.054] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 78750)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   277.054] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 94500)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "1024x768" (hsync out of range)
[   277.054] (II) CHROME(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 108000)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.054] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   277.054] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   277.054] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 108000)
[   277.054] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1280x960 (Clock: 148500)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1280x960" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 108000)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 135000)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1280x1024 (Clock: 157500)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1280x1024" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 162000)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 175500)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 189000)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 202500)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1600x1200 (Clock: 229500)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1600x1200" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): ViaValidMode: Validating 1792x1344 (Clock: 204800)
[   277.055] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.055] (II) CHROME(0): Not using default mode "1792x1344" (hsync out of range)
[   277.055] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   277.055] (II) CHROME(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): ViaValidMode: Validating 1856x1392 (Clock: 218300)
[   277.056] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.056] (II) CHROME(0): Not using default mode "1856x1392" (hsync out of range)
[   277.056] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): ViaValidMode: Validating 832x624 (Clock: 57284)
[   277.056] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.056] (II) CHROME(0): Not using default mode "832x624" (hsync out of range)
[   277.056] (II) CHROME(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 81620)
[   277.056] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.056] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   277.056] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 96770)
[   277.056] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.056] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   277.056] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 104990)
[   277.056] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.056] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   277.056] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   277.056] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 119650)
[   277.056] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.057] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   277.057] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   277.057] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 121500)
[   277.057] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.057] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   277.057] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   277.057] (II) CHROME(0): ViaValidMode: Validating 1152x864 (Clock: 143470)
[   277.057] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.057] (II) CHROME(0): Not using default mode "1152x864" (hsync out of range)
[   277.057] (II) CHROME(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
[   277.057] (II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 72000)
[   277.057] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.057] (II) CHROME(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[   277.057] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   277.057] (II) CHROME(0): ViaValidMode: Validating 1360x768 (Clock: 84750)
[   277.057] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.057] (II) CHROME(0): Not using default mode "1360x768" (mode clock too high)
[   277.057] (II) CHROME(0): Not using default mode "680x384" (bad mode clock/interlace/doublescan)
[   277.057] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 122000)
[   277.057] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.057] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   277.057] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   277.057] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 145060)
[   277.057] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.058] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   277.058] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   277.058] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 155800)
[   277.058] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.058] (II) CHROME(0): Not using default mode "1400x1050" (horizontal sync too wide)
[   277.058] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   277.058] (II) CHROME(0): ViaValidMode: Validating 1400x1050 (Clock: 179260)
[   277.058] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.058] (II) CHROME(0): Not using default mode "1400x1050" (hsync out of range)
[   277.058] (II) CHROME(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
[   277.058] (II) CHROME(0): ViaValidMode: Validating 1440x900 (Clock: 106500)
[   277.058] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.058] (II) CHROME(0): Not using default mode "1440x900" (hsync out of range)
[   277.058] (II) CHROME(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
[   277.058] (II) CHROME(0): ViaValidMode: Validating 1600x1024 (Clock: 103125)
[   277.058] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.058] (II) CHROME(0): Not using default mode "1600x1024" (hsync out of range)
[   277.058] (II) CHROME(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
[   277.058] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 119000)
[   277.058] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.058] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   277.058] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   277.058] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 146250)
[   277.058] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.059] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   277.059] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   277.059] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 174000)
[   277.059] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.059] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   277.059] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   277.059] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 187000)
[   277.059] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.059] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   277.059] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   277.059] (II) CHROME(0): ViaValidMode: Validating 1680x1050 (Clock: 214750)
[   277.059] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.059] (II) CHROME(0): Not using default mode "1680x1050" (hsync out of range)
[   277.059] (II) CHROME(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
[   277.059] (II) CHROME(0): ViaValidMode: Validating 1920x1080 (Clock: 138500)
[   277.059] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.059] (II) CHROME(0): Not using default mode "1920x1080" (hsync out of range)
[   277.059] (II) CHROME(0): Not using default mode "960x540" (bad mode clock/interlace/doublescan)
[   277.059] (II) CHROME(0): ViaValidMode: Validating 1920x1200 (Clock: 154000)
[   277.059] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.059] (II) CHROME(0): Not using default mode "1920x1200" (hsync out of range)
[   277.059] (II) CHROME(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
[   277.059] (II) CHROME(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
[   277.059] (II) CHROME(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
[   277.060] (II) CHROME(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
[   277.060] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   277.060] (II) CHROME(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
[   277.060] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   277.060] (II) CHROME(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
[   277.060] (II) CHROME(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
[   277.060] (II) CHROME(0): ViaValidMode: Validating 1024x768 (Clock: 65000)
[   277.060] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.060] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 40000)
[   277.060] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.060] (II) CHROME(0): ViaValidMode: Validating 800x600 (Clock: 36000)
[   277.060] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.060] (II) CHROME(0): ViaValidMode: Validating 640x480 (Clock: 25175)
[   277.060] (II) CHROME(0): ViaFirstCRTCModeValid
[   277.060] (--) CHROME(0): Virtual size is 1024x768 (pitch 1024)
[   277.060] (**) CHROME(0): *Default mode "1024x768": 65.0 MHz (scaled from 173160.0 MHz), 48.4 kHz, 60.0 Hz
[   277.060] (II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   277.060] (**) CHROME(0): *Default mode "800x600": 40.0 MHz (scaled from 106560.0 MHz), 37.9 kHz, 60.3 Hz
[   277.060] (II) CHROME(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   277.060] (**) CHROME(0): *Default mode "800x600": 36.0 MHz (scaled from 95904.0 MHz), 35.2 kHz, 56.2 Hz
[   277.060] (II) CHROME(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[   277.060] (**) CHROME(0): *Default mode "640x480": 25.2 MHz (scaled from 67066.2 MHz), 31.5 kHz, 59.9 Hz
[   277.060] (II) CHROME(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   277.060] (==) CHROME(0): DPI set to (96, 96)
[   277.060] (II) Loading sub module "fb"
[   277.060] (II) LoadModule: "fb"
[   277.061] (II) Loading /usr/lib/xorg/modules/libfb.so
[   277.074] (II) Module fb: vendor="X.Org Foundation"
[   277.074]     compiled for 1.11.3, module version = 1.0.0
[   277.074]     ABI class: X.Org ANSI C Emulation, version 0.4
[   277.074] (II) Loading sub module "xaa"
[   277.074] (II) LoadModule: "xaa"
[   277.075] (II) Loading /usr/lib/xorg/modules/libxaa.so
[   277.081] (II) Module xaa: vendor="X.Org Foundation"
[   277.082]     compiled for 1.11.3, module version = 1.2.1
[   277.082]     ABI class: X.Org Video Driver, version 11.0
[   277.082] (II) Loading sub module "ramdac"
[   277.082] (II) LoadModule: "ramdac"
[   277.082] (II) Module "ramdac" already built-in
[   277.082] (II) CHROME(0): VIAUnmapMem
[   277.082] (II) UnloadModule: "vesa"
[   277.083] (II) Unloading vesa
[   277.083] (II) UnloadModule: "fbdev"
[   277.083] (II) Unloading fbdev
[   277.083] (II) UnloadModule: "fbdevhw"
[   277.083] (II) Unloading fbdevhw
[   277.083] (--) Depth 24 pixmap format is 32 bpp
[   277.083] (II) CHROME(0): VIAScreenInit
[   277.083] (II) CHROME(0): VIAMapFB
[   277.083] (--) CHROME(0): mapping framebuffer @ 0xf0000000 with size 0x4000000
[   277.103] (--) CHROME(0): Frame buffer start: 0xb3714000, free start: 0x300000 end: 0x4000000
[   277.103] (II) CHROME(0): VIAMapMMIO
[   277.103] (--) CHROME(0): mapping MMIO @ 0xfd000000 with size 0x9000
[   277.103] (--) CHROME(0): mapping BitBlt MMIO @ 0xfd200000 with size 0x200000
[   277.104] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   277.104] (II) CHROME(0): VIASave
[   277.104] (II) CHROME(0): Primary
[   277.105] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[   277.105] (II) CHROME(0): Crtc...
[   277.105] (II) CHROME(0): TVSave...
[   277.105] (II) CHROME(0): VIAWriteMode
[   277.105] (II) CHROME(0): ViaModeSet
[   277.105] (II) CHROME(0): Name: 1024x768
[   277.105] (II) CHROME(0): Clock: 65000
[   277.105] (II) CHROME(0): VRefresh: 60.003841
[   277.105] (II) CHROME(0): HSync: 48.363094
[   277.105] (II) CHROME(0): HDisplay: 1024
[   277.106] (II) CHROME(0): HSyncStart: 1048
[   277.106] (II) CHROME(0): HSyncEnd: 1184
[   277.106] (II) CHROME(0): HTotal: 1344
[   277.106] (II) CHROME(0): HSkew: 0
[   277.106] (II) CHROME(0): VDisplay: 768
[   277.106] (II) CHROME(0): VSyncStart: 771
[   277.106] (II) CHROME(0): VSyncEnd: 777
[   277.106] (II) CHROME(0): VTotal: 806
[   277.106] (II) CHROME(0): VScan: 0
[   277.106] (II) CHROME(0): Flags: 10
[   277.106] (II) CHROME(0): CrtcHDisplay: 0x400
[   277.106] (II) CHROME(0): CrtcHBlankStart: 0x400
[   277.106] (II) CHROME(0): CrtcHSyncStart: 0x418
[   277.106] (II) CHROME(0): CrtcHSyncEnd: 0x4a0
[   277.106] (II) CHROME(0): CrtcHBlankEnd: 0x540
[   277.106] (II) CHROME(0): CrtcHTotal: 0x540
[   277.106] (II) CHROME(0): CrtcHSkew: 0x0
[   277.106] (II) CHROME(0): CrtcVDisplay: 0x300
[   277.106] (II) CHROME(0): CrtcVBlankStart: 0x300
[   277.106] (II) CHROME(0): CrtcVSyncStart: 0x303
[   277.106] (II) CHROME(0): CrtcVSyncEnd: 0x309
[   277.106] (II) CHROME(0): CrtcVBlankEnd: 0x326
[   277.106] (II) CHROME(0): CrtcVTotal: 0x326
[   277.106] (II) CHROME(0): ViaDisplaySetStreamOnCRT
[   277.106] (II) CHROME(0): ViaDisplayEnableCRT
[   277.106] (II) CHROME(0): ViaModeFirstCRTC
[   277.106] (II) CHROME(0): ViaFirstCRTCSetMode
[   277.106] (II) CHROME(0): Setting up 1024x768
[   277.106] (II) CHROME(0): ViaSetPrimaryFIFO
[   277.106] (II) CHROME(0): ViaSetDotclock to 0x06d06d
[   277.106] (II) CHROME(0): ViaSetUseExternalClock
[   277.106] (II) CHROME(0): ViaDisplayDisableSimultaneous
[   277.106] (II) CHROME(0): VIAAdjustFrame 0x0
[   277.106] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   277.106] (II) CHROME(0): VIAAdjustFrame 0x0
[   277.106] (II) CHROME(0): ViaFirstCRTCSetStartingAddress
[   277.106] (II) CHROME(0): - Blanked
[   277.107] drmOpenDevice: node name is /dev/dri/card0
[   277.107] drmOpenDevice: open result is 22, (OK)
[   277.107] drmOpenDevice: node name is /dev/dri/card0
[   277.107] drmOpenDevice: open result is 22, (OK)
[   277.107] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   277.107] drmOpenDevice: node name is /dev/dri/card0
[   277.107] drmOpenDevice: open result is 22, (OK)
[   277.107] drmOpenByBusid: drmOpenMinor returns 22
[   277.107] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   277.107] (II) [drm] DRM interface version 1.4
[   277.107] (II) [drm] DRM open master succeeded.
[   277.107] (II) CHROME(0): [drm] Using the DRM lock SAREA also for drawables.
[   277.108] (II) CHROME(0): [drm] framebuffer handle = 0xf0000000
[   277.108] (II) CHROME(0): [drm] added 1 reserved context for kernel
[   277.108] (II) CHROME(0): X context handle = 0x1
[   277.108] (II) CHROME(0): [drm] installed DRM signal handler
[   277.108] (II) CHROME(0): [dri] visual configs initialized.
[   277.108] (II) CHROME(0): [drm] register handle = 0xfd000000
[   277.109] (II) CHROME(0): [drm] framebuffer handle = 0xf0000000
[   277.109] (II) CHROME(0): [drm] mmio Registers = 0xfd000000
[   277.109] (II) CHROME(0): [dri] mmio mapped.
[   277.109] (II) CHROME(0): - Visuals set up
[   277.109] (II) CHROME(0): VIAInternalScreenInit
[   277.109] (II) CHROME(0): - B & W
[   277.109] (II) CHROME(0): CursorStart: 0x3fc0000
[   277.109] (II) CHROME(0): Frame Buffer From (0,0) To (1024,3072)
[   277.109] (II) CHROME(0): Using 2304 lines for offscreen memory.
[   277.109] (II) CHROME(0): Using XFree86 Acceleration Architecture (XAA)
[   277.109]     Screen to screen bit blits
[   277.109]     Solid filled rectangles
[   277.109]     8x8 mono pattern filled rectangles
[   277.109]     8x8 color pattern filled rectangles
[   277.109]     Solid Lines
[   277.109]     Dashed Lines
[   277.109]     Image Writes
[   277.110]     Setting up tile and stipple cache:
[   277.110]         31 128x128 slots
[   277.110]         12 256x256 slots
[   277.110]         4 512x512 slots
[   277.110]         32 8x8 color pattern slots
[   277.110] (==) CHROME(0): Backing store disabled
[   277.110] (II) CHROME(0): - Backing store set up
[   277.110] (II) CHROME(0): - SW cursor set up
[   277.110] (II) CHROME(0): VIAHWCursorInit
[   277.110] (II) CHROME(0): HWCursor ARGB enabled
[   277.110] (II) CHROME(0): - Def Color map set up
[   277.110] (II) CHROME(0): VIALoadPalette: numColors: 256
[   277.110] (II) CHROME(0): VIALoadRgbLut
[   277.110] (II) CHROME(0): - Palette loaded
[   277.110] (==) CHROME(0): DPMS enabled
[   277.110] (II) CHROME(0): - DPMS set up
[   277.110] (II) CHROME(0): - Color maps etc. set up
[   277.111] (II) CHROME(0): [drm] Detected AGP vendor 0x1106, device 0x0314
[   277.111] (II) CHROME(0): [drm] Found AGP v3 compatible device. Trying AGP 8X mode.
[   277.111] (II) CHROME(0): [drm] Trying to enable AGP fast writes.
[   277.111] (II) CHROME(0): [drm] drmAgpEnabled succeeded
[   277.176] (II) CHROME(0): [drm] agpAddr = 0xf8000000
[   277.185] (II) CHROME(0): [drm] agpBase = (nil)
[   277.185] (II) CHROME(0): [drm] agpAddr = 0xf8000000
[   277.185] (II) CHROME(0): [drm] agpSize = 0x01e00000
[   277.185] (II) CHROME(0): [drm] agp physical addr = 0x00000000
[   277.185] (II) CHROME(0): [dri] Using AGP.
[   277.185] (II) CHROME(0): [drm] Using 54255584 bytes for DRM memory heap.
[   277.185] (II) CHROME(0): [dri] Frame buffer initialized.
[   277.185] (II) CHROME(0): [DRI] installation complete
[   277.185] (II) CHROME(0): [dri] Kernel data initialized.
[   277.185] (II) CHROME(0): [drm] IRQ handler installed, using IRQ 16.
[   277.186] (II) CHROME(0): [drm] Initialized AGP ring-buffer, size 0x200000 at AGP offset 0x1e00000.
[   277.186] (II) CHROME(0): direct rendering enabled
[   277.188] (II) CHROME(0): [Xv] Using PCI DMA for Xv image transfer.
[   277.188] Fulfilled via DRI at 12587008
[   277.189] (II) CHROME(0): Benchmarking video copy.  Less time is better.
[   277.194] (--) CHROME(0): Timed   libc YUV420 copy... 2444728. Throughput: 517.6 MiB/s.
[   277.198] (--) CHROME(0): Timed kernel YUV420 copy... 2446184. Throughput: 517.3 MiB/s.
[   277.202] (--) CHROME(0): Timed    SSE YUV420 copy... 2327904. Throughput: 543.6 MiB/s.
[   277.206] (--) CHROME(0): Timed    MMX YUV420 copy... 2329672. Throughput: 543.2 MiB/s.
[   277.206] (--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
[   277.210] (--) CHROME(0): Timed   MMX2 YUV420 copy... 2203760. Throughput: 574.2 MiB/s.
[   277.210] Freed 12587008 (pool 2)
[   277.211] (--) CHROME(0): Using MMX2 YUV42X copy for video.
[   277.211] (II) CHROME(0): [XvMC] Registering chromeXvMC.
[   277.211] (II) CHROME(0): [XvMC] Initialized XvMC extension.
[   277.211] (II) CHROME(0): - Done
[   277.211] (==) RandR enabled
[   277.211] (II) Initializing built-in extension Generic Event Extension
[   277.211] (II) Initializing built-in extension SHAPE
[   277.211] (II) Initializing built-in extension MIT-SHM
[   277.211] (II) Initializing built-in extension XInputExtension
[   277.211] (II) Initializing built-in extension XTEST
[   277.211] (II) Initializing built-in extension BIG-REQUESTS
[   277.211] (II) Initializing built-in extension SYNC
[   277.211] (II) Initializing built-in extension XKEYBOARD
[   277.211] (II) Initializing built-in extension XC-MISC
[   277.211] (II) Initializing built-in extension SECURITY
[   277.211] (II) Initializing built-in extension XINERAMA
[   277.211] (II) Initializing built-in extension XFIXES
[   277.211] (II) Initializing built-in extension RENDER
[   277.211] (II) Initializing built-in extension RANDR
[   277.211] (II) Initializing built-in extension COMPOSITE
[   277.211] (II) Initializing built-in extension DAMAGE
[   277.232] (II) AIGLX: Screen 0 is not DRI2 capable
[   277.233] drmOpenDevice: node name is /dev/dri/card0
[   277.233] drmOpenDevice: open result is 23, (OK)
[   277.233] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   277.233] drmOpenDevice: node name is /dev/dri/card0
[   277.233] drmOpenDevice: open result is 23, (OK)
[   277.233] drmOpenByBusid: drmOpenMinor returns 23
[   277.233] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[   277.233] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   277.233] (EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/unichrome_dri.so failed (/usr/lib/i386-linux-gnu/dri/unichrome_dri.so: cannot open shared object file: No such file or directory)
[   277.233] (EE) AIGLX: reverting to software rendering
[   277.278] (II) AIGLX: Loaded and initialized swrast
[   277.278] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   277.301] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   277.309] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   277.309] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   277.309] (II) LoadModule: "evdev"
[   277.310] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.333] (II) Module evdev: vendor="X.Org Foundation"
[   277.333]     compiled for 1.11.3, module version = 2.6.99
[   277.333]     Module class: X.Org XInput Driver
[   277.333]     ABI class: X.Org XInput driver, version 16.0
[   277.333] (II) Using input driver 'evdev' for 'Power Button'
[   277.333] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.333] (**) Power Button: always reports core events
[   277.333] (**) evdev: Power Button: Device: "/dev/input/event1"
[   277.334] (--) evdev: Power Button: Vendor 0 Product 0x1
[   277.334] (--) evdev: Power Button: Found keys
[   277.334] (II) evdev: Power Button: Configuring as keyboard
[   277.334] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   277.334] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   277.334] (**) Option "xkb_rules" "evdev"
[   277.334] (**) Option "xkb_model" "pc105"
[   277.334] (**) Option "xkb_layout" "us"
[   277.336] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   277.336] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   277.336] (II) Using input driver 'evdev' for 'Power Button'
[   277.336] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.336] (**) Power Button: always reports core events
[   277.337] (**) evdev: Power Button: Device: "/dev/input/event0"
[   277.337] (--) evdev: Power Button: Vendor 0 Product 0x1
[   277.337] (--) evdev: Power Button: Found keys
[   277.337] (II) evdev: Power Button: Configuring as keyboard
[   277.337] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   277.337] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   277.337] (**) Option "xkb_rules" "evdev"
[   277.337] (**) Option "xkb_model" "pc105"
[   277.337] (**) Option "xkb_layout" "us"
[   277.339] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   277.339] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   277.339] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   277.339] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.339] (**) AT Translated Set 2 keyboard: always reports core events
[   277.339] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   277.339] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   277.346] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   277.347] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   277.347] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   277.347] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 8)
[   277.347] (**) Option "xkb_rules" "evdev"
[   277.347] (**) Option "xkb_model" "pc105"
[   277.347] (**) Option "xkb_layout" "us"
[   277.349] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/event3)
[   277.349] (**) ImExPS/2 Generic Explorer Mouse: Applying InputClass "evdev pointer catchall"
[   277.349] (II) Using input driver 'evdev' for 'ImExPS/2 Generic Explorer Mouse'
[   277.349] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   277.349] (**) ImExPS/2 Generic Explorer Mouse: always reports core events
[   277.349] (**) evdev: ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event3"
[   277.349] (--) evdev: ImExPS/2 Generic Explorer Mouse: Vendor 0x2 Product 0x6
[   277.349] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
[   277.349] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
[   277.349] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found relative axes
[   277.349] (--) evdev: ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
[   277.350] (II) evdev: ImExPS/2 Generic Explorer Mouse: Configuring as mouse
[   277.350] (II) evdev: ImExPS/2 Generic Explorer Mouse: Adding scrollwheel support
[   277.350] (**) evdev: ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
[   277.350] (**) evdev: ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   277.350] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input3/event3"
[   277.350] (II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE, id 9)
[   277.350] (II) evdev: ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
[   277.350] (**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
[   277.351] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration profile 0
[   277.351] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration factor: 2.000
[   277.351] (**) ImExPS/2 Generic Explorer Mouse: (accel) acceleration threshold: 4
[   277.358] (II) config/udev: Adding input device ImExPS/2 Generic Explorer Mouse (/dev/input/mouse0)
[   277.358] (II) No input driver specified, ignoring this device.
[   277.358] (II) This device may have been added with another device file.
[   287.920] (II) CHROME(0): ViaDisplayEnableCRT
[  1881.634] (II) CHROME(0): ViaDisplayDisableCRT
[  1888.799] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1888.799] (II) CHROME(0): VIALoadRgbLut
[  1888.849] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1888.849] (II) CHROME(0): VIALoadRgbLut
[  1888.850] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1888.850] (II) CHROME(0): VIALoadRgbLut
[  1888.900] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1888.900] (II) CHROME(0): VIALoadRgbLut
[  1888.901] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1888.902] (II) CHROME(0): VIALoadRgbLut
[  1888.952] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1888.952] (II) CHROME(0): VIALoadRgbLut
[  1888.953] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1888.953] (II) CHROME(0): VIALoadRgbLut
[  1889.003] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.003] (II) CHROME(0): VIALoadRgbLut
[  1889.004] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.004] (II) CHROME(0): VIALoadRgbLut
[  1889.054] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.054] (II) CHROME(0): VIALoadRgbLut
[  1889.055] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.055] (II) CHROME(0): VIALoadRgbLut
[  1889.105] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.105] (II) CHROME(0): VIALoadRgbLut
[  1889.106] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.106] (II) CHROME(0): VIALoadRgbLut
[  1889.157] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.157] (II) CHROME(0): VIALoadRgbLut
[  1889.158] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.158] (II) CHROME(0): VIALoadRgbLut
[  1889.208] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.208] (II) CHROME(0): VIALoadRgbLut
[  1889.209] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.209] (II) CHROME(0): VIALoadRgbLut
[  1889.259] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.259] (II) CHROME(0): VIALoadRgbLut
[  1889.260] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.260] (II) CHROME(0): VIALoadRgbLut
[  1889.310] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.310] (II) CHROME(0): VIALoadRgbLut
[  1889.311] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.311] (II) CHROME(0): VIALoadRgbLut
[  1889.361] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.362] (II) CHROME(0): VIALoadRgbLut
[  1889.362] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.362] (II) CHROME(0): VIALoadRgbLut
[  1889.413] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.413] (II) CHROME(0): VIALoadRgbLut
[  1889.414] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.414] (II) CHROME(0): VIALoadRgbLut
[  1889.464] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.464] (II) CHROME(0): VIALoadRgbLut
[  1889.465] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.465] (II) CHROME(0): VIALoadRgbLut
[  1889.515] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.515] (II) CHROME(0): VIALoadRgbLut
[  1889.516] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.516] (II) CHROME(0): VIALoadRgbLut
[  1889.566] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.566] (II) CHROME(0): VIALoadRgbLut
[  1889.567] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.567] (II) CHROME(0): VIALoadRgbLut
[  1889.617] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.618] (II) CHROME(0): VIALoadRgbLut
[  1889.619] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.619] (II) CHROME(0): VIALoadRgbLut
[  1889.669] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.669] (II) CHROME(0): VIALoadRgbLut
[  1889.670] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.670] (II) CHROME(0): VIALoadRgbLut
[  1889.720] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.720] (II) CHROME(0): VIALoadRgbLut
[  1889.721] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.721] (II) CHROME(0): VIALoadRgbLut
[  1889.771] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.771] (II) CHROME(0): VIALoadRgbLut
[  1889.772] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.772] (II) CHROME(0): VIALoadRgbLut
[  1889.822] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.823] (II) CHROME(0): VIALoadRgbLut
[  1889.823] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.823] (II) CHROME(0): VIALoadRgbLut
[  1889.874] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.874] (II) CHROME(0): VIALoadRgbLut
[  1889.875] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.875] (II) CHROME(0): VIALoadRgbLut
[  1889.925] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.925] (II) CHROME(0): VIALoadRgbLut
[  1889.926] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.926] (II) CHROME(0): VIALoadRgbLut
[  1889.976] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.976] (II) CHROME(0): VIALoadRgbLut
[  1889.977] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1889.977] (II) CHROME(0): VIALoadRgbLut
[  1890.027] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.027] (II) CHROME(0): VIALoadRgbLut
[  1890.028] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.028] (II) CHROME(0): VIALoadRgbLut
[  1890.078] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.079] (II) CHROME(0): VIALoadRgbLut
[  1890.079] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.079] (II) CHROME(0): VIALoadRgbLut
[  1890.130] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.130] (II) CHROME(0): VIALoadRgbLut
[  1890.131] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.131] (II) CHROME(0): VIALoadRgbLut
[  1890.181] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.181] (II) CHROME(0): VIALoadRgbLut
[  1890.182] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.182] (II) CHROME(0): VIALoadRgbLut
[  1890.232] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.232] (II) CHROME(0): VIALoadRgbLut
[  1890.233] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.233] (II) CHROME(0): VIALoadRgbLut
[  1890.283] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.284] (II) CHROME(0): VIALoadRgbLut
[  1890.284] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.285] (II) CHROME(0): VIALoadRgbLut
[  1890.335] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.335] (II) CHROME(0): VIALoadRgbLut
[  1890.438] (II) CHROME(0): VIALoadPalette: numColors: 256
[  1890.438] (II) CHROME(0): VIALoadRgbLut
[  1947.489] (II) CHROME(0): ViaDisplayEnableCRT
[  3428.901] (II) Open ACPI successful (/var/run/acpid.socket)
[  3515.659] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.659] (II) CHROME(0): VIALoadRgbLut
[  3515.691] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.691] (II) CHROME(0): VIALoadRgbLut
[  3515.710] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.710] (II) CHROME(0): VIALoadRgbLut
[  3515.742] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.742] (II) CHROME(0): VIALoadRgbLut
[  3515.760] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.761] (II) CHROME(0): VIALoadRgbLut
[  3515.793] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.793] (II) CHROME(0): VIALoadRgbLut
[  3515.811] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.811] (II) CHROME(0): VIALoadRgbLut
[  3515.843] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.844] (II) CHROME(0): VIALoadRgbLut
[  3515.862] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.862] (II) CHROME(0): VIALoadRgbLut
[  3515.894] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.894] (II) CHROME(0): VIALoadRgbLut
[  3515.913] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.913] (II) CHROME(0): VIALoadRgbLut
[  3515.945] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.945] (II) CHROME(0): VIALoadRgbLut
[  3515.964] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.964] (II) CHROME(0): VIALoadRgbLut
[  3515.996] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3515.996] (II) CHROME(0): VIALoadRgbLut
[  3516.015] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.015] (II) CHROME(0): VIALoadRgbLut
[  3516.047] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.047] (II) CHROME(0): VIALoadRgbLut
[  3516.065] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.065] (II) CHROME(0): VIALoadRgbLut
[  3516.097] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.097] (II) CHROME(0): VIALoadRgbLut
[  3516.116] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.116] (II) CHROME(0): VIALoadRgbLut
[  3516.148] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.148] (II) CHROME(0): VIALoadRgbLut
[  3516.167] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.167] (II) CHROME(0): VIALoadRgbLut
[  3516.199] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.199] (II) CHROME(0): VIALoadRgbLut
[  3516.218] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.218] (II) CHROME(0): VIALoadRgbLut
[  3516.250] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.250] (II) CHROME(0): VIALoadRgbLut
[  3516.268] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.268] (II) CHROME(0): VIALoadRgbLut
[  3516.300] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.301] (II) CHROME(0): VIALoadRgbLut
[  3516.319] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.319] (II) CHROME(0): VIALoadRgbLut
[  3516.351] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.352] (II) CHROME(0): VIALoadRgbLut
[  3516.370] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.370] (II) CHROME(0): VIALoadRgbLut
[  3516.402] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.402] (II) CHROME(0): VIALoadRgbLut
[  3516.421] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.421] (II) CHROME(0): VIALoadRgbLut
[  3516.453] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.453] (II) CHROME(0): VIALoadRgbLut
[  3516.471] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.472] (II) CHROME(0): VIALoadRgbLut
[  3516.504] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.504] (II) CHROME(0): VIALoadRgbLut
[  3516.522] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.523] (II) CHROME(0): VIALoadRgbLut
[  3516.555] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.555] (II) CHROME(0): VIALoadRgbLut
[  3516.573] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.574] (II) CHROME(0): VIALoadRgbLut
[  3516.606] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.606] (II) CHROME(0): VIALoadRgbLut
[  3516.624] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.625] (II) CHROME(0): VIALoadRgbLut
[  3516.657] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.657] (II) CHROME(0): VIALoadRgbLut
[  3516.675] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.676] (II) CHROME(0): VIALoadRgbLut
[  3516.708] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.708] (II) CHROME(0): VIALoadRgbLut
[  3516.726] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.727] (II) CHROME(0): VIALoadRgbLut
[  3516.759] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.759] (II) CHROME(0): VIALoadRgbLut
[  3516.777] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.778] (II) CHROME(0): VIALoadRgbLut
[  3516.810] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.810] (II) CHROME(0): VIALoadRgbLut
[  3516.828] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.828] (II) CHROME(0): VIALoadRgbLut
[  3516.861] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.861] (II) CHROME(0): VIALoadRgbLut
[  3516.879] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.879] (II) CHROME(0): VIALoadRgbLut
[  3516.912] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.912] (II) CHROME(0): VIALoadRgbLut
[  3516.930] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.930] (II) CHROME(0): VIALoadRgbLut
[  3516.963] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.963] (II) CHROME(0): VIALoadRgbLut
[  3516.981] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3516.981] (II) CHROME(0): VIALoadRgbLut
[  3517.014] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.014] (II) CHROME(0): VIALoadRgbLut
[  3517.032] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.032] (II) CHROME(0): VIALoadRgbLut
[  3517.065] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.065] (II) CHROME(0): VIALoadRgbLut
[  3517.083] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.083] (II) CHROME(0): VIALoadRgbLut
[  3517.116] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.116] (II) CHROME(0): VIALoadRgbLut
[  3517.134] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.134] (II) CHROME(0): VIALoadRgbLut
[  3517.167] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.167] (II) CHROME(0): VIALoadRgbLut
[  3517.288] (II) CHROME(0): VIALoadPalette: numColors: 256
[  3517.288] (II) CHROME(0): VIALoadRgbLut
[  6137.163] (II) evdev: Power Button: Close
[  6137.594] (II) UnloadModule: "evdev"
[  6137.594] (II) Unloading evdev
[  6137.738] (II) evdev: Power Button: Close
[  6137.946] (II) UnloadModule: "evdev"
[  6137.946] (II) Unloading evdev
[  6137.946] (II) evdev: AT Translated Set 2 keyboard: Close
[  6137.946] (II) UnloadModule: "evdev"
[  6137.946] (II) Unloading evdev
[  6137.947] (II) evdev: ImExPS/2 Generic Explorer Mouse: Close
[  6137.947] (II) UnloadModule: "evdev"
[  6137.947] (II) Unloading evdev
[  6138.351] (II) CHROME(0): ViaDisplayEnableCRT
[  6138.351] (II) CHROME(0): VIACloseScreen
[  6138.445] (II) CHROME(0): [drm] Cleaning up DMA ring-buffer.
[  6138.457] (II) CHROME(0): [drm] Freeing agp memory
[  6138.470] (II) CHROME(0): [drm] Releasing agp module
[  6138.471] (II) CHROME(0): [drm] removed 1 reserved context for kernel
[  6138.471] (II) CHROME(0): [drm] unmapping 8192 bytes of SAREA 0xec7c2000 at 0xb7755000
[  6138.472] (II) CHROME(0): [drm] Closed DRM master.
[  6138.472] Freed 12587008 (pool 1)
[  6138.504] (II) CHROME(0): [drm] IRQ handler uninstalled.
[  6138.979] (II) CHROME(0): VIARestore
[  6138.981] (II) CHROME(0): ViaDisablePrimaryFIFO
[  6138.981] (II) CHROME(0): VIAUnmapMem
[  6139.071]  ddxSigGiveUp: Closing log
[  6139.071] Server terminated successfully (0). Closing log file.
```

**Please have in mind that the Ubuntu version 9.10 I'm currently on is from a live CD(I don't want to install anymore unless I can fix it). If this xorg logs can help you I will install it as soon as possible, just say it :)

---

### Post by qneill on 2012-03-28
Ooops I meant to write

```
sudo apt-get install xserver-xorg-video-openchrome
```

---

### Post by qneill on 2012-03-28
There's your mode line from the 9.10 Xorg.0.log:

```
[   277.060] (II) CHROME(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)

```

The Xorg.0.log.old is just the last Xorg.0.log, moved out of the way.

On 11.10, the X11 output file is probably kept somewhere else...  you might have an /etc/X11/xorg.conf which tells you where it is, or it might be in /var/log/Xorg.XX.log where XX is a different number.

---

### Post by BicyclerBoy on 2012-03-28
The /var/log/Xorg.0.log shows you have kernel 3.2...this was never used with 9.10-11.10..
The Xorg versions look too new as well
Are you sure those log files are from the same 9.10 session..

AFAIK The old *buntus should run on newer kernels.
The chrome chipset doesn't have enough to run unity3d but you could use:
unity2d or gnome-fallback-session (bit like classic).

But Xubuntu uses Xfce & should one of the least demanding desktop managers (could be the ugliest as well..).

---

### Post by qneill on 2012-03-28
This looks like good information:

[http://openchrome.org/trac/wiki/SupportedHardware](http://openchrome.org/trac/wiki/SupportedHardware)

---

### Post by Sseo on 2012-03-29
@qneill - I'm on my college right now, I will try to install openchrome once I get home.

> There's your mode line from the 9.10 Xorg.0.log:
Should I use xrandr to add this modeline ? Not sure what are you telling me.

> On 11.10, the X11 output file is probably kept somewhere else... you might have an /etc/X11/xorg.conf which tells you where it is, or it might be in /var/log/Xorg.XX.log where XX is a different number.
I'm trying to set 1024x768 on 9.10 or 10.04. Resolution on 11.10 is working like a charm but it is lagging due to my old hardware(weird thing is that Xubuntu 11.10 is also lagging and I think its not that bad configuration, maybe I'm wrong).

@BicyclerBoy
> The /var/log/Xorg.0.log shows you have kernel 3.2...this was never used with 9.10-11.10..
The Xorg versions look too new as well
Are you sure those log files are from the same 9.10 session..

AFAIK The old *buntus should run on newer kernels.
The chrome chipset doesn't have enough to run unity3d but you could use:
unity2d or gnome-fallback-session (bit like classic).

But Xubuntu uses Xfce & should one of the least demanding desktop managers (could be the ugliest as well..).

Both log files are from the same Ubuntu 9.10 in live mode. When I install Ubuntu 10.04 I don't have the log files.(I can try again or try to get them from live mode if you wish).

I know my graphic card is bad, and I don't expect to run Unity nor have any 3D things and fancy stuff. I know Ubuntu 10.04 Gnome can work with my graphic card(I used to get it with old monitor via xrandr). 

**One question:** If my PC works great(no lagging) on Gnome 10.04, can I install Gnome with "sudo apt-get install gnome-shell" on 11.10 and have same non-lagging system ?

Thanks

---

### Post by Sseo on 2012-03-29
This is the output when I try to install openchrome :S

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by BicyclerBoy on 2012-03-29
Run *buntu 11.10 of your choosing ( to get res right) & then install
gnome-session-fallback
logout
select user
pick the session (gnome classic)
enter password
</done>

disable desktop effects (somewhere)..

The gnomes have used one of: metacity, mutter or clutter.
unity uses compiz

gnome-shell is different again --it is gnome3 & looks more like unity.

---

### Post by Sseo on 2012-03-30
I installed Ubuntu 11.10 and then the gnome you suggested to me, then I restarted the PC and logged in with "Gnome(No effects)" and it works better, but unfortunately still not good enough(not even close to 10.04). 

I don't know if there is any option left except buying a normal graphic card or even a normal PC, but if there is anything else you guys think that can help, don't hestitate to share it here :)

*And offcourse thanks for your advices, I really appreciate them :)

---

### Post by BicyclerBoy on 2012-03-30
Sorry that was not good enough..

I would have to agree that 10.04 just works better/faster than later versions..

The difference between 10.04 & later w.r.t openchrome graphics is probably not too much..Xorg & kernel versions

You could try:
10.04 and add in xorg-edgers launchpad ppa to update Xorg & openchrome driver..
You could try backported kernels to update the kernel driver modules if the above fails.

---

### Post by qneill on 2012-03-30
Sorry @Sseo it's not working out.

Yes I was thinking the modeline from the log file might be worth trying with xrandr since we can reasonably assume it is correct.

@BicyclerBoy sounds like he has some good ideas too, way ahead of my understanding :)

I'm still wondering where 11.10 is storing the log file.  I'm running 11.04 and have /var/log/Xorg.0.log as always.  The key for me would be to see what the 11.04 driver is doing differently.

You should try posting on an openchrome mailing list ([http://wiki.openchrome.org/mailman/listinfo]("http://wiki.openchrome.org/mailman/listinfo")) and see what they say.

Good luck,
-- 
Quentin

---

### Post by BicyclerBoy on 2012-03-31
There was an importent difference in the 2 Xorg.0.log files posted previously..

The 2nd file has:
277.233] (EE) AIGLX error: dlopen of /usr/lib/i386-linux-gnu/dri/unichrome_dri.so failed (/usr/lib/i386-linux-gnu/dri/unichrome_dri.so: cannot open shared object file: No such file or directory)
[   277.233] (EE) AIGLX: reverting to software rendering
[   277.278] (II) AIGLX: Loaded and initialized swrast

Software rendering/rasteriser instead of DRI interface would make all the difference..

Do you know how the machine status when it generated each file ?

So the best idea maybe 10.04 & then we can explain how to use a modeline if required..

Can you:
xrandr -q

or try:
xrandr --output default --mode 1024x768

---

### Post by Sseo on 2012-03-31
Thank you mates for amazing support but someone fixed it(maybe God while I was sleeping) :D Anyway, I installed Windows XP on first partition, then I installed Ubuntu 11.10 on second partition, and then I installed Ubuntu 10.04 on third partition. 

The question is: Does two Ubuntus in my case use the same kernel, or each uses its own ? Because I'm pretty much sure that having 11.10 installed is giving me 1024x768 on 10.04. I'm asking this because I would like to know what will happend if I delete 11.10 and XP now :)

Note - I got 1024x768 without any kind of tweaking, xrandr, updating etc. I started the installation before I went to bed, then got up few minutes ago, restarted the pc and "1024x768" was there :D

---

### Post by BicyclerBoy on 2012-03-31
Each ubuntu will be using its own boot image (kernel etc).

Sometimes computers work in (more) mysterious ways!

As long as **cold reset/starting** is working, there should be complete independence..

But be aware that warm resets/restarts between OS/ ubuntu release could leave things in different state to cold starts.
This tends to confuse problems like missing firmware etc..

So if you can cold start (from turned completely off over night) into 10.04 & the resolution is good, you should be okay with removing 11.10 etc.

---

### Post by Sseo on 2012-04-01
Great :) Thank you :)

---

