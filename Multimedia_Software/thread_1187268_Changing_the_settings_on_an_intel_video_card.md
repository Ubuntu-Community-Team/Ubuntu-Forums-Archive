---
title: "Changing the settings on an intel video card"
date: 2009-06-14
forum: Multimedia Software
---

### Post by kd0afk on 2009-06-14
How do I change the settings on my Intel video card? I would like to be able to change the acceleration, refresh rates, etc. I am getting no help with the Blender thing so I am taking a different approach to the problem. Maybe messing with the video card setttings will let me run Blender.

---

### Post by overdrank on 2009-06-14
> **kd0afk said:**
> How do I change the settings on my Intel video card? I would like to be able to change the acceleration, refresh rates, etc. I am getting no help with the Blender thing so I am taking a different approach to the problem. Maybe messing with the video card setttings will let me run Blender.

Hi and as you mentioned in your last thread if you are using Jaunty you may look at [Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")
You may also look in your bios to see how much memory is shared with the intel graphics.

---

### Post by kd0afk on 2009-06-14
Thanks for the reply.
I did check out the guide. One thing that scared me was the disclaimer:

[COLOR=Red]***Disclaimer:** Using a third-party kernel means that you will no longer have access to "restricted" drivers such as FGLRX, NVIDIA, some Broadcom wireless chipsets, certain webcams and a handful new sound cards that require restricted firmware to function. If you believe that you have restricted hardware on your machine, you should continue using the official Jaunty kernel - in other words, stick to the **Safe** configuration.

[COLOR=Black]I don't want to limit myself on options for drivers.

About checking the bios, is there a way to get into the bios check it and change it if needs be without a reboot? 
[/COLOR][/COLOR]

---

### Post by kd0afk on 2009-06-14
I went ahead and did the "safe" configuration and it seemed to do the trick till I opened Blender a second time and it was back to "normal" (messed up) I am going to try the optimal configuration.

---

### Post by kd0afk on 2009-06-14
I restarted my computer and got into the bios but it didn't give me any options for changing the memory allocation let alone even knowing what the memory allocation is.

---

### Post by kd0afk on 2009-06-14
I did notice that whatever I did, made my track pad really choppy.

---

### Post by kd0afk on 2009-06-15
Here is my system information.
I STILL need to know how to adjust the settings.
[SIZE=7]BUMP[/SIZE]

---

### Post by kd0afk on 2009-06-15
This is what I found in the documentation :lolflag: for Ubuntu when I typed "intel" into the search bar.
NOWHERE does it say how to get into the utility to use the commands listed in the article.

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
found). Some outputs have unique properties which are described below. See the "MULTIHEAD CONFIGURATIONS" section below for additional information.
VGA

VGA output port (typically exposed via an HD15 connector).
LVDS

Low Voltage Differential Signalling output (typically a laptop LCD panel).  Available properties:


BACKLIGHT
- current backlight level (adjustable)

By adjusting the BACKLIGHT property, the brightness on the LVDS output can be adjusted. In some cases, this property may be unavailable (for example if your platform uses an external microcontroller to control the backlight).


BACKLIGHT_CONTROL
- method used to control backlight

The driver will attempt to automatically detect the backlight control method for your platform. If this fails however, you can select another method which may allow you to control your backlight. Available methods include:


native

Intel chipsets include backlight control registers, which on some platforms may be wired to control the backlight directly. This method uses those registers.


legacy

The legacy backlight control registers exist in PCI configuration space, and have fewer available backlight levels than the native registers. However, some platforms are wired this way and so need to use this method.


combo

This method attempts to use the native registers where possible, resorting to the legacy, configuration space registers only to enable the backlight if needed. On platforms that have both wired this can be a good choice as it allows the fine grained backlight control of the native interface.


kernel

On some system, the kernel may provide a backlight control driver. In that case, using the kernel interfaces is preferable, as the same driver may respond to hotkey events or external APIs.


PANEL_FITTING
- control LCD panel fitting

By default, the driver will attempt to upscale resolutions smaller than the LCD's native size while preserving the aspect ratio. Other modes are available however:


center

Simply center the image on-screen, without scaling.


full_aspect

The default mode. Try to upscale the image to the screen size, while preserving aspect ratio. May result in letterboxing or pillar-boxing with some resolutions.


full

Upscale the image to the native screen size without regard to aspect ratio. In this mode, the full screen image may appear distorted in some resolutions.

TV

Integrated TV output.  Available properties include:


BOTTOM, RIGHT, TOP, LEFT
- margins

Adjusting these properties allows you to control the placement of your TV output buffer on the screen. The options with the same name can also be set in xorg.conf with integer value.


TV_FORMAT
- output standard

This property allows you to control the output standard used on your TV output port. You can select between NTSC-M, NTSC-443, NTSC-J, PAL-M, PAL-N, and PAL.

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
[http://www.intellinuxgraphics.org/ho...eport_bug.html]("http://www.intellinuxgraphics.org/how_to_report_bug.html").  Mailing
lists are also commonly used to report experiences and ask questions
about configuration and other topics.  See lists.freedesktop.org for
more information (the [EMAIL="xorg@lists.freedesktop.org"]xorg@lists.freedesktop.org[/EMAIL] mailing list is the
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

[COLOR=Black]Maybe someone has some insight on this.[/COLOR]
[/COLOR]

---

### Post by kd0afk on 2009-06-16
Could someone please help me with this?

---

