---
title: "Voodoo 3 Driver"
date: 2006-03-10
forum: Multimedia &amp; Video
---

### Post by ubuntukid on 2006-03-10
I`ve been trying to play a few games that I installed from the "Add Aplications" menu item. Nothing really worked without a horribly low FPS and then I realised that I need to install drivers for my Voodoo 3 card. Could someone please take me step by step through this as I`ve never installed a driver on Linux before. I`ve used Synaptic Package Manager to install something called glide or something like that, but where do I go from there?

---

### Post by qrazi on 2006-03-14
unfortunately i havent found anyway yet to get hardware 3d working on the voodoo 3/4/5 cards. I use a voodoo5 in this machine, and the best i could find is that some driver version used to work on the old kernel 2.4 (from before ubuntu).

I did try to compile a new xorg server together with the DRI driver for the voodoo cards, but i couldnt get it to compile the driver itself....

---

### Post by cronholio on 2006-03-14
I used to run Ubuntu on a system with a Vodoo3 and it worked perfectly after installing the Glide driver through Synaptic. Did you install it and restart X? Is it loaded in your xorg.conf?

---

### Post by McQuaid on 2006-03-15
Well, my gf4ti just died so I had to resort to my old voodoo3 pci.

I as well can't get it to work in 3d.  I've investigated for hours but can't find the solution.  I'll post what I have discovered and maybe it will work for you or someone else can shed light on this(as voodoo3 used to be easy on older distros).

The first thing you should install is libglide3.  This is for banshee, v3, v4, v5 but NOT v2.  What is installed by default is libglade2 for v2.  Supposedly this made the difference for other people but not for me.  I wanted to remove libglade2 to ensure it was using libglide3 but deps don't allow it. It flags xserver-org to be removed.  Why do they do that?!

But anyways the next thing is to make sure you've set up your xorg.conf correctly.

bring up /etc/X11/xorg.conf in your favourite editor.

In section module I have this:

Section "Module"
	Load	"GLcore"
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

Then section device:

Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	BusID		"PCI:2:12:0"
EndSection

Now, notice the busID, because mine is PCI and not agp, that had to be accurate.  I ran dpkg-reconfigure xserver-xorg to create a new xorg.conf and it filled in the busid for me as I wasn't sure how to determine that value.  If you don't want to muck with your xorg.conf manually run that cmd I just stated but back up your xorg.conf first.

Finally there is section screen:

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection

EndSection

Notice I only have depth 16.  Voodoo 3's (and I believe 4,s and 5's as well, not sure) can only provide opengl hardware accel with a colour depth of 16.  So make sure you have that.

So from what I've read you do the above and you'll be working.  But not so far for me. So let's continue.

From a term run this: 

mcquaid@mcquaid:~$ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

Right there you know you have a problem.  Direct rendering must say yes and they mesa indirect refers to opengl is being done by software.

So next I check out /var/log/Xorg.0.log to see if anything here will shed some light.

In here some things seem fine but not all:
```

(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found

```

I assume that's bad, not sure how to debug that further.

```

(**) Option "dpms"
(**) TDFX(0): DPMS enabled
(II) TDFX(0): X context handle = 0x00000001
(II) TDFX(0): [drm] installed DRM signal handler
(II) TDFX(0): [DRI] installation complete
(==) TDFX(0): Direct rendering enabled
(==) RandR enabled

```

But this tells me Direct rendering is enabled, wtf?

```

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:02:0c.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:02:0c.0

```

That looks fine as well.

The last thing I verified was the modules were actually loading:
do a lsmod and look:

Module                  Size  Used by
tdfx                         3840  1
drm                       67348  2 tdfx
intel_agp              22940  1
agpgart                34856  2 drm,intel_agp

Looks good to me, but not sure about the intel_agp port still being used even though I'm not using it.  I tried rmmod but didn't fix anything.

Also, the last thing I read was you must have bus mastering enabled for DRI to work.  

I don't use hdparm to force dma as most users do.  I load the chipset module for my chipset and that gaves me dma access for my hard drives, cdrom without any need for hdparm to force anything.

You can look quickly by doing:

root@mcquaid:/home/mcquaid # hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 78177792, start = 0

If you see using_dma you should be good as far as bus mastering goes, but I'd like another way to verify.

This DRI guide here talks about determining if bus mastering is available, but I didn't really get how to run it.  There should be an easier way to verify bus mastering is in fact enabled.

[http://dri.sourceforge.net/doc/DRIuserguide.html](http://dri.sourceforge.net/doc/DRIuserguide.html)

> 
9.1 Bus Mastering

DMA-based DRI drivers (that's most DRI drivers) cannot function unless bus mastering is enabled for your graphics card. By default, some systems don't having bus mastering on. You should enable it in your BIOS.

Alternately, you can check the status of bus mastering and change the setting from within Linux. There may be similar procedures for other operating systems.

Run lspci (as root) and find the information describing your graphics adapter. For example:

    00:00.0 Host bridge: Intel Corporation 440BX/ZX - 82443BX/ZX Host bridge (rev 03)
    00:01.0 PCI bridge: Intel Corporation 440BX/ZX - 82443BX/ZX AGP bridge (rev 03)
    00:07.0 ISA bridge: Intel Corporation 82371AB PIIX4 ISA (rev 02)
    00:07.1 IDE interface: Intel Corporation 82371AB PIIX4 IDE (rev 01)
    00:07.2 USB Controller: Intel Corporation 82371AB PIIX4 USB (rev 01)
    00:07.3 Bridge: Intel Corporation 82371AB PIIX4 ACPI (rev 02)
    00:11.0 Ethernet controller: Intel Corporation 82557 [Ethernet Pro 100] (rev 08)
    00:12.0 SCSI storage controller: Symbios Logic Inc. (formerly NCR) 53c895 (rev 02)
    00:14.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
    01:00.0 VGA compatible controller: 3Dfx Interactive, Inc.: Unknown device 0009 (rev 01)
        

The bus, device, and function number comprise the device id, which is conventionally written in the form bus:dev.func, or in this case 01:00.0.

Use the setpci command to examine bit two of register 4 for your graphics card. This will indicate whether or not bus mastering is enabled.

        setpci -s 01:00.0 4.w
        

A hexadecimal value will be printed. Convert the least significant digit to binary. For example, if you see 3, that's 0011 in binary (bit two is 0). If you see 7, that's 0111 in binary (bit two is 1). In the first example, bus mastering is disabled. It's enabled in the second example.

The following shell script will enabled bus mastering for your graphics card and host bridge. Run it as root.

    #!/bin/bash
    dev=01:00.0   # change as appropriate
    echo Enabling bus mastering on device $dev
    setpci -s $dev 4.w=$(printf %x $((0x$(setpci -s $dev 4.w)|4)))
    dev=00:00.0
    echo Enabling bus mastering on host bridge $dev
    setpci -s $dev 4.w=$(printf %x $((0x$(setpci -s $dev 4.w)|4)))
        

You can check if this worked by running the first setpci command again.


Also, I've read other users from other recent distros are having this problem.  The two were gentoo and mandriva.  But both solved it by installing the libglide3 pkg.  One said it was something with incorrect sym links.  There are symlinks all over the place for these drivers, and not sure how to verify libglide3 is in fact being used instead of libglide2.


So that's as far as I have gotten.  This really should be easier at this point especially since were dealing with an open source driver and not a binary.

Hoping someone else can shed some light on this scenario.

---

### Post by McQuaid on 2006-03-15
Ok investigating more.  To get more info out of glxinfo first do this:
export LIBGL_DEBUG=verbose
then run glxinfo

At the top I get:

```
mcquaid@mcquaid:/usr/lib$ glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 1.1.0 tdfx (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/tdfx_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/tdfx_dri.so failed (/usr/X11R6/lib/modules/dri/tdfx_dri.so: undefined symbol: _glapi_add_dispatch)
libGL error: unable to find driver: tdfx_dri.so
display: :0  screen: 0
direct rendering: No

```

Now at first, I didn't even have a dri directory under /usr/X11R6/lib/modules, so I thought being smart i sym linked it to where it actually exists.  Which is /usr/lib/dri.  I tried running ldconfig afterwards but same thing.

Now looking at this troubleshooting guide:
[http://dri.freedesktop.org/wiki/DriTroubleshooting]("http://dri.freedesktop.org/wiki/DriTroubleshooting")

> 
If the driver complains about unresolved symbols:

libGL error: dlopen /usr/X11R6/lib/modules/dri/radeon_dri.so failed
   (/usr/X11R6/lib/modules/dri/radeon_dri.so: undefined symbol: _glapi_noop_enable_warnings)

then your libGL is out of sync with your DRI drivers. Because APIs change, you typically need a libGL from the latest X.Org release to run DRI drivers, and sometimes you need a libGL from X.Org CVS for the latest drivers. Reinstall both your drivers and your libGL from sources from the same date.


So, is there I can bring them in sync?  Can I just compile libglide3? If so, how would I obtain the source just for that.  Wouldn't want to be forced to compile all of xorg or something.  If not libglide3, what is actually the out of sync file?

---

