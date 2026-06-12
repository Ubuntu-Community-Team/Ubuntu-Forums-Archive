---
title: "New nvidia card mirroring dual monitors only, wont extend"
date: 2011-01-03
forum: Multimedia Software
---

### Post by apokkalyps on 2011-01-03
i am trying to use install my new nvidia gts 450 to do dual monitors on its dual DVI heads, on my karmic 9.10 install.  My problem is I can only get the monitors to mirror each other, instead of extending into the second space.

My onboard chip is nvidia and so the first thing I did was blow away all nvidia packages and reinstall them all.  Then I did nvidia-xconfig, and then ran nvidia-settings.  nvidia-settings has a layout display panel under "X Server Display Configuration".  Originally, even before trying to enable the other monitor, the layout panel showed two monitors side by side, with the right one disabled.  I tried twinview, and the screens mirrored each other.  Then I tried 'seperate x screens' restarted, and they were still mirrored.  I opened nvidia-settings again and now there is only one monitor at a time shown in the layout panel.  I can chose the other display device under the model dropbox in the lower right panel, and this will change the layout to show the other screen, but it wont show them both at the same time.  I dont know if this has to do with them being mirrored or not but it might be relevant.

Many people have told me to just go to preferences > Monitors and change the simple obvious setting.  But as far as i know, with an NVIDIA driver you have to use the ugly nvidia-settings app instead, where I can't find any obvious setting to make it mirror or not.  (also in 9.10 it would be pref > display not pref > monitors)

---

### Post by tjones00 on 2011-01-03
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.original

sudo nvidia-xconfig --xinerama --separate-x-screens --no-twinview

sudo reboot
```Should work.

Check ```
nvidia-xconfig -A
``` if it's still giving you issues maybe there is an option that will fix it.

Output from nvidia-xconfig -A.

```
nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13
07:06:38 PDT 2010
  The NVIDIA X Configuration Tool.

  This program is used to manipulate X configuration files, specifically to
  enable NVIDIA X driver functionality.

  Copyright (C) 2005 - 2010 NVIDIA Corporation.


  In its normal operation, nvidia-xconfig finds the system X configuration file
  (or generates a new X configuration if it cannot find the system file), makes
  sure the configuration is usable by the NVIDIA X driver, applies any updates
  requested on the commandline, and writes the new configuration to file.

  Please see the NVIDIA README for a description of NVIDIA X configuration file
  options.


nvidia-xconfig [options]

  -c XCONFIG, --xconfig=XCONFIG
      Use XCONFIG as the input X config file; if this option is not specified,
      then the same search path used by the X server will be used to find the X
      configuration file.

  -o OUTPUT-XCONFIG, --output-xconfig=OUTPUT-XCONFIG
      Use OUTPUT-XCONFIG as the output X configuration file; if this option is
      not specified, then the input X configuration filename will also be used
      as the output X configuration filename.

  -s, --silent
      Run silently; no messages will be printed to stdout, except for warning
      and error messages to stderr.

  -t, --tree
      Read the X configuration file, print to stdout the X configuration data
      in a tree format, and exit.

  -v, --version
      Print the nvidia-xconfig version and exit.

  -h, --help
      Print usage information for the common commandline options and exit.

  -A, --advanced-help
      Print usage information for the common commandline options as well as the
      advanced options, and then exit.

  --acpid-socket-path=ACPID-SOCKET-PATH, --no-acpid-socket-path
      Set this option to specify an alternate path to the Linux ACPI daemon
      (acpid)'s socket, which the NVIDIA X driver will use to connect to
      acpid.

  --add-argb-glx-visuals, --no-add-argb-glx-visuals
      Enables or disables support for OpenGL rendering into 32-bit ARGB windows
      and pixmaps.

  --allow-glx-with-composite, --no-allow-glx-with-composite
      Enable or disable the "AllowGLXWithComposite" X configuration option.

  --bandwidth-test, --no-bandwidth-test
      Disable or enable the "NoBandWidthTest" X configuration option.

  --busid=BUSID, --no-busid
      This option writes the specified BusID to the device section of the X
      configuration file.  If there are multiple device sections, then it adds
      the BusID field to each of them.  To add the BusID to only a specific
      device or screen section, use the '--device' or '--screen' options.

  --preserve-busid, --no-preserve-busid
      By default, nvidia-xconfig preserves the existing BusID in the X
      configuration file only if there are multiple X screens configured for
      the X server.  Use '--preserve-busid' or '--no-preserve-busid' to force
      the BusID to be preserved or not preserved, overriding the default
      behavior.

  --cool-bits=COOL-BITS, --no-cool-bits
      Enable or disable the "Coolbits" X configuration option.  Setting this
      option will enable support in the NV-CONTROL X extension for manipulating
      GPU clock and GPU fan control settings. Default value is 0.  For fan
      control set it to 4.  WARNING: this may cause system damage and void
      warranties.

  --composite, --no-composite
      Enable or disable the "Composite" X extension.

  --connected-monitor=CONNECTED-MONITOR, --no-connected-monitor
      Enable or disable the  "ConnectedMonitor" X configuration option; setting
      this option forces the X driver to behave as if the specified display
      devices are connected to the GPU.

  --connect-to-acpid, --no-connect-to-acpid
      Enable or disable the "ConnectToAcpid" X configuration option.  If this
      option is set, the NVIDIA X driver will attempt to connect to the Linux
      ACPI daemon (acpid).  Set this option to off to prevent the X driver from
      attempting to connect to acpid.

  --constant-dpi, --no-constant-dpi
      Enable or disable the "ConstantDPI" X configuration option, which
      controls whether the NVIDIA X driver maintains a constant dots per inch
      (DPI) value by recomputing the reported size in millimeters of the X
      screen when XRandR changes the size in pixels of the X screen.

  --custom-edid=CUSTOM-EDID, --no-custom-edid
      Enable or disable the  "CustomEDID" X configuration option; setting this
      option forces the X driver to use the EDID specified.This option is a
      semicolon-separated list of pairs of display device names and filename
      pairs; e.g "CRT-0:\tmp\edid.bin". Note that a display device name must
      always be specified even if only one EDID is specified. 

  --dac-8bit, --no-dac-8bit
      Most Quadro parts by default use a 10 bit color look up table (LUT) by
      default; setting this option to TRUE forces these graphics chips to use
      an 8 bit (LUT).

  -d DEPTH, --depth=DEPTH
      Set the default depth to DEPTH; valid values for DEPTH are 8, 15, 16, 24,
      and 30.

  --device=DEVICE
      The nvidia-xconfig utility operates on one or more devices in the X
      configuration file.  If this option is specified, the device named DEVICE
      in the X configuration file will be used.  If this option is not
      specified, all the devices within the X configuration file will be used.

  --disable-glx-root-clipping, --no-disable-glx-root-clipping
      Disable or enable clipping OpenGL rendering to the root window via the
      "DisableGLXRootClipping" X configuration option.

  --damage-events, --no-damage-events
      Use OS-level events to notify the X server when a direct-rendering client
      has performed rendering that needs to be composited to the screen. 
      Improves performance when using GLX with the composite extension.

  --dynamic-twinview, --no-dynamic-twinview
      Enable or disable support for dynamically configuring TwinView.

  --preserve-driver-name
      By default nvidia-xconfig changes the  display  driver  to "nvidia" for
      all configured X screens; this option preserves the existing driver name
      of each X screen.

  --enable-acpi-hotkeys, --no-enable-acpi-hotkeys
      The "EnableACPIHotkeys" option can be specified to override the NVIDIA X
      driver's default decision to enable or disable ACPI display change hotkey
      events.

  -a, --enable-all-gpus
      Configure an X screen on every GPU in the system.

  --exact-mode-timings-dvi, --no-exact-mode-timings-dvi
      Forces the initialization of the X server with the exact timings
      specified in the ModeLine.

  -E FILE, --extract-edids-from-file=FILE
      Extract any raw EDID byte blocks contained in the specified X log file
      LOG; raw EDID bytes are printed by the NVIDIA X driver to the X log as
      hexidecimal when verbose logging is enabled with the "-logverbose 6" X
      server commandline option.  Any extracted EDIDs are then written as
      binary data to individual files.  These files can later be used by the
      NVIDIA X driver through the "CustomEDID" X configuration option.

  --extract-edids-output-file=FILENAME
      When the '--extract-edids-from-file' option is used, nvidia-xconfig
      writes any extracted EDID to a file, typically "edid.bin" in the current
      directory.  Use this option to specify an alternate filename.  Note that
      nvidia-xconfig, if necessary, will append a unique number to the EDID
      filename, to avoid overwriting existing files (e.g., "edid.bin.1" if
      "edid.bin" already exists).

  --flatpanel-properties=FLATPANEL-PROPERTIES, --no-flatpanel-properties
      Set the flat panel properties. The supported properties are: 'scaling',
      'dithering' & 'ditheringmode'.  Please see the NVIDIA README 'Appendix B.
      X Config Options' for more details on the possible values and syntax.

  --flip, --no-flip
      Enable or disable OpenGL flipping

  --force-generate
      Force generation of a new X config file, ignoring any existing system X
      config file.  This is not typically recommended, as things like the mouse
      protocol, keyboard layout, font paths, etc, are setup by your Unix
      distribution.  While nvidia-xconfig can attempt to infer these values, it
      is best to use your Unix distribution's X config file for the basis of
      anything that nvidia-xconfig creates.

  --force-stereo-flipping, --no-force-stereo-flipping
      Normally, stereo flipping is only performed when a stereo drawable is
      visible. This option forces stereo flipping even when no stereo drawables
      are visible.

  --handle-special-keys=WHEN, --no-handle-special-keys
      Specify when the X server should use the builtin keyboard handler to
      process special key combinations (such as Ctrl+Alt+Backspace); see the X
      configuration man page for details.  The value of WHEN can be 'Always',
      'Never', or 'WhenNeeded'.

  --include-implicit-metamodes, --no-include-implicit-metamodes
      Enable or disable the "IncludeImplicitMetaModes" X configuration option.

  --keyboard=KEYBOARD
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use KEYBOARD as the keyboard type, rather than attempting to
      probe the system for the keyboard type.  For a list of possible keyboard
      types, see the '--keyboard-list' option.

  --keyboard-driver=DRIVER
      In most cases nvidia-xconfig can automatically determine the correct
      keyboard driver to use (either 'kbd' or 'keyboard'). Use this option to
      override what nvidia-xconfig detects. Typically, if you are using an
      X.Org X server, use 'kdb'; if you are using an XFree86 X server, use
      'keyboard'.

  --keyboard-list
      Print to stdout the available keyboard types recognized by the
      '--keyboard' option, and then exit.

  --layout=LAYOUT
      The nvidia-xconfig utility operates on a Server Layout within the X
      configuration file.  If this option is specified, the layout named LAYOUT
      in the X configuration file will be used.  If this option is not
      specified, the first Server Layout in the X configuration file is used.

  --logo, --no-logo
      Disable or enable the "NoLogo" X configuration option.

  --logo-path=PATH, --no-logo-path
      Set the path to the PNG file to be used as the logo splash screen at X
      server startup.

  --mode=MODE
      Add the specified mode to the mode list.

  --mode-debug, --no-mode-debug
      Enable or disable the "ModeDebug" X configuration option; when enabled,
      this option causes the X driver to print verbose details about mode
      validation to the X log file.

  --mode-list=MODELIST
      Remove all existing modes from the X configuration's modelist and add the
      one(s) specified in the MODELIST string.

  --remove-mode=MODE
      Remove the specified mode from the mode list.

  --metamodes=METAMODES
      Add the MetaMode X configuration option with the value METAMODES which
      will replace any existing MetaMode option already in the X configuration
      file.

  --mouse=MOUSE
      When generating a new X configuration file (which happens when no system
      X configuration file can be found, or the '--force-generate' option is
      specified), use MOUSE as the mouse type, rather than attempting to probe
      the system for the mouse type.  For a list of possible mouse types, see
      the '--mouse-list' option.

  --mouse-list
      Print to stdout the available mouse types recognized by the '--mouse'
      option, and then exit.

  --multigpu=MULTIGPU, --no-multigpu
      Enable or disable MultiGPU.  Valid values for MULTIGPU are 'Off', 'On',
      'Auto', 'AFR', 'SFR', 'AA'.

  --multisample-compatibility, --no-multisample-compatibility
      Enable or disable the use of separate front and back multisample
      buffers.

  --nvagp=NVAGP, --no-nvagp
      Set the NvAGP X config option value.  Possible values are 0 (no AGP), 1
      (NVIDIA's AGP), 2 (AGPGART), 3 (try AGPGART, then try NVIDIA's AGP);
      these values can also be specified as 'none', 'nvagp', 'agpgart', or
      'any'.

  --nvidia-cfg-path=PATH
      The nvidia-cfg library is used to communicate with the NVIDIA kernel
      module to query basic properties of every GPU in the system.  This
      library is typically only used by nvidia-xconfig when configuring
      multiple X screens.  This option tells nvidia-xconfig where to look for
      this library (in case it cannot find it on its own).  This option should
      normally not be needed.

  --only-one-x-screen
      Disable all but one X screen.

  --overlay, --no-overlay
      Enable or disable the "Overlay" X configuration option.

  --cioverlay, --no-cioverlay
      Enable or disable the color index overlay.

  --overlay-default-visual, --no-overlay-default-visual
      Enable or disable the "OverlayDefaultVisual" X configuration option.

  --transparent-index=INDEX, --no-transparent-index
      Pixel to use as transparent when using color index overlays.  Valid
      values for TRANSPARENT-INDEX are 0-255.

  -T, --post-tree
      Like the '--tree' option, but goes through the full process of applying
      any user requested updates to the X configuration, before printing the
      final configuration to stdout in a tree format.  Effectively, this option
      just causes the configuration to be printed to stdout as a tree instead
      of writing the results to file.

  --power-connector-check, --no-power-connector-check
      Disable or enable the "NoPowerConnectorCheck" X configuration option.

  --probe-all-gpus, --no-probe-all-gpus
      Disable or enable the "ProbeAllGpus" X configuration option.

  --query-gpu-info
      Print information about all recognized NVIDIA GPUs in the system.

  --randr-rotation, --no-randr-rotation
      Enable or disable the "RandRRotation" X configuration option.

  --registry-dwords=REGISTRY-DWORDS, --no-registry-dwords
      Enable or disable the "RegistryDwords" X configuration option.

  --render-accel, --no-render-accel
      Enable or disable the "RenderAccel" X configuration option.

  --render-extension, --no-render-extension
      Disable or enable the "NoRenderExtension" X configuration option.

  --rotate=ROTATE, --no-rotate
      Enable or disable the "Rotate" X configuration option.  Valid values for
      ROTATE are 'normal', 'left', 'CCW', 'inverted', 'right', and 'CW'. 
      Rotation can be disabled 

  --screen=SCREEN
      The nvidia-xconfig utility operates on one or more screens within a
      Server Layout in the X configuration file.  If this option is specified,
      the screen named SCREEN in the X configuration file will be used.  If
      this option is not specified, all screens within the selected Server
      Layout in the X configuration file will be used used.

  --separate-x-screens, --no-separate-x-screens
      A GPU that supports multiple simultaneous display devices can either
      drive these display devices in TwinView, or as separate X screens.  When
      the '--separate-x-screens' option is specified, each GPU on which an X
      screen is currently configured will be updated to have two X screens
      configured.  The '--no-separate-x-screens' option will remove the second
      configured X screen on each GPU.  Please see the NVIDIA README
      description of "Separate X Screens on One GPU" for further details.

  --sli=SLI, --no-sli
      Enable or disable SLI.  Valid values for SLI are 'Off', 'On', 'Auto',
      'AFR', 'SFR', 'AA', 'AFRofAA', 'Mosaic'.

  --stereo=STEREO, --no-stereo
      Enable or disable the stereo mode.  Valid values for STEREO are: 0
      (Disabled), 1 (DDC glasses), 2 (Blueline glasses), 3 (Onboard stereo), 4
      (TwinView clone mode stereo), 5 (SeeReal digital flat panel), 6 (Sharp3D
      digital flat panel), 7 (Arisawa/Hyundai/Zalman/Pavione/Miracube), 8 (3D
      DLP), 9 (3D DLP INV), 10 (NVIDIA 3D VISION).

  --thermal-configuration-check, --no-thermal-configuration-check
      Disable or enable the "ThermalConfigurationCheck" X configuration
      option.

  --tv-standard=TV-STANDARD, --no-tv-standard
      Enable or disable the "TVStandard" X configuration option. Valid values
      for "TVStandard" are: "PAL-B", "PAL-D", "PAL-G", "PAL-H", "PAL-I",
      "PAL-K1", "PAL-M", "PAL-N", "PAL-NC", "NTSC-J", "NTSC-M", "HD480i",
      "HD480p", "HD720p", "HD1080i", "HD1080p", "HD576i", "HD576p".

  --tv-out-format=TV-OUT-FORMAT, --no-tv-out-format
      Enable or disable the "TVOutFormat" X configuration option. Valid values
      for "TVOutFormat" are: "SVIDEO" and "COMPOSITE".

  --tv-over-scan=TV-OVER-SCAN, --no-tv-over-scan
      Enable or disable the "TVOverScan" X configuration option. Valid values
      are decimal values in the range 1.0 and 0.0.

  --twinview, --no-twinview
      Enable or disable TwinView.

  --twinview-orientation=ORIENTATION, --no-twinview-orientation
      Specify the TwinViewOrientation.  Valid values for ORIENTATION are:
      "RightOf" (the default), "LeftOf", "Above", "Below", or "Clone".

  --twinview-xinerama-info, --no-twinview-xinerama-info
      Prohibits providing Xinerama information when in TwinView.

  --twinview-xinerama-info-order=TWINVIEW-XINERAMA-INFO-ORDER,
  --no-twinview-xinerama-info-order
      Enable or disable the "TwinViewXineramaInfoOrder" X configuration option.
      TWINVIEW-XINERAMA-INFO-ORDER is a comma-separated list of display device
      names that describe the order in which TwinViewXineramaInfo should be
      reported.  E.g., "CRT, DFP, TV".

  --ubb, --no-ubb
      Enable or disable the "UBB" X configuration option.

  --use-edid, --no-use-edid
      Enable or disable use of the EDID (Extended Display Identification Data)
      from your display device(s).  The EDID will be used for driver operations
      such as building lists of available modes, determining valid frequency
      ranges, and computing the DPI (Dots Per Inch).  This option defaults to
      TRUE (the NVIDIA X driver will use the EDID, when available).  It is NOT
      recommended that you use this option to globally disable use of the EDID;
      instead, use '--no-use-edid-freqs' or '--no-use-edid-dpi' to disable
      specific uses of the EDID.

  --use-edid-dpi, --no-use-edid-dpi
      Enable or disable use of the physical size information in the display
      device's EDID, if any, to compute the DPI (Dots Per Inch) of the X
      screen.  This option defaults to TRUE (the NVIDIA X driver uses the
      EDID's physical size, when available, to compute the DPI).

  --use-edid-freqs, --no-use-edid-freqs
      Enable or disable use of the HorizSync and VertRefresh ranges given in a
      display device's EDID, if any.  EDID provided range information will
      override the HorizSync and VertRefresh ranges specified in the Monitor
      section.  This option defaults to TRUE (the NVIDIA X driver will use
      frequency information from the EDID, when available).

  --use-int10-module, --no-use-int10-module
      Enable use of the X Int10 module to soft-boot all secondary cards, rather
      than POSTing the cards through the NVIDIA kernel module.

  --use-display-device=DISPLAY-DEVICE, --no-use-display-device
      Force the X driver to use the display device specified.

  --use-events, --no-use-events
      Enable or disable "UseEvents" X configuration option. Setting this option
      will enable the X driver to use the system events in some cases when it
      is waiting for the hardware. With this option X driver sets an event
      handler and waits for the hardware through the poll() system call. This
      option defaults to FALSE.

  --virtual=WIDTHxHEIGHT, --no-virtual
      Specify the virtual screen resolution.

  --x-prefix=X-PREFIX
      The X installation prefix; the default is /usr/X11R6/.  Only under rare
      circumstances should this option be needed.

  --xinerama, --no-xinerama
      Enable or disable Xinerama.

  --xvmc-uses-textures, --no-xvmc-uses-textures
      Forces XvMC to use the 3D engine for XvMCPutSurface requests rather than
      the video overlay.

  --color-space=COLORSPACE, --no-color-space
      Enable or disable the "ColorSpace" X configuration option. Valid values
      for "COLORSPACE" are: "RGB" and "YCbCr444".

  --color-range=COLORRANGE, --no-color-range
      Sets the "ColorRange" X configuration option. Valid values for
      "COLORRANGE" are: "Full" and "Limited".

```

---

### Post by apokkalyps on 2011-01-06
Thanks tjones00! The manual enable of twinview and disable of the other is exactly what i needed.

---

