---
title: "FINALLY!!! How I got fglrx/edgy from Ubuntu repos WITH DRI WORKING!"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by hurrrtin on 2006-10-09
After COUNTLESS guides and experiments, reinstalls, and headaches, here is
what I did to get the fglrx drivers from ATI to work with acceleration with
DRI. Seems I could always get fglrx driver, but it would always show MesaGL
instead of ATI OpenGL 2.x. But I fresh installed edgy, and did the following:

! If you have custom-built your own ATI debs using the actual ATI installer,
you should remove them first. You should be able to find them in Synaptic
under the 'Local or Obsolete' category. Right click the packages and select
"MARK FOR COMPLETE REMOVAL" before applying.

! If you have blacklisted the fglrx module from the linux-restricted-modules
you need to remove it from the blacklist:

```
$ sudo gedit /etc/default/linux-restricted-modules-common
```

Remove fglrx from the blacklisted modules.

* First, lets remove the packages relating to fglrx, so we can be sure we do
this correctly. In a terminal:

```
$ sudo apt-get --purge remove xorg-driver-fglrx linux-restricted-modules-386 linux-restricted-modules-generic
```

* Now, reboot, but DON'T log in. (You could boot into the single user mode
for your kernel as well.) When you get to login menu, press CONTROL+ALT+F1 to
go to terminal and login to it. Then type:

```
$ sudo /etc/init.d/gdm stop

```
* Now, reinstall the restricted-modules for your kernel. (If you don't need
both kernels, remove the one you don't need. I am including both for safety.)

```
$ sudo apt-get install linux-restricted-modules-386 linux-restricted-modules-generic

```
* Now, install fglrx driver.

```
$ sudo apt-get install xorg-driver-fglrx
```

* HERE is the meat of the problem. We need to do 2 things now. First, lets
tell the kernel to load the module at startup:
```

$ sudo echo "fglrx" >> /etc/modules
```

* We also need to make a symbolic link to the DRI modules so modular Xorg can
get to them.

```
$ sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

* Make sure you have fglrx selected as the module to use for Xorg:
```

$ sudo aticonfig --initial
```

* Now, if you have a bunch of xorg.conf backup files in your /etc/X11 folder,
you can either remove them or leave them. But I don't like messy stuffs in
there when they never even worked in the first place, so, ignore this part if
you want to, OR to clean it up, do:
```

$ sudo rm /etc/X11/xorg.conf?*
```

* Finally, reboot. See if it worked. I hope this helps any of you get this
solved. It seems to me, that my problem was that modular xorg never could
find the DRI modules, and the fglrx module wouldn't really load correctly
until I told the kernel to boot it at startup. You can check if it worked
using any of these after you log in:

```
$ sudo cat /var/log/Xorg.0.log | grep fglrx
```
```

$ sudo cat /var/log/Xorg.0.log | grep fglrx | grep -i DRI
```
```

$ glxinfo | grep GL
```

```
$ fglrxinfo
```

Now that this is solved for me, next stop: XGL... ](*,)

---

### Post by igknighted on 2006-10-09
i followed this and when i got to the "aticonfig --initial line" it told me there was nothing to do, so I rebooted into X and it was a no-go.  NOTE: I tried this on Kubuntu, swapping gdm for kdm... are there any other tricks that are needed on KDE?

---

### Post by jdong on 2006-10-09
weird... All I had to do to get fglrx working on Edgy was to install xorg-driver-fglrx and add Option Composite 0 to xorg.conf..... :)


And Xgl does work too... the only thing that doesn't really work is xvideo.

---

### Post by ilbozo on 2006-10-09
Ehi nice work! It worked for me too!
Only a newbie question:
I found with grep this line

```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
```

what does it mean?

---

### Post by mvarga on 2006-10-09
Thank you,

this worked for me. However, I hadn't stop the gdm or whatsoever, just made the symlink of /usr/lib/dri, and put the "fgrlx" line in /etc/modules. And reboot, of course.

---

### Post by hurrrtin on 2006-10-09
> **ilbozo said:**
> Ehi nice work! It worked for me too!
Only a newbie question:
I found with grep this line

```
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
```

what does it mean?

I get that error as well. I think it is related to this particular version of the driver not being compatible with AIGLX, which AFAIK is being included with edgy by default. It doesn't seem to create any problems for me, but I havent tried XGL yet either.

---

### Post by hurrrtin on 2006-10-09
> **igknighted said:**
> i followed this and when i got to the "aticonfig --initial line" it told me there was nothing to do, so I rebooted into X and it was a no-go.  NOTE: I tried this on Kubuntu, swapping gdm for kdm... are there any other tricks that are needed on KDE?

I don't really use kde much, but unless the xorg used in kubuntu is a completely different version than the ones in (x)ubuntu, this should work. Post a reply with the results of the following:

```
$ cat /var/log/Xorg.0.log | grep fglrx
```
And:
```
$ cat /etc/default/linux-restricted-modules-common
```
And:
```
$ sudo lsmod | grep fglrx
```

---

### Post by lilbudda on 2006-10-09
> **hurrrtin said:**
> I get that error as well. I think it is related to this particular version of the driver not being compatible with AIGLX, which AFAIK is being included with edgy by default. It doesn't seem to create any problems for me, but I havent tried XGL yet either.

I get the same error message and OpenGL stuff doesn't seem to be accelerated. I have tried XGL/Beryl stuff too, with mixed results. But I want to get 3D working smoothly first. 

> I used the latest ATI driver. fglrxinfo gives:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.6065 (8.29.6)

---

### Post by hurrrtin on 2006-10-09
> **lilbudda said:**
> I get the same error message and OpenGL stuff doesn't seem to be accelerated. I have tried XGL/Beryl stuff too, with mixed results. But I want to get 3D working smoothly first.

It could be an issue with your xorg.conf. Is compositing enabled? I believe this disables DRI if so, and I also believe fglrx enables it by default unless you disable it. Try adding the following to the end of your xorg.conf:
```
Section "Extensions"
        Option           "Composite" "Disable"
EndSection
```
Also, try adding the following to your DEVICE section, just to see if this makes any difference:
```
Option     "UseFBDev" "True"
Option     "VideoOverlay" "on"
```
Reboot and check the logs:
```
cat /var/log/Xorg.0.log | grep fglrx | grep -i DRI
```

---

### Post by dollarbill on 2006-10-09
Kudos!!!! It worked for me and I even got beryl rockin. You have allowed my headaches](*,)  migrate to other issues I have....here are some screenshots!!!! And once again....THANK YOU!!!!:D

---

### Post by lilbudda on 2006-10-10
> cat /var/log/Xorg.0.log | grep fglrx | grep -i DRI

results:
> (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

the xorg.conf contains the aforementioned code.

---

### Post by mbluethgen on 2006-10-14
hi folks,

is it possible with this configuration to use beryl on edgy without xgl?

bye 
marco

---

### Post by tseliot on 2006-10-14
**[SIZE="3"][COLOR="Red"]Warning[/COLOR][/SIZE]**: if you use a wireless cards which needs the driver in the restricted modules you will lose your Internet connection if you remove the linux-restricted-modules

---

### Post by jdong on 2006-10-14
> **mbluethgen said:**
> hi folks,

is it possible with this configuration to use beryl on edgy without xgl?

bye 
marco

No. fglrx does not support the necessary extensions for AIGLX.

---

### Post by hurrrtin on 2006-10-15
I apologize for not clarifying that this might break certain wi-fi adapters. I also didn't intend this to be used in conjunction with compiz/beryl/composite.

---

### Post by napoleon on 2006-10-17
Am I wrong in thinking that it's a lot less hassle to just edit your xorg.conf and make sure "fglrx" is your driver instead of running aticonfig --initial?

---

### Post by jdong on 2006-10-17
> **napoleon said:**
> Am I wrong in thinking that it's a lot less hassle to just edit your xorg.conf and make sure "fglrx" is your driver instead of running aticonfig --initial?
It's a lot harder to say than "run aticonfig --initial", not to mention it leaves the factor of human error in the equation. Typically for me aticonfig does a great job.

---

### Post by Foxen on 2006-10-17
Would you mind if I created a HOWTO about getting the fglrx working with a X1600 Mobility Radeon in Dapper?

The reason I ask is because I got part of the solution by reading this thread ;)

---

### Post by Analord on 2006-10-22
Unfortunatly, after i disable composite under extensions in xorg i get good output in terminal (everything is installed), but when i move window in XFCE, everything freezes.

Only hardware reset does the stuff.

Ati radeon 8500le, edgy.

In dapper everything worked fine (except p00r ati performance).

---

### Post by MiF on 2006-10-22
"Jdong" totally solved my problems. xorg-driver-fglrx, add the composite option and change vesa to fglrx in xorg.conf. Restart X and you're set!

Tnx a bunch!

---

### Post by Kangaroo on 2006-10-25
I have exactly the same problem as Analord. 

Radeon 8500. Sometimes my desktop boots up to the point where the icons on
the panels should appear, but they do not, (i have auto-login enabled) and sometimes it 
boots completely, but then freezes upon moving a window.

---

### Post by Rackerz on 2006-10-26
10 points go to hurrrtin, this worked for me :D. Now to get Beryl going.

---

### Post by leetcharmer on 2006-10-26
I did every single step from the first page and DRI is still not available according to all the logs.  How can I fix this?

---

### Post by leetcharmer on 2006-10-26
```
leetcharmer@lappyx64:~$ sudo echo "fglrx" >> /etc/modules
bash: /etc/modules: Permission denied

```

hrm :/  I did sudo su to run this command successfully.  Is this the meat of my problem?

--

I don't think so, fglrx shows up in the modules file

---

### Post by leetcharmer on 2006-10-26
Solution to Enable DRI:

```
Section "Extensions"
Option "Composite" "disable"
EndSection
```

Add this to the end of /etc/X11/xorg.conf

---

### Post by bicchi on 2006-10-27
Thanks, I followed your tutorial and got DRI working. In my case fglrx needed to be loaded at startup. I think the key ingredient for me was to add the fglrx module to /etc/modules with the command: sudo echo "fglrx" >> /etc/modules

I am not sure if its happening to a lot of people but perhaps we need to edit the wiki entry at: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") to reflect this problem. Actually it would be nice that when the package xorg-driver-fglrx is installed the entry in /etc/modules gets added. Maybe this should be pointed out to the ubuntu developers.

---

### Post by azrielmackay on 2006-10-28
For those of you having the aiglx lib loading errors, I have found the solution (wasnt easy to find either)
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
 apparently thats something ati's drivers dont always work with

---

### Post by gundog on 2006-10-30
The /etc/init.d/gdm stop command from TTY1 kills everything. Black screen of nothing at all. Manual power down required since nothing else is accessible (none of the other terminals).

---

### Post by jdong on 2006-10-31
That is also a known bug... usplash corrupts the consoles with ATI cards. Either turn off usplash or add vga=791 to bootup arguments.

---

### Post by howipepper on 2006-11-01
Ok, I've done pretty much everything I can do.  I have an ATi Radeon X1300 Pro video card, and I'm running Edgy.  I've installed the xorg-driver-fglrx and the restricted modules.  I've edited /etc/X11/xorg.conf and added the Composite section.  I've made a simlink for /usr/lib/dri to /usr/lib/xorg/modules.  I've even made sure "fglrx" is in the /etc/modules file.  All the indications are positive and the screen sure feels much faster than it did under the vesa driver.  My problem is, if I try to run any of the OpenGL examples (glxgears, etc...), the window opens, but the screen is black!  No other error message.

Now, here's another thing:  When I run the "sudo grep fglrx /var/log/Xorg.0.log, I get this:

(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(WW) fglrx(0): Video Overlay not supported on AVIVO based graphics cards. For XVideo support please upgrade to Xorg 6.9 or later and use Option "TexturedVideo".
(II) fglrx(0): Interrupt handler installed at IRQ 169.
(II) fglrx(0): Exposed events to the /proc interface
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

Am I missing something, or am I going to have to rip this $%@^ ATi video card out and go buy an nVidia card?

---

### Post by JackandJohn on 2006-11-02
Finally got it going on mine: Disable composite, and throw in the videooverlay setting: it all looks good..



Now if Only I can keep my upgrade trigger from attempting the new binary ati drivers... 8.30? That's a whole new Tenth!

---

### Post by xnn on 2006-11-03
It seems like your guide was good, but I have a little problem. I'm running Kubuntu and all is good, until I reboot. I try to run fglrxinfo and it freezes. After 5 minutes I press ctrl+c and return to the command line...strange...the DRI module is loaded correctly I suppose. This is my xorg.conf:

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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

  # path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "glx"
	Load  "GLcore"
	Load  "v4l"
	Load  "dri"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	VendorName   "Plug 'n' Play"
	ModelName    "Plug 'n' Play"
	Gamma        1
	ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
 # 
	Identifier   "monitor1"
	Gamma        1
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Driver      "ati"
	BoardName   "ati"
	Option	    "MergedFB" "off"
	Option      "UseFBDev" "True"
	Option	    "VideoOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
 # 
	Identifier  "device1"
	Driver      "ati"
	BoardName   "ati"
	Option	    "MergedFB" "off"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "640x480@60"
	EndSubSection
EndSection

Section "Screen"
 # 
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection

```

**sudo cat /var/log/Xorg.0.log | grep fglrx** says it's ok (I think), except a small error (last 2 lines):

```
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): cpuSpeedMHz: 0x00000682
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(II) fglrx(0): UMM Bus area:     0xd0701000 (size=0x078ff000)
(II) fglrx(0): UMM area:     0xd0701000 (size=0x078ff000)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.1.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x23000
(II) fglrx(0): [drm] mapped SAREA 0x23000 to 0xb7f07000
(II) fglrx(0): [drm] framebuffer handle = 0x24000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.28.8
(II) fglrx(0):     Date: Aug 17 2006
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.17-10-386
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00025000
(II) fglrx(0): [agp] Mode=0x1f000a0b bridge: 0x1106/0x3189
(II) fglrx(0): [agp] AGP v1/2 disable mask 0x00000000
(II) fglrx(0): [agp] AGP v3 disable mask   0x00000000
(II) fglrx(0): [agp] enabling AGP with mode=0x1f000b0a
(II) fglrx(0): [agp] Remapping MC AGP space (new MCAGPBase = 0xe0000000)
(II) fglrx(0): [agp] AGP protocol is enabled for graphics board. (cmd=0x1f000302)
(II) fglrx(0): [agp] graphics chipset has AGP v3.0 (native mode)
(II) fglrx(0): [drm] ringbuffer size = 0x00100000 bytes
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(II) fglrx(0): [drm] texture shared area handle = 0x00029000
(II) fglrx(0): shared FSAAScale=1
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x00701000
(II) fglrx(0): Splitting WC range: base: 0xd0000000, size: 0x701000
(II) fglrx(0): Splitting WC range: base: 0xd0400000, size: 0x301000
(II) fglrx(0): Splitting WC range: base: 0xd0600000, size: 0x101000
(==) fglrx(0): Write-combining range (0xd0700000,0x1000)
(==) fglrx(0): Write-combining range (0xd0600000,0x101000)
(==) fglrx(0): Write-combining range (0xd0400000,0x301000)
(==) fglrx(0): Write-combining range (0xd0000000,0x701000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,1434)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1280 x 410
(II) fglrx(0): Interrupt handler installed at IRQ 10.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x23000 at 0xb7f07000
```

and **sudo cat /var/log/Xorg.0.log | grep fglrx | grep DRI** says the same:

```
(==) fglrx(0): NoDRI = NO
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete
```

Please help me solve this out. I'm using an ATI 9250 Pro. Thanks in advance.

---

### Post by happy-and-lost on 2006-11-07
So... is it possible to Beryl using an ATi card? If so, how did you do it?

---

### Post by circuitsurfer on 2006-11-08
Hello

Trying to get FGLRX working, think I am close but recently I started getting Unable to open display :0
As below. Anyone wann help me with this Pleeeazee.

kaiser@kaiser-desktop:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

kaiser@kaiser-desktop:~$ fglrxinfo
Error: unable to open display :0
kaiser@kaiser-desktop:~$](*,) 

Help would be appreciated.

---

### Post by Don_DiZzLe on 2006-11-13
After doing this sudo cat /var/log/Xorg.0.log | grep fglrx | grep -i DRI I get this for error

(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

How do I fix this?

---

### Post by TemporalRift on 2006-11-14
It Works It Works Oh Sweet Master of the Penguin It WORKS! You sir, are my hero. I've been trying to get this to work for DAYS.

---

### Post by sparqle on 2006-12-02
I have followed the exact procedure on Kubuntu edgy and my graphics card is still not being used. I still get the same error of DRI not working.

Here is the output from fglrxinfo:
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

Here is my xorg.conf file. Please help me!
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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

  # path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"

  # /dev/input/event
  # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"# Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	VendorName   "Plug 'n' Play"
	ModelName    "Plug 'n' Play"
	Gamma        1
	ModeLine     "1280x800@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
 #  
	Identifier   "monitor1"
	VendorName   "Plug 'n' Play"
	ModelName    "Plug 'n' Play"
	Gamma        1
	ModeLine     "1280x800@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	BoardName   "ati"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
 #  
	Identifier  "device1"
	Driver      "fglrx"
	BoardName   "ati"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1280 800
		Depth     24
		Modes    "128x800@60"
	EndSubSection
EndSection

Section "Screen"
 #  
	Identifier "screen1"
	Device     "device1"
	Monitor    "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x800@60"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "ServerFlags"
 Option "AIGLX" "off"
EndSection

Section "Extensions"
	Option	"Composite" "0"
EndSection

---

### Post by deethree on 2006-12-09
> **Don_DiZzLe said:**
> After doing this sudo cat /var/log/Xorg.0.log | grep fglrx | grep -i DRI I get this for error

(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)

How do I fix this?

I see that _DiZzLe lilbudda and myself seem to have to same issue, anyone figured out whats the issue? My other 3 tries didn't get me as far as this, so here's to hoping this is lucky #4. :D

[edi: I've got a 9800 pro (non AIW) I  don't know what the others have. I used linux-restricted-modules-generic rather then the 386... wondering if thats a good idea after the fact.]

---

### Post by kalahari875 on 2006-12-09
Somebody kill me. I've been noticing that my Kubuntu Edgy performance sucks compared to a much slower computer that I also have it installed on... and discovered that fglrx isn't loading right. I have an ATI Radeon All in Wonder 8500DV. I am trying to use the Edgy fglrx package.

I have added fglrx to /etc/modules, added the symlink (ln -s /usr/lib/dri /usr/lib/xorg/modules/dri), and added Option "Composite" "Disable" to Section "Extensions" in xorg.conf. I have verified that I am trying to load fglrx (the default ati driver caused my machine to hang).

Still, fglrxinfo reports:
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

If I try sudo modprobe fglrx:
```
FATAL: Error running install command for fglrx
```

When I look at Xorg.0.log, apparently the DRI driver isn't loading:
```
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
```

When I ls /dev/dri, there's nothing there. Is that the problem?

Any ideas? I am at my wits' end. I have attached my xorg.conf ([ATTACH]20802[/ATTACH]) and Xorg.0.log ([ATTACH]20803[/ATTACH]) files.

PLEASE HELP!!!

---

### Post by deethree on 2006-12-10
> **deethree said:**
> [edit: I've got a 9800 pro (non AIW) I  don't know what the others have. I used linux-restricted-modules-generic rather then the 386... wondering if thats a good idea after the fact.]

ok, re-tried using the linux-restricted-modules--386  version... no change. odly enough says my card is at 2 rather then 1.

---

### Post by deethree on 2006-12-10
[http://www.ubuntuforums.org/showthread.php?t=305665](http://www.ubuntuforums.org/showthread.php?t=305665)

Worked for me... maybe a few others...

cheers!


d3.

---

### Post by Choxo on 2006-12-11
> **deethree said:**
> I see that _DiZzLe lilbudda and myself seem to have to same issue, anyone figured out whats the issue? My other 3 tries didn't get me as far as this, so here's to hoping this is lucky #4. :D

[edi: I've got a 9800 pro (non AIW) I  don't know what the others have. I used linux-restricted-modules-generic rather then the 386... wondering if thats a good idea after the fact.]

At this into your xorg.conf:

```

Section "ServerFlags"
    Option "AIGLX" "off"
EndSection

```

That would remove the error...

---

### Post by kEinstein on 2006-12-16
> **hurrrtin said:**
> After COUNTLESS guides and experiments, reinstalls, and headaches, here is
what I did to get the fglrx drivers from ATI to work with acceleration with
DRI. Seems I could always get fglrx driver, but it would always show MesaGL
instead of ATI OpenGL 2.x. But I fresh installed edgy, and did the following...


Thank you!!! Finally - with some hints from hurrrtin I have fglrx + dual-head + 3D support + [a clean mouse cursor]("http://ubuntuforums.org/showthread.php?t=273213") running smoothly on my T43.

In my case, having previously installed fglrx from restricted kernel modules, adding 'fglrx' in /etc/modules and setting up the DRI link did the trick in edgy. 
```

$ sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```


Cheers!!!

---

### Post by aboutTOpullmyhairout on 2006-12-18
[QUOTE=
Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "glx"
	Load  "dbe"
	Load  "v4l"
EndSection
[/QUOTE] 

inthis section i think you need to ad a load for dri

[QUOTE=
Section "ServerFlags"
 Option "AIGLX" "off"
EndSection

Section "Extensions"
	Option	"Composite" "0"
EndSection   [/QUOTE]

in my opinion you do not even need the AIGLX off and as far as the composite it should look like this(or atleast that is how mine is and it works)

Section "Extensions"
Option  "Composite" "Disable"
EndSection




one last thing your guide was great but it did work for me, for some reason wheni i used the aticonfig -initial i omitted the busid for my video card.

this little situation helped me remeber why there are log files lol

---

