---
title: "[SOLVED] Nvidia Driver &amp;amp; Low Resolution"
date: 2008-07-21
forum: Multimedia Software
---

### Post by Anlace on 2008-07-21
Update:
This issue was caused by the monitor passing bad (corrupt) edid info to xorg.  See posts at:

[SOLVED] Low Resolution Issues Solved (when nothing else works. . . .)
[http://ubuntuforums.org/showthread.php?t=884211](http://ubuntuforums.org/showthread.php?t=884211)

Nvidia just won't work! Why, why, why?!
[http://ubuntuforums.org/showthread.php?t=883938](http://ubuntuforums.org/showthread.php?t=883938)


Original post:

Greetings,

I have struggled with this issue in the past ([http://ubuntuforums.org/showthread.php?t=605460](http://ubuntuforums.org/showthread.php?t=605460)) and ended up resolving it by staying with Feisty instead of upgrading.

Now I have a brand new computer built with the best hardware that I could afford:
Nvidia nForce 780i 3-Way SLI MB
Intel Core 2 Duo E8400 CPU
4 GB RAM
Nvidia GeForce 9800 GTX(G92) XXX 512MB 256-bit GDDR3 video card
ViewSonic VX2025WM 20" LCD Monitor

I installed the system from a recent ISO of Kubuntu (8.04.1).

The problem is I can only get the native 1680x1050 resolution on my monitor by using the generic vesa driver.  Everything else gives me either 680x420 or 800x600 resolution.

Please read what I have done already before making suggestions, that will save us both some effort.  I am also very willing to spend time with someone knowledgeable on IRC or Kopete if someone has the time to do that with me.

First this is what works:
Used System Settings > Monitor and Display to change the monitor from Plug 'n' Play to Generic LCD 1680x1050 (Widescreen).

This is what did not work:
Used System Settings > Monitor and Display to change the monitor from Plug 'n' Play to Generic LCD 1680x1050 (Widescreen) and changed the driver to nv.  Rebooted to a resolution of 800x600 that could not be changed.  The only way that I could get acceptable resolution was to go back to the vesa driver.  (Please see below for the changes that I have made by hand to the xorg.conf file).

Installed nvidia_new_glx, when I rebooted from this I got resolutions of 640x480.  Nvidia Settings was inaccessible due to the low resolution of the screen.  The only way that I could get acceptable resolution was to go back to the vesa driver.

Installed Envy and got resolutions that were even lower - in the neighborhood of 320x200-something with no means of raising the resolution.

At this point I dumped Kubuntu and reinstalled from scratch.

I began to suspect that the resolution issue is due to xorg and/or the nvidia drivers not picking up correct EDID info from my monitor.  I added my situation to Bug 194760 :EDID fail at [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760).

That gave me hope so I added specific information about my monitor to xorg.conf:

Horizsync	30.0 - 82.0
Vertrefresh	50.0 - 75.0

I also added these lines as per the Nvidia ReadMe for their latest driver:  ([ftp://download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-b.html](ftp://download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-b.html))

Option		"ConnectedMonitor" "DFP"
Option		"UseEDID" "FALSE"
Option		"UseEDIDFreqs" "FALSE"
Option		"UseEDIDDpi" "FALSE"
Option		"ModeValidation" "NoEdidModes"
Option		"ExactModeTimingsDVI" "TRUE"
Option		"SLI" "Single"
Option		"DPI" "96 x 96"
Option		"IncludeImplicitMetaModes" "FALSE"

None of these options has worked, changing the metamodes and the mode lines to only the desired resolution has not worked, and including the specific refresh rates has not worked.

I tried using a known good xorg.conf from a previous installation, that has not worked.

The Hardware Drivers Manager program for Kubuntu did not work because my video card was not recognized or at least that's what I think when it says "No proprietary drivers are in use by this system" even though I have the Nvidia drivers installed.

I used these resources to try and correct resolution issues:

BinaryDriverHowtoNvidia
([https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia))

FixVideoResolutionHowto
([https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto))

HowTo: ViewSonic 20.1" LCD with with nVidia drivers 
([http://ubuntuforums.org/showthread.php?p=1597740](http://ubuntuforums.org/showthread.php?p=1597740))

New nVidia driver ver 173.14.05
([http://ubuntuforums.org/showthread.php?t=810661&highlight=nvidia+nv+nvidia_new](http://ubuntuforums.org/showthread.php?t=810661&highlight=nvidia+nv+nvidia_new))

Plus a handful of other postings in the forums I haven't bookmarked.

Here is the issue as I am trying to get help in the xorg-server launchpad Answers:
How Do I Override EDID Info in Xorg.conf?
([https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299](https://answers.launchpad.net/ubuntu/+source/xorg-server/+question/39299))

I can post my xorg.conf file and all of the variations that haven't worked.  I can also post the xorg.log file and edid.bin if that helps.

So . . . . who is up to the challenge?  It is really discouraging to not be able to use this very nice video card to its capacity, at least to the point of being able to get any 3D or GL out of it at all.  As it is I can't even run screensavers if I want full resolution.

Can anyone help?  Please post and I would be happy to fire up my other computer into IRC and go through a concentrated session of troubleshooting.

Peace,
Gail

---

### Post by Anlace on 2008-07-21
Contents of xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"GeForce 9800GTX"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Option		"ConnectedMonitor" "DFP-0"
	Option		"IgnoreEDID" "TRUE"
	Option		"UseEDID" "FALSE"
	Option		"UseEDIDFreqs" "FALSE"
	Option		"UseEDIDDpi" "FALSE"
	Option		"ModeValidation" "NoEdidModes"
	Option		"DPI" "96 x 96"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1680x1050"
	Horizsync	30.0 - 82.0
	Vertrefresh	50.0 - 75.0
	Option		"MetaModes" "1680x1050_60"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1680x1050_60"
	EndSubSection
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

---

### Post by Anlace on 2008-07-21
From Xorg.0.log:

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "IgnoreEDID" "TRUE"
(**) NVIDIA(0): Option "UseEDID" "FALSE"
(**) NVIDIA(0): Option "ConnectedMonitor" "DFP-0"
(**) NVIDIA(0): Option "UseEdidFreqs" "FALSE"
(**) NVIDIA(0): Option "MetaModes" "1680x1050_60"
(**) NVIDIA(0): Option "UseEdidDpi" "FALSE"
(**) NVIDIA(0): Option "DPI" "96 x 96"
(**) NVIDIA(0): Option "ModeValidation" "NoEdidModes"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(**) NVIDIA(0): ConnectedMonitor string: "DFP-0"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): The IgnoreEDID and NoDDC options have been deprecated.  The
(WW) NVIDIA(0):     NVIDIA X driver makes use of a display device's EDID
(WW) NVIDIA(0):     during construction of its modePool.  It is recommended
(WW) NVIDIA(0):     that you allow the X driver to make use of any available
(WW) NVIDIA(0):     EDID.  If, however, you know what you are doing and have
(WW) NVIDIA(0):     good reason to do so, you can disable the X driver's use
(WW) NVIDIA(0):     of EDIDs by setting the "UseEDID" X configuration option
(WW) NVIDIA(0):     to FALSE; e.g.,
(WW) NVIDIA(0): 
(WW) NVIDIA(0):   Option "UseEDID" "FALSE"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Note that, rather than globally disable all uses of the EDID,
(WW) NVIDIA(0):     you can individually disable each particular use of the
(WW) NVIDIA(0):     EDID; e.g.,
(WW) NVIDIA(0): 
(WW) NVIDIA(0):   Option "UseEDIDFreqs" "FALSE"
(WW) NVIDIA(0):   Option "UseEDIDDpi" "FALSE"
(WW) NVIDIA(0):   Option "ModeValidation" "NoEdidModes"
(WW) NVIDIA(0): 
(WW) NVIDIA(0): See Appendix B: X Config Options in the README for details on
(WW) NVIDIA(0):     each of these options.
(WW) NVIDIA(0): 
(**) NVIDIA(0): Ignoring EDIDs
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(GPU-0): Not probing EDID on DFP-0.
(II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX (G92) at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.92.3b.00.0b
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9800 GTX at PCI:3:0:0:
(--) NVIDIA(0):     DFP-0
(--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
(--) NVIDIA(0): DFP-0: Internal Dual Link TMDS
(II) NVIDIA(0): Mode Validation Overrides for DFP-0:
(II) NVIDIA(0):     NoEdidModes
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1680x1050_60"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(**) NVIDIA(0): DPI set to (96, 96); computed from "DPI" X config option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp

---

### Post by Anlace on 2008-07-21
The driver works with the analog cable.  That means having to use analog over digital but apparently this monitor is not passing along valid EDID values for its DVI connection and it's no longer possible to ignore EDID information in xorg.conf, at least not with the current Nvidia driver.

Hope this information helps someone else.

---

### Post by Anlace on 2008-07-21
Ok, this feels a lot like talking to myself but here goes.

I used the Nvidia Settings program to generate a valid EDID.bin profile, after I successfully logged into Kubuntu using the analog connection.  It's under the setting for GPU-0 > DFP-0 > Acquire EDID.  I saved it onto my hard drive.

Then I added the "Option "CustomEDID" "DFP-0:/path/to/edid.bin".  I shut down the computer, unplugged the analog cable, plugged in the digital and booted into perfect resolution.

When I ran sudo get-edid I still got EDID failure so that confirmed that the solution above is working.  Now to turn on the bells and whistles.  I am very happy to have found a solution and I hope that this helps others out as well.


get-edid: get-edid version 1.4.1

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
        Function supported
        Call successful

        VBE version 300
        VBE string at 0x11110 "NVIDIA"

VBE/DDC service about to be called
        Report DDC capabilities

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
        Function supported
        Call successful

        Monitor and video card combination does not support DDC1 transfers
        Monitor and video card combination supports DDC2 transfers
        0 seconds per 128 byte EDID block transfer
        Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
        Read EDID

        Performing real mode VBE call
        Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
        Function supported
        Call failed

The EDID data should not be trusted as the VBE call failed
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Zc&#65533;&#65533;&#65533;&#65533;+.&#65533;&#65533;&#65533;ZI&#65533;$PT&#65533;&#61491;&#65533;&#65533;&#65533;@qO1
!9&#65533;0b&#9618;'@h&#65533;6&#65533;&#65533;Q6Y062507673
&#65533;2KR
      &#65533;VX2025wm

---

