---
title: "Blender Display Problems"
date: 2009-06-12
forum: Multimedia Software
---

### Post by kd0afk on 2009-06-12
I am having the same problems as in this thread:
[http://ubuntuforums.org/showthread.php?t=436693](http://ubuntuforums.org/showthread.php?t=436693)
I have tried asking about the problem on the Blender forum but all I get is snide comments and an uber geek attitude.
Could someone help me out on this. I am new to Ubuntu and I will post my video card stats and what not if someone would help me find them.

---

### Post by kd0afk on 2009-06-13
I know that I am supposed to wait 48 hours to bump but damnit, I need someone to help me get this fixed. I heard about an intel video card settings manager but I can't find it anywhere. Someone please help me out please.

---

### Post by kd0afk on 2009-06-13
This link:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
looks very intriguing. Could this help my display problems?

---

### Post by kd0afk on 2009-06-13
The oddest thing. I upgraded to 9.04 JJ and it completely messed my system up. It would boot up and the screen would flash twice like normal and then it would flash three more times and I would have a REALLY screwed up screen so I reinstalled Ibex and now Blender works fine. Still a bit of a refresh/redraw problem. New question; how can I prevent Blender from messing up again and still upgrade to Jaunty?

---

### Post by kd0afk on 2009-06-13
I needed to upgrade and since nobody deemed me worthy of helping me, I did. Now blender is right back to doing the same thing it was doing.
NOW, Can someone PLEASE help me fix it?
Like I said before, I can post my system specs if someone would be so kind as to let me know where to find them.
I won't be on line tomorrow but I really don't think it matters, I will probably have to bump this thread on monday.

---

### Post by kd0afk on 2009-06-14
So, I found this on the help documentation of Ubuntu. I read it and read it and for the life of me, I can't figure out how to get into the program that let's my change the many options listed in this article. If anyone can enlighten me, that would be swell.

[COLOR=Red]intel(4)
NAME

intel - Intel integrated graphics chipsets
SYNOPSIS

Section qDeviceq
  Identifier qdevnameq
  Driver qintelq
  ...
EndSection

DESCRIPTION

intel
is an Xorg driver for Intel integrated graphics chipsets.
The driver supports depths 8, 15, 16 and 24.  All visual types are
supported in depth 8.  For the i810/i815 other depths support the
TrueColor and DirectColor visuals.  For the i830M and later, only the
TrueColor visual is supported for depths greater than 8.  The driver
supports hardware accelerated 3D via the Direct Rendering Infrastructure
(DRI), but only in depth 16 for the i810/i815 and depths 16 and 24 for
the 830M and later.
SUPPORTED HARDWARE

intel
supports the i810, i810-DC100, i810e, i815, i830M, 845G, 852GM, 855GM,
865G, 915G, 915GM, 945G, 945GM, 965G, 965Q, 946GZ, 965GM, 945GME,
G33, Q33, Q35, G35, GM45, G45, Q45, G43 and G41 chipsets.
CONFIGURATION DETAILS

Please refer to (5) for general configuration
details.  This section only covers configuration details specific to this
driver.


The Intel 8xx and 9xx families of integrated graphics chipsets have a unified
memory architecture meaning that system memory is used as video RAM.  For the
i810 and i815 family of chipsets, operating system support for allocating system
memory is required in order to use this driver.  For the 830M
and later, this is required in order for the driver to use more video RAM
than has been pre-allocated at boot time by the BIOS.  This is usually
achieved with an "agpgart" or "agp" kernel driver.  Linux, FreeBSD, OpenBSD,
NetBSD, and Solaris have such kernel drivers available.


By default, the i810/i815 will use 8 MB of system memory for graphics if AGP
allocable memory is < 128 MB, 16 MB if < 192 MB or 24 MB if higher. Use the
VideoRam
option to change the default value.


For the 830M and later, the driver will automatically size its memory
allocation according to the features it will support.  Therefore, the
VideoRam
option, which in the past had been necessary to allow more than some small
amount of memory to be allocated, is now ignored.


The following driver
Options
are supported

Option qNoAccelq qbooleanq
    Disable or enable acceleration.  Default: acceleration is enabled.
Option qSWCursorq qbooleanq
    Disable or enable software cursor.  Default: software cursor is disable
    and a hardware cursor is used for configurations where the hardware cursor
    is available.
Option qColorKeyq qintegerq
    This sets the default pixel value for the YUV video overlay key.
    Default: undefined.
Option qCacheLinesq qintegerq
    This allows the user to change the amount of graphics memory used for
    2D acceleration and video when XAA acceleration is enabled.  Decreasing this
    amount leaves more for 3D textures.  Increasing it can improve 2D performance
    at the expense of 3D performance.
    Default: depends on the resolution, depth, and available video memory.  The
    driver attempts to allocate space for at 3 screenfuls of pixmaps plus an
    HD-sized XV video.  The default used for a specific configuration can be found
    by examining the Xorg log file.
Option qFramebufferCompressionq qbooleanq
    This option controls whether the framebuffer compression feature is enabled.
    If possible, the front buffer will be allocated in a tiled format and compressed
    periodically to save memory bandwidth and power.
    This option is only available on mobile chipsets.
    Default: enabled on supported configurations.
Option qTilingq qbooleanq
    This option controls whether memory buffers are allocated in tiled mode.  In
    most cases (especially for complex rendering), tiling dramatically improves
    performance.
    Default: enabled.
Option qDRIq qbooleanq
    Disable or enable DRI support.
    Default: DRI is enabled for configurations where it is supported.


The following driver
Options
are supported for the i810 and i815 chipsets:

Option qDDCq qbooleanq
    Disable or enable DDC support.
    Default: enabled.
Option qDac6Bitq qbooleanq
    Enable or disable 6-bits per RGB for 8-bit modes.
    Default: 8-bits per RGB for 8-bit modes.
Option qXvMCSurfacesq qintegerq
    This option enables XvMC.  The integer parameter specifies the number of
    surfaces to use.  Valid values are 6 and 7.
    Default: XvMC is disabled.
VideoRam integer
    This option specifies the amount of system memory to use for graphics, in KB.
    The default is 8192 if AGP allocable memory is < 128 MB, 16384 if < 192 MB,
    24576 if higher. DRI require at least a value of 16384. Higher values may give
    better 3D performance, at expense of available system memory.


The following driver
Options
are supported for the 830M and later chipsets:

Option qVideoKeyq qintegerq
    This is the same as the
    qColorKeyq
    option described above.  It is provided for compatibility with most
    other drivers.
Option qXVideoq qbooleanq
    Disable or enable XVideo support.
    Default: XVideo is enabled for configurations where it is supported.
Option qXvPreferOverlayq qbooleanq
    Make hardware overlay be the first XV adaptor.
    The overlay behaves incorrectly in the presence of compositing, but some prefer
    it due to it syncing to vblank in the absence of compositing.  While most
    XV-using applications have options to select which XV adaptor to use, this
    option can be used to place the overlay first for applications which don't
    have options for selecting adaptors.
    Default: Textured video adaptor is preferred.
Option qAccelMethodq qstringq
    Choose acceleration architecture, either "XAA" or "EXA".  XAA is the old
    XFree86 based acceleration architecture.  EXA is a newer and simpler
    acceleration architecture designed to better accelerate the X Render extension.
    Default: "EXA".
Option qModeDebugq qbooleanq
    Enable printing of additional debugging information about modesetting to
    the server log.
    Default: Disabled
Option qFallbackDebugq qbooleanq
    Enable printing of debugging information on acceleration fallbacks to the
    server log.
    Default: Disabled
Option qForceEnablePipeAq qbooleanq
    Force the driver to leave pipe A enabled.  May be necessary in configurations
    where the BIOS accesses pipe registers during display hotswitch or lid close,
    causing a crash.  If you find that your platform needs this option, please file
    a bug (see REPORTING BUGS below) including the output of 'lspci -v' and 'lspci -vn'.
Option qLVDS24Bitq qbooleanq
    Specify 24 bit pixel format (i.e. 8 bits per color) to be used for the
    LVDS output.  Some newer LCD panels expect pixels to be formatted and
    sent as 8 bits per color channel instead of the more common 6 bits per
    color channel.  Set this option to true to enable the newer format.
    Note that this concept is entirely different and independent from the
    frame buffer color depth - which is still controlled in the usual way
    within the X server.  This option instead selects the physical format
    / sequencing of the digital bits sent to the display.  Setting the
    frame buffer color depth is really a matter of preference by the user,
    while setting the pixel format here is a requirement of the connected
    hardware.  Leaving this unset implies the default value of false,
    which is almost always going to be right choice.  If your
    LVDS-connected display on the other hand is extremely washed out
    (e.g. white on a lighter white), trying this option might clear the
    problem.
Option qLVDSFixedModeq qbooleanq
    Use a fixed set of timings for the LVDS output, independent of normal
    xorg specified timings.  The default value if left unspecified is
    true, which is what you want for a normal LVDS-connected LCD type of
    panel.  If you are not sure about this, leave it at its default, which
    allows the driver to automatically figure out the correct fixed panel
    timings.  See further in the section about LVDS fixed timing for more
    information.
Option qXvMCq qbooleanq
    Enable XvMC driver. Current support MPEG2 MC on 915/945 and G33 series.
    User should provide absolute path to libIntelXvMC.so in XvMCConfig file.
    Default: Disabled.
Option qForceSDVODetectq qbooleanq
    Instead of depending on SDVO detect status bit to initialize SDVO outputs,
    this option trys to ignore that status bit and try to probe on all SDVO
    ports anyway. Try this if some output is not detected on your ADD2 card.
    Use of this option will slow down your startup time. Default: Disabled.

OUTPUT CONFIGURATION

On 830M and better chipsets, the driver supports runtime configuration of
detected outputs.  You can use the
xrandr
tool to control outputs on the command line.  Each output listed below may have
one or more properties associated with it (like a binary EDID block if one is
found).  Some outputs have unique properties which are described below.  See the "MULTIHEAD CONFIGURATIONS" section below for additional information.
VGA

VGA output port (typically exposed via an HD15 connector).
LVDS

Low Voltage Differential Signalling output (typically a laptop LCD panel).  Available properties:


BACKLIGHT
- current backlight level (adjustable)

By adjusting the BACKLIGHT property, the brightness on the LVDS output can be adjusted.  In some cases, this property may be unavailable (for example if your platform uses an external microcontroller to control the backlight).


BACKLIGHT_CONTROL
- method used to control backlight

The driver will attempt to automatically detect the backlight control method for your platform.  If this fails however, you can select another method which may allow you to control your backlight.  Available methods include:


native

Intel chipsets include backlight control registers, which on some platforms may be wired to control the backlight directly.  This method uses those registers.


legacy

The legacy backlight control registers exist in PCI configuration space, and have fewer available backlight levels than the native registers.  However, some platforms are wired this way and so need to use this method.


combo

This method attempts to use the native registers where possible, resorting to the legacy, configuration space registers only to enable the backlight if needed.  On platforms that have both wired this can be a good choice as it allows the fine grained backlight control of the native interface.


kernel

On some system, the kernel may provide a backlight control driver.  In that case, using the kernel interfaces is preferable, as the same driver may respond to hotkey events or external APIs.


PANEL_FITTING
- control LCD panel fitting

By default, the driver will attempt to upscale resolutions smaller than the LCD's native size while preserving the aspect ratio.  Other modes are available however:


center

Simply center the image on-screen, without scaling.


full_aspect

The default mode.  Try to upscale the image to the screen size, while preserving aspect ratio.  May result in letterboxing or pillar-boxing with some resolutions.


full

Upscale the image to the native screen size without regard to aspect ratio.  In this mode, the full screen image may appear distorted in some resolutions.

TV

Integrated TV output.  Available properties include:


BOTTOM, RIGHT, TOP, LEFT
- margins

Adjusting these properties allows you to control the placement of your TV output buffer on the screen. The options with the same name can also be set in xorg.conf with integer value.


TV_FORMAT
- output standard

This property allows you to control the output standard used on your TV output port.  You can select between NTSC-M, NTSC-443, NTSC-J, PAL-M, PAL-N, and PAL.

TMDS-1

First DVI SDVO output
TMDS-2

Second DVI SDVO output


SDVO and DVO TV outputs are not supported by the driver at this time.


See (5) for information on associating Monitor
sections with these outputs for configuration.  Associating Monitor sections
with each output can be helpful if you need to ignore a specific output, for
example, or statically configure an extended desktop monitor layout.
HARDWARE LVDS FIXED TIMINGS AND SCALING

Following here is a discussion that should shed some light on the
nature and reasoning behind the LVDSFixedMode option.

Unlike a CRT display, an LCD has a "native" resolution corresponding
to the actual pixel geometry.  A graphics controller under all normal
circumstances should always output that resolution (and timings) to
the display.  Anything else and the image might not fill the display,
it might not be centered, or it might have information missing - any
manner of strange effects can happen if an LCD panel is not fed with
the expected resolution and timings.

However there are cases where one might want to run an LCD panel at an
effective resolution other than the native one.  And for this reason,
GPUs which drive LCD panels typically include a hardware scaler to
match the user-configured frame buffer size to the actual size of the
panel.  Thus when one "sets" his/her 1280x1024 panel to only 1024x768,
the GPU happily configures a 1024x768 frame buffer, but it scans the
buffer out in such a way that the image is scaled to 1280x1024 and in
fact sends 1280x1024 to the panel.  This is normally invisible to the
user; when a "fuzzy" LCD image is seen, scaling like this is why this
happens.

In order to make this magic work, this driver logically has to be
configured with two sets of monitor timings - the set specified (or
otherwise determined) as the normal xorg "mode", and the "fixed"
timings that are actually sent to the monitor.  But with xorg, it's
only possible to specify the first user-driven set, and not the second
fixed set.  So how does the driver figure out the correct fixed panel
timings?  Normally it will attempt to detect the fixed timings, and it
uses a number of strategies to figure this out.  First it attempts to
read EDID data from whatever is connected to the LVDS port.  Failing
that, it will check if the LVDS output is already configured (perhaps
previously by the video BIOS) and will adopt those settings if found.
Failing that, it will scan the video BIOS ROM, looking for an embedded
mode table from which it can infer the proper timings.  If even that
fails, then the driver gives up, prints the message "Couldn't detect
panel mode.  Disabling panel" to the X server log, and shuts down the
LVDS output.

Under most circumstances, the detection scheme works.  However there
are cases when it can go awry.  For example, if you have a panel
without EDID support and it isn't integral to the motherboard
(i.e. not a laptop), then odds are the driver is either not going to
find something suitable to use or it is going to find something
flat-out wrong, leaving a messed up display.  Remember that this is
about the fixed timings being discussed here and not the
user-specified timings which can always be set in xorg.conf in the
worst case.  So when this process goes awry there seems to be little
recourse.  This sort of scenario can happen in some embedded
applications.

The LVDSFixedMode option is present to deal with this.  This option
normally enables the above-described detection strategy.  And since it
defaults to true, this is in fact what normally happens.  However if
the detection fails to do the right thing, the LVDSFixedMode option
can instead be set to false, which disables all the magic.  With
LVDSFixedMode set to false, the detection steps are skipped and the
driver proceeds without a specified fixed mode timing.  This then
causes the hardware scaler to be disabled, and the actual timings then
used fall back to those normally configured via the usual xorg
mechanisms.

Having LVDSFixedMode set to false means that whatever is used for the
monitor's mode (e.g. a modeline setting) is precisely what is sent to
the device connected to the LVDS port.  This also means that the user
now has to determine the correct mode to use - but it's really no
different than the work for correctly configuring an old-school CRT
anyway, and the alternative if detection fails will be a useless
display.

In short, leave LVDSFixedMode alone (thus set to true) and normal
fixed mode detection will take place, which in most cases is exactly
what is needed.  Set LVDSFixedMode to false and then the user has full
control over the resolution and timings sent to the LVDS-connected
device, through the usual means in xorg.
MULTIHEAD CONFIGURATIONS

The number of independent outputs is dictated by the number of CRTCs
(in X parlance) a given chip supports.  Most recent Intel chips have
two CRTCs, meaning that two separate framebuffers can be displayed
simultaneously, in an extended desktop configuration.  If a chip
supports more outputs than it has CRTCs (say local flat panel, VGA and
TV in the case of many outputs), two of the outputs will have to be
"cloned", meaning that they display the same framebuffer contents (or
one displays a subset of another's framebuffer if the modes aren't
equal).

You can use the "xrandr" tool, or various desktop utilities, to change
your output configuration at runtime.  To statically configure your
outputs, you can use the "Monitor-<type>" options along with
additional monitor sections in your xorg.conf to create your screen
topology.  The example below puts the VGA output to the right of the
builtin laptop screen, both running at 1024x768.

Section qMonitorq
  Identifier qLaptop FooBar Internal Displayq
  Option qPositionq q0 0q
EndSection

Section qMonitorq
  Identifier qSome Random CRTq
  Option qPositionq q1024 0q
  Option qRightOfq qLaptop FoodBar Internal Displayq
EndSection

Section qDeviceq
  Driver qintelq
  Option qmonitor-LVDSq qLaptop FooBar Internal Displayq
  Option qmonitor-VGAq qSome Random CRTq
EndSection
REPORTING BUGS

The xf86-video-intel driver is part of the X.Org and Freedesktop.org
umbrella projects.  Details on bug reporting can be found at
[http://www.intellinuxgraphics.org/how_to_report_bug.html](http://www.intellinuxgraphics.org/how_to_report_bug.html).  Mailing
lists are also commonly used to report experiences and ask questions
about configuration and other topics.  See lists.freedesktop.org for
more information (the [email]xorg@lists.freedesktop.org[/email] mailing list is the
most appropriate place to ask X.Org and driver related questions).
SEE ALSO

(1), (5), (1), (7)
AUTHORS

Authors include: Keith Whitwell, and also Jonathan Bian, Matthew J Sottek,
Jeff Hartmann, Mark Vojkovich, Alan Hourihane, H. J. Lu.  830M and 845G
support reworked for XFree86 4.3 by David Dawes and Keith Whitwell.  852GM,
855GM, and 865G support added by David Dawes and Keith Whitwell.  915G,
915GM, 945G, 945GM, 965G, 965Q and 946GZ support added by Alan Hourihane and
Keith Whitwell. Lid status support added by Alan Hourihane. Textured video
support for 915G and later chips, RandR 1.2 and hardware modesetting added
by Eric Anholt and Keith Packard. EXA and Render acceleration added by Wang
Zhenyu. TV out support added by Zou Nan Hai and Keith Packard. 965GM, G33,
Q33, and Q35 support added by Wang Zhenyu.
[/COLOR]

---

### Post by kd0afk on 2009-06-14
I did the "Safe" configuration as per [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
and it did the trick till I opened Blender a second time then it was back to the way it was. Time for the optimal thing.

---

### Post by kd0afk on 2009-06-15
Still no reply and I started this thread two days ago.

---

### Post by kd0afk on 2009-06-15
Bump

---

### Post by kd0afk on 2009-06-15
Here is my system information:

System information report, generated by Sysinfo: 6/15/2009 2:59:08 PM
[http://sourceforge.net/projects/gsysinfo](http://sourceforge.net/projects/gsysinfo)

SYSTEM INFORMATION
    Running Ubuntu Linux, the 5.0 release.
    GNOME: 2.26.1 (Ubuntu 2009-05-06)
    Kernel version: 2.6.28-11-generic (#42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009)
    GCC: 4.3.3 (i486-linux-gnu)
    Xorg: unknown (24 May 2009  12:33:40AM) (24 May 2009  12:33:40AM)
    Hostname: HAL
    Uptime: 0 days 0 h 33 min

CPU INFORMATION
    GenuineIntel, Intel(R) Celeron(R) M processor         1.50GHz
    Number of CPUs: 1
    CPU clock currently at 1496.269 MHz with 1024 KB cache
    Numbering: family(6) model(13) stepping(8)
    Bogomips: 2992.53
    Flags: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts

MEMORY INFORMATION
    Total memory: 481 MB
    Total swap: 1419 MB

STORAGE INFORMATION
    SCSI device -  scsi0
        Vendor:  ATA      
        Model:  HTS541040G9AT00  
    SCSI device -  scsi1
        Vendor:  MATSHITA 
        Model:  UJDA760 DVD/CDRW 

HARDWARE INFORMATION
MOTHERBOARD
    Host bridge
        Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
        Subsystem: Toshiba America Info Systems Device 0001
    PCI bridge(s)
        Intel Corporation 82801 Mobile PCI Bridge (rev 83)
        Intel Corporation 82801 Mobile PCI Bridge (rev 83)
    USB controller(s)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
        Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
        Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03) (prog-if 20)
    ISA bridge
        Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
    IDE interface
        Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems Device 0001

GRAPHIC CARD
    VGA controller
        Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
        Subsystem: Toshiba America Info Systems Device 0005

SOUND CARD
    Multimedia controller
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
        Subsystem: Toshiba America Info Systems Device 0412

NETWORK
    Ethernet controller
        Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
        Subsystem: Toshiba America Info Systems Device 0001
    Modem
        Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
        Subsystem: Toshiba America Info Systems Device 0001

---

### Post by kd0afk on 2009-06-16
HOLY FRIGGIN CRAP!!!!!!!!!!!!!!!!!
There isn't ONE person on this forum who even has a clue about how to make Blender work right?
That is pretty damn sad.

---

### Post by kd0afk on 2009-06-16
I figured it out. I typed metacity into the terminal and I got an error which said to try  " --replace". So I did and closed terminal and it didn't help. I did a search and there was one instance where someone posted about switching to metacity that you should use "metacity --replace &"
Evidently, if you don't put the "&" at the end of it, it will revert back to compiz when you close the terminal.
It works fine now.
Thanks for all the help though.

---

### Post by hardnrg on 2009-06-16
I'm extremely interested in the exact steps you took to resolve this...

Did you just do the Safe configuration, and then do the metacity command?

---

### Post by kd0afk on 2009-06-16
> **hardnrg said:**
> I'm extremely interested in the exact steps you took to resolve this...

Did you just do the Safe configuration, and then do the metacity command?

I tried the intel configuration tutorial all the way up to bleeding edge but it didn't do a thing so I undid everything. What worked was:
Open terminal.
Type in: "metacity --replace &"

Like I said, evidently the "&" keeps the change active after terminal is closed.

---

### Post by hardnrg on 2009-06-16
Tried reverting to 2.4 drivers -->  still ~1/3 lower part of blender 3D view not updating
I tried the Safe configuration, then metacity --> metacity error, same issue in Blender
reverted to original, then metacity --> metacity error, same issue in Blender
updated to Preview 2.8 --> extremely slow GUI throughout OS, but issue gone
reverted to 2.4 drivers --> issue gone, acceleration of GUI restored, no offset issues in Windowed or Fullscreen

I guess some part of the 2.8 driver package corrected the Blender 3D viewport updating issue, and then reverting to 2.4 drivers restored the hardware acceleration


For posterity:

Asus EeePC 1000H (Intel 945GME / GMA950)
Ubuntu 9.04 Netbook Remix

---

### Post by kd0afk on 2009-06-17
> **hardnrg said:**
> Tried reverting to 2.4 drivers -->  still ~1/3 lower part of blender 3D view not updating
I tried the Safe configuration, then metacity --> metacity error, same issue in Blender
reverted to original, then metacity --> metacity error, same issue in Blender
updated to Preview 2.8 --> extremely slow GUI throughout OS, but issue gone
reverted to 2.4 drivers --> issue gone, acceleration of GUI restored, no offset issues in Windowed or Fullscreen

I guess some part of the 2.8 driver package corrected the Blender 3D viewport updating issue, and then reverting to 2.4 drivers restored the hardware acceleration


For posterity:

Asus EeePC 1000H (Intel 945GME / GMA950)
Ubuntu 9.04 Netbook Remix

Try this:

code:
$ metacity --replace &

you need to have the "&" at the end of the metacity command to make it stick after the terminal is closed. If that doesn't work, I can't help you further, sorry. I am a new linux user and I am still learning about code and such. Good luck.

---

### Post by redradish on 2009-06-19
Woah, I have exactly the same problem it sounds- Blender runs fine, but the lower third of the 3D view and a teeny strip at the top aren't refreshing properly. I'm running an intel chipset, and just 'downgraded' to 2.4 too, which sorted out all my general performance problems I've been having but hasn't helped the refreshing story at all. 

hardnrg: Can you clarify what caused yours to work properly? I was running Blender 2.48a, and upgraded to 2.49, but there is no change. By 'Preview 2.8' do you mean your graphics driver? Cuz then it seems like we're at the same point. Except mine's not working :P Any ideas anyone?

Anyone know if there are any settings in blender dealing with refreshing?

Oh by the way, thanks for the hint about the "metacity --replace &" vibe, kd0afk, though for me I've just been using fusion-icon to switch between the two, which seems to do exactly the same thing, so it's not that

---

### Post by kd0afk on 2009-06-20
It may be that what worked for me was a combination of doing the bleeding edge intel thing, undoing it AND switching to metacity. I just don't know.
Wish you the best of luck though. Let me know if you find a solution.

---

### Post by Climb-nut on 2009-06-30
):P Hi, I had the same problem,

However I solved it differently then using metacity.

1) First of all I used the safe method of the bugtrack that you specified, [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) :p

2) Restarting my Jaunty 9.04 after the update did not change anything, still the same weird buttons on the display of blender.

3) Then I looked back to the ubuntu Xorg information and set DRI and Tiling option to false in my Xorg.conf. Suddenly all the buttons were normal and the mouse reacted perfectly.

Here is the device section of xorg.conf for my 855GM Intel card:
[COLOR=Lime]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "false"    
    Option        "DRI"                "false"
EndSection[/COLOR]

My computer specs:
Dell Inspiron 1150, Italian specs
1024 MB RAM
855GM Intel onboard graphics card

Hope this helps or maybe somebody else can use it to see what is wrong with Blender support

Greets Climb-nut

---

### Post by redradish on 2009-07-04
Ha! Thanks for your post Climb-nut, I followed your solution exactly (except I didn't do a full update in the Safe Configuration, I just installed the new driver file, cuz cap isn't plentiful), and blender works perfectly!!! The only problem is that now compiz seems to be broken: Ubuntu no longer starts up with compiz (maybe because of the script we set to run on start up?) and if I try to switch from metacity to compiz my whole screen goes completely white and I have to power off! Any ideas why this might be happening or why how I can fix it? 
At least blenders working :P
Thanks

---

### Post by redradish on 2009-07-05
Oh, and this would probably help, when I try run compiz through the terminal (just typing 'compiz') then the following is outputted:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

should I post anything from the log file?
:-\"

---

### Post by babygenius55 on 2009-07-25
> **Climb-nut said:**
> ):P Hi, I had the same problem,

However I solved it differently then using metacity.

1) First of all I used the safe method of the bugtrack that you specified, [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) :p

2) Restarting my Jaunty 9.04 after the update did not change anything, still the same weird buttons on the display of blender.

3) Then I looked back to the ubuntu Xorg information and set DRI and Tiling option to false in my Xorg.conf. Suddenly all the buttons were normal and the mouse reacted perfectly.

Here is the device section of xorg.conf for my 855GM Intel card:
[COLOR=Lime]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "false"    
    Option        "DRI"                "false"
EndSection[/COLOR]

My computer specs:
Dell Inspiron 1150, Italian specs
1024 MB RAM
855GM Intel onboard graphics card

Hope this helps or maybe somebody else can use it to see what is wrong with Blender support

Greets Climb-nut

     Hey there, I was having the refresh prob...You helped out alot Thanks a bunch. I did a combination of uninstalling the i7xx drivers(i had 2 sets of drivers for some reason) And adding The extra lines to my .conf file and the metacity line. Not sure if the metacity made a difference, but it sure didn't hurt anything. Worked like a beauty. I love you nerds. I aspire to be one someday.

Post Scriptum -- Also going to the proper drivers also made a small but very welcom difference throughout my sytem. For one thing when I had to input into text fields i.e. user name and password, the little dots that showed up are smaller.

I recommend follwing all of the advice here, if you have an acer aspire with an intel (crappy) Video chipset


OK, since about 20 minutes ago...I've been turning off/on the 'DRI' option (true/false)in the xorg.conf file in conjunction with laptop resets, and that seems to limit/open my ability to use enhanced effects for the system(System>Preferences>Appearance---->Visual Effects). When I have it false, I don't get all of the pretty windows morphs and what not(The system tells me it can't enable them or some such), but I can use blender without any refresh problems.  When it's true, wonderful eyecandy, but blender f's up with the refresh. I haven't touched the tiling yet, as there has been no real reason to, but I'm sure it's there for a reason.  i need someone way smarter than me to build a wall between general desktop usage, and OpenGL, or whatever Blender uses so that I can still have the eyecandy and impress my friends when I'm too drunk to use the terminal to go into gedit by using the up arrow *snicker*.  

I want the world to use linux.


Bring me a cup of Ubuntu...and a banana cognac b1tch.  Hope this doesn't offend too much.

---

### Post by nexes128 on 2009-10-22
> **Climb-nut said:**
> ):P Hi, I had the same problem,

However I solved it differently then using metacity.

1) First of all I used the safe method of the bugtrack that you specified, [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) :p

2) Restarting my Jaunty 9.04 after the update did not change anything, still the same weird buttons on the display of blender.

3) Then I looked back to the ubuntu Xorg information and set DRI and Tiling option to false in my Xorg.conf. Suddenly all the buttons were normal and the mouse reacted perfectly.

Here is the device section of xorg.conf for my 855GM Intel card:
[COLOR=Lime]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
    Option        "AccelMethod"            "uxa"
    Option        "EXAOptimizeMigration"        "true"
    Option        "MigrationHeuristic"        "greedy"
    Option        "Tiling"            "false"    
    Option        "DRI"                "false"
EndSection[/COLOR]

My computer specs:
Dell Inspiron 1150, Italian specs
1024 MB RAM
855GM Intel onboard graphics card

Hope this helps or maybe somebody else can use it to see what is wrong with Blender support

Greets Climb-nut

Thank you so much worked like a charm.
Recap:
I went to [https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)
and downloaded libdrm-intel1_2.4.15+git, xserver-xorg-core_1.6.3+git (xorg-server), and xserver-xorg-video-intel for my arch and installed, then i just cut and paste ur xorg config settings in my device config

---

