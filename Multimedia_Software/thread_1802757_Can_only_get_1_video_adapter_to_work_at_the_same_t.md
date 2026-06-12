---
title: "Can only get 1 video adapter to work at the same time"
date: 2011-07-12
forum: Multimedia Software
---

### Post by mick171 on 2011-07-12
Hello, I am knew to Linux but I don't mind having a crack at fixing things.

With out going into 2 much detail at this point this is my issue.

I have installed unbuntu 11.04. I have 3 screens. 2 are attached to a ATi adapter and 1 screen is a sandy bridge video adapter. 

I have already used the forums a lot to reach this point so thanks everybody for that.

When i change my bios to set the primary adapter to sandy bridge, I can only get 1 screen to work.

When I set my bios to point to the Ati adapter as primary, then only the 2 screens connected to that adapter work.

How do I get both video adapters and all 3 screens to work?

I have run out of ideas on what my next step should be.

Any suggestions would be most welcome.

Ati adapter is a Radeon HD 4800 Series. The Sandy bridge one HD Graphics Family

---

### Post by BicyclerBoy on 2011-07-12
There is likely some clever udev rule to handle this but nobody understands them..

I believe you need a simple xorg.conf file that lists a device section for each attached screen (3). In each device section you can state the driver "intel" & the PCI BusID.
I don't know what driver to use with AMD/ATI.

You find the PCI BusID from 
**lspci -qnn | grep VGA**
Note that lspci reports hexadecimal & Xorg requires decimal.

You may find that
**Xorg -configure**
solves your problem in one step..

If you are using 32 bit system you may need to increase the amount of RAM assigned at boot (some Grub config) as dual video cards uses more ram than default.

---

### Post by mick171 on 2011-07-13
Thank you for your quick reply.

Ok, i've had a look around and found this statement in Zorg.o.log

(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

so i updated xorg.conf as follows

Section "Device"
    Identifier  "amdcccle-Device[1]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:1"
    Screen      1
EndSection

rebooted but it's still complaining.

I have included my xorg.conf for refenece and some of my log

I'm still on a steep learning curve so I expect this to mean more to others than it does to me.

Can anyone see anything obviously wrong here?

---

### Post by mick171 on 2011-07-14
In my enthusiasm I forgot to repond to BicyclerBoy requests.. whoops

[B]lspci -qnn | grep VGA
0300

[/B][B]Xorg -configure
No I had already done this to get to my existing state.
I did go through the hoops again but ended putting back the original xorg.conf
as it was the best one.

I am using a 64bit os.

I booted to the one screen case (Sandly bridge) and it said it was using the Ati
controller. It's amazing it worked at all as the screen that worked wasn't attached to the Ati card.

I think I am way over my head on this. I tired to make sense of the xorg.conf file.
It would be useful if I could get my hands on a xorg.conf with 2 adapters and 3 screens to compare. Anyone got this?

Still I now know how to change the xorg.conf file, boot into terminal mode etc.. all useful stuff.

I spent the whole day running Linux(first ever) and managed to keep working to a fashion.. still lots of hardware not working but each day I make a little more progress. (managed to get 1 of the 2 printers working)

Anyway it's the 3 screens thats my most important issue. So any help is always welcome and thanks again for the help so far.


[/B][LEFT]
[IMG]http://www.answers.com/main/images/close.gif[/IMG] Read more >>   Options >>  
[[IMG]http://www.answers.com/main/images/answers-logo.gif[/IMG]]("http://www.answers.com?initiator=FFANS")

 
 


	

[/LEFT]

---

### Post by BicyclerBoy on 2011-07-15
The ATI spin on the xorg.conf file is very messy..

Both ATI device sections need to have the **same** PCI busID
BusID       "PCI:1:0:0"

There is **no** BusID       "PCI:1:0:1"...see the error in the Xorg.0.log

The ATI idea of having two/any monitors listed in the device section is not familiar ...
I would comment out the 
```
Option        "Monitor-CRT2" "0-CRT2"
```stuff...

The intel device section could be
```
Section "Device"
    Identifier     "Device2"
    Driver         "intel"
    VendorName     "Intel Graphicsp"
    BoardName      "something"
    BusID       "PCI:0:2:0"
    Screen        2
EndSection
```

---

### Post by mick171 on 2011-07-15
thank you [BicyclerBoy]("http://ubuntuforums.org/member.php?u=816321") for your support.
I played around with xorg.conf alone the lines you suggested and now it fails with Caught signal 11 (Segmentation fault). Server aborting

This seems to be quite a common error. I'm not even sure if this is moving forward or not??

Any ideas.

I've uploaded the xorg.conf, Xorg.0.log and output from lspci to aid PD.

I think I am now at my maximum for doing something really stupid... 'a little knowledge' :D

---

### Post by mick171 on 2011-07-15
whoops lost the files.. trying again..

---

### Post by mick171 on 2011-07-15
Oh well playing around and now no errors in Xorg.0.log

However only 2 the screens attached to the Ati card are working properly.
The other screen is active but with only a blank screen.

Using the Ati catalyst control still only shows 2 screens and the system monitors appl still only shows 2 screens.

I feel I am very close but what do I do now???

---

### Post by BicyclerBoy on 2011-07-15
I think your posted Xorg.0.log is truncated..
There should be a screen number in the "intel" device section.
It is possible that the AMD/ATI devices will be screens 0 & 1..

I would doubt any configuration of the intel GPU/screen is possible from the catalyst control panel.

---

### Post by mick171 on 2011-07-15
I was wondering about what determines the screen numbering system. Is there some command that I can issue that will help me determinate what screen has which number allocated to it?

I'l code up Screen 0 tomorrow and give it another go.
I had to trancate the log file , it was far too big. I'l be a little more careful next time.

time for some sleep...

---

### Post by mick171 on 2011-07-16
Right here are my latest offerings:
Seem to be getting less errors in the X log file

The X log referred to DFP1 and DFP2 so I added some new entries.
```

[     9.276] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[     9.276] X Protocol Version 11, Revision 0
[     9.276] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     9.276] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[     9.276] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=CC2420C52420B47C loop=/ubuntu/disks/root.disk ro quiet splash
[     9.276] Build Date: 21 May 2011  11:48:41AM
[     9.276] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     9.276] Current version of pixman: 0.20.2
[     9.276]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     9.276] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.276] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 16 13:22:22 2011
[     9.276] (==) Using config file: "/etc/X11/xorg.conf"
[     9.276] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.277] (==) ServerLayout "aticonfig Layout"
[     9.277] (**) |-->Screen "amdcccle-Screen[1]-0" (0)
[     9.277] (**) |   |-->Monitor "<default monitor>"
[     9.277] (**) |   |-->Device "amdcccle-Device[1]-0"
[     9.277] (==) No monitor specified for screen "amdcccle-Screen[1]-0".
    Using a default monitor configuration.
[     9.277] (==) Automatically adding devices
[     9.277] (==) Automatically enabling devices
[     9.277] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     9.277] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.277] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.277] (II) Loader magic: 0x7e0280
[     9.277] (II) Module ABI versions:
[     9.277]     X.Org ANSI C Emulation: 0.4
[     9.277]     X.Org Video Driver: 10.0
[     9.277]     X.Org XInput driver : 12.3
[     9.277]     X.Org Server Extension : 5.0
[     9.278] (--) PCI: (0:0:2:0) 8086:0112:1458:d000 rev 9, Mem @ 0xfb400000/4194304, 0xd0000000/268435456, I/O @ 0x0000ff00/64
[     9.278] (--) PCI:*(0:1:0:0) 1002:9460:1043:030c rev 0, Mem @ 0xe0000000/268435456, 0xfbae0000/65536, I/O @ 0x0000ce00/256, BIOS @ 0x????????/131072
[     9.278] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.278] (II) "extmod" will be loaded by default.
[     9.278] (II) "dbe" will be loaded by default.
[     9.278] (II) "glx" will be loaded by default.
[     9.278] (II) "record" will be loaded by default.
[     9.278] (II) "dri" will be loaded by default.
[     9.278] (II) "dri2" will be loaded by default.
[     9.278] (II) LoadModule: "extmod"
[     9.278] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.278] (II) Module extmod: vendor="X.Org Foundation"
[     9.278]     compiled for 1.10.1, module version = 1.0.0
[     9.278]     Module class: X.Org Server Extension
[     9.278]     ABI class: X.Org Server Extension, version 5.0
[     9.278] (II) Loading extension MIT-SCREEN-SAVER
[     9.279] (II) Loading extension XFree86-VidModeExtension
[     9.279] (II) Loading extension XFree86-DGA
[     9.279] (II) Loading extension DPMS
[     9.279] (II) Loading extension XVideo
[     9.279] (II) Loading extension XVideo-MotionCompensation
[     9.279] (II) Loading extension X-Resource
[     9.279] (II) LoadModule: "dbe"
[     9.279] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.279] (II) Module dbe: vendor="X.Org Foundation"
[     9.279]     compiled for 1.10.1, module version = 1.0.0
[     9.279]     Module class: X.Org Server Extension
[     9.279]     ABI class: X.Org Server Extension, version 5.0
[     9.279] (II) Loading extension DOUBLE-BUFFER
[     9.279] (II) LoadModule: "glx"
[     9.279] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[     9.279] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[     9.279]     compiled for 6.9.0, module version = 1.0.0
[     9.279] (II) Loading extension GLX
[     9.279] (II) LoadModule: "record"
[     9.279] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.279] (II) Module record: vendor="X.Org Foundation"
[     9.279]     compiled for 1.10.1, module version = 1.13.0
[     9.279]     Module class: X.Org Server Extension
[     9.279]     ABI class: X.Org Server Extension, version 5.0
[     9.279] (II) Loading extension RECORD
[     9.279] (II) LoadModule: "dri"
[     9.279] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.279] (II) Module dri: vendor="X.Org Foundation"
[     9.279]     compiled for 1.10.1, module version = 1.0.0
[     9.279]     ABI class: X.Org Server Extension, version 5.0
[     9.279] (II) Loading extension XFree86-DRI
[     9.279] (II) LoadModule: "dri2"
[     9.280] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.280] (II) Module dri2: vendor="X.Org Foundation"
[     9.280]     compiled for 1.10.1, module version = 1.2.0
[     9.280]     ABI class: X.Org Server Extension, version 5.0
[     9.280] (II) Loading extension DRI2
[     9.280] (II) LoadModule: "fglrx"
[     9.280] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.289] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[     9.289]     compiled for 1.4.99.906, module version = 8.86.5
[     9.289]     Module class: X.Org Video Driver
[     9.289] (II) Loading sub module "fglrxdrm"
[     9.289] (II) LoadModule: "fglrxdrm"
[     9.289] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.289] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.289]     compiled for 1.4.99.906, module version = 8.86.5
[     9.289] (II) ATI Proprietary Linux Driver Version Identifier:8.86.5
[     9.289] (II) ATI Proprietary Linux Driver Release Identifier: 8.861                                
[     9.289] (II) ATI Proprietary Linux Driver Build Date: May 24 2011 22:46:53
[     9.289] (++) using VT number 7

[     9.290] (WW) Falling back to old probe method for fglrx
[     9.294] (II) Loading PCS database from /etc/ati/amdpcsdb
[     9.295] (--) Chipset Supported AMD Graphics Processor (0x9460) found
[     9.295] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     9.295] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     9.295] (II) AMD Video driver is signed
[     9.296] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.296] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.296] (II) fglrx(0): pEnt->device->identifier=0x1c22120
[     9.296] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[     9.296] (II) Loading sub module "vgahw"
[     9.296] (II) LoadModule: "vgahw"
[     9.296] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     9.296] (II) Module vgahw: vendor="X.Org Foundation"
[     9.296]     compiled for 1.10.1, module version = 0.1.0
[     9.296]     ABI class: X.Org Video Driver, version 10.0
[     9.296] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     9.296] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     9.296] (==) fglrx(0): Default visual is TrueColor
[     9.296] (==) fglrx(0): RGB weight 888
[     9.296] (II) fglrx(0): Using 8 bits per RGB 
[     9.296] (==) fglrx(0): Buffer Tiling is ON
[     9.296] (II) Loading sub module "fglrxdrm"
[     9.296] (II) LoadModule: "fglrxdrm"
[     9.296] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.296] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.296]     compiled for 1.4.99.906, module version = 8.86.5
[     9.382] ukiDynamicMajor: found major device number 250
[     9.382] ukiDynamicMajor: found major device number 250
[     9.382] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.382] ukiOpenDevice: node name is /dev/ati/card0
[     9.382] ukiOpenDevice: open result is 11, (OK)
[     9.382] ukiOpenByBusid: ukiOpenMinor returns 11
[     9.382] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.382] (==) fglrx(0): NoAccel = NO
[     9.382] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[     9.382] (--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series           " (Chipset = 0x9460)
[     9.382] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x030c)
[     9.382] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     9.382] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     9.382] (--) fglrx(0): MMIO registers at 0xfbae0000
[     9.383] (--) fglrx(0): I/O port at 0x0000ce00
[     9.383] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     9.383] (II) fglrx(0): AC Adapter is used
[     9.385] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     9.466] (II) Loading sub module "vbe"
[     9.466] (II) LoadModule: "vbe"
[     9.477] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     9.478] (II) Module vbe: vendor="X.Org Foundation"
[     9.478]     compiled for 1.10.1, module version = 1.1.0
[     9.478]     ABI class: X.Org Video Driver, version 10.0
[     9.478] (II) fglrx(0): VESA BIOS detected
[     9.478] (II) fglrx(0): VESA VBE Version 3.0
[     9.478] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     9.478] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[     9.478] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[     9.478] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[     9.478] (II) fglrx(0): VESA VBE OEM Product: RV790
[     9.478] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     9.498] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[     9.498] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[     9.498] (II) fglrx(0): PCIE card detected
[     9.498] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     9.498] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     9.501] (II) fglrx(0): Using adapter: 1:0.0.
[     9.527] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[     9.549] (II) fglrx(0): Interrupt handler installed at IRQ 54.
[     9.549] (II) fglrx(0): RandR 1.2 support is enabled!
[     9.549] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     9.549] (==) fglrx(0): Center Mode is disabled 
[     9.549] (II) Loading sub module "fb"
[     9.549] (II) LoadModule: "fb"
[     9.549] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.550] (II) Module fb: vendor="X.Org Foundation"
[     9.550]     compiled for 1.10.1, module version = 1.0.0
[     9.550]     ABI class: X.Org ANSI C Emulation, version 0.4
[     9.550] (II) Loading sub module "ddc"
[     9.550] (II) LoadModule: "ddc"
[     9.550] (II) Module "ddc" already built-in
[    10.982] (II) fglrx(0): Finished Initialize PPLIB!
[    10.984] (II) fglrx(0): Output DFP1 using monitor section DFP1
[    10.984] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[    10.984] (II) fglrx(0): Output DFP2 using monitor section DFP2
[    10.984] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[    10.984] (II) fglrx(0): Output CRT1 using monitor section 0-CRT1
[    10.984] (**) fglrx(0): Option "PreferredMode" "1680x1050"
[    10.984] (**) fglrx(0): Option "Position" "0 0"
[    10.984] (**) fglrx(0): Option "Disable" "false"
[    10.984] (**) fglrx(0): Option "Rotate" "normal"
[    10.984] (**) fglrx(0): Option "TargetRefresh" "60"
[    10.984] (II) fglrx(0): Output CRT2 using monitor section 0-CRT2
[    10.984] (**) fglrx(0): Option "PreferredMode" "1680x1050"
[    10.984] (**) fglrx(0): Option "Position" "1680 0"
[    10.984] (**) fglrx(0): Option "Disable" "false"
[    10.984] (**) fglrx(0): Option "Rotate" "normal"
[    10.984] (**) fglrx(0): Option "TargetRefresh" "60"
[    10.984] (II) fglrx(0): Output TV has no monitor section
[    10.984] (II) fglrx(0): Output CV has no monitor section
[    10.984] (II) Loading sub module "ddc"
[    10.984] (II) LoadModule: "ddc"
[    10.984] (II) Module "ddc" already built-in
[    10.984] (II) fglrx(0): Connected Display0: CRT1
[    10.984] (II) fglrx(0): Display0 EDID data ---------------------------
[    10.984] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    10.984] (II) fglrx(0): Year: 2009  Week: 46
[    10.984] (II) fglrx(0): EDID Version: 1.3
[    10.984] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    10.984] (II) fglrx(0): Sync:  Separate
[    10.984] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    10.984] (II) fglrx(0): Gamma: 2.20
[    10.984] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    10.984] (II) fglrx(0): First detailed timing is preferred mode
[    10.984] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    10.984] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    10.984] (II) fglrx(0): Supported established timings:
[    10.984] (II) fglrx(0): 720x400@70Hz
[    10.984] (II) fglrx(0): 640x480@60Hz
[    10.984] (II) fglrx(0): 640x480@67Hz
[    10.984] (II) fglrx(0): 640x480@72Hz
[    10.984] (II) fglrx(0): 640x480@75Hz
[    10.984] (II) fglrx(0): 800x600@56Hz
[    10.984] (II) fglrx(0): 800x600@60Hz
[    10.984] (II) fglrx(0): 800x600@72Hz
[    10.984] (II) fglrx(0): 800x600@75Hz
[    10.984] (II) fglrx(0): 832x624@75Hz
[    10.984] (II) fglrx(0): 1024x768@60Hz
[    10.984] (II) fglrx(0): 1024x768@70Hz
[    10.984] (II) fglrx(0): 1024x768@75Hz
[    10.984] (II) fglrx(0): 1280x1024@75Hz
[    10.984] (II) fglrx(0): 1152x864@75Hz
[    10.984] (II) fglrx(0): Manufacturer's mask: 0
[    10.984] (II) fglrx(0): Supported standard timings:
[    10.984] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    10.984] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    10.984] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    10.984] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    10.984] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    10.984] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    10.984] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    10.984] (II) fglrx(0): Supported detailed timing:
[    10.984] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    10.984] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    10.984] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    10.984] (II) fglrx(0): Serial No: 1105594601134
[    10.984] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    10.984] (II) fglrx(0): Monitor name: PLT2250MTS
[    10.984] (II) fglrx(0): EDID (in hex):
[    10.984] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    10.984] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    10.984] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    10.984] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    10.984] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    10.985] (II) fglrx(0):     35353934363031313334000000fd0037
[    10.985] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    10.985] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    10.985] (II) fglrx(0): End of Display0 EDID data --------------------
[    10.985] (II) fglrx(0): Connected Display1: CRT2
[    10.985] (II) fglrx(0): Display1 EDID data ---------------------------
[    10.985] (II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    10.985] (II) fglrx(0): Year: 2006  Week: 31
[    10.985] (II) fglrx(0): EDID Version: 1.3
[    10.985] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    10.985] (II) fglrx(0): Sync:  Separate
[    10.985] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    10.985] (II) fglrx(0): Gamma: 2.20
[    10.985] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    10.985] (II) fglrx(0): Default color space is primary color space
[    10.985] (II) fglrx(0): First detailed timing is preferred mode
[    10.985] (II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    10.985] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    10.985] (II) fglrx(0): Supported established timings:
[    10.985] (II) fglrx(0): 720x400@70Hz
[    10.985] (II) fglrx(0): 640x480@60Hz
[    10.985] (II) fglrx(0): 640x480@67Hz
[    10.985] (II) fglrx(0): 640x480@72Hz
[    10.985] (II) fglrx(0): 640x480@75Hz
[    10.985] (II) fglrx(0): 800x600@56Hz
[    10.985] (II) fglrx(0): 800x600@60Hz
[    10.985] (II) fglrx(0): 800x600@72Hz
[    10.985] (II) fglrx(0): 800x600@75Hz
[    10.985] (II) fglrx(0): 832x624@75Hz
[    10.985] (II) fglrx(0): 1024x768@60Hz
[    10.985] (II) fglrx(0): 1024x768@70Hz
[    10.985] (II) fglrx(0): 1024x768@75Hz
[    10.985] (II) fglrx(0): 1280x1024@75Hz
[    10.985] (II) fglrx(0): Manufacturer's mask: 0
[    10.985] (II) fglrx(0): Supported standard timings:
[    10.985] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    10.985] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    10.985] (II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    10.985] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    10.985] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    10.985] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    10.985] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    10.985] (II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    10.985] (II) fglrx(0): Supported detailed timing:
[    10.985] (II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    10.985] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    10.985] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    10.985] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    10.985] (II) fglrx(0): Monitor name: Acer AL2216W
[    10.985] (II) fglrx(0): Serial No: ETL7409045
[    10.985] (II) fglrx(0): EDID (in hex):
[    10.985] (II) fglrx(0):     00ffffffffffff00047274ad7f321063
[    10.985] (II) fglrx(0):     1f100103682f1e782ec585a459499a24
[    10.985] (II) fglrx(0):     125054bfef0081808140714f9500950f
[    10.985] (II) fglrx(0):     b30081c08bc021399030621a274068b0
[    10.985] (II) fglrx(0):     3600d9281100001c000000fd00384c1e
[    10.985] (II) fglrx(0):     5215000a202020202020000000fc0041
[    10.985] (II) fglrx(0):     63657220414c32323136570a000000ff
[    10.985] (II) fglrx(0):     0045544c3734303930343520202000c7
[    10.985] (II) fglrx(0): End of Display1 EDID data --------------------
[    11.121] (II) fglrx(0): EDID for output DFP1
[    11.121] (II) fglrx(0): EDID for output DFP2
[    11.122] (II) fglrx(0): EDID for output CRT1
[    11.122] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    11.122] (II) fglrx(0): Year: 2009  Week: 46
[    11.122] (II) fglrx(0): EDID Version: 1.3
[    11.122] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    11.122] (II) fglrx(0): Sync:  Separate
[    11.122] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    11.122] (II) fglrx(0): Gamma: 2.20
[    11.122] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    11.122] (II) fglrx(0): First detailed timing is preferred mode
[    11.122] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    11.122] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    11.122] (II) fglrx(0): Supported established timings:
[    11.122] (II) fglrx(0): 720x400@70Hz
[    11.122] (II) fglrx(0): 640x480@60Hz
[    11.122] (II) fglrx(0): 640x480@67Hz
[    11.122] (II) fglrx(0): 640x480@72Hz
[    11.122] (II) fglrx(0): 640x480@75Hz
[    11.122] (II) fglrx(0): 800x600@56Hz
[    11.122] (II) fglrx(0): 800x600@60Hz
[    11.122] (II) fglrx(0): 800x600@72Hz
[    11.122] (II) fglrx(0): 800x600@75Hz
[    11.122] (II) fglrx(0): 832x624@75Hz
[    11.122] (II) fglrx(0): 1024x768@60Hz
[    11.122] (II) fglrx(0): 1024x768@70Hz
[    11.122] (II) fglrx(0): 1024x768@75Hz
[    11.122] (II) fglrx(0): 1280x1024@75Hz
[    11.122] (II) fglrx(0): 1152x864@75Hz
[    11.122] (II) fglrx(0): Manufacturer's mask: 0
[    11.122] (II) fglrx(0): Supported standard timings:
[    11.122] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    11.122] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    11.122] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    11.122] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    11.122] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    11.122] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    11.122] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    11.122] (II) fglrx(0): Supported detailed timing:
[    11.122] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    11.122] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    11.122] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    11.122] (II) fglrx(0): Serial No: 1105594601134
[    11.122] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    11.122] (II) fglrx(0): Monitor name: PLT2250MTS
[    11.122] (II) fglrx(0): EDID (in hex):
[    11.122] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    11.122] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    11.122] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    11.122] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    11.122] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    11.122] (II) fglrx(0):     35353934363031313334000000fd0037
[    11.122] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    11.122] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    11.122] (II) fglrx(0): Printing probed modes for output CRT1
[    11.122] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 -hsync -vsync (75.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    11.122] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    11.122] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    11.122] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    11.122] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    11.122] (II) fglrx(0): EDID for output CRT2
[    11.122] (II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    11.122] (II) fglrx(0): Year: 2006  Week: 31
[    11.122] (II) fglrx(0): EDID Version: 1.3
[    11.122] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    11.122] (II) fglrx(0): Sync:  Separate
[    11.122] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    11.122] (II) fglrx(0): Gamma: 2.20
[    11.122] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    11.122] (II) fglrx(0): Default color space is primary color space
[    11.122] (II) fglrx(0): First detailed timing is preferred mode
[    11.122] (II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    11.122] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    11.122] (II) fglrx(0): Supported established timings:
[    11.122] (II) fglrx(0): 720x400@70Hz
[    11.122] (II) fglrx(0): 640x480@60Hz
[    11.122] (II) fglrx(0): 640x480@67Hz
[    11.122] (II) fglrx(0): 640x480@72Hz
[    11.122] (II) fglrx(0): 640x480@75Hz
[    11.122] (II) fglrx(0): 800x600@56Hz
[    11.122] (II) fglrx(0): 800x600@60Hz
[    11.122] (II) fglrx(0): 800x600@72Hz
[    11.122] (II) fglrx(0): 800x600@75Hz
[    11.122] (II) fglrx(0): 832x624@75Hz
[    11.122] (II) fglrx(0): 1024x768@60Hz
[    11.122] (II) fglrx(0): 1024x768@70Hz
[    11.122] (II) fglrx(0): 1024x768@75Hz
[    11.122] (II) fglrx(0): 1280x1024@75Hz
[    11.122] (II) fglrx(0): Manufacturer's mask: 0
[    11.122] (II) fglrx(0): Supported standard timings:
[    11.122] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    11.122] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    11.122] (II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    11.122] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    11.122] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    11.122] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    11.122] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    11.122] (II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    11.122] (II) fglrx(0): Supported detailed timing:
[    11.122] (II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    11.122] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    11.122] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    11.122] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    11.122] (II) fglrx(0): Monitor name: Acer AL2216W
[    11.122] (II) fglrx(0): Serial No: ETL7409045
[    11.122] (II) fglrx(0): EDID (in hex):
[    11.122] (II) fglrx(0):     00ffffffffffff00047274ad7f321063
[    11.122] (II) fglrx(0):     1f100103682f1e782ec585a459499a24
[    11.122] (II) fglrx(0):     125054bfef0081808140714f9500950f
[    11.122] (II) fglrx(0):     b30081c08bc021399030621a274068b0
[    11.122] (II) fglrx(0):     3600d9281100001c000000fd00384c1e
[    11.122] (II) fglrx(0):     5215000a202020202020000000fc0041
[    11.122] (II) fglrx(0):     63657220414c32323136570a000000ff
[    11.122] (II) fglrx(0):     0045544c3734303930343520202000c7
[    11.122] (II) fglrx(0): Printing probed modes for output CRT2
[    11.122] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    11.123] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    11.123] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    11.123] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    11.123] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    11.123] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    11.123] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    11.123] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    11.123] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    11.123] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    11.123] (II) fglrx(0): EDID for output TV
[    11.123] (II) fglrx(0): EDID for output CV
[    11.123] (II) fglrx(0): Output DFP1 disconnected
[    11.123] (II) fglrx(0): Output DFP2 disconnected
[    11.123] (II) fglrx(0): Output CRT1 connected
[    11.123] (II) fglrx(0): Output CRT2 connected
[    11.123] (II) fglrx(0): Output TV disconnected
[    11.123] (II) fglrx(0): Output CV disconnected
[    11.123] (II) fglrx(0): Using user preference for initial modes
[    11.123] (II) fglrx(0): Output CRT1 using initial mode 1680x1050
[    11.123] (II) fglrx(0): Output CRT2 using initial mode 1680x1050
[    11.123] (II) fglrx(0): DPI set to (96, 96)
[    11.123] (II) fglrx(0): Adapter ATI Radeon HD 4800 Series            has 2 configurable heads and 2 displays connected.
[    11.123] (==) fglrx(0):  PseudoColor visuals disabled
[    11.123] (II) Loading sub module "ramdac"
[    11.123] (II) LoadModule: "ramdac"
[    11.123] (II) Module "ramdac" already built-in
[    11.123] (==) fglrx(0): NoDRI = NO
[    11.123] (==) fglrx(0): Capabilities: 0x00000000
[    11.123] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    11.123] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    11.123] (==) fglrx(0): UseFastTLS=0
[    11.123] (==) fglrx(0): BlockSignalsOnLock=1
[    11.123] (--) Depth 24 pixmap format is 32 bpp
[    11.123] (II) Loading extension ATIFGLRXDRI
[    11.123] (II) fglrx(0): doing swlDriScreenInit
[    11.123] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    11.123] ukiDynamicMajor: found major device number 250
[    11.123] ukiDynamicMajor: found major device number 250
[    11.123] ukiDynamicMajor: found major device number 250
[    11.123] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    11.123] ukiOpenDevice: node name is /dev/ati/card0
[    11.123] ukiOpenDevice: open result is 16, (OK)
[    11.123] ukiOpenByBusid: ukiOpenMinor returns 16
[    11.123] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    11.123] (II) fglrx(0): [uki] DRM interface version 1.0
[    11.123] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    11.123] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    11.123] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f585ae5e000
[    11.123] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    11.123] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    11.123] (II) fglrx(0): swlDriScreenInit done
[    11.123] (II) fglrx(0): Kernel Module Version Information:
[    11.123] (II) fglrx(0):     Name: fglrx
[    11.123] (II) fglrx(0):     Version: 8.86.5
[    11.123] (II) fglrx(0):     Date: May 24 2011
[    11.123] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    11.123] (II) fglrx(0): Kernel Module version matches driver.
[    11.123] (II) fglrx(0): Kernel Module Build Time Information:
[    11.123] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-8-generic
[    11.123] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    11.123] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    11.123] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    11.123] (II) fglrx(0): [uki] register handle = 0x00004000
[    11.134] (II) fglrx(0): DRI initialization successfull
[    11.134] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x018d8000
[    11.134] (==) fglrx(0): Backing store disabled
[    11.134] (II) Loading extension FGLRXEXTENSION
[    11.134] (==) fglrx(0): DPMS enabled
[    11.134] (II) fglrx(0): Initialized in-driver Xinerama extension
[    11.134] (**) fglrx(0): Textured Video is enabled.
[    11.134] (II) LoadModule: "glesx"
[    11.134] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    11.134] (II) Module glesx: vendor="X.Org Foundation"
[    11.134]     compiled for 1.4.99.906, module version = 1.0.0
[    11.134] (II) Loading extension GLESX
[    11.134] (II) fglrx(0): GLESX enableFlags = 528
[    11.134] (II) fglrx(0): GLESX is enabled
[    11.134] (II) LoadModule: "amdxmm"
[    11.134] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    11.134] (II) Module amdxmm: vendor="X.Org Foundation"
[    11.134]     compiled for 1.4.99.906, module version = 2.0.0
[    11.135] (II) Loading extension AMDXVOPL
[    11.135] (II) Loading extension AMDXVBA
[    11.135] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    11.137] (II) fglrx(0): Enable composite support successfully
[    11.137] (II) fglrx(0): X context handle = 0x1
[    11.137] (II) fglrx(0): [DRI] installation complete
[    11.137] (==) fglrx(0): Silken mouse enabled
[    11.137] (==) fglrx(0): Using HW cursor of display infrastructure!
[    11.137] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    11.137] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    11.137] (II) fglrx(0): Cannot set TV horizontal size.
[    11.137] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    11.137] (II) fglrx(0): Cannot set TV horizontal position.
[    11.137] (II) fglrx(0): Cannot set TV vertical position.
[    11.200] (II) fglrx(0): User Preference Output CRT2 using refresh rate 60.0 Hz.
[    11.243] (II) fglrx(0): User Preference Output CRT1 using refresh rate 60.0 Hz.
[    11.265] (--) RandR disabled

```
I'm not sure what to do next. Do you think we are getting closer?

---

### Post by mick171 on 2011-07-16
Here is my latest offering.
I spotted that references were being made to DFP1 & 2 so I added some new entries.
```

[     9.276] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[     9.276] X Protocol Version 11, Revision 0
[     9.276] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     9.276] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[     9.276] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=CC2420C52420B47C loop=/ubuntu/disks/root.disk ro quiet splash
[     9.276] Build Date: 21 May 2011  11:48:41AM
[     9.276] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     9.276] Current version of pixman: 0.20.2
[     9.276]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     9.276] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.276] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 16 13:22:22 2011
[     9.276] (==) Using config file: "/etc/X11/xorg.conf"
[     9.276] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.277] (==) ServerLayout "aticonfig Layout"
[     9.277] (**) |-->Screen "amdcccle-Screen[1]-0" (0)
[     9.277] (**) |   |-->Monitor "<default monitor>"
[     9.277] (**) |   |-->Device "amdcccle-Device[1]-0"
[     9.277] (==) No monitor specified for screen "amdcccle-Screen[1]-0".
    Using a default monitor configuration.
[     9.277] (==) Automatically adding devices
[     9.277] (==) Automatically enabling devices
[     9.277] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.277]     Entry deleted from font path.
[     9.277] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     9.277] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.277] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.277] (II) Loader magic: 0x7e0280
[     9.277] (II) Module ABI versions:
[     9.277]     X.Org ANSI C Emulation: 0.4
[     9.277]     X.Org Video Driver: 10.0
[     9.277]     X.Org XInput driver : 12.3
[     9.277]     X.Org Server Extension : 5.0
[     9.278] (--) PCI: (0:0:2:0) 8086:0112:1458:d000 rev 9, Mem @ 0xfb400000/4194304, 0xd0000000/268435456, I/O @ 0x0000ff00/64
[     9.278] (--) PCI:*(0:1:0:0) 1002:9460:1043:030c rev 0, Mem @ 0xe0000000/268435456, 0xfbae0000/65536, I/O @ 0x0000ce00/256, BIOS @ 0x????????/131072
[     9.278] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.278] (II) "extmod" will be loaded by default.
[     9.278] (II) "dbe" will be loaded by default.
[     9.278] (II) "glx" will be loaded by default.
[     9.278] (II) "record" will be loaded by default.
[     9.278] (II) "dri" will be loaded by default.
[     9.278] (II) "dri2" will be loaded by default.
[     9.278] (II) LoadModule: "extmod"
[     9.278] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.278] (II) Module extmod: vendor="X.Org Foundation"
[     9.278]     compiled for 1.10.1, module version = 1.0.0
[     9.278]     Module class: X.Org Server Extension
[     9.278]     ABI class: X.Org Server Extension, version 5.0
[     9.278] (II) Loading extension MIT-SCREEN-SAVER
[     9.279] (II) Loading extension XFree86-VidModeExtension
[     9.279] (II) Loading extension XFree86-DGA
[     9.279] (II) Loading extension DPMS
[     9.279] (II) Loading extension XVideo
[     9.279] (II) Loading extension XVideo-MotionCompensation
[     9.279] (II) Loading extension X-Resource
[     9.279] (II) LoadModule: "dbe"
[     9.279] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.279] (II) Module dbe: vendor="X.Org Foundation"
[     9.279]     compiled for 1.10.1, module version = 1.0.0
[     9.279]     Module class: X.Org Server Extension
[     9.279]     ABI class: X.Org Server Extension, version 5.0
[     9.279] (II) Loading extension DOUBLE-BUFFER
[     9.279] (II) LoadModule: "glx"
[     9.279] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[     9.279] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[     9.279]     compiled for 6.9.0, module version = 1.0.0
[     9.279] (II) Loading extension GLX
[     9.279] (II) LoadModule: "record"
[     9.279] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.279] (II) Module record: vendor="X.Org Foundation"
[     9.279]     compiled for 1.10.1, module version = 1.13.0
[     9.279]     Module class: X.Org Server Extension
[     9.279]     ABI class: X.Org Server Extension, version 5.0
[     9.279] (II) Loading extension RECORD
[     9.279] (II) LoadModule: "dri"
[     9.279] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.279] (II) Module dri: vendor="X.Org Foundation"
[     9.279]     compiled for 1.10.1, module version = 1.0.0
[     9.279]     ABI class: X.Org Server Extension, version 5.0
[     9.279] (II) Loading extension XFree86-DRI
[     9.279] (II) LoadModule: "dri2"
[     9.280] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.280] (II) Module dri2: vendor="X.Org Foundation"
[     9.280]     compiled for 1.10.1, module version = 1.2.0
[     9.280]     ABI class: X.Org Server Extension, version 5.0
[     9.280] (II) Loading extension DRI2
[     9.280] (II) LoadModule: "fglrx"
[     9.280] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.289] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[     9.289]     compiled for 1.4.99.906, module version = 8.86.5
[     9.289]     Module class: X.Org Video Driver
[     9.289] (II) Loading sub module "fglrxdrm"
[     9.289] (II) LoadModule: "fglrxdrm"
[     9.289] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.289] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.289]     compiled for 1.4.99.906, module version = 8.86.5
[     9.289] (II) ATI Proprietary Linux Driver Version Identifier:8.86.5
[     9.289] (II) ATI Proprietary Linux Driver Release Identifier: 8.861                                
[     9.289] (II) ATI Proprietary Linux Driver Build Date: May 24 2011 22:46:53
[     9.289] (++) using VT number 7

[     9.290] (WW) Falling back to old probe method for fglrx
[     9.294] (II) Loading PCS database from /etc/ati/amdpcsdb
[     9.295] (--) Chipset Supported AMD Graphics Processor (0x9460) found
[     9.295] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     9.295] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     9.295] (II) AMD Video driver is signed
[     9.296] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.296] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.296] (II) fglrx(0): pEnt->device->identifier=0x1c22120
[     9.296] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[     9.296] (II) Loading sub module "vgahw"
[     9.296] (II) LoadModule: "vgahw"
[     9.296] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     9.296] (II) Module vgahw: vendor="X.Org Foundation"
[     9.296]     compiled for 1.10.1, module version = 0.1.0
[     9.296]     ABI class: X.Org Video Driver, version 10.0
[     9.296] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     9.296] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     9.296] (==) fglrx(0): Default visual is TrueColor
[     9.296] (==) fglrx(0): RGB weight 888
[     9.296] (II) fglrx(0): Using 8 bits per RGB 
[     9.296] (==) fglrx(0): Buffer Tiling is ON
[     9.296] (II) Loading sub module "fglrxdrm"
[     9.296] (II) LoadModule: "fglrxdrm"
[     9.296] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.296] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.296]     compiled for 1.4.99.906, module version = 8.86.5
[     9.382] ukiDynamicMajor: found major device number 250
[     9.382] ukiDynamicMajor: found major device number 250
[     9.382] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.382] ukiOpenDevice: node name is /dev/ati/card0
[     9.382] ukiOpenDevice: open result is 11, (OK)
[     9.382] ukiOpenByBusid: ukiOpenMinor returns 11
[     9.382] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.382] (==) fglrx(0): NoAccel = NO
[     9.382] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[     9.382] (--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series           " (Chipset = 0x9460)
[     9.382] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x030c)
[     9.382] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     9.382] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     9.382] (--) fglrx(0): MMIO registers at 0xfbae0000
[     9.383] (--) fglrx(0): I/O port at 0x0000ce00
[     9.383] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     9.383] (II) fglrx(0): AC Adapter is used
[     9.385] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     9.466] (II) Loading sub module "vbe"
[     9.466] (II) LoadModule: "vbe"
[     9.477] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     9.478] (II) Module vbe: vendor="X.Org Foundation"
[     9.478]     compiled for 1.10.1, module version = 1.1.0
[     9.478]     ABI class: X.Org Video Driver, version 10.0
[     9.478] (II) fglrx(0): VESA BIOS detected
[     9.478] (II) fglrx(0): VESA VBE Version 3.0
[     9.478] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     9.478] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[     9.478] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[     9.478] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[     9.478] (II) fglrx(0): VESA VBE OEM Product: RV790
[     9.478] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     9.498] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[     9.498] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[     9.498] (II) fglrx(0): PCIE card detected
[     9.498] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     9.498] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     9.501] (II) fglrx(0): Using adapter: 1:0.0.
[     9.527] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[     9.549] (II) fglrx(0): Interrupt handler installed at IRQ 54.
[     9.549] (II) fglrx(0): RandR 1.2 support is enabled!
[     9.549] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     9.549] (==) fglrx(0): Center Mode is disabled 
[     9.549] (II) Loading sub module "fb"
[     9.549] (II) LoadModule: "fb"
[     9.549] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.550] (II) Module fb: vendor="X.Org Foundation"
[     9.550]     compiled for 1.10.1, module version = 1.0.0
[     9.550]     ABI class: X.Org ANSI C Emulation, version 0.4
[     9.550] (II) Loading sub module "ddc"
[     9.550] (II) LoadModule: "ddc"
[     9.550] (II) Module "ddc" already built-in
[    10.982] (II) fglrx(0): Finished Initialize PPLIB!
[    10.984] (II) fglrx(0): Output DFP1 using monitor section DFP1
[    10.984] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[    10.984] (II) fglrx(0): Output DFP2 using monitor section DFP2
[    10.984] (**) fglrx(0): Option "PreferredMode" "1280x1024"
[    10.984] (II) fglrx(0): Output CRT1 using monitor section 0-CRT1
[    10.984] (**) fglrx(0): Option "PreferredMode" "1680x1050"
[    10.984] (**) fglrx(0): Option "Position" "0 0"
[    10.984] (**) fglrx(0): Option "Disable" "false"
[    10.984] (**) fglrx(0): Option "Rotate" "normal"
[    10.984] (**) fglrx(0): Option "TargetRefresh" "60"
[    10.984] (II) fglrx(0): Output CRT2 using monitor section 0-CRT2
[    10.984] (**) fglrx(0): Option "PreferredMode" "1680x1050"
[    10.984] (**) fglrx(0): Option "Position" "1680 0"
[    10.984] (**) fglrx(0): Option "Disable" "false"
[    10.984] (**) fglrx(0): Option "Rotate" "normal"
[    10.984] (**) fglrx(0): Option "TargetRefresh" "60"
[    10.984] (II) fglrx(0): Output TV has no monitor section
[    10.984] (II) fglrx(0): Output CV has no monitor section
[    10.984] (II) Loading sub module "ddc"
[    10.984] (II) LoadModule: "ddc"
[    10.984] (II) Module "ddc" already built-in
[    10.984] (II) fglrx(0): Connected Display0: CRT1
[    10.984] (II) fglrx(0): Display0 EDID data ---------------------------
[    10.984] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    10.984] (II) fglrx(0): Year: 2009  Week: 46
[    10.984] (II) fglrx(0): EDID Version: 1.3
[    10.984] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    10.984] (II) fglrx(0): Sync:  Separate
[    10.984] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    10.984] (II) fglrx(0): Gamma: 2.20
[    10.984] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    10.984] (II) fglrx(0): First detailed timing is preferred mode
[    10.984] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    10.984] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    10.984] (II) fglrx(0): Supported established timings:
[    10.984] (II) fglrx(0): 720x400@70Hz
[    10.984] (II) fglrx(0): 640x480@60Hz
[    10.984] (II) fglrx(0): 640x480@67Hz
[    10.984] (II) fglrx(0): 640x480@72Hz
[    10.984] (II) fglrx(0): 640x480@75Hz
[    10.984] (II) fglrx(0): 800x600@56Hz
[    10.984] (II) fglrx(0): 800x600@60Hz
[    10.984] (II) fglrx(0): 800x600@72Hz
[    10.984] (II) fglrx(0): 800x600@75Hz
[    10.984] (II) fglrx(0): 832x624@75Hz
[    10.984] (II) fglrx(0): 1024x768@60Hz
[    10.984] (II) fglrx(0): 1024x768@70Hz
[    10.984] (II) fglrx(0): 1024x768@75Hz
[    10.984] (II) fglrx(0): 1280x1024@75Hz
[    10.984] (II) fglrx(0): 1152x864@75Hz
[    10.984] (II) fglrx(0): Manufacturer's mask: 0
[    10.984] (II) fglrx(0): Supported standard timings:
[    10.984] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    10.984] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    10.984] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    10.984] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    10.984] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    10.984] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    10.984] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    10.984] (II) fglrx(0): Supported detailed timing:
[    10.984] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    10.984] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    10.984] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    10.984] (II) fglrx(0): Serial No: 1105594601134
[    10.984] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    10.984] (II) fglrx(0): Monitor name: PLT2250MTS
[    10.984] (II) fglrx(0): EDID (in hex):
[    10.984] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    10.984] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    10.984] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    10.984] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    10.984] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    10.985] (II) fglrx(0):     35353934363031313334000000fd0037
[    10.985] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    10.985] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    10.985] (II) fglrx(0): End of Display0 EDID data --------------------
[    10.985] (II) fglrx(0): Connected Display1: CRT2
[    10.985] (II) fglrx(0): Display1 EDID data ---------------------------
[    10.985] (II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    10.985] (II) fglrx(0): Year: 2006  Week: 31
[    10.985] (II) fglrx(0): EDID Version: 1.3
[    10.985] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    10.985] (II) fglrx(0): Sync:  Separate
[    10.985] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    10.985] (II) fglrx(0): Gamma: 2.20
[    10.985] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    10.985] (II) fglrx(0): Default color space is primary color space
[    10.985] (II) fglrx(0): First detailed timing is preferred mode
[    10.985] (II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    10.985] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    10.985] (II) fglrx(0): Supported established timings:
[    10.985] (II) fglrx(0): 720x400@70Hz
[    10.985] (II) fglrx(0): 640x480@60Hz
[    10.985] (II) fglrx(0): 640x480@67Hz
[    10.985] (II) fglrx(0): 640x480@72Hz
[    10.985] (II) fglrx(0): 640x480@75Hz
[    10.985] (II) fglrx(0): 800x600@56Hz
[    10.985] (II) fglrx(0): 800x600@60Hz
[    10.985] (II) fglrx(0): 800x600@72Hz
[    10.985] (II) fglrx(0): 800x600@75Hz
[    10.985] (II) fglrx(0): 832x624@75Hz
[    10.985] (II) fglrx(0): 1024x768@60Hz
[    10.985] (II) fglrx(0): 1024x768@70Hz
[    10.985] (II) fglrx(0): 1024x768@75Hz
[    10.985] (II) fglrx(0): 1280x1024@75Hz
[    10.985] (II) fglrx(0): Manufacturer's mask: 0
[    10.985] (II) fglrx(0): Supported standard timings:
[    10.985] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    10.985] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    10.985] (II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    10.985] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    10.985] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    10.985] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    10.985] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    10.985] (II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    10.985] (II) fglrx(0): Supported detailed timing:
[    10.985] (II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    10.985] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    10.985] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    10.985] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    10.985] (II) fglrx(0): Monitor name: Acer AL2216W
[    10.985] (II) fglrx(0): Serial No: ETL7409045
[    10.985] (II) fglrx(0): EDID (in hex):
[    10.985] (II) fglrx(0):     00ffffffffffff00047274ad7f321063
[    10.985] (II) fglrx(0):     1f100103682f1e782ec585a459499a24
[    10.985] (II) fglrx(0):     125054bfef0081808140714f9500950f
[    10.985] (II) fglrx(0):     b30081c08bc021399030621a274068b0
[    10.985] (II) fglrx(0):     3600d9281100001c000000fd00384c1e
[    10.985] (II) fglrx(0):     5215000a202020202020000000fc0041
[    10.985] (II) fglrx(0):     63657220414c32323136570a000000ff
[    10.985] (II) fglrx(0):     0045544c3734303930343520202000c7
[    10.985] (II) fglrx(0): End of Display1 EDID data --------------------
[    11.121] (II) fglrx(0): EDID for output DFP1
[    11.121] (II) fglrx(0): EDID for output DFP2
[    11.122] (II) fglrx(0): EDID for output CRT1
[    11.122] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    11.122] (II) fglrx(0): Year: 2009  Week: 46
[    11.122] (II) fglrx(0): EDID Version: 1.3
[    11.122] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    11.122] (II) fglrx(0): Sync:  Separate
[    11.122] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    11.122] (II) fglrx(0): Gamma: 2.20
[    11.122] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    11.122] (II) fglrx(0): First detailed timing is preferred mode
[    11.122] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    11.122] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    11.122] (II) fglrx(0): Supported established timings:
[    11.122] (II) fglrx(0): 720x400@70Hz
[    11.122] (II) fglrx(0): 640x480@60Hz
[    11.122] (II) fglrx(0): 640x480@67Hz
[    11.122] (II) fglrx(0): 640x480@72Hz
[    11.122] (II) fglrx(0): 640x480@75Hz
[    11.122] (II) fglrx(0): 800x600@56Hz
[    11.122] (II) fglrx(0): 800x600@60Hz
[    11.122] (II) fglrx(0): 800x600@72Hz
[    11.122] (II) fglrx(0): 800x600@75Hz
[    11.122] (II) fglrx(0): 832x624@75Hz
[    11.122] (II) fglrx(0): 1024x768@60Hz
[    11.122] (II) fglrx(0): 1024x768@70Hz
[    11.122] (II) fglrx(0): 1024x768@75Hz
[    11.122] (II) fglrx(0): 1280x1024@75Hz
[    11.122] (II) fglrx(0): 1152x864@75Hz
[    11.122] (II) fglrx(0): Manufacturer's mask: 0
[    11.122] (II) fglrx(0): Supported standard timings:
[    11.122] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    11.122] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    11.122] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    11.122] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    11.122] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    11.122] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    11.122] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    11.122] (II) fglrx(0): Supported detailed timing:
[    11.122] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    11.122] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    11.122] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    11.122] (II) fglrx(0): Serial No: 1105594601134
[    11.122] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    11.122] (II) fglrx(0): Monitor name: PLT2250MTS
[    11.122] (II) fglrx(0): EDID (in hex):
[    11.122] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    11.122] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    11.122] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    11.122] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    11.122] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    11.122] (II) fglrx(0):     35353934363031313334000000fd0037
[    11.122] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    11.122] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    11.122] (II) fglrx(0): Printing probed modes for output CRT1
[    11.122] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 -hsync -vsync (75.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    11.122] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    11.122] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    11.122] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    11.122] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    11.122] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    11.122] (II) fglrx(0): EDID for output CRT2
[    11.122] (II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    11.122] (II) fglrx(0): Year: 2006  Week: 31
[    11.122] (II) fglrx(0): EDID Version: 1.3
[    11.122] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    11.122] (II) fglrx(0): Sync:  Separate
[    11.122] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    11.122] (II) fglrx(0): Gamma: 2.20
[    11.122] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    11.122] (II) fglrx(0): Default color space is primary color space
[    11.122] (II) fglrx(0): First detailed timing is preferred mode
[    11.122] (II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    11.122] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    11.122] (II) fglrx(0): Supported established timings:
[    11.122] (II) fglrx(0): 720x400@70Hz
[    11.122] (II) fglrx(0): 640x480@60Hz
[    11.122] (II) fglrx(0): 640x480@67Hz
[    11.122] (II) fglrx(0): 640x480@72Hz
[    11.122] (II) fglrx(0): 640x480@75Hz
[    11.122] (II) fglrx(0): 800x600@56Hz
[    11.122] (II) fglrx(0): 800x600@60Hz
[    11.122] (II) fglrx(0): 800x600@72Hz
[    11.122] (II) fglrx(0): 800x600@75Hz
[    11.122] (II) fglrx(0): 832x624@75Hz
[    11.122] (II) fglrx(0): 1024x768@60Hz
[    11.122] (II) fglrx(0): 1024x768@70Hz
[    11.122] (II) fglrx(0): 1024x768@75Hz
[    11.122] (II) fglrx(0): 1280x1024@75Hz
[    11.122] (II) fglrx(0): Manufacturer's mask: 0
[    11.122] (II) fglrx(0): Supported standard timings:
[    11.122] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    11.122] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    11.122] (II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    11.122] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    11.122] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    11.122] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    11.122] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    11.122] (II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    11.122] (II) fglrx(0): Supported detailed timing:
[    11.122] (II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    11.122] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    11.122] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    11.122] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    11.122] (II) fglrx(0): Monitor name: Acer AL2216W
[    11.122] (II) fglrx(0): Serial No: ETL7409045
[    11.122] (II) fglrx(0): EDID (in hex):
[    11.122] (II) fglrx(0):     00ffffffffffff00047274ad7f321063
[    11.122] (II) fglrx(0):     1f100103682f1e782ec585a459499a24
[    11.122] (II) fglrx(0):     125054bfef0081808140714f9500950f
[    11.122] (II) fglrx(0):     b30081c08bc021399030621a274068b0
[    11.122] (II) fglrx(0):     3600d9281100001c000000fd00384c1e
[    11.122] (II) fglrx(0):     5215000a202020202020000000fc0041
[    11.122] (II) fglrx(0):     63657220414c32323136570a000000ff
[    11.122] (II) fglrx(0):     0045544c3734303930343520202000c7
[    11.122] (II) fglrx(0): Printing probed modes for output CRT2
[    11.122] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    11.122] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    11.122] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    11.122] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    11.123] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    11.123] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    11.123] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    11.123] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    11.123] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    11.123] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    11.123] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    11.123] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    11.123] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    11.123] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    11.123] (II) fglrx(0): EDID for output TV
[    11.123] (II) fglrx(0): EDID for output CV
[    11.123] (II) fglrx(0): Output DFP1 disconnected
[    11.123] (II) fglrx(0): Output DFP2 disconnected
[    11.123] (II) fglrx(0): Output CRT1 connected
[    11.123] (II) fglrx(0): Output CRT2 connected
[    11.123] (II) fglrx(0): Output TV disconnected
[    11.123] (II) fglrx(0): Output CV disconnected
[    11.123] (II) fglrx(0): Using user preference for initial modes
[    11.123] (II) fglrx(0): Output CRT1 using initial mode 1680x1050
[    11.123] (II) fglrx(0): Output CRT2 using initial mode 1680x1050
[    11.123] (II) fglrx(0): DPI set to (96, 96)
[    11.123] (II) fglrx(0): Adapter ATI Radeon HD 4800 Series            has 2 configurable heads and 2 displays connected.
[    11.123] (==) fglrx(0):  PseudoColor visuals disabled
[    11.123] (II) Loading sub module "ramdac"
[    11.123] (II) LoadModule: "ramdac"
[    11.123] (II) Module "ramdac" already built-in
[    11.123] (==) fglrx(0): NoDRI = NO
[    11.123] (==) fglrx(0): Capabilities: 0x00000000
[    11.123] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    11.123] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    11.123] (==) fglrx(0): UseFastTLS=0
[    11.123] (==) fglrx(0): BlockSignalsOnLock=1
[    11.123] (--) Depth 24 pixmap format is 32 bpp
[    11.123] (II) Loading extension ATIFGLRXDRI
[    11.123] (II) fglrx(0): doing swlDriScreenInit
[    11.123] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    11.123] ukiDynamicMajor: found major device number 250
[    11.123] ukiDynamicMajor: found major device number 250
[    11.123] ukiDynamicMajor: found major device number 250
[    11.123] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    11.123] ukiOpenDevice: node name is /dev/ati/card0
[    11.123] ukiOpenDevice: open result is 16, (OK)
[    11.123] ukiOpenByBusid: ukiOpenMinor returns 16
[    11.123] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    11.123] (II) fglrx(0): [uki] DRM interface version 1.0
[    11.123] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    11.123] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    11.123] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f585ae5e000
[    11.123] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    11.123] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    11.123] (II) fglrx(0): swlDriScreenInit done
[    11.123] (II) fglrx(0): Kernel Module Version Information:
[    11.123] (II) fglrx(0):     Name: fglrx
[    11.123] (II) fglrx(0):     Version: 8.86.5
[    11.123] (II) fglrx(0):     Date: May 24 2011
[    11.123] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    11.123] (II) fglrx(0): Kernel Module version matches driver.
[    11.123] (II) fglrx(0): Kernel Module Build Time Information:
[    11.123] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-8-generic
[    11.123] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    11.123] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    11.123] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    11.123] (II) fglrx(0): [uki] register handle = 0x00004000
[    11.134] (II) fglrx(0): DRI initialization successfull
[    11.134] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x018d8000
[    11.134] (==) fglrx(0): Backing store disabled
[    11.134] (II) Loading extension FGLRXEXTENSION
[    11.134] (==) fglrx(0): DPMS enabled
[    11.134] (II) fglrx(0): Initialized in-driver Xinerama extension
[    11.134] (**) fglrx(0): Textured Video is enabled.
[    11.134] (II) LoadModule: "glesx"
[    11.134] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    11.134] (II) Module glesx: vendor="X.Org Foundation"
[    11.134]     compiled for 1.4.99.906, module version = 1.0.0
[    11.134] (II) Loading extension GLESX
[    11.134] (II) fglrx(0): GLESX enableFlags = 528
[    11.134] (II) fglrx(0): GLESX is enabled
[    11.134] (II) LoadModule: "amdxmm"
[    11.134] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    11.134] (II) Module amdxmm: vendor="X.Org Foundation"
[    11.134]     compiled for 1.4.99.906, module version = 2.0.0
[    11.135] (II) Loading extension AMDXVOPL
[    11.135] (II) Loading extension AMDXVBA
[    11.135] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    11.137] (II) fglrx(0): Enable composite support successfully
[    11.137] (II) fglrx(0): X context handle = 0x1
[    11.137] (II) fglrx(0): [DRI] installation complete
[    11.137] (==) fglrx(0): Silken mouse enabled
[    11.137] (==) fglrx(0): Using HW cursor of display infrastructure!
[    11.137] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    11.137] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    11.137] (II) fglrx(0): Cannot set TV horizontal size.
[    11.137] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    11.137] (II) fglrx(0): Cannot set TV horizontal position.
[    11.137] (II) fglrx(0): Cannot set TV vertical position.
[    11.200] (II) fglrx(0): User Preference Output CRT2 using refresh rate 60.0 Hz.
[    11.243] (II) fglrx(0): User Preference Output CRT1 using refresh rate 60.0 Hz.
[    11.265] (--) RandR disabled

```
What do I do now?

---

### Post by mick171 on 2011-07-17
whoops apologies for several duplicate posts.

---

### Post by BicyclerBoy on 2011-07-17
You should only have (3) device sections..

Maybe the AMD/ATi driver can support the intel graphics device; the log file kind-off suggests it is supported.

I could be wrong about the PCI BusIDs for your GPU, it appears that some old dual-head GPUs are actually dual-GPUs...

Post this cmd output (last time was not useful)
lspci -nn

There  some similar bugs/errors reported on the net that suggest there is a  Xorg ABI library mis-match with natty Xorg & older ATI drivers..
It may be worth trying the xorg-edgers ppa but I'm not sure they have the fglrx driver..

FWIU The Xorg changes have broken video drivers in 10.10 & 10.04.

---

### Post by mick171 on 2011-07-18
Please see below output form lspci --n, latest xorg with same driver and log file.

Identifier     "aticonfig Layout"
    Screen      0  "0-CRT1" 0 0
    Screen      2  "VGA1"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "VGA1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1440x900"
EndSection

Section "Device"
    Identifier  "aticonfig-Device1"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
    Screen      0
EndSection

Section "Device"
    Identifier  "aticonfig-Device2"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "amdcccle-Device"
    Driver      "fglrx"
    Option        "Monitor-VGA1" "VGA1"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "0-CRT1"
    Device     "aticonfig-Device1"
    DefaultDepth     24
    SubSection "Display"
        Virtual   3600 1920
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "0-CRT2"
    Device     "aticonfig-Device2"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "VGA1"
    Device     "amdcccle-Device"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

log
[     9.237] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[     9.237] X Protocol Version 11, Revision 0
[     9.237] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[     9.237] Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64
[     9.237] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=CC2420C52420B47C loop=/ubuntu/disks/root.disk ro quiet splash
[     9.237] Build Date: 21 May 2011  11:48:41AM
[     9.237] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     9.237] Current version of pixman: 0.20.2
[     9.237]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     9.237] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.237] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 18 14:27:15 2011
[     9.237] (==) Using config file: "/etc/X11/xorg.conf"
[     9.237] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.237] (==) ServerLayout "aticonfig Layout"
[     9.237] (**) |-->Screen "0-CRT1" (0)
[     9.237] (**) |   |-->Monitor "<default monitor>"
[     9.237] (**) |   |-->Device "aticonfig-Device1"
[     9.237] (==) No monitor specified for screen "0-CRT1".
    Using a default monitor configuration.
[     9.237] (**) |-->Screen "VGA1" (2)
[     9.237] (**) |   |-->Monitor "<default monitor>"
[     9.237] (**) |   |-->Device "amdcccle-Device"
[     9.237] (==) No monitor specified for screen "VGA1".
    Using a default monitor configuration.
[     9.237] (==) Automatically adding devices
[     9.237] (==) Automatically enabling devices
[     9.237] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     9.237]     Entry deleted from font path.
[     9.237] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     9.237]     Entry deleted from font path.
[     9.237] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     9.237]     Entry deleted from font path.
[     9.237] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     9.237]     Entry deleted from font path.
[     9.237] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     9.237]     Entry deleted from font path.
[     9.237] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     9.237] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.237] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.237] (II) Loader magic: 0x7e0280
[     9.237] (II) Module ABI versions:
[     9.237]     X.Org ANSI C Emulation: 0.4
[     9.237]     X.Org Video Driver: 10.0
[     9.237]     X.Org XInput driver : 12.3
[     9.237]     X.Org Server Extension : 5.0
[     9.238] (--) PCI: (0:0:2:0) 8086:0112:1458:d000 rev 9, Mem @ 0xfb400000/4194304, 0xd0000000/268435456, I/O @ 0x0000ff00/64
[     9.238] (--) PCI:*(0:1:0:0) 1002:9460:1043:030c rev 0, Mem @ 0xe0000000/268435456, 0xfbae0000/65536, I/O @ 0x0000ce00/256, BIOS @ 0x????????/131072
[     9.238] (II) Open ACPI successful (/var/run/acpid.socket)
[     9.238] (II) "extmod" will be loaded by default.
[     9.238] (II) "dbe" will be loaded by default.
[     9.238] (II) "glx" will be loaded by default.
[     9.238] (II) "record" will be loaded by default.
[     9.238] (II) "dri" will be loaded by default.
[     9.238] (II) "dri2" will be loaded by default.
[     9.238] (II) LoadModule: "extmod"
[     9.259] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     9.259] (II) Module extmod: vendor="X.Org Foundation"
[     9.259]     compiled for 1.10.1, module version = 1.0.0
[     9.259]     Module class: X.Org Server Extension
[     9.259]     ABI class: X.Org Server Extension, version 5.0
[     9.259] (II) Loading extension MIT-SCREEN-SAVER
[     9.259] (II) Loading extension XFree86-VidModeExtension
[     9.259] (II) Loading extension XFree86-DGA
[     9.259] (II) Loading extension DPMS
[     9.259] (II) Loading extension XVideo
[     9.259] (II) Loading extension XVideo-MotionCompensation
[     9.259] (II) Loading extension X-Resource
[     9.259] (II) LoadModule: "dbe"
[     9.259] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     9.259] (II) Module dbe: vendor="X.Org Foundation"
[     9.259]     compiled for 1.10.1, module version = 1.0.0
[     9.259]     Module class: X.Org Server Extension
[     9.259]     ABI class: X.Org Server Extension, version 5.0
[     9.259] (II) Loading extension DOUBLE-BUFFER
[     9.259] (II) LoadModule: "glx"
[     9.259] (II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
[     9.259] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[     9.259]     compiled for 6.9.0, module version = 1.0.0
[     9.259] (II) Loading extension GLX
[     9.259] (II) LoadModule: "record"
[     9.259] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     9.259] (II) Module record: vendor="X.Org Foundation"
[     9.259]     compiled for 1.10.1, module version = 1.13.0
[     9.259]     Module class: X.Org Server Extension
[     9.259]     ABI class: X.Org Server Extension, version 5.0
[     9.259] (II) Loading extension RECORD
[     9.259] (II) LoadModule: "dri"
[     9.260] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     9.260] (II) Module dri: vendor="X.Org Foundation"
[     9.260]     compiled for 1.10.1, module version = 1.0.0
[     9.260]     ABI class: X.Org Server Extension, version 5.0
[     9.260] (II) Loading extension XFree86-DRI
[     9.260] (II) LoadModule: "dri2"
[     9.260] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     9.260] (II) Module dri2: vendor="X.Org Foundation"
[     9.260]     compiled for 1.10.1, module version = 1.2.0
[     9.260]     ABI class: X.Org Server Extension, version 5.0
[     9.260] (II) Loading extension DRI2
[     9.260] (II) LoadModule: "fglrx"
[     9.260] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.269] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[     9.269]     compiled for 1.4.99.906, module version = 8.86.5
[     9.269]     Module class: X.Org Video Driver
[     9.269] (II) Loading sub module "fglrxdrm"
[     9.269] (II) LoadModule: "fglrxdrm"
[     9.269] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.269] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.269]     compiled for 1.4.99.906, module version = 8.86.5
[     9.269] (II) ATI Proprietary Linux Driver Version Identifier:8.86.5
[     9.269] (II) ATI Proprietary Linux Driver Release Identifier: 8.861                                
[     9.269] (II) ATI Proprietary Linux Driver Build Date: May 24 2011 22:46:53
[     9.269] (++) using VT number 7

[     9.269] (WW) Falling back to old probe method for fglrx
[     9.274] (II) Loading PCS database from /etc/ati/amdpcsdb
[     9.274] (--) Chipset Supported AMD Graphics Processor (0x9460) found
[     9.274] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     9.275] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[     9.275] (II) AMD Video driver is signed
[     9.275] (II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
[     9.275] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.275] (II) fglrx(0): pEnt->device->identifier=0x1167500
[     9.275] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[     9.275] (II) Loading sub module "vgahw"
[     9.275] (II) LoadModule: "vgahw"
[     9.275] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[     9.275] (II) Module vgahw: vendor="X.Org Foundation"
[     9.275]     compiled for 1.10.1, module version = 0.1.0
[     9.275]     ABI class: X.Org Video Driver, version 10.0
[     9.275] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[     9.275] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[     9.275] (==) fglrx(0): Default visual is TrueColor
[     9.275] (**) fglrx(0): Option "UseFastTLS" "1"
[     9.275] (==) fglrx(0): RGB weight 888
[     9.275] (II) fglrx(0): Using 8 bits per RGB 
[     9.275] (==) fglrx(0): Buffer Tiling is ON
[     9.275] (II) Loading sub module "fglrxdrm"
[     9.275] (II) LoadModule: "fglrxdrm"
[     9.275] (II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
[     9.275] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[     9.275]     compiled for 1.4.99.906, module version = 8.86.5
[     9.390] ukiDynamicMajor: found major device number 250
[     9.390] ukiDynamicMajor: found major device number 250
[     9.390] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[     9.390] ukiOpenDevice: node name is /dev/ati/card0
[     9.390] ukiOpenDevice: open result is 11, (OK)
[     9.390] ukiOpenByBusid: ukiOpenMinor returns 11
[     9.390] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[     9.390] (==) fglrx(0): NoAccel = NO
[     9.390] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[     9.390] (--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series           " (Chipset = 0x9460)
[     9.390] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x030c)
[     9.390] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[     9.390] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[     9.390] (--) fglrx(0): MMIO registers at 0xfbae0000
[     9.390] (--) fglrx(0): I/O port at 0x0000ce00
[     9.390] (==) fglrx(0): ROM-BIOS at 0x000c0000
[     9.391] (II) fglrx(0): AC Adapter is used
[     9.392] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[     9.473] (II) Loading sub module "vbe"
[     9.473] (II) LoadModule: "vbe"
[     9.483] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     9.484] (II) Module vbe: vendor="X.Org Foundation"
[     9.484]     compiled for 1.10.1, module version = 1.1.0
[     9.484]     ABI class: X.Org Video Driver, version 10.0
[     9.484] (II) fglrx(0): VESA BIOS detected
[     9.484] (II) fglrx(0): VESA VBE Version 3.0
[     9.484] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[     9.484] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[     9.484] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[     9.484] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[     9.484] (II) fglrx(0): VESA VBE OEM Product: RV790
[     9.484] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[     9.509] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[     9.509] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[     9.509] (II) fglrx(0): PCIE card detected
[     9.509] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[     9.509] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     9.511] (II) fglrx(0): Using adapter: 1:0.0.
[     9.538] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[     9.559] (II) fglrx(0): Interrupt handler installed at IRQ 54.
[     9.560] (II) fglrx(0): RandR 1.2 support is enabled!
[     9.560] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[     9.560] (==) fglrx(0): Center Mode is disabled 
[     9.560] (II) Loading sub module "fb"
[     9.560] (II) LoadModule: "fb"
[     9.560] (II) Loading /usr/lib/xorg/modules/libfb.so
[     9.560] (II) Module fb: vendor="X.Org Foundation"
[     9.560]     compiled for 1.10.1, module version = 1.0.0
[     9.560]     ABI class: X.Org ANSI C Emulation, version 0.4
[     9.560] (II) Loading sub module "ddc"
[     9.560] (II) LoadModule: "ddc"
[     9.560] (II) Module "ddc" already built-in
[    10.992] (II) fglrx(0): Finished Initialize PPLIB!
[    10.994] (II) fglrx(0): Output DFP1 has no monitor section
[    10.994] (II) fglrx(0): Output DFP2 has no monitor section
[    10.995] (II) fglrx(0): Output CRT1 using monitor section 0-CRT1
[    10.995] (**) fglrx(0): Option "PreferredMode" "1920x1080"
[    10.995] (**) fglrx(0): Option "Position" "0 0"
[    10.995] (**) fglrx(0): Option "Disable" "false"
[    10.995] (**) fglrx(0): Option "Rotate" "normal"
[    10.995] (**) fglrx(0): Option "TargetRefresh" "60"
[    10.995] (II) fglrx(0): Output CRT2 has no monitor section
[    10.995] (II) fglrx(0): Output TV has no monitor section
[    10.995] (II) fglrx(0): Output CV has no monitor section
[    10.995] (II) Loading sub module "ddc"
[    10.995] (II) LoadModule: "ddc"
[    10.995] (II) Module "ddc" already built-in
[    10.995] (II) fglrx(0): Connected Display0: CRT1
[    10.995] (II) fglrx(0): Display0 EDID data ---------------------------
[    10.995] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    10.995] (II) fglrx(0): Year: 2009  Week: 46
[    10.995] (II) fglrx(0): EDID Version: 1.3
[    10.995] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    10.995] (II) fglrx(0): Sync:  Separate
[    10.995] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    10.995] (II) fglrx(0): Gamma: 2.20
[    10.995] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    10.995] (II) fglrx(0): First detailed timing is preferred mode
[    10.995] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    10.995] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    10.995] (II) fglrx(0): Supported established timings:
[    10.995] (II) fglrx(0): 720x400@70Hz
[    10.995] (II) fglrx(0): 640x480@60Hz
[    10.995] (II) fglrx(0): 640x480@67Hz
[    10.995] (II) fglrx(0): 640x480@72Hz
[    10.995] (II) fglrx(0): 640x480@75Hz
[    10.995] (II) fglrx(0): 800x600@56Hz
[    10.995] (II) fglrx(0): 800x600@60Hz
[    10.995] (II) fglrx(0): 800x600@72Hz
[    10.995] (II) fglrx(0): 800x600@75Hz
[    10.995] (II) fglrx(0): 832x624@75Hz
[    10.995] (II) fglrx(0): 1024x768@60Hz
[    10.995] (II) fglrx(0): 1024x768@70Hz
[    10.995] (II) fglrx(0): 1024x768@75Hz
[    10.995] (II) fglrx(0): 1280x1024@75Hz
[    10.995] (II) fglrx(0): 1152x864@75Hz
[    10.995] (II) fglrx(0): Manufacturer's mask: 0
[    10.995] (II) fglrx(0): Supported standard timings:
[    10.995] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    10.995] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    10.995] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    10.995] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    10.995] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    10.995] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    10.995] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    10.995] (II) fglrx(0): Supported detailed timing:
[    10.995] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    10.995] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    10.995] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    10.995] (II) fglrx(0): Serial No: 1105594601134
[    10.995] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    10.995] (II) fglrx(0): Monitor name: PLT2250MTS
[    10.995] (II) fglrx(0): EDID (in hex):
[    10.995] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    10.995] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    10.995] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    10.995] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    10.995] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    10.995] (II) fglrx(0):     35353934363031313334000000fd0037
[    10.995] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    10.995] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    10.995] (II) fglrx(0): End of Display0 EDID data --------------------
[    10.995] (II) fglrx(0): Connected Display1: CRT2
[    10.995] (II) fglrx(0): Display1 EDID data ---------------------------
[    10.995] (II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    10.995] (II) fglrx(0): Year: 2006  Week: 31
[    10.995] (II) fglrx(0): EDID Version: 1.3
[    10.995] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    10.995] (II) fglrx(0): Sync:  Separate
[    10.995] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    10.995] (II) fglrx(0): Gamma: 2.20
[    10.995] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    10.995] (II) fglrx(0): Default color space is primary color space
[    10.995] (II) fglrx(0): First detailed timing is preferred mode
[    10.995] (II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    10.995] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    10.995] (II) fglrx(0): Supported established timings:
[    10.995] (II) fglrx(0): 720x400@70Hz
[    10.995] (II) fglrx(0): 640x480@60Hz
[    10.995] (II) fglrx(0): 640x480@67Hz
[    10.995] (II) fglrx(0): 640x480@72Hz
[    10.995] (II) fglrx(0): 640x480@75Hz
[    10.995] (II) fglrx(0): 800x600@56Hz
[    10.995] (II) fglrx(0): 800x600@60Hz
[    10.995] (II) fglrx(0): 800x600@72Hz
[    10.995] (II) fglrx(0): 800x600@75Hz
[    10.995] (II) fglrx(0): 832x624@75Hz
[    10.995] (II) fglrx(0): 1024x768@60Hz
[    10.995] (II) fglrx(0): 1024x768@70Hz
[    10.995] (II) fglrx(0): 1024x768@75Hz
[    10.995] (II) fglrx(0): 1280x1024@75Hz
[    10.995] (II) fglrx(0): Manufacturer's mask: 0
[    10.995] (II) fglrx(0): Supported standard timings:
[    10.995] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    10.995] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    10.995] (II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    10.995] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    10.995] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    10.995] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    10.995] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    10.995] (II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    10.995] (II) fglrx(0): Supported detailed timing:
[    10.995] (II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    10.995] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    10.995] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    10.995] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    10.995] (II) fglrx(0): Monitor name: Acer AL2216W
[    10.995] (II) fglrx(0): Serial No: ETL7409045
[    10.995] (II) fglrx(0): EDID (in hex):
[    10.995] (II) fglrx(0):     00ffffffffffff00047274ad7f321063
[    10.995] (II) fglrx(0):     1f100103682f1e782ec585a459499a24
[    10.995] (II) fglrx(0):     125054bfef0081808140714f9500950f
[    10.995] (II) fglrx(0):     b30081c08bc021399030621a274068b0
[    10.995] (II) fglrx(0):     3600d9281100001c000000fd00384c1e
[    10.996] (II) fglrx(0):     5215000a202020202020000000fc0041
[    10.996] (II) fglrx(0):     63657220414c32323136570a000000ff
[    10.996] (II) fglrx(0):     0045544c3734303930343520202000c7
[    10.996] (II) fglrx(0): End of Display1 EDID data --------------------
[    11.133] (II) fglrx(0): EDID for output DFP1
[    11.133] (II) fglrx(0): EDID for output DFP2
[    11.133] (II) fglrx(0): EDID for output CRT1
[    11.133] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    11.133] (II) fglrx(0): Year: 2009  Week: 46
[    11.133] (II) fglrx(0): EDID Version: 1.3
[    11.133] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    11.133] (II) fglrx(0): Sync:  Separate
[    11.133] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    11.133] (II) fglrx(0): Gamma: 2.20
[    11.133] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    11.133] (II) fglrx(0): First detailed timing is preferred mode
[    11.133] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    11.133] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    11.133] (II) fglrx(0): Supported established timings:
[    11.133] (II) fglrx(0): 720x400@70Hz
[    11.133] (II) fglrx(0): 640x480@60Hz
[    11.133] (II) fglrx(0): 640x480@67Hz
[    11.133] (II) fglrx(0): 640x480@72Hz
[    11.133] (II) fglrx(0): 640x480@75Hz
[    11.133] (II) fglrx(0): 800x600@56Hz
[    11.133] (II) fglrx(0): 800x600@60Hz
[    11.133] (II) fglrx(0): 800x600@72Hz
[    11.133] (II) fglrx(0): 800x600@75Hz
[    11.133] (II) fglrx(0): 832x624@75Hz
[    11.133] (II) fglrx(0): 1024x768@60Hz
[    11.133] (II) fglrx(0): 1024x768@70Hz
[    11.133] (II) fglrx(0): 1024x768@75Hz
[    11.133] (II) fglrx(0): 1280x1024@75Hz
[    11.133] (II) fglrx(0): 1152x864@75Hz
[    11.133] (II) fglrx(0): Manufacturer's mask: 0
[    11.133] (II) fglrx(0): Supported standard timings:
[    11.133] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    11.133] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    11.133] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    11.133] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    11.134] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    11.134] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    11.134] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    11.134] (II) fglrx(0): Supported detailed timing:
[    11.134] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    11.134] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    11.134] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    11.134] (II) fglrx(0): Serial No: 1105594601134
[    11.134] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    11.134] (II) fglrx(0): Monitor name: PLT2250MTS
[    11.134] (II) fglrx(0): EDID (in hex):
[    11.134] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    11.134] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    11.134] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    11.134] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    11.134] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    11.134] (II) fglrx(0):     35353934363031313334000000fd0037
[    11.134] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    11.134] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    11.134] (II) fglrx(0): Printing probed modes for output CRT1
[    11.134] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    11.134] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 -hsync -vsync (75.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    11.134] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    11.134] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    11.134] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    11.134] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    11.134] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    11.134] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    11.134] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    11.134] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    11.134] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    11.134] (II) fglrx(0): EDID for output CRT2
[    11.134] (II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    11.134] (II) fglrx(0): Year: 2006  Week: 31
[    11.134] (II) fglrx(0): EDID Version: 1.3
[    11.134] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    11.134] (II) fglrx(0): Sync:  Separate
[    11.134] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    11.134] (II) fglrx(0): Gamma: 2.20
[    11.134] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    11.134] (II) fglrx(0): Default color space is primary color space
[    11.134] (II) fglrx(0): First detailed timing is preferred mode
[    11.134] (II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    11.134] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    11.134] (II) fglrx(0): Supported established timings:
[    11.134] (II) fglrx(0): 720x400@70Hz
[    11.134] (II) fglrx(0): 640x480@60Hz
[    11.134] (II) fglrx(0): 640x480@67Hz
[    11.134] (II) fglrx(0): 640x480@72Hz
[    11.134] (II) fglrx(0): 640x480@75Hz
[    11.134] (II) fglrx(0): 800x600@56Hz
[    11.134] (II) fglrx(0): 800x600@60Hz
[    11.134] (II) fglrx(0): 800x600@72Hz
[    11.134] (II) fglrx(0): 800x600@75Hz
[    11.134] (II) fglrx(0): 832x624@75Hz
[    11.134] (II) fglrx(0): 1024x768@60Hz
[    11.134] (II) fglrx(0): 1024x768@70Hz
[    11.134] (II) fglrx(0): 1024x768@75Hz
[    11.134] (II) fglrx(0): 1280x1024@75Hz
[    11.134] (II) fglrx(0): Manufacturer's mask: 0
[    11.134] (II) fglrx(0): Supported standard timings:
[    11.134] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    11.134] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    11.134] (II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    11.134] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    11.134] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    11.134] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    11.134] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    11.134] (II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    11.134] (II) fglrx(0): Supported detailed timing:
[    11.134] (II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    11.134] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    11.134] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    11.134] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    11.134] (II) fglrx(0): Monitor name: Acer AL2216W
[    11.134] (II) fglrx(0): Serial No: ETL7409045
[    11.134] (II) fglrx(0): EDID (in hex):
[    11.134] (II) fglrx(0):     00ffffffffffff00047274ad7f321063
[    11.134] (II) fglrx(0):     1f100103682f1e782ec585a459499a24
[    11.134] (II) fglrx(0):     125054bfef0081808140714f9500950f
[    11.134] (II) fglrx(0):     b30081c08bc021399030621a274068b0
[    11.134] (II) fglrx(0):     3600d9281100001c000000fd00384c1e
[    11.134] (II) fglrx(0):     5215000a202020202020000000fc0041
[    11.134] (II) fglrx(0):     63657220414c32323136570a000000ff
[    11.134] (II) fglrx(0):     0045544c3734303930343520202000c7
[    11.134] (II) fglrx(0): Printing probed modes for output CRT2
[    11.134] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    11.134] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    11.134] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    11.134] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    11.134] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    11.134] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    11.134] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    11.134] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    11.134] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    11.134] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    11.134] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    11.134] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    11.134] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    11.134] (II) fglrx(0): EDID for output TV
[    11.134] (II) fglrx(0): EDID for output CV
[    11.134] (II) fglrx(0): Output DFP1 disconnected
[    11.134] (II) fglrx(0): Output DFP2 disconnected
[    11.134] (II) fglrx(0): Output CRT1 connected
[    11.134] (II) fglrx(0): Output CRT2 connected
[    11.134] (II) fglrx(0): Output TV disconnected
[    11.134] (II) fglrx(0): Output CV disconnected
[    11.134] (II) fglrx(0): Using user preference for initial modes
[    11.134] (II) fglrx(0): Output CRT1 using initial mode 1920x1080
[    11.134] (II) fglrx(0): Output CRT2 using initial mode 1680x1050
[    11.134] (II) fglrx(0): DPI set to (96, 96)
[    11.134] (II) fglrx(0): Adapter ATI Radeon HD 4800 Series            has 2 configurable heads and 2 displays connected.
[    11.134] (==) fglrx(0):  PseudoColor visuals disabled
[    11.134] (II) Loading sub module "ramdac"
[    11.134] (II) LoadModule: "ramdac"
[    11.134] (II) Module "ramdac" already built-in
[    11.135] (==) fglrx(0): NoDRI = NO
[    11.135] (==) fglrx(0): Capabilities: 0x00000000
[    11.135] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    11.135] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    11.135] (**) fglrx(0): UseFastTLS=1
[    11.135] (==) fglrx(0): BlockSignalsOnLock=1
[    11.135] (--) Depth 24 pixmap format is 32 bpp
[    11.135] (II) Loading extension ATIFGLRXDRI
[    11.135] (II) fglrx(0): doing swlDriScreenInit
[    11.135] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    11.135] ukiDynamicMajor: found major device number 250
[    11.135] ukiDynamicMajor: found major device number 250
[    11.135] ukiDynamicMajor: found major device number 250
[    11.135] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    11.135] ukiOpenDevice: node name is /dev/ati/card0
[    11.135] ukiOpenDevice: open result is 16, (OK)
[    11.135] ukiOpenByBusid: ukiOpenMinor returns 16
[    11.135] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    11.135] (II) fglrx(0): [uki] DRM interface version 1.0
[    11.135] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    11.135] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    11.135] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7fc1a33bf000
[    11.135] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    11.135] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    11.135] (II) fglrx(0): swlDriScreenInit done
[    11.135] (II) fglrx(0): Kernel Module Version Information:
[    11.135] (II) fglrx(0):     Name: fglrx
[    11.135] (II) fglrx(0):     Version: 8.86.5
[    11.135] (II) fglrx(0):     Date: May 24 2011
[    11.135] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    11.135] (II) fglrx(0): Kernel Module version matches driver.
[    11.135] (II) fglrx(0): Kernel Module Build Time Information:
[    11.135] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-8-generic
[    11.135] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    11.135] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    11.135] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    11.135] (II) fglrx(0): [uki] register handle = 0x00004000
[    11.146] (II) fglrx(0): DRI initialization successfull
[    11.146] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01ab8000
[    11.146] (==) fglrx(0): Backing store disabled
[    11.146] (II) Loading extension FGLRXEXTENSION
[    11.146] (==) fglrx(0): DPMS enabled
[    11.147] (II) fglrx(0): Initialized in-driver Xinerama extension
[    11.147] (**) fglrx(0): Textured Video is enabled.
[    11.147] (II) LoadModule: "glesx"
[    11.147] (II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
[    11.147] (II) Module glesx: vendor="X.Org Foundation"
[    11.147]     compiled for 1.4.99.906, module version = 1.0.0
[    11.147] (II) Loading extension GLESX
[    11.147] (II) fglrx(0): GLESX enableFlags = 528
[    11.147] (II) fglrx(0): GLESX is enabled
[    11.147] (II) LoadModule: "amdxmm"
[    11.147] (II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
[    11.147] (II) Module amdxmm: vendor="X.Org Foundation"
[    11.147]     compiled for 1.4.99.906, module version = 2.0.0
[    11.147] (II) Loading extension AMDXVOPL
[    11.147] (II) Loading extension AMDXVBA
[    11.148] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    11.150] (II) fglrx(0): Enable composite support successfully
[    11.150] (II) fglrx(0): X context handle = 0x1
[    11.150] (II) fglrx(0): [DRI] installation complete
[    11.150] (==) fglrx(0): Silken mouse enabled
[    11.150] (==) fglrx(0): Using HW cursor of display infrastructure!
[    11.150] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    11.150] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    11.150] (II) fglrx(0): Cannot set TV horizontal size.
[    11.150] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    11.150] (II) fglrx(0): Cannot set TV horizontal position.
[    11.150] (II) fglrx(0): Cannot set TV vertical position.
[    11.253] (II) fglrx(0): User Preference Output CRT1 using refresh rate 60.0 Hz.
[    11.273] (--) RandR disabled
[    11.273] (II) Initializing built-in extension Generic Event Extension
[    11.273] (II) Initializing built-in extension SHAPE
[    11.273] (II) Initializing built-in extension MIT-SHM
[    11.273] (II) Initializing built-in extension XInputExtension
[    11.273] (II) Initializing built-in extension XTEST
[    11.273] (II) Initializing built-in extension BIG-REQUESTS
[    11.273] (II) Initializing built-in extension SYNC
[    11.273] (II) Initializing built-in extension XKEYBOARD
[    11.273] (II) Initializing built-in extension XC-MISC
[    11.273] (II) Initializing built-in extension SECURITY
[    11.273] (II) Initializing built-in extension XINERAMA
[    11.273] (II) Initializing built-in extension XFIXES
[    11.273] (II) Initializing built-in extension RENDER
[    11.273] (II) Initializing built-in extension RANDR
[    11.273] (II) Initializing built-in extension COMPOSITE
[    11.273] (II) Initializing built-in extension DAMAGE
[    11.273] (II) Initializing built-in extension GESTURE
[    11.274] ukiDynamicMajor: found major device number 250
[    11.274] ukiDynamicMajor: found major device number 250
[    11.274] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    11.274] ukiOpenDevice: node name is /dev/ati/card0
[    11.274] ukiOpenDevice: open result is 17, (OK)
[    11.274] ukiOpenByBusid: ukiOpenMinor returns 17
[    11.274] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    11.324] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    11.331] (II) fglrx(0): Enable the clock gating!
[    11.331] (II) fglrx(0): Setting screen physical size to 508 x 285
[    11.335] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    11.340] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    11.340] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.340] (II) LoadModule: "evdev"
[    11.340] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.341] (II) Module evdev: vendor="X.Org Foundation"
[    11.341]     compiled for 1.10.0.902, module version = 2.6.0
[    11.341]     Module class: X.Org XInput Driver
[    11.341]     ABI class: X.Org XInput driver, version 12.3
[    11.341] (II) Using input driver 'evdev' for 'Power Button'
[    11.341] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.341] (**) Power Button: always reports core events
[    11.341] (**) Power Button: Device: "/dev/input/event1"
[    11.390] (--) Power Button: Found keys
[    11.390] (II) Power Button: Configuring as keyboard
[    11.390] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    11.390] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    11.390] (**) Option "xkb_rules" "evdev"
[    11.390] (**) Option "xkb_model" "pc105"
[    11.390] (**) Option "xkb_layout" "gb"
[    11.391] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    11.392] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    11.392] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    11.392] (II) Using input driver 'evdev' for 'Power Button'
[    11.392] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.392] (**) Power Button: always reports core events
[    11.392] (**) Power Button: Device: "/dev/input/event0"
[    11.430] (--) Power Button: Found keys
[    11.430] (II) Power Button: Configuring as keyboard
[    11.430] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    11.430] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    11.430] (**) Option "xkb_rules" "evdev"
[    11.430] (**) Option "xkb_model" "pc105"
[    11.430] (**) Option "xkb_layout" "gb"
[    11.431] (II) config/udev: Adding input device Logitech Logitech Gaming Keyboard (/dev/input/event5)
[    11.431] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.431] (II) Using input driver 'evdev' for 'Logitech Logitech Gaming Keyboard'
[    11.431] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.431] (**) Logitech Logitech Gaming Keyboard: always reports core events
[    11.431] (**) Logitech Logitech Gaming Keyboard: Device: "/dev/input/event5"
[    11.470] (--) Logitech Logitech Gaming Keyboard: Found keys
[    11.470] (II) Logitech Logitech Gaming Keyboard: Configuring as keyboard
[    11.470] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input5/event5"
[    11.470] (II) XINPUT: Adding extended input device "Logitech Logitech Gaming Keyboard" (type: KEYBOARD)
[    11.470] (**) Option "xkb_rules" "evdev"
[    11.470] (**) Option "xkb_model" "pc105"
[    11.470] (**) Option "xkb_layout" "gb"
[    11.470] (II) config/udev: Adding input device Logitech Logitech Gaming Keyboard (/dev/input/event6)
[    11.470] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.470] (II) Using input driver 'evdev' for 'Logitech Logitech Gaming Keyboard'
[    11.470] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.470] (**) Logitech Logitech Gaming Keyboard: always reports core events
[    11.470] (**) Logitech Logitech Gaming Keyboard: Device: "/dev/input/event6"
[    11.530] (--) Logitech Logitech Gaming Keyboard: Found keys
[    11.530] (II) Logitech Logitech Gaming Keyboard: Configuring as keyboard
[    11.530] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1/input/input6/event6"
[    11.530] (II) XINPUT: Adding extended input device "Logitech Logitech Gaming Keyboard" (type: KEYBOARD)
[    11.530] (**) Option "xkb_rules" "evdev"
[    11.530] (**) Option "xkb_model" "pc105"
[    11.530] (**) Option "xkb_layout" "gb"
[    11.530] (II) config/udev: Adding input device G15 Keyboard G15 Keyboard (/dev/input/event7)
[    11.530] (**) G15 Keyboard G15 Keyboard: Applying InputClass "evdev keyboard catchall"
[    11.530] (II) Using input driver 'evdev' for 'G15 Keyboard G15 Keyboard'
[    11.530] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.530] (**) G15 Keyboard G15 Keyboard: always reports core events
[    11.530] (**) G15 Keyboard G15 Keyboard: Device: "/dev/input/event7"
[    11.550] (--) G15 Keyboard G15 Keyboard: Found keys
[    11.550] (II) G15 Keyboard G15 Keyboard: Configuring as keyboard
[    11.550] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.4/1-1.3.4:1.0/input/input7/event7"
[    11.550] (II) XINPUT: Adding extended input device "G15 Keyboard G15 Keyboard" (type: KEYBOARD)
[    11.550] (**) Option "xkb_rules" "evdev"
[    11.550] (**) Option "xkb_model" "pc105"
[    11.550] (**) Option "xkb_layout" "gb"
[    11.550] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[    11.550] (II) No input driver/identifier specified (ignoring)
[    11.552] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event2)
[    11.552] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    11.552] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    11.552] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.552] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    11.552] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event2"
[    11.560] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    11.560] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    11.560] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2/event2"
[    11.560] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    11.560] (**) Option "xkb_rules" "evdev"
[    11.560] (**) Option "xkb_model" "pc105"
[    11.560] (**) Option "xkb_layout" "gb"
[    11.560] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event3)
[    11.560] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev pointer catchall"
[    11.560] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    11.560] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    11.560] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.560] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    11.560] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event3"
[    11.560] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found 9 mouse buttons
[    11.560] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    11.560] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    11.560] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y relative axes
[    11.560] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    11.560] (II) evdev-grail: failed to open grail, no gesture support
[    11.560] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    11.560] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    11.560] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    11.560] (II) Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    11.560] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    11.560] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.560] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input3/event3"
[    11.560] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    11.560] (**) Option "xkb_rules" "evdev"
[    11.560] (**) Option "xkb_model" "pc105"
[    11.560] (**) Option "xkb_layout" "gb"
[    11.560] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for relative axes.
[    11.560] (WW) Microsoft Microsoft® Nano Transceiver v1.0: ignoring absolute axes.
[    11.561] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    11.561] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    11.561] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    11.561] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    11.561] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/mouse0)
[    11.561] (II) No input driver/identifier specified (ignoring)
[    11.561] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event4)
[    11.561] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    11.561] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    11.561] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.561] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    11.561] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event4"
[    11.610] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found 1 mouse buttons
[    11.610] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    11.610] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    11.610] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    11.610] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y absolute axes
[    11.610] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    11.610] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    11.610] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    11.610] (II) Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    11.610] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    11.610] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.610] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/input/input4/event4"
[    11.610] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    11.610] (**) Option "xkb_rules" "evdev"
[    11.610] (**) Option "xkb_model" "pc105"
[    11.610] (**) Option "xkb_layout" "gb"
[    11.610] (EE) Microsoft Microsoft® Nano Transceiver v1.0: failed to initialize for relative axes.
[    11.611] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    11.611] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    11.611] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for absolute axes.
[    11.611] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    11.611] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    11.611] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    11.611] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    11.611] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/js0)
[    11.611] (II) No input driver/identifier specified (ignoring)
[    11.612] (II) config/udev: Adding input device Quanta Computer Inc. Optical Touch Screen (/dev/input/event8)
[    11.612] (**) Quanta Computer Inc. Optical Touch Screen: Applying InputClass "evdev touchscreen catchall"
[    11.612] (II) Using input driver 'evdev' for 'Quanta Computer Inc. Optical Touch Screen'
[    11.612] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    11.612] (**) Quanta Computer Inc. Optical Touch Screen: always reports core events
[    11.612] (**) Quanta Computer Inc. Optical Touch Screen: Device: "/dev/input/event8"
[    11.670] (--) Quanta Computer Inc. Optical Touch Screen: Found absolute axes
[    11.670] (--) Quanta Computer Inc. Optical Touch Screen: Found x and y absolute axes
[    11.670] (--) Quanta Computer Inc. Optical Touch Screen: Found absolute touchscreen
[    11.670] (II) Quanta Computer Inc. Optical Touch Screen: Configuring as touchscreen
[    11.670] (**) Quanta Computer Inc. Optical Touch Screen: YAxisMapping: buttons 4 and 5
[    11.670] (**) Quanta Computer Inc. Optical Touch Screen: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    11.670] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3.2/2-1.3.2:1.0/input/input8/event8"
[    11.670] (II) XINPUT: Adding extended input device "Quanta Computer Inc. Optical Touch Screen" (type: TOUCHSCREEN)
[    11.670] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    11.670] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    11.670] (II) Quanta Computer Inc. Optical Touch Screen: initialized for absolute axes.
[    11.670] (**) Quanta Computer Inc. Optical Touch Screen: (accel) keeping acceleration scheme 1
[    11.670] (**) Quanta Computer Inc. Optical Touch Screen: (accel) acceleration profile 0
[    11.670] (**) Quanta Computer Inc. Optical Touch Screen: (accel) acceleration factor: 2.000
[    11.670] (**) Quanta Computer Inc. Optical Touch Screen: (accel) acceleration threshold: 4
[    11.670] (II) config/udev: Adding input device Quanta Computer Inc. Optical Touch Screen (/dev/input/mouse1)
[    11.670] (II) No input driver/identifier specified (ignoring)
[    11.706] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    12.565] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    12.565] (II) fglrx(0): Using EDID range info for horizontal sync
[    12.565] (II) fglrx(0): Using EDID range info for vertical refresh
[    12.565] (II) fglrx(0): Printing DDC gathered Modelines:
[    12.565] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    12.565] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    12.565] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    12.565] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    12.565] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    12.565] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    12.565] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    12.566] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    12.566] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    12.566] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    12.566] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    12.566] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    12.566] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    12.566] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    12.566] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    12.566] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    12.566] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    12.566] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    12.566] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    12.566] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    12.566] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    12.566] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    12.743] (WW) fglrx(0): Cannot get updated TV attributes.
[    13.368] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    13.368] (II) fglrx(0): Using hsync ranges from config file
[    13.368] (II) fglrx(0): Using vrefresh ranges from config file
[    13.368] (II) fglrx(0): Printing DDC gathered Modelines:
[    13.368] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    13.368] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    13.368] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    13.368] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    13.368] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    13.368] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    13.368] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    13.368] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    13.368] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    13.368] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    13.368] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    13.368] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    13.368] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    13.368] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    13.368] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    13.368] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    13.368] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    13.368] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    13.368] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    13.368] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    13.368] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    13.368] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    13.545] (WW) fglrx(0): Cannot get updated TV attributes.
[    14.173] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    14.173] (II) fglrx(0): Using hsync ranges from config file
[    14.173] (II) fglrx(0): Using vrefresh ranges from config file
[    14.173] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.173] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    14.173] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.173] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.173] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.173] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    14.173] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    14.173] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.173] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.173] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.173] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.174] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    14.174] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.174] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    14.174] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.174] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    14.174] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.174] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    14.174] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.174] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.174] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    14.174] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    14.174] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    14.353] (WW) fglrx(0): Cannot get updated TV attributes.
[    14.988] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    14.988] (II) fglrx(0): Using hsync ranges from config file
[    14.988] (II) fglrx(0): Using vrefresh ranges from config file
[    14.988] (II) fglrx(0): Printing DDC gathered Modelines:
[    14.988] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    14.988] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.988] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.988] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.988] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    14.988] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    14.988] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.989] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    14.989] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.989] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.989] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    14.989] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.989] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    14.989] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.989] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    14.989] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.989] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    14.989] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.989] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.989] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    14.989] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    14.989] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    15.168] (WW) fglrx(0): Cannot get updated TV attributes.
[    15.823] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    15.823] (II) fglrx(0): Using hsync ranges from config file
[    15.823] (II) fglrx(0): Using vrefresh ranges from config file
[    15.823] (II) fglrx(0): Printing DDC gathered Modelines:
[    15.823] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    15.823] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.823] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.823] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.823] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    15.823] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    15.823] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.823] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    15.823] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.823] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.823] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    15.823] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.823] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    15.823] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.823] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    15.823] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.823] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.823] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.823] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    15.823] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    15.823] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    15.823] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    16.033] (II) fglrx(0): xdl_xs110_atiddxDisplayScreenEnableDisplays
[    16.174] (WW) fglrx(0): Cannot get updated TV attributes.
[    16.318] (WW) fglrx(0): Cannot get updated TV attributes.
[    16.319] (WW) fglrx(0): Cannot get updated TV attributes.
[    16.448] (WW) fglrx(0): Cannot get updated TV attributes.
[    16.450] (WW) fglrx(0): Cannot get updated TV attributes.
[    20.801] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    21.584] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    21.584] (II) fglrx(0): Using hsync ranges from config file
[    21.584] (II) fglrx(0): Using vrefresh ranges from config file
[    21.584] (II) fglrx(0): Printing DDC gathered Modelines:
[    21.584] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    21.584] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.584] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    21.584] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.584] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    21.584] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    21.584] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.584] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    21.584] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    21.584] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.584] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    21.584] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.584] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    21.584] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.584] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    21.584] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    21.584] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    21.584] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    21.584] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    21.584] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    21.584] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    21.584] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    21.764] (WW) fglrx(0): Cannot get updated TV attributes.
[    22.407] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    22.407] (II) fglrx(0): Using hsync ranges from config file
[    22.407] (II) fglrx(0): Using vrefresh ranges from config file
[    22.407] (II) fglrx(0): Printing DDC gathered Modelines:
[    22.407] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    22.407] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    22.407] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    22.407] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    22.407] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    22.407] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    22.407] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    22.407] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    22.407] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    22.407] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    22.407] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    22.407] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    22.407] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    22.407] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    22.407] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    22.407] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    22.407] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    22.407] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    22.407] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    22.407] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    22.407] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    22.407] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    22.586] (WW) fglrx(0): Cannot get updated TV attributes.
[    23.221] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    23.221] (II) fglrx(0): Using hsync ranges from config file
[    23.221] (II) fglrx(0): Using vrefresh ranges from config file
[    23.221] (II) fglrx(0): Printing DDC gathered Modelines:
[    23.221] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    23.221] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.221] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.221] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.221] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    23.221] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    23.221] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.221] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.221] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    23.221] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.221] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    23.221] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.221] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.221] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.221] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    23.221] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.221] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.221] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.221] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    23.221] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    23.221] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    23.221] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    23.400] (WW) fglrx(0): Cannot get updated TV attributes.
[    24.057] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    24.057] (II) fglrx(0): Using hsync ranges from config file
[    24.057] (II) fglrx(0): Using vrefresh ranges from config file
[    24.057] (II) fglrx(0): Printing DDC gathered Modelines:
[    24.057] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    24.057] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    24.057] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    24.057] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    24.057] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    24.057] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    24.057] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    24.057] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    24.057] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    24.057] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    24.057] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    24.057] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    24.057] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    24.057] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    24.057] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    24.057] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    24.057] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    24.057] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    24.057] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    24.057] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    24.057] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    24.057] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    24.236] (II) fglrx(0): xdl_xs110_atiddxDisplayScreenEnableDisplays
[    24.236] (II) fglrx(0): User Preference Output CRT1 using refresh rate 60.0 Hz.
[    24.507] (WW) fglrx(0): Cannot get updated TV attributes.
[    25.699] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    25.699] (II) fglrx(0): Using hsync ranges from config file
[    25.699] (II) fglrx(0): Using vrefresh ranges from config file
[    25.699] (II) fglrx(0): Printing DDC gathered Modelines:
[    25.699] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.699] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.699] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.699] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.699] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.699] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.699] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.699] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.699] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.699] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.699] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.699] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.699] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.699] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.699] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.699] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.699] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    25.699] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.699] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.699] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    25.699] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    25.699] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    25.877] (WW) fglrx(0): Cannot get updated TV attributes.
[    25.879] (WW) fglrx(0): Cannot get updated TV attributes.
[    25.961] (WW) fglrx(0): Cannot get updated TV attributes.
[    32.262] (II) fglrx(0): EDID vendor "ACR", prod id 44404
[    32.262] (II) fglrx(0): Using hsync ranges from config file
[    32.262] (II) fglrx(0): Using vrefresh ranges from config file
[    32.262] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.262] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    32.262] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    32.262] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    32.262] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    32.262] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    32.262] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    32.262] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    32.262] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    32.262] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    32.262] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    32.262] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    32.262] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.262] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    32.262] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    32.262] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    32.262] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    32.262] (II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    32.262] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    32.262] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    32.262] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    32.262] (II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    32.262] (II) fglrx(0): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    32.444] (WW) fglrx(0): Cannot get updated TV attributes.

and finally

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0100] (rev 09)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port [8086:0101] (rev 09)
00:02.0 Display controller [0380]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0112] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev b5)
00:1c.4 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 [8086:1c18] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1c.6 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 7 [8086:1c1c] (rev b5)
00:1c.7 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 [8086:1c1e] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Z68 Express Chipset Family LPC Controller [8086:1c44] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c02] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV790 [Radeon HD 4890] [1002:9460]
01:00.1 Audio device [0403]: ATI Technologies Inc HD48x0 audio [1002:aa30]
02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
03:00.0 PCI bridge [0604]: Integrated Technology Express, Inc. Device [1283:8892] (rev 10)
05:00.0 USB Controller [0c03]: Device [1b6f:7023] (rev 01)
06:00.0 USB Controller [0c03]: Device [1b6f:7023] (rev 01)
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
08:00.0 SATA controller [0106]: Marvell Technology Group Ltd. Device [1b4b:9172] (rev 11)

I'm begining to lose the will to continue... I've invested a hugh amount of time. I'm been trying to move to Linux for over 10 yrs now... this is the closest I have ever got! 

As a last desparate attempt I might put back an old Ati card and disable the Intel built in video adapter.

I guess the  lesson is research a rig that you know will work.. the trouble is I'm migrating form windows to linux..I wonder if such a rig exists that is suitable for windows and Linux??

---

### Post by BicyclerBoy on 2011-07-19
Windows had dual video card (mixed brand) & multi-monitor working perfect on NT3.0.

The are many things in that xorg.conf file that could be wrong to know where to start.
Xorg does not even need that file in most cases.

The problems are caused by trying to get the intel driver & ATI driver to co-exist.
It has been done before.
I know very little about AMD/ATI drivers (with good reason) but ..
I'm not convinced that your ATI driver is new enough/matches your Xorg.
I would try Ubuntu 10.10 as 11.04 seems to be very problematic with video drivers.

Dump/disable the intel graphics & just use one brand of GPU. (SLI or crossfire if you need power)
With such a good CPU & chipset get a better graphics solution to match.

I would:
- get nVidia GT430 (video performance) or GTX560 for everything..
- Or find a video card with four outputs.
You will need the latest drivers from nVidia for the latest models tho. 
- Run Ubuntu 10.04 or 10.10 64 bit.

---

### Post by mick171 on 2011-07-19
Good advice. Right I've put back in old Ati card... now I can get all 3 screens to display. I have also disabled the on board video adapter.
This is what I have now:

aticonfig --list-adapters 
* 0. 01:00.0 ATI Radeon HD 4800 Series            
  1. 02:00.0 ATI Radeon HD 5670

I downloaded and installed the latest video drivers from AMD.

In the process I've lost Unity and I can't actually use the desktop of CRT2 and CRT3.
Mouse will go those screens but I can't say drag Firefox or anything else to them.

I have had a play and only ever get the screens to 1 video adapter to ever work at the same time.

Here is my latest xorg and log files. Progress at last. Thanks again for your support BicyclerBoy. 
What do I do now?

log 

[    13.804] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    13.804] X Protocol Version 11, Revision 0
[    13.804] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    13.804] Current Operating System: Linux ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:07:17 UTC 2011 x86_64
[    13.804] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-10-generic root=UUID=CC2420C52420B47C loop=/ubuntu/disks/root.disk ro quiet splash
[    13.804] Build Date: 21 May 2011  11:48:41AM
[    13.804] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    13.804] Current version of pixman: 0.20.2
[    13.804]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    13.804] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    13.804] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul 19 10:25:35 2011
[    13.804] (==) Using config file: "/etc/X11/xorg.conf"
[    13.804] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    13.804] (==) ServerLayout "aticonfig Layout"
[    13.804] (**) |-->Screen "0-CRT1" (0)
[    13.804] (**) |   |-->Monitor "<default monitor>"
[    13.804] (**) |   |-->Device "aticonfig-Device1"
[    13.804] (==) No monitor specified for screen "0-CRT1".
    Using a default monitor configuration.
[    13.804] (**) |-->Screen "0-CRT3" (1)
[    13.804] (**) |   |-->Monitor "<default monitor>"
[    13.804] (**) |   |-->Device "aticonfig-Device3"
[    13.804] (==) No monitor specified for screen "0-CRT3".
    Using a default monitor configuration.
[    13.804] (**) |-->Screen "0-CRT2" (2)
[    13.804] (**) |   |-->Monitor "<default monitor>"
[    13.804] (**) |   |-->Device "aticonfig-Device2"
[    13.804] (==) No monitor specified for screen "0-CRT2".
    Using a default monitor configuration.
[    13.804] (==) Automatically adding devices
[    13.804] (==) Automatically enabling devices
[    13.804] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    13.804]     Entry deleted from font path.
[    13.804] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    13.804]     Entry deleted from font path.
[    13.804] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    13.804]     Entry deleted from font path.
[    13.804] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    13.804]     Entry deleted from font path.
[    13.804] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    13.804]     Entry deleted from font path.
[    13.804] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    13.804] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    13.804] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    13.804] (II) Loader magic: 0x7e0280
[    13.804] (II) Module ABI versions:
[    13.804]     X.Org ANSI C Emulation: 0.4
[    13.804]     X.Org Video Driver: 10.0
[    13.804]     X.Org XInput driver : 12.3
[    13.804]     X.Org Server Extension : 5.0
[    13.805] (--) PCI:*(0:1:0:0) 1002:9460:1043:030c rev 0, Mem @ 0xd0000000/268435456, 0xfb9e0000/65536, I/O @ 0x0000ae00/256, BIOS @ 0x????????/131072
[    13.805] (--) PCI: (0:2:0:0) 1002:68d8:1787:2294 rev 0, Mem @ 0xe0000000/268435456, 0xfbac0000/131072, I/O @ 0x0000ee00/256, BIOS @ 0x????????/131072
[    13.805] (II) Open ACPI successful (/var/run/acpid.socket)
[    13.805] (II) "extmod" will be loaded by default.
[    13.805] (II) "dbe" will be loaded by default.
[    13.805] (II) "glx" will be loaded by default.
[    13.805] (II) "record" will be loaded by default.
[    13.805] (II) "dri" will be loaded by default.
[    13.805] (II) "dri2" will be loaded by default.
[    13.805] (II) LoadModule: "extmod"
[    13.805] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    13.806] (II) Module extmod: vendor="X.Org Foundation"
[    13.806]     compiled for 1.10.1, module version = 1.0.0
[    13.806]     Module class: X.Org Server Extension
[    13.806]     ABI class: X.Org Server Extension, version 5.0
[    13.806] (II) Loading extension MIT-SCREEN-SAVER
[    13.806] (II) Loading extension XFree86-VidModeExtension
[    13.806] (II) Loading extension XFree86-DGA
[    13.806] (II) Loading extension DPMS
[    13.806] (II) Loading extension XVideo
[    13.806] (II) Loading extension XVideo-MotionCompensation
[    13.806] (II) Loading extension X-Resource
[    13.806] (II) LoadModule: "dbe"
[    13.806] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    13.806] (II) Module dbe: vendor="X.Org Foundation"
[    13.806]     compiled for 1.10.1, module version = 1.0.0
[    13.806]     Module class: X.Org Server Extension
[    13.806]     ABI class: X.Org Server Extension, version 5.0
[    13.806] (II) Loading extension DOUBLE-BUFFER
[    13.806] (II) LoadModule: "glx"
[    13.806] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    13.806] (II) Module glx: vendor="FireGL - ATI Technologies Inc."
[    13.806]     compiled for 6.9.0, module version = 1.0.0
[    13.806] (II) Loading extension GLX
[    13.806] (II) LoadModule: "record"
[    13.807] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    13.807] (II) Module record: vendor="X.Org Foundation"
[    13.807]     compiled for 1.10.1, module version = 1.13.0
[    13.807]     Module class: X.Org Server Extension
[    13.807]     ABI class: X.Org Server Extension, version 5.0
[    13.807] (II) Loading extension RECORD
[    13.807] (II) LoadModule: "dri"
[    13.807] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    13.807] (II) Module dri: vendor="X.Org Foundation"
[    13.807]     compiled for 1.10.1, module version = 1.0.0
[    13.807]     ABI class: X.Org Server Extension, version 5.0
[    13.807] (II) Loading extension XFree86-DRI
[    13.807] (II) LoadModule: "dri2"
[    13.807] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    13.807] (II) Module dri2: vendor="X.Org Foundation"
[    13.807]     compiled for 1.10.1, module version = 1.2.0
[    13.807]     ABI class: X.Org Server Extension, version 5.0
[    13.807] (II) Loading extension DRI2
[    13.807] (II) LoadModule: "fglrx"
[    13.807] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    13.816] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    13.816]     compiled for 1.4.99.906, module version = 8.86.5
[    13.816]     Module class: X.Org Video Driver
[    13.816] (II) Loading sub module "fglrxdrm"
[    13.816] (II) LoadModule: "fglrxdrm"
[    13.816] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    13.816] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.816]     compiled for 1.4.99.906, module version = 8.86.5
[    13.816] (II) ATI Proprietary Linux Driver Version Identifier:8.86.5
[    13.816] (II) ATI Proprietary Linux Driver Release Identifier: 8.861                                
[    13.816] (II) ATI Proprietary Linux Driver Build Date: May 24 2011 22:46:53
[    13.816] (++) using VT number 7

[    13.817] (WW) Falling back to old probe method for fglrx
[    13.822] (II) Loading PCS database from /etc/ati/amdpcsdb
[    13.822] (--) Chipset Supported AMD Graphics Processor (0x9460) found
[    13.822] (--) Chipset Supported AMD Graphics Processor (0x68D8) found
[    13.822] (--) Chipset Supported AMD Graphics Processor (0x9460) found
[    13.822] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    13.822] (WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
[    13.823] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    13.823] (II) AMD Video driver is signed
[    13.823] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    13.823] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    13.823] (II) fglrx(0): pEnt->device->identifier=0x9df7a0
[    13.824] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    13.824] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    13.824] (II) fglrx(1): pEnt->device->identifier=0x9dff80
[    13.824] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    13.824] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    13.824] (II) fglrx(2): pEnt->device->identifier=0x9df7a0
[    13.824] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[    13.824] (II) Loading sub module "vgahw"
[    13.824] (II) LoadModule: "vgahw"
[    13.824] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    13.824] (II) Module vgahw: vendor="X.Org Foundation"
[    13.824]     compiled for 1.10.1, module version = 0.1.0
[    13.824]     ABI class: X.Org Video Driver, version 10.0
[    13.824] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    13.824] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    13.824] (==) fglrx(0): Default visual is TrueColor
[    13.824] (**) fglrx(0): Option "UseFastTLS" "1"
[    13.824] (==) fglrx(0): RGB weight 888
[    13.824] (II) fglrx(0): Using 8 bits per RGB 
[    13.824] (==) fglrx(0): Buffer Tiling is ON
[    13.824] (II) Loading sub module "fglrxdrm"
[    13.824] (II) LoadModule: "fglrxdrm"
[    13.824] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    13.824] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    13.824]     compiled for 1.4.99.906, module version = 8.86.5
[    13.825] ukiDynamicMajor: found major device number 250
[    13.825] ukiDynamicMajor: found major device number 250
[    13.825] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    13.825] ukiOpenDevice: node name is /dev/ati/card0
[    13.825] ukiOpenDevice: open result is 14, (OK)
[    13.825] ukiOpenByBusid: ukiOpenMinor returns 14
[    13.825] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    13.825] ukiOpenDevice: node name is /dev/ati/card1
[    13.825] ukiOpenDevice: open result is 14, (OK)
[    13.825] ukiOpenByBusid: ukiOpenMinor returns 14
[    13.825] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    13.825] (==) fglrx(0): NoAccel = NO
[    13.825] (==) fglrx(0): ATI 2D Acceleration Architecture enabled
[    13.826] (--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series           " (Chipset = 0x9460)
[    13.826] (--) fglrx(0): (PciSubVendor = 0x1043, PciSubDevice = 0x030c)
[    13.826] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
[    13.826] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[    13.826] (--) fglrx(0): MMIO registers at 0xfb9e0000
[    13.826] (--) fglrx(0): I/O port at 0x0000ae00
[    13.826] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    13.826] (II) fglrx(0): AC Adapter is used
[    13.828] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[    13.911] (II) Loading sub module "vbe"
[    13.911] (II) LoadModule: "vbe"
[    13.911] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    13.911] (II) Module vbe: vendor="X.Org Foundation"
[    13.911]     compiled for 1.10.1, module version = 1.1.0
[    13.911]     ABI class: X.Org Video Driver, version 10.0
[    13.911] (II) fglrx(0): VESA BIOS detected
[    13.912] (II) fglrx(0): VESA VBE Version 3.0
[    13.912] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[    13.912] (II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
[    13.912] (II) fglrx(0): VESA VBE OEM Software Rev: 11.22
[    13.912] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    13.912] (II) fglrx(0): VESA VBE OEM Product: RV790
[    13.912] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[    13.943] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    13.943] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[    13.943] (II) fglrx(0): PCIE card detected
[    13.943] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    13.943] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    13.945] (II) fglrx(0): Using adapter: 1:0.0.
[    13.971] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    13.992] (II) fglrx(0): Interrupt handler installed at IRQ 50.
[    13.992] (II) fglrx(0): RandR 1.2 support is enabled!
[    13.992] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    13.992] (==) fglrx(0): Center Mode is disabled 
[    13.992] (II) Loading sub module "fb"
[    13.992] (II) LoadModule: "fb"
[    13.992] (II) Loading /usr/lib/xorg/modules/libfb.so
[    13.992] (II) Module fb: vendor="X.Org Foundation"
[    13.992]     compiled for 1.10.1, module version = 1.0.0
[    13.992]     ABI class: X.Org ANSI C Emulation, version 0.4
[    13.992] (II) Loading sub module "ddc"
[    13.992] (II) LoadModule: "ddc"
[    13.992] (II) Module "ddc" already built-in
[    15.412] (II) fglrx(0): Finished Initialize PPLIB!
[    15.414] (II) fglrx(0): Output DFP1 has no monitor section
[    15.414] (II) fglrx(0): Output DFP2 has no monitor section
[    15.414] (II) fglrx(0): Output CRT1 using monitor section 0-CRT1
[    15.414] (**) fglrx(0): Option "PreferredMode" "1680x1050"
[    15.414] (**) fglrx(0): Option "Position" "0 0"
[    15.414] (**) fglrx(0): Option "Disable" "false"
[    15.414] (**) fglrx(0): Option "Rotate" "normal"
[    15.414] (**) fglrx(0): Option "TargetRefresh" "60"
[    15.414] (II) fglrx(0): Output CRT2 has no monitor section
[    15.414] (II) fglrx(0): Output TV has no monitor section
[    15.414] (II) fglrx(0): Output CV has no monitor section
[    15.414] (II) Loading sub module "ddc"
[    15.414] (II) LoadModule: "ddc"
[    15.414] (II) Module "ddc" already built-in
[    15.414] (II) fglrx(0): Connected Display0: CRT1
[    15.414] (II) fglrx(0): Display0 EDID data ---------------------------
[    15.414] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    15.414] (II) fglrx(0): Year: 2009  Week: 46
[    15.414] (II) fglrx(0): EDID Version: 1.3
[    15.414] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    15.414] (II) fglrx(0): Sync:  Separate
[    15.414] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    15.414] (II) fglrx(0): Gamma: 2.20
[    15.414] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    15.414] (II) fglrx(0): First detailed timing is preferred mode
[    15.414] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    15.414] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    15.414] (II) fglrx(0): Supported established timings:
[    15.414] (II) fglrx(0): 720x400@70Hz
[    15.414] (II) fglrx(0): 640x480@60Hz
[    15.414] (II) fglrx(0): 640x480@67Hz
[    15.414] (II) fglrx(0): 640x480@72Hz
[    15.414] (II) fglrx(0): 640x480@75Hz
[    15.414] (II) fglrx(0): 800x600@56Hz
[    15.414] (II) fglrx(0): 800x600@60Hz
[    15.414] (II) fglrx(0): 800x600@72Hz
[    15.414] (II) fglrx(0): 800x600@75Hz
[    15.414] (II) fglrx(0): 832x624@75Hz
[    15.414] (II) fglrx(0): 1024x768@60Hz
[    15.414] (II) fglrx(0): 1024x768@70Hz
[    15.414] (II) fglrx(0): 1024x768@75Hz
[    15.414] (II) fglrx(0): 1280x1024@75Hz
[    15.414] (II) fglrx(0): 1152x864@75Hz
[    15.414] (II) fglrx(0): Manufacturer's mask: 0
[    15.414] (II) fglrx(0): Supported standard timings:
[    15.414] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.414] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    15.414] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.414] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    15.414] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.414] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    15.414] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.414] (II) fglrx(0): Supported detailed timing:
[    15.414] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    15.414] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.414] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.414] (II) fglrx(0): Serial No: 1105594601134
[    15.414] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    15.414] (II) fglrx(0): Monitor name: PLT2250MTS
[    15.414] (II) fglrx(0): EDID (in hex):
[    15.414] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    15.414] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    15.414] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    15.414] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    15.414] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    15.414] (II) fglrx(0):     35353934363031313334000000fd0037
[    15.414] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    15.414] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    15.414] (II) fglrx(0): End of Display0 EDID data --------------------
[    15.414] (II) fglrx(0): Connected Display1: CRT2
[    15.414] (II) fglrx(0): Display1 EDID data ---------------------------
[    15.414] (II) fglrx(0): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    15.414] (II) fglrx(0): Year: 2006  Week: 31
[    15.414] (II) fglrx(0): EDID Version: 1.3
[    15.414] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    15.414] (II) fglrx(0): Sync:  Separate
[    15.414] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    15.414] (II) fglrx(0): Gamma: 2.20
[    15.414] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    15.414] (II) fglrx(0): Default color space is primary color space
[    15.414] (II) fglrx(0): First detailed timing is preferred mode
[    15.414] (II) fglrx(0): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    15.414] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    15.414] (II) fglrx(0): Supported established timings:
[    15.414] (II) fglrx(0): 720x400@70Hz
[    15.414] (II) fglrx(0): 640x480@60Hz
[    15.414] (II) fglrx(0): 640x480@67Hz
[    15.414] (II) fglrx(0): 640x480@72Hz
[    15.414] (II) fglrx(0): 640x480@75Hz
[    15.414] (II) fglrx(0): 800x600@56Hz
[    15.414] (II) fglrx(0): 800x600@60Hz
[    15.414] (II) fglrx(0): 800x600@72Hz
[    15.414] (II) fglrx(0): 800x600@75Hz
[    15.414] (II) fglrx(0): 832x624@75Hz
[    15.414] (II) fglrx(0): 1024x768@60Hz
[    15.414] (II) fglrx(0): 1024x768@70Hz
[    15.414] (II) fglrx(0): 1024x768@75Hz
[    15.414] (II) fglrx(0): 1280x1024@75Hz
[    15.414] (II) fglrx(0): Manufacturer's mask: 0
[    15.414] (II) fglrx(0): Supported standard timings:
[    15.414] (II) fglrx(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.414] (II) fglrx(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.414] (II) fglrx(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.414] (II) fglrx(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.414] (II) fglrx(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    15.414] (II) fglrx(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.414] (II) fglrx(0): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    15.414] (II) fglrx(0): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    15.414] (II) fglrx(0): Supported detailed timing:
[    15.414] (II) fglrx(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    15.414] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    15.414] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    15.415] (II) fglrx(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    15.415] (II) fglrx(0): Monitor name: Acer AL2216W
[    15.415] (II) fglrx(0): Serial No: ETL7409045
[    15.415] (II) fglrx(0): EDID (in hex):
[    15.415] (II) fglrx(0):     00ffffffffffff00047274ad7f321063
[    15.415] (II) fglrx(0):     1f100103682f1e782ec585a459499a24
[    15.415] (II) fglrx(0):     125054bfef0081808140714f9500950f
[    15.415] (II) fglrx(0):     b30081c08bc021399030621a274068b0
[    15.415] (II) fglrx(0):     3600d9281100001c000000fd00384c1e
[    15.415] (II) fglrx(0):     5215000a202020202020000000fc0041
[    15.415] (II) fglrx(0):     63657220414c32323136570a000000ff
[    15.415] (II) fglrx(0):     0045544c3734303930343520202000c7
[    15.415] (II) fglrx(0): End of Display1 EDID data --------------------
[    15.551] (II) fglrx(0): EDID for output DFP1
[    15.551] (II) fglrx(0): EDID for output DFP2
[    15.551] (II) fglrx(0): EDID for output CRT1
[    15.551] (II) fglrx(0): Manufacturer: IVM  Model: 5613  Serial#: 16843009
[    15.551] (II) fglrx(0): Year: 2009  Week: 46
[    15.551] (II) fglrx(0): EDID Version: 1.3
[    15.551] (II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    15.551] (II) fglrx(0): Sync:  Separate
[    15.551] (II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
[    15.551] (II) fglrx(0): Gamma: 2.20
[    15.551] (II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
[    15.551] (II) fglrx(0): First detailed timing is preferred mode
[    15.551] (II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[    15.551] (II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.312 whiteY: 0.329
[    15.551] (II) fglrx(0): Supported established timings:
[    15.551] (II) fglrx(0): 720x400@70Hz
[    15.551] (II) fglrx(0): 640x480@60Hz
[    15.551] (II) fglrx(0): 640x480@67Hz
[    15.551] (II) fglrx(0): 640x480@72Hz
[    15.551] (II) fglrx(0): 640x480@75Hz
[    15.551] (II) fglrx(0): 800x600@56Hz
[    15.551] (II) fglrx(0): 800x600@60Hz
[    15.551] (II) fglrx(0): 800x600@72Hz
[    15.551] (II) fglrx(0): 800x600@75Hz
[    15.551] (II) fglrx(0): 832x624@75Hz
[    15.551] (II) fglrx(0): 1024x768@60Hz
[    15.551] (II) fglrx(0): 1024x768@70Hz
[    15.551] (II) fglrx(0): 1024x768@75Hz
[    15.551] (II) fglrx(0): 1280x1024@75Hz
[    15.551] (II) fglrx(0): 1152x864@75Hz
[    15.551] (II) fglrx(0): Manufacturer's mask: 0
[    15.551] (II) fglrx(0): Supported standard timings:
[    15.551] (II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.551] (II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    15.551] (II) fglrx(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.551] (II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 75  vid: 36737
[    15.551] (II) fglrx(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.551] (II) fglrx(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    15.551] (II) fglrx(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.551] (II) fglrx(0): Supported detailed timing:
[    15.551] (II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
[    15.551] (II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    15.551] (II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    15.551] (II) fglrx(0): Serial No: 1105594601134
[    15.551] (II) fglrx(0): Ranges: V min: 55 V max: 76 Hz, H min: 29 H max: 83 kHz, PixClock max 175 MHz
[    15.551] (II) fglrx(0): Monitor name: PLT2250MTS
[    15.551] (II) fglrx(0): EDID (in hex):
[    15.551] (II) fglrx(0):     00ffffffffffff0026cd135601010101
[    15.551] (II) fglrx(0):     2e13010368301b782a3581a656489a24
[    15.551] (II) fglrx(0):     125054bfef80b300a9409500818f8180
[    15.551] (II) fglrx(0):     950f714f0101023a801871382d40582c
[    15.551] (II) fglrx(0):     4500dd0c1100001e000000ff00313130
[    15.551] (II) fglrx(0):     35353934363031313334000000fd0037
[    15.551] (II) fglrx(0):     4c1d5311000a202020202020000000fc
[    15.551] (II) fglrx(0):     00504c54323235304d54530a202000a8
[    15.551] (II) fglrx(0): Printing probed modes for output CRT1
[    15.551] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    15.551] (II) fglrx(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz)
[    15.551] (II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 -hsync -vsync (75.0 kHz)
[    15.551] (II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    15.551] (II) fglrx(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    15.551] (II) fglrx(0): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    15.551] (II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    15.551] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    15.551] (II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    15.551] (II) fglrx(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    15.551] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    15.551] (II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    15.551] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    15.551] (II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    15.551] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    15.551] (II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    15.551] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    15.551] (II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    15.551] (II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    15.551] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    15.551] (II) fglrx(0): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    15.551] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    15.551] (II) fglrx(0): EDID for output CRT2
[    15.551] (II) fglrx(0): EDID for output TV
[    15.551] (II) fglrx(0): EDID for output CV
[    15.551] (II) fglrx(0): Output DFP1 disconnected
[    15.551] (II) fglrx(0): Output DFP2 disconnected
[    15.551] (II) fglrx(0): Output CRT1 connected
[    15.551] (II) fglrx(0): Output CRT2 disconnected
[    15.551] (II) fglrx(0): Output TV disconnected
[    15.551] (II) fglrx(0): Output CV disconnected
[    15.551] (II) fglrx(0): Using user preference for initial modes
[    15.551] (II) fglrx(0): Output CRT1 using initial mode 1680x1050
[    15.551] (II) fglrx(0): DPI set to (96, 96)
[    15.551] (II) fglrx(0): Adapter ATI Radeon HD 4800 Series            has 2 configurable heads and 2 displays connected.
[    15.552] (==) fglrx(0):  PseudoColor visuals disabled
[    15.552] (II) Loading sub module "ramdac"
[    15.552] (II) LoadModule: "ramdac"
[    15.552] (II) Module "ramdac" already built-in
[    15.552] (==) fglrx(0): NoDRI = NO
[    15.552] (==) fglrx(0): Capabilities: 0x00000000
[    15.552] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    15.552] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    15.552] (**) fglrx(0): UseFastTLS=1
[    15.552] (==) fglrx(0): BlockSignalsOnLock=1
[    15.552] (II) fglrx(1): === [xdl_xs110_atiddxPreInit] === begin
[    15.552] (**) fglrx(1): Depth 24, (--) framebuffer bpp 32
[    15.552] (II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    15.552] (==) fglrx(1): Default visual is TrueColor
[    15.552] (==) fglrx(1): RGB weight 888
[    15.552] (II) fglrx(1): Using 8 bits per RGB 
[    15.552] (==) fglrx(1): Buffer Tiling is ON
[    15.552] (II) Loading sub module "fglrxdrm"
[    15.552] (II) LoadModule: "fglrxdrm"
[    15.552] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[    15.552] (II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
[    15.552]     compiled for 1.4.99.906, module version = 8.86.5
[    15.553] ukiDynamicMajor: found major device number 250
[    15.553] ukiDynamicMajor: found major device number 250
[    15.553] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    15.553] ukiOpenDevice: node name is /dev/ati/card0
[    15.553] ukiOpenDevice: open result is 19, (OK)
[    15.553] ukiOpenByBusid: ukiOpenMinor returns 19
[    15.553] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    15.553] (==) fglrx(1): NoAccel = NO
[    15.553] (==) fglrx(1): ATI 2D Acceleration Architecture enabled
[    15.553] (--) fglrx(1): Chipset: "ATI Radeon HD 5670" (Chipset = 0x68d8)
[    15.553] (--) fglrx(1): (PciSubVendor = 0x1787, PciSubDevice = 0x2294)
[    15.553] (==) fglrx(1): board vendor info: third party graphics adapter - NOT original ATI
[    15.553] (--) fglrx(1): Linear framebuffer (phys) at 0xe0000000
[    15.553] (--) fglrx(1): MMIO registers at 0xfbac0000
[    15.553] (--) fglrx(1): I/O port at 0x0000ee00
[    15.553] (==) fglrx(1): ROM-BIOS at 0x000c0000
[    15.553] (II) fglrx(0): AC Adapter is used
[    15.556] (II) fglrx(0): Invalid ATI BIOS from int10, the adapter is not VGA-enabled
[    15.804] (II) fglrx(0): ATI Video BIOS revision 9 or later detected
[    15.804] (--) fglrx(1): Video RAM: 524288 kByte, Type: GDDR5
[    15.804] (II) fglrx(1): PCIE card detected
[    15.804] (--) fglrx(1): Using per-process page tables (PPPT) as GART.
[    15.804] (WW) fglrx(1): board is an unknown third party board, chipset is supported
[    15.805] (II) fglrx(0): Using adapter: 2:0.0.
[    15.810] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x20000000)
[    15.831] (II) fglrx(0): Interrupt handler installed at IRQ 51.
[    15.831] (II) fglrx(1): RandR 1.2 support is enabled!
[    15.831] (II) fglrx(1): RandR 1.2 rotation support is enabled!
[    15.831] (==) fglrx(1): Center Mode is disabled 
[    15.831] (II) Loading sub module "fb"
[    15.831] (II) LoadModule: "fb"
[    15.831] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.831] (II) Module fb: vendor="X.Org Foundation"
[    15.831]     compiled for 1.10.1, module version = 1.0.0
[    15.831]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.831] (II) Loading sub module "ddc"
[    15.831] (II) LoadModule: "ddc"
[    15.831] (II) Module "ddc" already built-in
[    15.936] (WW) fglrx(0): Unable to register ADL handler for 0x00C00000
[    15.936] (II) fglrx(0): Finished Initialize PPLIB!
[    15.936] (II) fglrx(1): Output DFP1 has no monitor section
[    15.936] (II) fglrx(1): Output DFP2 has no monitor section
[    15.936] (II) fglrx(1): Output DFP3 has no monitor section
[    15.936] (II) fglrx(1): Output DFP4 has no monitor section
[    15.936] (II) fglrx(1): Output CRT1 has no monitor section
[    15.936] (II) fglrx(1): Output CRT2 has no monitor section
[    15.936] (II) Loading sub module "ddc"
[    15.936] (II) LoadModule: "ddc"
[    15.936] (II) Module "ddc" already built-in
[    15.936] (II) fglrx(1): Connected Display0: CRT2
[    15.936] (II) fglrx(1): Display0 EDID data ---------------------------
[    15.936] (II) fglrx(1): Manufacturer: ACI  Model: 22a5  Serial#: 109855
[    15.936] (II) fglrx(1): Year: 2008  Week: 39
[    15.936] (II) fglrx(1): EDID Version: 1.3
[    15.936] (II) fglrx(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    15.936] (II) fglrx(1): Sync:  Separate
[    15.936] (II) fglrx(1): Max Image Size [cm]: horiz.: 47  vert.: 30
[    15.936] (II) fglrx(1): Gamma: 2.20
[    15.936] (II) fglrx(1): DPMS capabilities: Off; RGB/Color Display
[    15.936] (II) fglrx(1): First detailed timing is preferred mode
[    15.936] (II) fglrx(1): redX: 0.644 redY: 0.332   greenX: 0.286 greenY: 0.601
[    15.936] (II) fglrx(1): blueX: 0.152 blueY: 0.076   whiteX: 0.312 whiteY: 0.328
[    15.936] (II) fglrx(1): Supported established timings:
[    15.936] (II) fglrx(1): 720x400@70Hz
[    15.936] (II) fglrx(1): 640x480@60Hz
[    15.936] (II) fglrx(1): 640x480@67Hz
[    15.936] (II) fglrx(1): 640x480@72Hz
[    15.936] (II) fglrx(1): 640x480@75Hz
[    15.936] (II) fglrx(1): 800x600@56Hz
[    15.936] (II) fglrx(1): 800x600@60Hz
[    15.936] (II) fglrx(1): 800x600@72Hz
[    15.936] (II) fglrx(1): 800x600@75Hz
[    15.936] (II) fglrx(1): 832x624@75Hz
[    15.936] (II) fglrx(1): 1024x768@60Hz
[    15.936] (II) fglrx(1): 1024x768@70Hz
[    15.936] (II) fglrx(1): 1024x768@75Hz
[    15.936] (II) fglrx(1): 1280x1024@75Hz
[    15.936] (II) fglrx(1): Manufacturer's mask: 0
[    15.936] (II) fglrx(1): Supported standard timings:
[    15.936] (II) fglrx(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.936] (II) fglrx(1): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.936] (II) fglrx(1): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.936] (II) fglrx(1): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.936] (II) fglrx(1): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.936] (II) fglrx(1): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.936] (II) fglrx(1): Supported detailed timing:
[    15.936] (II) fglrx(1): clock: 146.0 MHz   Image Size:  473 x 296 mm
[    15.936] (II) fglrx(1): h_active: 1680  h_sync: 1960  h_sync_end 2136 h_blank_end 2240 h_border: 0
[    15.936] (II) fglrx(1): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    15.936] (II) fglrx(1): Serial No: 89LMTF109855
[    15.936] (II) fglrx(1): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 85 kHz, PixClock max 165 MHz
[    15.936] (II) fglrx(1): Monitor name: ASUS VK222
[    15.936] (II) fglrx(1): EDID (in hex):
[    15.936] (II) fglrx(1):     00ffffffffffff000469a5221fad0100
[    15.936] (II) fglrx(1):     27120103682f1e782ac720a455499927
[    15.936] (II) fglrx(1):     135054bfef00714f814081809500b300
[    15.936] (II) fglrx(1):     81000101010108399030621a274018b0
[    15.936] (II) fglrx(1):     3640d9281100001c000000ff0038394c
[    15.936] (II) fglrx(1):     4d54463130393835350a000000fd0037
[    15.936] (II) fglrx(1):     4b1e5510000a202020202020000000fc
[    15.936] (II) fglrx(1):     004153555320564b3232320a202000f6
[    15.936] (II) fglrx(1): End of Display0 EDID data --------------------
[    15.946] (II) fglrx(1): EDID for output DFP1
[    15.946] (II) fglrx(1): EDID for output DFP2
[    15.946] (II) fglrx(1): EDID for output DFP3
[    15.946] (II) fglrx(1): EDID for output DFP4
[    15.946] (II) fglrx(1): EDID for output CRT1
[    15.946] (II) fglrx(1): EDID for output CRT2
[    15.946] (II) fglrx(1): Manufacturer: ACI  Model: 22a5  Serial#: 109855
[    15.946] (II) fglrx(1): Year: 2008  Week: 39
[    15.946] (II) fglrx(1): EDID Version: 1.3
[    15.946] (II) fglrx(1): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    15.946] (II) fglrx(1): Sync:  Separate
[    15.946] (II) fglrx(1): Max Image Size [cm]: horiz.: 47  vert.: 30
[    15.946] (II) fglrx(1): Gamma: 2.20
[    15.946] (II) fglrx(1): DPMS capabilities: Off; RGB/Color Display
[    15.946] (II) fglrx(1): First detailed timing is preferred mode
[    15.946] (II) fglrx(1): redX: 0.644 redY: 0.332   greenX: 0.286 greenY: 0.601
[    15.946] (II) fglrx(1): blueX: 0.152 blueY: 0.076   whiteX: 0.312 whiteY: 0.328
[    15.946] (II) fglrx(1): Supported established timings:
[    15.946] (II) fglrx(1): 720x400@70Hz
[    15.946] (II) fglrx(1): 640x480@60Hz
[    15.946] (II) fglrx(1): 640x480@67Hz
[    15.946] (II) fglrx(1): 640x480@72Hz
[    15.946] (II) fglrx(1): 640x480@75Hz
[    15.946] (II) fglrx(1): 800x600@56Hz
[    15.946] (II) fglrx(1): 800x600@60Hz
[    15.946] (II) fglrx(1): 800x600@72Hz
[    15.946] (II) fglrx(1): 800x600@75Hz
[    15.946] (II) fglrx(1): 832x624@75Hz
[    15.946] (II) fglrx(1): 1024x768@60Hz
[    15.946] (II) fglrx(1): 1024x768@70Hz
[    15.946] (II) fglrx(1): 1024x768@75Hz
[    15.946] (II) fglrx(1): 1280x1024@75Hz
[    15.946] (II) fglrx(1): Manufacturer's mask: 0
[    15.946] (II) fglrx(1): Supported standard timings:
[    15.946] (II) fglrx(1): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.946] (II) fglrx(1): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.947] (II) fglrx(1): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.947] (II) fglrx(1): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.947] (II) fglrx(1): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.947] (II) fglrx(1): #5: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    15.947] (II) fglrx(1): Supported detailed timing:
[    15.947] (II) fglrx(1): clock: 146.0 MHz   Image Size:  473 x 296 mm
[    15.947] (II) fglrx(1): h_active: 1680  h_sync: 1960  h_sync_end 2136 h_blank_end 2240 h_border: 0
[    15.947] (II) fglrx(1): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    15.947] (II) fglrx(1): Serial No: 89LMTF109855
[    15.947] (II) fglrx(1): Ranges: V min: 55 V max: 75 Hz, H min: 30 H max: 85 kHz, PixClock max 165 MHz
[    15.947] (II) fglrx(1): Monitor name: ASUS VK222
[    15.947] (II) fglrx(1): EDID (in hex):
[    15.947] (II) fglrx(1):     00ffffffffffff000469a5221fad0100
[    15.947] (II) fglrx(1):     27120103682f1e782ac720a455499927
[    15.947] (II) fglrx(1):     135054bfef00714f814081809500b300
[    15.947] (II) fglrx(1):     81000101010108399030621a274018b0
[    15.947] (II) fglrx(1):     3640d9281100001c000000ff0038394c
[    15.947] (II) fglrx(1):     4d54463130393835350a000000fd0037
[    15.947] (II) fglrx(1):     4b1e5510000a202020202020000000fc
[    15.947] (II) fglrx(1):     004153555320564b3232320a202000f6
[    15.947] (II) fglrx(1): Printing probed modes for output CRT2
[    15.947] (II) fglrx(1): Modeline "1680x1050"x60.0  146.00  1680 1960 2136 2240  1050 1053 1059 1089 -hsync +vsync (65.2 kHz)
[    15.947] (II) fglrx(1): Modeline "1400x1050"x60.0  146.00  1400 1960 2136 2240  1050 1053 1059 1089 -hsync +vsync (65.2 kHz)
[    15.947] (II) fglrx(1): Modeline "1600x900"x60.0  146.00  1600 1960 2136 2240  900 1053 1059 1089 -hsync +vsync (65.2 kHz)
[    15.947] (II) fglrx(1): Modeline "1360x1024"x60.0  146.00  1360 1960 2136 2240  1024 1053 1059 1089 -hsync +vsync (65.2 kHz)
[    15.947] (II) fglrx(1): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    15.947] (II) fglrx(1): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    15.947] (II) fglrx(1): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    15.947] (II) fglrx(1): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    15.947] (II) fglrx(1): Modeline "1280x800"x60.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    15.947] (II) fglrx(1): Modeline "1152x864"x60.0  146.00  1152 1960 2136 2240  864 1053 1059 1089 -hsync +vsync (65.2 kHz)
[    15.947] (II) fglrx(1): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    15.947] (II) fglrx(1): Modeline "1280x768"x60.0   83.50  1280 1352 1480 1680  768 803 809 831 -hsync +vsync (49.7 kHz)
[    15.947] (II) fglrx(1): Modeline "1280x720"x60.0   83.50  1280 1352 1480 1680  720 803 809 831 -hsync +vsync (49.7 kHz)
[    15.947] (II) fglrx(1): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    15.947] (II) fglrx(1): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    15.947] (II) fglrx(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    15.947] (II) fglrx(1): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    15.947] (II) fglrx(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    15.947] (II) fglrx(1): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    15.947] (II) fglrx(1): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    15.947] (II) fglrx(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    15.947] (II) fglrx(1): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 -hsync -vsync (37.9 kHz)
[    15.947] (II) fglrx(1): Modeline "640x480"x67.0   27.28  640 664 728 816  480 481 484 499 -hsync +vsync (33.4 kHz)
[    15.947] (II) fglrx(1): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    15.947] (II) fglrx(1): Output DFP1 disconnected
[    15.947] (II) fglrx(1): Output DFP2 disconnected
[    15.947] (II) fglrx(1): Output DFP3 disconnected
[    15.947] (II) fglrx(1): Output DFP4 disconnected
[    15.947] (II) fglrx(1): Output CRT1 disconnected
[    15.947] (II) fglrx(1): Output CRT2 connected
[    15.947] (II) fglrx(1): Using exact sizes for initial modes
[    15.947] (II) fglrx(1): Output CRT2 using initial mode 1680x1050
[    15.947] (II) fglrx(1): DPI set to (96, 96)
[    15.947] (WW) fglrx(0): Unable to register ADL handler for 0x00110000
[    15.947] (WW) fglrx(0): Unable to register ADL handler for 0x00120000
[    15.947] (WW) fglrx(0): Unable to register ADL handler for 0x00130000
[    15.947] (WW) fglrx(0): Unable to register ADL handler for 0x00150000
[    15.947] (II) fglrx(1): Eyefinity capable adapter detected.
[    15.947] (II) fglrx(1): Adapter ATI Radeon HD 5670 has 3 configurable heads and 1 displays connected.
[    15.947] (==) fglrx(1):  PseudoColor visuals disabled
[    15.947] (II) Loading sub module "ramdac"
[    15.947] (II) LoadModule: "ramdac"
[    15.947] (II) Module "ramdac" already built-in
[    15.947] (==) fglrx(1): NoDRI = NO
[    15.947] (==) fglrx(1): Capabilities: 0x00000000
[    15.947] (==) fglrx(1): CapabilitiesEx: 0x00000000
[    15.947] (==) fglrx(1): OpenGL ClientDriverName: "fglrx_dri.so"
[    15.947] (==) fglrx(1): UseFastTLS=0
[    15.947] (==) fglrx(1): BlockSignalsOnLock=1
[    15.947] (II) fglrx(2): === [xdl_xs110_atiddxPreInit] === begin
[    15.947] (II) Loading sub module "vgahw"
[    15.947] (II) LoadModule: "vgahw"
[    15.947] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    15.947] (II) Module vgahw: vendor="X.Org Foundation"
[    15.947]     compiled for 1.10.1, module version = 0.1.0
[    15.947]     ABI class: X.Org Video Driver, version 10.0
[    15.947] (**) fglrx(2): Depth 24, (--) framebuffer bpp 32
[    15.947] (II) fglrx(2): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    15.947] (==) fglrx(2): Default visual is TrueColor
[    15.947] (==) fglrx(2): RGB weight 888
[    15.947] (II) fglrx(2): Using 8 bits per RGB 
[    15.947] (==) fglrx(2): Buffer Tiling is ON (copy from primary)
[    15.947] (==) fglrx(2): NoAccel = NO (copy from primary screen)
[    15.947] (==) fglrx(2): ATI 2D Acceleration Architecture enabled
[    15.947] (II) Loading sub module "fb"
[    15.947] (II) LoadModule: "fb"
[    15.947] (II) Loading /usr/lib/xorg/modules/libfb.so
[    15.947] (II) Module fb: vendor="X.Org Foundation"
[    15.947]     compiled for 1.10.1, module version = 1.0.0
[    15.947]     ABI class: X.Org ANSI C Emulation, version 0.4
[    15.947] (II) Loading sub module "ddc"
[    15.947] (II) LoadModule: "ddc"
[    15.947] (II) Module "ddc" already built-in
[    15.947] (II) fglrx(2): Output DFP1 has no monitor section
[    15.947] (II) fglrx(2): Output DFP2 has no monitor section
[    15.947] (II) fglrx(2): Output CRT1 has no monitor section
[    15.947] (II) fglrx(2): Output CRT2 using monitor section 0-CRT2
[    15.947] (**) fglrx(2): Option "PreferredMode" "1680x1050"
[    15.947] (**) fglrx(2): Option "Position" "0 0"
[    15.947] (**) fglrx(2): Option "Disable" "false"
[    15.948] (**) fglrx(2): Option "Rotate" "normal"
[    15.948] (**) fglrx(2): Option "TargetRefresh" "60"
[    15.948] (II) fglrx(2): Output TV has no monitor section
[    15.948] (II) fglrx(2): Output CV has no monitor section
[    15.948] (II) fglrx(2): EDID for output DFP1
[    15.948] (II) fglrx(2): EDID for output DFP2
[    15.948] (II) fglrx(2): EDID for output CRT1
[    15.948] (II) fglrx(2): EDID for output CRT2
[    15.948] (II) fglrx(2): Manufacturer: ACR  Model: ad74  Serial#: 1662005887
[    15.948] (II) fglrx(2): Year: 2006  Week: 31
[    15.948] (II) fglrx(2): EDID Version: 1.3
[    15.948] (II) fglrx(2): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    15.948] (II) fglrx(2): Sync:  Separate
[    15.948] (II) fglrx(2): Max Image Size [cm]: horiz.: 47  vert.: 30
[    15.948] (II) fglrx(2): Gamma: 2.20
[    15.948] (II) fglrx(2): DPMS capabilities: Off; RGB/Color Display
[    15.948] (II) fglrx(2): Default color space is primary color space
[    15.948] (II) fglrx(2): First detailed timing is preferred mode
[    15.948] (II) fglrx(2): redX: 0.644 redY: 0.348   greenX: 0.286 greenY: 0.603
[    15.948] (II) fglrx(2): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[    15.948] (II) fglrx(2): Supported established timings:
[    15.948] (II) fglrx(2): 720x400@70Hz
[    15.948] (II) fglrx(2): 640x480@60Hz
[    15.948] (II) fglrx(2): 640x480@67Hz
[    15.948] (II) fglrx(2): 640x480@72Hz
[    15.948] (II) fglrx(2): 640x480@75Hz
[    15.948] (II) fglrx(2): 800x600@56Hz
[    15.948] (II) fglrx(2): 800x600@60Hz
[    15.948] (II) fglrx(2): 800x600@72Hz
[    15.948] (II) fglrx(2): 800x600@75Hz
[    15.948] (II) fglrx(2): 832x624@75Hz
[    15.948] (II) fglrx(2): 1024x768@60Hz
[    15.948] (II) fglrx(2): 1024x768@70Hz
[    15.948] (II) fglrx(2): 1024x768@75Hz
[    15.948] (II) fglrx(2): 1280x1024@75Hz
[    15.948] (II) fglrx(2): Manufacturer's mask: 0
[    15.948] (II) fglrx(2): Supported standard timings:
[    15.948] (II) fglrx(2): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    15.948] (II) fglrx(2): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    15.948] (II) fglrx(2): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    15.948] (II) fglrx(2): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    15.948] (II) fglrx(2): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    15.948] (II) fglrx(2): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    15.948] (II) fglrx(2): #6: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    15.948] (II) fglrx(2): #7: hsize: 1360  vsize 765  refresh: 60  vid: 49291
[    15.948] (II) fglrx(2): Supported detailed timing:
[    15.948] (II) fglrx(2): clock: 146.2 MHz   Image Size:  473 x 296 mm
[    15.948] (II) fglrx(2): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    15.948] (II) fglrx(2): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    15.948] (II) fglrx(2): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 82 kHz, PixClock max 215 MHz
[    15.948] (II) fglrx(2): Monitor name: Acer AL2216W
[    15.948] (II) fglrx(2): Serial No: ETL7409045
[    15.948] (II) fglrx(2): EDID (in hex):
[    15.948] (II) fglrx(2):     00ffffffffffff00047274ad7f321063
[    15.948] (II) fglrx(2):     1f100103682f1e782ec585a459499a24
[    15.948] (II) fglrx(2):     125054bfef0081808140714f9500950f
[    15.948] (II) fglrx(2):     b30081c08bc021399030621a274068b0
[    15.948] (II) fglrx(2):     3600d9281100001c000000fd00384c1e
[    15.948] (II) fglrx(2):     5215000a202020202020000000fc0041
[    15.948] (II) fglrx(2):     63657220414c32323136570a000000ff
[    15.948] (II) fglrx(2):     0045544c3734303930343520202000c7
[    15.948] (II) fglrx(2): Printing probed modes for output CRT2
[    15.948] (II) fglrx(2): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +hsync -vsync (65.3 kHz)
[    15.948] (II) fglrx(2): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync -vsync (65.3 kHz)
[    15.948] (II) fglrx(2): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 -hsync -vsync (60.0 kHz)
[    15.948] (II) fglrx(2): Modeline "1360x1024"x60.0  116.01  1360 1448 1592 1824  1024 1025 1028 1060 +hsync -vsync (63.6 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 -hsync -vsync (80.0 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 -hsync -vsync (64.0 kHz)
[    15.948] (II) fglrx(2): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +hsync -vsync (55.9 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x960"x75.0  129.86  1280 1368 1504 1728  960 961 964 1002 +hsync -vsync (75.2 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 -hsync -vsync (60.0 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x800"x75.0  107.21  1280 1360 1496 1712  800 801 804 835 +hsync -vsync (62.6 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 +hsync -vsync (49.7 kHz)
[    15.948] (II) fglrx(2): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 -hsync -vsync (67.5 kHz)
[    15.948] (II) fglrx(2): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync -vsync (53.7 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x768"x75.0  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    15.948] (II) fglrx(2): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 -hsync -vsync (45.0 kHz)
[    15.948] (II) fglrx(2): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 -hsync -vsync (60.0 kHz)
[    15.948] (II) fglrx(2): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
[    15.948] (II) fglrx(2): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
[    15.948] (II) fglrx(2): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 -hsync -vsync (48.1 kHz)
[    15.948] (II) fglrx(2): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 -hsync -vsync (46.9 kHz)
[    15.948] (II) fglrx(2): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync -vsync (43.8 kHz)
[    15.948] (II) fglrx(2): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 -hsync -vsync (37.9 kHz)
[    15.948] (II) fglrx(2): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 -hsync -vsync (35.2 kHz)
[    15.948] (II) fglrx(2): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync -vsync (29.8 kHz)
[    15.948] (II) fglrx(2): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
[    15.948] (II) fglrx(2): Modeline "640x480"x72.0   31.50  640 656 696 832  480 481 484 520 +hsync +vsync (37.9 kHz)
[    15.948] (II) fglrx(2): Modeline "640x480"x60.0   25.18  640 648 744 800  480 482 484 525 +hsync +vsync (31.5 kHz)
[    15.948] (II) fglrx(2): EDID for output TV
[    15.948] (II) fglrx(2): EDID for output CV
[    15.948] (II) fglrx(2): Output DFP1 disconnected
[    15.948] (II) fglrx(2): Output DFP2 disconnected
[    15.948] (II) fglrx(2): Output CRT1 disconnected
[    15.948] (II) fglrx(2): Output CRT2 connected
[    15.948] (II) fglrx(2): Output TV disconnected
[    15.948] (II) fglrx(2): Output CV disconnected
[    15.948] (II) fglrx(2): Using user preference for initial modes
[    15.948] (II) fglrx(2): Output CRT2 using initial mode 1680x1050
[    15.948] (II) fglrx(2): DPI set to (96, 96)
[    15.948] (WW) fglrx(0): Unable to register ADL handler for 0x00110000
[    15.948] (WW) fglrx(0): Unable to register ADL handler for 0x00120000
[    15.948] (WW) fglrx(0): Unable to register ADL handler for 0x00130000
[    15.948] (WW) fglrx(0): Unable to register ADL handler for 0x00150000
[    15.948] (II) fglrx(2): Adapter ATI Radeon HD 4800 Series            has 2 configurable heads and 2 displays connected.
[    15.948] (==) fglrx(2):  PseudoColor visuals disabled
[    15.948] (==) fglrx(2): bNoDRI = NO (copy from primary screen)
[    15.948] (==) fglrx(2): UseFastTLS=0
[    15.948] (==) fglrx(2): BlockSignalsOnLock=1
[    15.948] (--) Depth 24 pixmap format is 32 bpp
[    15.949] (II) Loading extension ATIFGLRXDRI
[    15.949] (II) fglrx(0): doing swlDriScreenInit
[    15.949] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    15.949] ukiDynamicMajor: found major device number 250
[    15.949] ukiDynamicMajor: found major device number 250
[    15.949] ukiDynamicMajor: found major device number 250
[    15.949] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    15.949] ukiOpenDevice: node name is /dev/ati/card0
[    15.949] ukiOpenDevice: open result is 20, (OK)
[    15.949] ukiOpenByBusid: ukiOpenMinor returns 20
[    15.949] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    15.949] ukiOpenDevice: node name is /dev/ati/card1
[    15.949] ukiOpenDevice: open result is 20, (OK)
[    15.949] ukiOpenByBusid: ukiOpenMinor returns 20
[    15.949] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    15.950] (II) fglrx(0): [uki] DRM interface version 1.0
[    15.950] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    15.950] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    15.950] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7fa8710e4000
[    15.950] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    15.950] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    15.950] (II) fglrx(0): swlDriScreenInit done
[    15.950] (II) fglrx(0): Kernel Module Version Information:
[    15.950] (II) fglrx(0):     Name: fglrx
[    15.950] (II) fglrx(0):     Version: 8.86.5
[    15.950] (II) fglrx(0):     Date: May 24 2011
[    15.950] (II) fglrx(0):     Desc: ATI FireGL DRM kernel module
[    15.950] (II) fglrx(0): Kernel Module version matches driver.
[    15.950] (II) fglrx(0): Kernel Module Build Time Information:
[    15.950] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.38-10-generic
[    15.950] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    15.950] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    15.950] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    15.950] (II) fglrx(0): [uki] register handle = 0x00004000
[    15.959] (II) fglrx(0): DRI initialization successfull
[    15.960] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01068000
[    15.960] (==) fglrx(0): Backing store disabled
[    15.960] (II) Loading extension FGLRXEXTENSION
[    15.960] (==) fglrx(0): DPMS enabled
[    15.960] (II) fglrx(0): Initialized in-driver Xinerama extension
[    15.960] (**) fglrx(0): Textured Video is enabled.
[    15.960] (II) LoadModule: "glesx"
[    15.960] (II) Loading /usr/lib/xorg/modules/glesx.so
[    15.960] (II) Module glesx: vendor="X.Org Foundation"
[    15.960]     compiled for 1.4.99.906, module version = 1.0.0
[    15.960] (II) Loading extension GLESX
[    15.960] (II) fglrx(0): GLESX enableFlags = 528
[    15.960] (II) fglrx(0): GLESX is enabled
[    15.960] (II) LoadModule: "amdxmm"
[    15.960] (II) Loading /usr/lib/xorg/modules/amdxmm.so
[    15.961] (II) Module amdxmm: vendor="X.Org Foundation"
[    15.961]     compiled for 1.4.99.906, module version = 2.0.0
[    15.961] (II) Loading extension AMDXVOPL
[    15.961] (II) Loading extension AMDXVBA
[    15.961] (II) fglrx(0): Enable composite support successfully
[    15.961] (II) fglrx(0): X context handle = 0x1
[    15.961] (II) fglrx(0): [DRI] installation complete
[    15.961] (==) fglrx(0): Silken mouse enabled
[    15.961] (==) fglrx(0): Using HW cursor of display infrastructure!
[    15.961] (II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    15.961] (II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
[    15.961] (II) fglrx(0): Cannot set TV horizontal size.
[    15.961] (II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    15.961] (II) fglrx(0): Cannot set TV horizontal position.
[    15.961] (II) fglrx(0): Cannot set TV vertical position.
[    15.996] (II) fglrx(0): User Preference Output CRT1 using refresh rate 60.0 Hz.
[    16.046] (--) RandR disabled
[    16.046] (II) fglrx(1): doing swlDriScreenInit
[    16.046] (II) fglrx(1): swlDriScreenInit for fglrx driver
[    16.046] ukiDynamicMajor: found major device number 250
[    16.046] ukiDynamicMajor: found major device number 250
[    16.046] ukiDynamicMajor: found major device number 250
[    16.046] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    16.046] ukiOpenDevice: node name is /dev/ati/card0
[    16.046] ukiOpenDevice: open result is 21, (OK)
[    16.046] ukiOpenByBusid: ukiOpenMinor returns 21
[    16.046] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    16.046] (II) fglrx(1): [uki] DRM interface version 1.0
[    16.046] (II) fglrx(1): [uki] created "fglrx" driver at busid "PCI:2:0:0"
[    16.046] (II) fglrx(1): [uki] added 8192 byte SAREA at 0xf000
[    16.046] (II) fglrx(1): [uki] mapped SAREA 0xf000 to 0x7fa8710c8000
[    16.046] (II) fglrx(1): [uki] framebuffer handle = 0x10000
[    16.046] (II) fglrx(1): [uki] added 1 reserved context for kernel
[    16.046] (II) fglrx(1): swlDriScreenInit done
[    16.046] (II) fglrx(1): Kernel Module Version Information:
[    16.046] (II) fglrx(1):     Name: fglrx
[    16.046] (II) fglrx(1):     Version: 8.86.5
[    16.046] (II) fglrx(1):     Date: May 24 2011
[    16.046] (II) fglrx(1):     Desc: ATI FireGL DRM kernel module
[    16.046] (II) fglrx(1): Kernel Module version matches driver.
[    16.047] (II) fglrx(1): Kernel Module Build Time Information:
[    16.047] (II) fglrx(1):     Build-Kernel UTS_RELEASE:        2.6.38-10-generic
[    16.047] (II) fglrx(1):     Build-Kernel MODVERSIONS:        yes
[    16.047] (II) fglrx(1):     Build-Kernel __SMP__:            yes
[    16.047] (II) fglrx(1):     Build-Kernel PAGE_SIZE:          0x1000
[    16.047] (II) fglrx(1): [uki] register handle = 0x00011000
[    16.056] (II) fglrx(1): DRI initialization successfull
[    16.056] (II) fglrx(1): FBADPhys: 0xf00000000 FBMappedSize: 0x01008000
[    16.056] (==) fglrx(1): Backing store disabled
[    16.056] (==) fglrx(1): DPMS enabled
[    16.057] (**) fglrx(1): Textured Video is enabled.
[    16.057] (II) fglrx(1): GLESX enableFlags = 592
[    16.057] (II) fglrx(1): GLESX is enabled
[    16.112] (II) Loading extension AMDXVOPL
[    16.112] (II) Loading extension AMDXVBA
[    16.112] (II) fglrx(1): Enable composite support successfully
[    16.112] (WW) fglrx(1): Option "Monitor-CRT3" is not used
[    16.112] (II) fglrx(1): X context handle = 0x1
[    16.112] (II) fglrx(1): [DRI] installation complete
[    16.112] (==) fglrx(1): Silken mouse enabled
[    16.112] (==) fglrx(1): Using HW cursor of display infrastructure!
[    16.112] (II) fglrx(1): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    16.171] (--) RandR disabled
[    16.171] (II) fglrx(2): doing swlDriScreenInit
[    16.171] (II) fglrx(2): swlDriScreenInit for fglrx driver
[    16.171] ukiDynamicMajor: found major device number 250
[    16.171] ukiDynamicMajor: found major device number 250
[    16.171] ukiDynamicMajor: found major device number 250
[    16.171] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    16.171] ukiOpenDevice: node name is /dev/ati/card0
[    16.171] ukiOpenDevice: open result is 22, (OK)
[    16.171] ukiOpenByBusid: ukiOpenMinor returns 22
[    16.171] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    16.171] ukiOpenDevice: node name is /dev/ati/card1
[    16.171] ukiOpenDevice: open result is 22, (OK)
[    16.171] ukiOpenByBusid: ukiOpenMinor returns 22
[    16.171] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    16.171] (II) fglrx(2): [uki] DRM interface version 1.0
[    16.171] (II) fglrx(2): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    16.171] (II) fglrx(2): [uki] added 8192 byte SAREA at 0x2000
[    16.171] (II) fglrx(2): [uki] mapped SAREA 0x2000 to 0x7fa868bd2000
[    16.171] (II) fglrx(2): [uki] framebuffer handle = 0x3000
[    16.171] (II) fglrx(2): [uki] added 1 reserved context for kernel
[    16.171] (II) fglrx(2): swlDriScreenInit done
[    16.173] (II) fglrx(2): DRI initialization successfull
[    16.173] (II) fglrx(2): FBADPhys: 0xf01084000 FBMappedSize: 0x00b64000
[    16.173] (==) fglrx(2): Backing store disabled
[    16.173] (==) fglrx(2): DPMS enabled
[    16.173] (**) fglrx(2): Textured Video is enabled.
[    16.173] (II) fglrx(2): GLESX enableFlags = 528
[    16.173] (II) fglrx(2): GLESX is enabled
[    16.992] (II) Loading extension AMDXVOPL
[    16.992] (II) Loading extension AMDXVBA
[    16.992] (II) fglrx(2): Enable composite support successfully
[    16.992] (WW) fglrx(2): Option "UseFastTLS" is not used
[    16.992] (II) fglrx(2): X context handle = 0x2
[    16.992] (II) fglrx(2): [DRI] installation complete
[    16.992] (==) fglrx(2): Silken mouse enabled
[    16.992] (==) fglrx(2): Using HW cursor of display infrastructure!
[    16.992] (II) fglrx(2): Disabling in-server RandR and enabling in-driver RandR 1.2.
[    16.992] (II) fglrx(2): Cannot get TV Format. Set all TV geometry value to zero!
[    16.992] (II) fglrx(2): Cannot set TV horizontal size.
[    16.992] (II) fglrx(2): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
[    16.992] (II) fglrx(2): Cannot set TV horizontal position.
[    16.992] (II) fglrx(2): Cannot set TV vertical position.
[    16.996] (II) fglrx(2): User Preference Output CRT2 using refresh rate 60.0 Hz.
[    17.016] (--) RandR disabled
[    17.016] (II) Initializing built-in extension Generic Event Extension
[    17.016] (II) Initializing built-in extension SHAPE
[    17.016] (II) Initializing built-in extension MIT-SHM
[    17.016] (II) Initializing built-in extension XInputExtension
[    17.016] (II) Initializing built-in extension XTEST
[    17.016] (II) Initializing built-in extension BIG-REQUESTS
[    17.016] (II) Initializing built-in extension SYNC
[    17.016] (II) Initializing built-in extension XKEYBOARD
[    17.016] (II) Initializing built-in extension XC-MISC
[    17.016] (II) Initializing built-in extension SECURITY
[    17.016] (II) Initializing built-in extension XINERAMA
[    17.016] (II) Initializing built-in extension XFIXES
[    17.016] (II) Initializing built-in extension RENDER
[    17.016] (II) Initializing built-in extension RANDR
[    17.016] (II) Initializing built-in extension COMPOSITE
[    17.016] (II) Initializing built-in extension DAMAGE
[    17.016] (II) Initializing built-in extension GESTURE
[    17.017] ukiDynamicMajor: found major device number 250
[    17.017] ukiDynamicMajor: found major device number 250
[    17.017] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    17.017] ukiOpenDevice: node name is /dev/ati/card0
[    17.017] ukiOpenDevice: open result is 23, (OK)
[    17.017] ukiOpenByBusid: ukiOpenMinor returns 23
[    17.017] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    17.017] ukiOpenDevice: node name is /dev/ati/card1
[    17.017] ukiOpenDevice: open result is 23, (OK)
[    17.017] ukiOpenByBusid: ukiOpenMinor returns 23
[    17.017] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    17.066] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    17.066] ukiDynamicMajor: found major device number 250
[    17.066] ukiDynamicMajor: found major device number 250
[    17.066] ukiOpenByBusid: Searching for BusID PCI:2:0:0
[    17.066] ukiOpenDevice: node name is /dev/ati/card0
[    17.066] ukiOpenDevice: open result is 26, (OK)
[    17.066] ukiOpenByBusid: ukiOpenMinor returns 26
[    17.066] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    17.086] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 1
[    17.086] ukiDynamicMajor: found major device number 250
[    17.086] ukiDynamicMajor: found major device number 250
[    17.086] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    17.086] ukiOpenDevice: node name is /dev/ati/card0
[    17.086] ukiOpenDevice: open result is 27, (OK)
[    17.086] ukiOpenByBusid: ukiOpenMinor returns 27
[    17.086] ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
[    17.086] ukiOpenDevice: node name is /dev/ati/card1
[    17.086] ukiOpenDevice: open result is 27, (OK)
[    17.086] ukiOpenByBusid: ukiOpenMinor returns 27
[    17.086] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    17.105] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 2
[    17.116] (II) fglrx(0): Enable the clock gating!
[    17.116] (II) fglrx(0): Setting screen physical size to 444 x 277
[    17.116] (II) fglrx(1): Enable the clock gating!
[    17.116] (II) fglrx(1): Setting screen physical size to 444 x 277
[    17.116] (II) fglrx(2): Setting screen physical size to 444 x 277
[    17.120] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.124] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.124] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.124] (II) LoadModule: "evdev"
[    17.124] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.125] (II) Module evdev: vendor="X.Org Foundation"
[    17.125]     compiled for 1.10.0.902, module version = 2.6.0
[    17.125]     Module class: X.Org XInput Driver
[    17.125]     ABI class: X.Org XInput driver, version 12.3
[    17.125] (II) Using input driver 'evdev' for 'Power Button'
[    17.125] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.125] (**) Power Button: always reports core events
[    17.125] (**) Power Button: Device: "/dev/input/event1"
[    17.130] (--) Power Button: Found keys
[    17.130] (II) Power Button: Configuring as keyboard
[    17.130] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    17.130] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.130] (**) Option "xkb_rules" "evdev"
[    17.130] (**) Option "xkb_model" "pc105"
[    17.130] (**) Option "xkb_layout" "gb"
[    17.131] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    17.132] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.132] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.132] (II) Using input driver 'evdev' for 'Power Button'
[    17.132] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.132] (**) Power Button: always reports core events
[    17.132] (**) Power Button: Device: "/dev/input/event0"
[    17.132] (--) Power Button: Found keys
[    17.132] (II) Power Button: Configuring as keyboard
[    17.132] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    17.132] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.132] (**) Option "xkb_rules" "evdev"
[    17.132] (**) Option "xkb_model" "pc105"
[    17.132] (**) Option "xkb_layout" "gb"
[    17.133] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event8)
[    17.133] (II) No input driver/identifier specified (ignoring)
[    17.135] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event2)
[    17.135] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    17.135] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    17.135] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.135] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    17.135] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event2"
[    17.140] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    17.140] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    17.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input2/event2"
[    17.140] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    17.140] (**) Option "xkb_rules" "evdev"
[    17.140] (**) Option "xkb_model" "pc105"
[    17.140] (**) Option "xkb_layout" "gb"
[    17.140] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event3)
[    17.140] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev pointer catchall"
[    17.140] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    17.140] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    17.140] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.140] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    17.140] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event3"
[    17.140] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found 9 mouse buttons
[    17.140] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    17.140] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    17.140] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y relative axes
[    17.140] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    17.140] (II) evdev-grail: failed to open grail, no gesture support
[    17.140] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    17.140] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    17.140] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    17.140] (II) Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    17.140] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    17.140] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.140] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.1/input/input3/event3"
[    17.140] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    17.140] (**) Option "xkb_rules" "evdev"
[    17.140] (**) Option "xkb_model" "pc105"
[    17.140] (**) Option "xkb_layout" "gb"
[    17.140] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for relative axes.
[    17.140] (WW) Microsoft Microsoft® Nano Transceiver v1.0: ignoring absolute axes.
[    17.140] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    17.141] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    17.141] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    17.141] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    17.141] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/mouse0)
[    17.141] (II) No input driver/identifier specified (ignoring)
[    17.141] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/event4)
[    17.141] (**) Microsoft Microsoft® Nano Transceiver v1.0: Applying InputClass "evdev keyboard catchall"
[    17.141] (II) Using input driver 'evdev' for 'Microsoft Microsoft® Nano Transceiver v1.0'
[    17.141] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.141] (**) Microsoft Microsoft® Nano Transceiver v1.0: always reports core events
[    17.141] (**) Microsoft Microsoft® Nano Transceiver v1.0: Device: "/dev/input/event4"
[    17.150] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found 1 mouse buttons
[    17.150] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found scroll wheel(s)
[    17.150] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found relative axes
[    17.150] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found absolute axes
[    17.150] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found x and y absolute axes
[    17.150] (--) Microsoft Microsoft® Nano Transceiver v1.0: Found keys
[    17.150] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as mouse
[    17.150] (II) Microsoft Microsoft® Nano Transceiver v1.0: Configuring as keyboard
[    17.150] (II) Microsoft Microsoft® Nano Transceiver v1.0: Adding scrollwheel support
[    17.150] (**) Microsoft Microsoft® Nano Transceiver v1.0: YAxisMapping: buttons 4 and 5
[    17.150] (**) Microsoft Microsoft® Nano Transceiver v1.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.150] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.2/input/input4/event4"
[    17.150] (II) XINPUT: Adding extended input device "Microsoft Microsoft® Nano Transceiver v1.0" (type: KEYBOARD)
[    17.150] (**) Option "xkb_rules" "evdev"
[    17.150] (**) Option "xkb_model" "pc105"
[    17.150] (**) Option "xkb_layout" "gb"
[    17.150] (EE) Microsoft Microsoft® Nano Transceiver v1.0: failed to initialize for relative axes.
[    17.151] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    17.151] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    17.151] (II) Microsoft Microsoft® Nano Transceiver v1.0: initialized for absolute axes.
[    17.151] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) keeping acceleration scheme 1
[    17.151] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration profile 0
[    17.151] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration factor: 2.000
[    17.151] (**) Microsoft Microsoft® Nano Transceiver v1.0: (accel) acceleration threshold: 4
[    17.151] (II) config/udev: Adding input device Microsoft Microsoft® Nano Transceiver v1.0 (/dev/input/js0)
[    17.151] (II) No input driver/identifier specified (ignoring)
[    17.152] (II) config/udev: Adding input device Logitech Logitech Gaming Keyboard (/dev/input/event5)
[    17.152] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    17.152] (II) Using input driver 'evdev' for 'Logitech Logitech Gaming Keyboard'
[    17.152] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.152] (**) Logitech Logitech Gaming Keyboard: always reports core events
[    17.152] (**) Logitech Logitech Gaming Keyboard: Device: "/dev/input/event5"
[    17.152] (--) Logitech Logitech Gaming Keyboard: Found keys
[    17.152] (II) Logitech Logitech Gaming Keyboard: Configuring as keyboard
[    17.152] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8.1/2-1.8.1:1.0/input/input5/event5"
[    17.152] (II) XINPUT: Adding extended input device "Logitech Logitech Gaming Keyboard" (type: KEYBOARD)
[    17.152] (**) Option "xkb_rules" "evdev"
[    17.152] (**) Option "xkb_model" "pc105"
[    17.152] (**) Option "xkb_layout" "gb"
[    17.152] (II) config/udev: Adding input device Logitech Logitech Gaming Keyboard (/dev/input/event6)
[    17.152] (**) Logitech Logitech Gaming Keyboard: Applying InputClass "evdev keyboard catchall"
[    17.152] (II) Using input driver 'evdev' for 'Logitech Logitech Gaming Keyboard'
[    17.152] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.152] (**) Logitech Logitech Gaming Keyboard: always reports core events
[    17.152] (**) Logitech Logitech Gaming Keyboard: Device: "/dev/input/event6"
[    17.160] (--) Logitech Logitech Gaming Keyboard: Found keys
[    17.160] (II) Logitech Logitech Gaming Keyboard: Configuring as keyboard
[    17.160] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8.1/2-1.8.1:1.1/input/input6/event6"
[    17.160] (II) XINPUT: Adding extended input device "Logitech Logitech Gaming Keyboard" (type: KEYBOARD)
[    17.160] (**) Option "xkb_rules" "evdev"
[    17.160] (**) Option "xkb_model" "pc105"
[    17.160] (**) Option "xkb_layout" "gb"
[    17.160] (II) config/udev: Adding input device G15 Keyboard G15 Keyboard (/dev/input/event7)
[    17.160] (**) G15 Keyboard G15 Keyboard: Applying InputClass "evdev keyboard catchall"
[    17.160] (II) Using input driver 'evdev' for 'G15 Keyboard G15 Keyboard'
[    17.160] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.160] (**) G15 Keyboard G15 Keyboard: always reports core events
[    17.160] (**) G15 Keyboard G15 Keyboard: Device: "/dev/input/event7"
[    17.160] (--) G15 Keyboard G15 Keyboard: Found keys
[    17.160] (II) G15 Keyboard G15 Keyboard: Configuring as keyboard
[    17.160] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.8/2-1.8.4/2-1.8.4:1.0/input/input7/event7"
[    17.160] (II) XINPUT: Adding extended input device "G15 Keyboard G15 Keyboard" (type: KEYBOARD)
[    17.160] (**) Option "xkb_rules" "evdev"
[    17.160] (**) Option "xkb_model" "pc105"
[    17.160] (**) Option "xkb_layout" "gb"
[    17.199] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    17.199] (II) fglrx(1): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    17.199] (II) fglrx(2): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    17.617] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    17.617] (II) fglrx(0): Using EDID range info for horizontal sync
[    17.617] (II) fglrx(0): Using EDID range info for vertical refresh
[    17.617] (II) fglrx(0): Printing DDC gathered Modelines:
[    17.617] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    17.617] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.617] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    17.617] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.617] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    17.617] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    17.617] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.617] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    17.617] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    17.617] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.617] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    17.617] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.617] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    17.617] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.617] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    17.617] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    17.617] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    17.617] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    17.617] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    17.617] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    17.617] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    17.790] (WW) fglrx(0): Cannot get updated TV attributes.
[    18.096] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    18.096] (II) fglrx(0): Using hsync ranges from config file
[    18.096] (II) fglrx(0): Using vrefresh ranges from config file
[    18.096] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.096] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    18.096] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.096] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.096] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.096] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.096] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.096] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.096] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.096] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.096] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.096] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.096] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.096] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.096] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.096] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.096] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.096] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.096] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.096] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.096] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.096] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    18.269] (WW) fglrx(0): Cannot get updated TV attributes.
[    18.574] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    18.574] (II) fglrx(0): Using hsync ranges from config file
[    18.574] (II) fglrx(0): Using vrefresh ranges from config file
[    18.574] (II) fglrx(0): Printing DDC gathered Modelines:
[    18.574] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    18.574] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.574] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    18.574] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.574] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    18.574] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    18.574] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.574] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    18.574] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    18.575] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.575] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    18.575] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.575] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    18.575] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.575] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    18.575] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    18.575] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    18.575] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    18.575] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    18.575] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    18.575] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    18.748] (WW) fglrx(0): Cannot get updated TV attributes.
[    19.057] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    19.057] (II) fglrx(0): Using hsync ranges from config file
[    19.057] (II) fglrx(0): Using vrefresh ranges from config file
[    19.057] (II) fglrx(0): Printing DDC gathered Modelines:
[    19.057] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    19.057] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    19.057] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    19.057] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    19.057] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    19.057] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    19.057] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    19.057] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    19.057] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    19.057] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    19.057] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    19.057] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    19.057] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    19.057] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    19.057] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    19.057] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    19.057] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    19.057] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    19.057] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    19.057] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    19.057] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    19.233] (WW) fglrx(0): Cannot get updated TV attributes.
[    24.922] Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
[    25.276] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    25.276] (II) fglrx(0): Using hsync ranges from config file
[    25.276] (II) fglrx(0): Using vrefresh ranges from config file
[    25.276] (II) fglrx(0): Printing DDC gathered Modelines:
[    25.276] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    25.276] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.276] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.276] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.276] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.276] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.276] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.276] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.276] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.276] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.276] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.276] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.276] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.276] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.276] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.276] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.276] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.276] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    25.276] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.276] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.276] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    25.452] (WW) fglrx(0): Cannot get updated TV attributes.
[    25.763] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    25.763] (II) fglrx(0): Using hsync ranges from config file
[    25.763] (II) fglrx(0): Using vrefresh ranges from config file
[    25.763] (II) fglrx(0): Printing DDC gathered Modelines:
[    25.763] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    25.763] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    25.763] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    25.763] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    25.763] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    25.763] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    25.763] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    25.763] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    25.763] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    25.763] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    25.763] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    25.763] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    25.763] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    25.763] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    25.763] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    25.763] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    25.763] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    25.763] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    25.763] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    25.763] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    25.763] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    25.939] (WW) fglrx(0): Cannot get updated TV attributes.
[    26.249] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    26.249] (II) fglrx(0): Using hsync ranges from config file
[    26.249] (II) fglrx(0): Using vrefresh ranges from config file
[    26.249] (II) fglrx(0): Printing DDC gathered Modelines:
[    26.249] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    26.249] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.249] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.249] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    26.249] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    26.249] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    26.249] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.249] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    26.249] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    26.249] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    26.249] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    26.249] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.249] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    26.249] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    26.249] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    26.249] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    26.249] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    26.249] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    26.249] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    26.249] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    26.249] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    26.425] (WW) fglrx(0): Cannot get updated TV attributes.
[    26.735] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    26.735] (II) fglrx(0): Using hsync ranges from config file
[    26.735] (II) fglrx(0): Using vrefresh ranges from config file
[    26.735] (II) fglrx(0): Printing DDC gathered Modelines:
[    26.735] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    26.735] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    26.735] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    26.735] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    26.735] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    26.735] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    26.735] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    26.735] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    26.735] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    26.735] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    26.735] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    26.735] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    26.735] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    26.735] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    26.735] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    26.735] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    26.735] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    26.735] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    26.735] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    26.735] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    26.735] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    26.911] (WW) fglrx(0): Cannot get updated TV attributes.
[    27.295] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    27.295] (II) fglrx(0): Using hsync ranges from config file
[    27.295] (II) fglrx(0): Using vrefresh ranges from config file
[    27.295] (II) fglrx(0): Printing DDC gathered Modelines:
[    27.295] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    27.295] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    27.295] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    27.295] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    27.295] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    27.295] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    27.295] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    27.295] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    27.295] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    27.295] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    27.295] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    27.295] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    27.295] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    27.295] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    27.295] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    27.295] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    27.295] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    27.295] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    27.295] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    27.295] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    27.295] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    32.593] (II) fglrx(0): EDID vendor "IVM", prod id 22035
[    32.593] (II) fglrx(0): Using hsync ranges from config file
[    32.593] (II) fglrx(0): Using vrefresh ranges from config file
[    32.593] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.593] (II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    32.593] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    32.593] (II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    32.593] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    32.593] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    32.593] (II) fglrx(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    32.593] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    32.593] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    32.593] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    32.593] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    32.593] (II) fglrx(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    32.593] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.593] (II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    32.593] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    32.593] (II) fglrx(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    32.593] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    32.593] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    32.593] (II) fglrx(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    32.593] (II) fglrx(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    32.593] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    32.593] (II) fglrx(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    32.770] (WW) fglrx(0): Cannot get updated TV attributes.
[    32.780] (II) fglrx(1): EDID vendor "ACI", prod id 8869
[    32.780] (II) fglrx(1): Using EDID range info for horizontal sync
[    32.780] (II) fglrx(1): Using EDID range info for vertical refresh
[    32.780] (II) fglrx(1): Printing DDC gathered Modelines:
[    32.780] (II) fglrx(1): Modeline "1680x1050"x0.0  146.00  1680 1960 2136 2240  1050 1053 1059 1089 -hsync +vsync (65.2 kHz)
[    32.780] (II) fglrx(1): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    32.780] (II) fglrx(1): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    32.780] (II) fglrx(1): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    32.780] (II) fglrx(1): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    32.780] (II) fglrx(1): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    32.780] (II) fglrx(1): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    32.780] (II) fglrx(1): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    32.780] (II) fglrx(1): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    32.780] (II) fglrx(1): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    32.780] (II) fglrx(1): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    32.780] (II) fglrx(1): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    32.780] (II) fglrx(1): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    32.780] (II) fglrx(1): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    32.780] (II) fglrx(1): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    32.780] (II) fglrx(1): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    32.780] (II) fglrx(1): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    32.780] (II) fglrx(1): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    32.781] (II) fglrx(1): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    32.781] (II) fglrx(1): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    32.781] (II) fglrx(1): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
[    33.091] (II) fglrx(2): EDID vendor "ACR", prod id 44404
[    33.091] (II) fglrx(2): Using EDID range info for horizontal sync
[    33.091] (II) fglrx(2): Using EDID range info for vertical refresh
[    33.091] (II) fglrx(2): Printing DDC gathered Modelines:
[    33.091] (II) fglrx(2): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    33.091] (II) fglrx(2): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    33.091] (II) fglrx(2): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    33.091] (II) fglrx(2): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    33.091] (II) fglrx(2): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    33.091] (II) fglrx(2): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    33.091] (II) fglrx(2): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    33.091] (II) fglrx(2): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    33.091] (II) fglrx(2): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    33.091] (II) fglrx(2): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    33.091] (II) fglrx(2): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    33.091] (II) fglrx(2): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    33.091] (II) fglrx(2): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    33.091] (II) fglrx(2): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    33.091] (II) fglrx(2): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    33.091] (II) fglrx(2): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    33.091] (II) fglrx(2): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    33.091] (II) fglrx(2): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    33.091] (II) fglrx(2): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    33.091] (II) fglrx(2): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    33.091] (II) fglrx(2): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    33.091] (II) fglrx(2): Modeline "1366x768"x59.8   84.75  1366 1431 1567 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    33.279] (WW) fglrx(2): Cannot get updated TV attributes.

and my xorg.conf

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen     0  "0-CRT1"
    Screen        "0-CRT3" LeftOf "0-CRT1"
    Screen        "0-CRT2" RightOf "0-CRT1"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT3"
    Option        "CRT3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device1"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
    Screen      0
EndSection

Section "Device"
    Identifier  "aticonfig-Device2"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "aticonfig-Device3"
    Driver      "fglrx"
    Option        "Monitor-CRT3" "0-CRT3"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "0-CRT1"
    Device     "aticonfig-Device1"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "0-CRT2"
    Device     "aticonfig-Device2"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "0-CRT3"
    Device     "aticonfig-Device3"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

---

### Post by mick171 on 2011-07-19
Whoops... Unity was working.. gone back to pre Unity desktop now.

---

### Post by BicyclerBoy on 2011-07-19
Does the catalyst control centre tool let you manage/massage the desktops into one big desktop ?
Else the (3) screens will be separate X screens (I think) so no dragging or icons.
Note that Xinerama does not work very well/obsolete & does not work with composite (desktop effects).

Can launch apps to any separate X screen with small script to set the DISPLAY:= variable..
DISPLAY:=0.1 firefox
or maybe
DISPLAY:=0.1 ; firefox

where 0.0 is primary, 0.1 is 2nd & 0.2 is 3rd screen

---

### Post by mick171 on 2011-07-20
Ok I can start up any app in each of the 3 monitors but I can only type into one of them. I can't drag windows around either between monitors and the mouse on one screen is currupted and the system has become unstable.

The catalyst control centre seems to see all 3 monitors but it's not helping fix any of my issues no matter how I set it.

Like you said 3 monitors is no big deal in windows. On my win 7 they work great.

Ok so I now abandon Ubuntu 11.04. sigh... learnt a lot though

Going to take another of your alternative actions and try using 10.04 LTS 64 bit.

Lets see how that goes before I consider buying a new video card. 

Would it be true to say , as you are recommending 10.04 that 11.04 is like Vista was in windows.. a bit of a no no?

---

### Post by mick171 on 2011-07-20
Well miracles do happen and I now have 3 full working screens and I can drag windows across from one monitor to another.

here's the working xorg.conf. Maybe it can help someone else. :)

The option Option "Xinerama" "on" eneabled the dragging of windows from monitor to monitor.

Now to get usb 3 working .. sigh

A big thank you to all. The forum was great. In almost every case someone had already been there seen it, got the T shirt etc and more often than not had a solution.

```

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen     0  "0-CRT1"
    Screen        "0-CRT3" LeftOf "0-CRT1"
    Screen        "0-CRT2" RightOf "0-CRT1"
    Option "Xinerama" "on"
    Option "Clone" "off"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT2"
    Option        "CRT2"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-CRT3"
    Option        "CRT3"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1680x1050"
    Option        "TargetRefresh" "60"
    Option        "Position" "1920 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "aticonfig-Device1"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
    Screen      0
EndSection

Section "Device"
    Identifier  "aticonfig-Device2"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    Option        "Monitor-CRT2" "0-CRT2"
    BusID       "PCI:1:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "aticonfig-Device3"
    Driver      "fglrx"
    Option        "Monitor-CRT3" "0-CRT3"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "0-CRT1"
    Device     "aticonfig-Device1"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "0-CRT2"
    Device     "aticonfig-Device2"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "0-CRT3"
    Device     "aticonfig-Device3"
    DefaultDepth     24
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

```

```

---

