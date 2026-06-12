---
title: "&quot;module-&gt;open() failed, error -5&quot; with Quadro NVS 450 Ubuntu 14.04"
date: 2014-05-20
forum: Multimedia Software
---

### Post by Tesreb on 2014-05-20
I would like to connect 7 screens on my computer under Ubuntu 14.04 x86  Kernel: 3.13.0-24. For that I have 2 graphical cards (Nvidia Quadro NVS  450 Nvidia driver: 331.67, version 11). The first 4 screens are  correctly detected and configured and work well, but the last 3 screens  are not loaded (see kern.log) and doesn't work (Failed to initialize,  see Xorg log). There is always 4 screens correctly configured, even  though if I swap the BusID on the xorg.conf file; the last 3 screens  never work. Physically, all output cards and screens works well.

How can I configure my computer, especially the /etc/X11/xorg.cof or other config file to have 7 screens on 2 graphical cards ?

thanks for any ides...

/etc/X11/xorg.conf:
```

[LIST]
[*]Section "ServerLayout" 
[*]    Identifier "Default Layout" 
[*]    Screen 0 "Screen0" 0 0 
[*]    Screen 1 "Screen1" RightOf "Screen0" 
[*]    Screen 2 "Screen2" RightOf "Screen1" 
[*]    Screen 3 "Screen3" RightOf "Screen2" 
[*]    Screen 4 "Screen4" RightOf "Screen3" 
[*]    Screen 5 "Screen5" RightOf "Screen4" 
[*]    Screen 6 "Screen6" RightOf "Screen5" 
[*]    InputDevice "Keyboard0" "CoreKeyboard" 
[*]    InputDevice "Mouse0" "CorePointer" 
[*]    Option "Xinerama" "0" 
[*]    EndSection 
[*]    Section "Files" 
[*]    FontPath "/usr/share/fonts/ncd/fonts" # from Git config management 
[*]    EndSection 
[*]    Section "ServerFlags" 
[*]    Option "BlankTime" "10000" 
[*]    Option "StandbyTime" "10000" 
[*]    Option "SuspendTime" "10000" 
[*]    Option "OffTime" "10000" 
[*]    EndSection 
[*]    Section "InputDevice" 
[*]    # generated from default 
[*]    Identifier "Mouse0" 
[*]    Driver "mouse" 
[*]    Option "Protocol" "auto" 
[*]    Option "Device" "/dev/psaux" 
[*]    Option "Emulate3Buttons" "no" 
[*]    Option "ZAxisMapping" "4 5" 
[*]    EndSection 
[*]    Section "InputDevice" 
[*]    # generated from default 
[*]    Identifier "Keyboard0" 
[*]    Driver "keyboard" 
[*]    Option    "XkbLayout" "fr_CH" 
[*]    Option    "XkbModel" "pc105" 
[*]    EndSection 
[*]    Section "Modes" 
[*]    Identifier "Modes[0]" 
[*]    # ModeLine "640x480" 25.20 640 656 752 800 480 490 492 525 -hsync -vsync # Original from Fedora 14 server 
[*]    ModeLine "640x480" 23.26 640 656 720 800 480 481 484 497 -hsync -vsync # Calculated with 640x480 60Hz config 
[*]    EndSection 
[*]    Section "Monitor" 
[*]    # HorizSync source: edid, VertRefresh source: edid 
[*]    Identifier "Monitor0" 
[*]    VendorName "Unknown" 
[*]    ModelName "CRT 640x480" # TBD LCD 640x480 or ??? 
[*]    UseModes "Modes[0]" 
[*]    HorizSync 31.5 - 38.5 
[*]    VertRefresh 50.0 - 60.0 
[*]    Option "DPMS" 
[*]    EndSection 
[*]    Section "Monitor" 
[*]    # HorizSync source: edid, VertRefresh source: edid 
[*]    Identifier "Monitor1" 
[*]    VendorName "Unknown" 
[*]    ModelName "CRT 640x480" # TBD LCD 640x480 or ??? 
[*]    UseModes "Modes[0]" 
[*]    HorizSync 31.5 - 38.5 
[*]    VertRefresh 50.0 - 60.0 
[*]    Option "DPMS" 
[*]    EndSection 
[*]    Section "Monitor" 
[*]    # HorizSync source: edid, VertRefresh source: edid 
[*]    Identifier "Monitor2" 
[*]    VendorName "Unknown" 
[*]    ModelName "CRT 640x480" # TBD LCD 640x480 or ??? 
[*]    UseModes "Modes[0]" 
[*]    HorizSync 31.5 - 38.5 
[*]    VertRefresh 50.0 - 60.0 
[*]    Option "DPMS" 
[*]    EndSection 
[*]    Section "Monitor" 
[*]    # HorizSync source: edid, VertRefresh source: edid 
[*]    Identifier "Monitor3" 
[*]    VendorName "Unknown" 
[*]    ModelName "CRT 640x480" # TBD LCD 640x480 or ??? 
[*]    UseModes "Modes[0]" 
[*]    HorizSync 31.5 - 38.5 
[*]    VertRefresh 50.0 - 60.0 
[*]    Option "DPMS" 
[*]    EndSection 
[*]    Section "Monitor" 
[*]    # HorizSync source: edid, VertRefresh source: edid 
[*]    Identifier "Monitor4" 
[*]    VendorName "Unknown" 
[*]    ModelName "CRT 640x480" # TBD LCD 640x480 or ??? 
[*]    UseModes "Modes[0]" 
[*]    HorizSync 31.5 - 38.5 
[*]    VertRefresh 50.0 - 60.0 
[*]    Option "DPMS" 
[*]    EndSection 
[*]    Section "Monitor" 
[*]     # HorizSync source: edid, VertRefresh source: edid 
[*]     Identifier "Monitor5" 
[*]     VendorName "Unknown" 
[*]     ModelName "CRT 640x480" # TBD LCD 640x480 or ??? 
[*]     UseModes "Modes[0]" 
[*]     HorizSync 31.5 - 38.5 
[*]     VertRefresh 50.0 - 60.0 
[*]     Option "DPMS" 
[*]    EndSection 
[*]    Section "Monitor" 
[*]     # HorizSync source: edid, VertRefresh source: edid 
[*]     Identifier "Monitor6" 
[*]     VendorName "Unknown" 
[*]     ModelName "CRT 640x480" # TBD LCD 640x480 or ??? 
[*]     UseModes "Modes[0]" 
[*]     HorizSync 31.5 - 38.5 
[*]     VertRefresh 50.0 - 60.0 
[*]     Option "DPMS" 
[*]    EndSection 
[*]    Section "Device" 
[*]    Identifier "Device0" 
[*]    Driver "nvidia" 
[*]    VendorName "NVIDIA Corporation" 
[*]    BoardName "Quadro NVS 450" 
[*]    BusID "PCI:5:0:0" 
[*]    Screen 0 
[*]    EndSection 
[*]    Section "Device" 
[*]    Identifier "Device1" 
[*]    Driver "nvidia" 
[*]    VendorName "NVIDIA Corporation" 
[*]    BoardName "Quadro NVS 450" 
[*]    BusID "PCI:5:0:0" 
[*]    Screen 1 
[*]    EndSection 
[*]    Section "Device" 
[*]    Identifier "Device2" 
[*]    Driver "nvidia" 
[*]    VendorName "NVIDIA Corporation" 
[*]    BoardName "Quadro NVS 450" 
[*]    BusID "PCI:6:0:0" 
[*]    Screen 0 
[*]    EndSection 
[*]    Section "Device" 
[*]    Identifier "Device3" 
[*]    Driver "nvidia" 
[*]    VendorName "NVIDIA Corporation" 
[*]    BoardName "Quadro NVS 450" 
[*]    BusID "PCI:6:0:0" 
[*]    Screen 1 
[*]    EndSection 
[*]    Section "Device" 
[*]    Identifier "Device4" 
[*]    Driver "nvidia" 
[*]    VendorName "NVIDIA Corporation" 
[*]    BoardName "Quadro NVS 450" 
[*]    BusID "PCI:9:0:0" 
[*]    Screen 0 
[*]    EndSection 
[*]    Section "Device" 
[*]    Identifier "Device5" 
[*]    Driver "nvidia" 
[*]    VendorName "NVIDIA Corporation" 
[*]    BoardName "Quadro NVS 450" 
[*]    BusID "PCI:9:0:0" 
[*]    Screen 1 
[*]    EndSection 
[*]    Section "Device" 
[*]    Identifier "Device6" 
[*]    Driver "nvidia" 
[*]    VendorName "NVIDIA Corporation" 
[*]    BoardName "Quadro NVS 450" 
[*]    BusID "PCI:10:0:0" 
[*]    Screen 0 
[*]    EndSection 
[*]    Section "Screen" 
[*]    Identifier "Screen0" 
[*]    Device "Device0" 
[*]    Monitor "Monitor0" 
[*]    DefaultDepth 16 
[*]    Option "Stereo" "0" 
[*]    Option "metamodes" "640x480 +0+0" 
[*]    SubSection "Display" 
[*]    Depth 16 
[*]    Modes "640x480" 
[*]    EndSubSection 
[*]    EndSection 
[*]    Section "Screen" 
[*]    Identifier "Screen1" 
[*]    Device "Device1" 
[*]    Monitor "Monitor1" 
[*]    DefaultDepth 16 
[*]    Option "Stereo" "0" 
[*]    Option "metamodes" "640x480 +0+0" 
[*]    SubSection "Display" 
[*]    Depth 16 
[*]    Modes "640x480" 
[*]    EndSubSection 
[*]    EndSection 
[*]    Section "Screen" 
[*]    Identifier "Screen2" 
[*]    Device "Device2" 
[*]    Monitor "Monitor2" 
[*]    DefaultDepth 16 
[*]    Option "Stereo" "0" 
[*]    Option "metamodes" "640x480 +0+0" 
[*]    SubSection "Display" 
[*]    Depth 16 
[*]    Modes "640x480" 
[*]    EndSubSection 
[*]    EndSection 
[*]    Section "Screen" 
[*]    Identifier "Screen3" 
[*]    Device "Device3" 
[*]    Monitor "Monitor3" 
[*]    DefaultDepth 16 
[*]    Option "Stereo" "0" 
[*]    Option "metamodes" "640x480 +0+0" 
[*]    SubSection "Display" 
[*]    Depth 16 
[*]    Modes "640x480" 
[*]    EndSubSection 
[*]    EndSection 
[*]    Section "Screen" 
[*]    Identifier "Screen4" 
[*]    Device "Device4" 
[*]    Monitor "Monitor4" 
[*]    DefaultDepth 16 
[*]    Option "Stereo" "0" 
[*]    Option "metamodes" "640x480 +0+0" 
[*]    SubSection "Display" 
[*]    Depth 16 
[*]    Modes "640x480" 
[*]    EndSubSection 
[*]    EndSection 
[*]    Section "Screen" 
[*]    Identifier "Screen5" 
[*]    Device "Device5" 
[*]    Monitor "Monitor5" 
[*]    DefaultDepth 16 
[*]    Option "Stereo" "0" 
[*]    Option "metamodes" "640x480 +0+0" 
[*]    SubSection "Display" 
[*]    Depth 16 
[*]    Modes "640x480" 
[*]    EndSubSection 
[*]    EndSection 
[*]    Section "Screen" 
[*]    Identifier "Screen6" 
[*]    Device "Device6" 
[*]    Monitor "Monitor6" 
[*]    DefaultDepth 16 
[*]    Option "Stereo" "0" 
[*]    Option "metamodes" "640x480 +0+0" 
[*]    SubSection "Display" 
[*]    Depth 16 
[*]    Modes "640x480" 
[*]    EndSubSection 
[*]    EndSection 
[/LIST]

```

lspci:
```

[LIST]
[*]03:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a3) 
[*]    04:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a3) 
[*]    04:02.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a3) 
[*]    05:00.0 3D controller: NVIDIA Corporation G98 [Quadro NVS 450] (rev a1) 
[*]    06:00.0 VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 450] (rev a1) 
[*]    07:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a3) 
[*]    08:00.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a3) 
[*]    08:02.0 PCI bridge: NVIDIA Corporation NF200 PCIe 2.0 switch for Quadro Plex S4 / Tesla S870 / Tesla S1070 / Tesla S2050 (rev a3) 
[*]    09:00.0 3D controller: NVIDIA Corporation G98 [Quadro NVS 450] (rev a1) 
[*]    0a:00.0 VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 450] (rev a1) 
[/LIST]

```

log files:
```

[LIST]
[*][ 547.273] 
[*]    X.Org X Server 1.15.1 
[*]    Release Date: 2014-04-13 
[*]    [ 547.275] X Protocol Version 11, Revision 0 
[*]    [ 547.276] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu 
[*]    [ 547.279] Current Operating System: Linux toto-av-display 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 
[*]    [ 547.279] Kernel command line: BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7 
[*]    [ 547.282] Build Date: 16 April 2014 01:40:08PM 
[*]    [ 547.284] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see[URL="http://www.ubuntu.com/support%29"] http://www.ubuntu.com/support)
[/URL] 
[*]    [ 547.285] Current version of pixman: 0.30.2 
[*]    [ 547.287] Before reporting problems, check[ ]("http://wiki.x.org")[http://wiki.x.org](http://wiki.x.org) 
[*]    to make sure that you have the latest version. 
[*]    [ 547.287] Markers: (--) probed, (**) from config file, (==) default setting, 
[*]    (++) from command line, (!!) notice, (II) informational, 
[*]    (WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
[*]    [ 547.352] (==) Log file: "/var/log/Xorg.0.log", Time: Fri May 16 14:35:35 2014 
[*]    [ 547.389] (==) Using config file: "/etc/X11/xorg.conf" 
[*]    [ 547.421] (==) Using system config directory "/usr/share/X11/xorg.conf.d" 
[*]    [ 547.440] (==) ServerLayout "Default Layout" 
[*]    [ 547.440] (**) |-->Screen "Screen0" (0) 
[*]    [ 547.440] (**) | |-->Monitor "Monitor0" 
[*]    [ 547.450] (**) | |-->Device "Device0" 
[*]    [ 547.450] (**) |-->Screen "Screen1" (1) 
[*]    [ 547.450] (**) | |-->Monitor "Monitor1" 
[*]    [ 547.450] (**) | |-->Device "Device1" 
[*]    [ 547.450] (**) |-->Screen "Screen2" (2) 
[*]    [ 547.450] (**) | |-->Monitor "Monitor2" 
[*]    [ 547.450] (**) | |-->Device "Device2" 
[*]    [ 547.450] (**) |-->Screen "Screen3" (3) 
[*]    [ 547.450] (**) | |-->Monitor "Monitor3" 
[*]    [ 547.450] (**) | |-->Device "Device3" 
[*]    [ 547.450] (**) |-->Screen "Screen4" (4) 
[*]    [ 547.450] (**) | |-->Monitor "Monitor4" 
[*]    [ 547.450] (**) | |-->Device "Device4" 
[*]    [ 547.450] (**) |-->Input Device "Keyboard0" 
[*]    [ 547.450] (**) |-->Input Device "Mouse0" 
[*]    [ 547.451] (**) Option "BlankTime" "10000" 
[*]    [ 547.451] (**) Option "StandbyTime" "10000" 
[*]    [ 547.451] (**) Option "SuspendTime" "10000" 
[*]    [ 547.451] (**) Option "OffTime" "10000" 
[*]    [ 547.451] (**) Option "Xinerama" "0" 
[*]    [ 547.451] (==) Automatically adding devices 
[*]    [ 547.451] (==) Automatically enabling devices 
[*]    [ 547.451] (==) Automatically adding GPU devices 
[*]    [ 547.456] (WW) The directory "/usr/share/fonts/ncd/fonts" does not exist. 
[*]    [ 547.456] Entry deleted from font path. 
[*]    [ 547.467] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. 
[*]    [ 547.467] Entry deleted from font path. 
[*]    [ 547.467] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist. 
[*]    [ 547.467] Entry deleted from font path. 
[*]    [ 547.467] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist. 
[*]    [ 547.467] Entry deleted from font path. 
[*]    [ 547.474] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist. 
[*]    [ 547.475] Entry deleted from font path. 
[*]    [ 547.475] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist. 
[*]    [ 547.475] Entry deleted from font path. 
[*]    [ 547.475] (**) FontPath set to: 
[*]    /usr/share/fonts/X11/misc, 
[*]    /usr/share/fonts/X11/Type1, 
[*]    built-ins 
[*]    [ 547.475] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules" 
[*]    [ 547.475] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled. 
[*]    [ 547.475] (WW) Disabling Keyboard0 
[*]    [ 547.475] (WW) Disabling Mouse0 
[*]    [ 547.475] (II) Loader magic: 0xb77a16c0 
[*]    [ 547.475] (II) Module ABI versions: 
[*]    [ 547.475] X.Org ANSI C Emulation: 0.4 
[*]    [ 547.475] X.Org Video Driver: 15.0 
[*]    [ 547.475] X.Org XInput driver : 20.0 
[*]    [ 547.475] X.Org Server Extension : 8.0 
[*]    [ 547.475] (II) xfree86: Adding drm device (/dev/dri/card2) 
[*]    [ 547.475] (II) xfree86: Adding drm device (/dev/dri/card0) 
[*]    [ 547.475] (II) xfree86: Adding drm device (/dev/dri/card3) 
[*]    [ 547.475] (II) xfree86: Adding drm device (/dev/dri/card1) 
[*]    [ 547.478] (--) PCI: (0:5:0:0) 10de:06fa:10de:0619 rev 161, Mem @ 0xf0000000/16777216, 0xe4000000/67108864, 0xee000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072 
[*]    [ 547.478] (--) PCI:*(0:6:0:0) 10de:06fa:10de:0619 rev 161, Mem @ 0xec000000/16777216, 0xe0000000/67108864, 0xea000000/33554432, I/O @ 0x0000cf00/128, BIOS @ 0x????????/131072 
[*]    [ 547.478] (--) PCI: (0:9:0:0) 10de:06fa:10de:0619 rev 161, Mem @ 0xf8000000/16777216, 0xd8000000/67108864, 0xf6000000/33554432, I/O @ 0x0000bf00/128, BIOS @ 0x????????/131072 
[*]    [ 547.478] (--) PCI: (0:10:0:0) 10de:06fa:10de:0619 rev 161, Mem @ 0xf4000000/16777216, 0xd4000000/67108864, 0xf2000000/33554432, I/O @ 0x0000af00/128, BIOS @ 0x????????/131072 
[*]    [ 547.511] Initializing built-in extension Generic Event Extension 
[*]    [ 547.542] Initializing built-in extension SHAPE 
[*]    [ 547.572] Initializing built-in extension MIT-SHM 
[*]    [ 547.601] Initializing built-in extension XInputExtension 
[*]    [ 547.630] Initializing built-in extension XTEST 
[*]    [ 547.658] Initializing built-in extension BIG-REQUESTS 
[*]    [ 547.685] Initializing built-in extension SYNC 
[*]    [ 547.712] Initializing built-in extension XKEYBOARD 
[*]    [ 547.740] Initializing built-in extension XC-MISC 
[*]    [ 547.767] Initializing built-in extension SECURITY 
[*]    [ 547.794] Initializing built-in extension XINERAMA 
[*]    [ 547.820] Initializing built-in extension XFIXES 
[*]    [ 547.845] Initializing built-in extension RENDER 
[*]    [ 547.869] Initializing built-in extension RANDR 
[*]    [ 547.892] Initializing built-in extension COMPOSITE 
[*]    [ 547.913] Initializing built-in extension DAMAGE 
[*]    [ 547.933] Initializing built-in extension MIT-SCREEN-SAVER 
[*]    [ 547.953] Initializing built-in extension DOUBLE-BUFFER 
[*]    [ 547.971] Initializing built-in extension RECORD 
[*]    [ 547.988] Initializing built-in extension DPMS 
[*]    [ 548.005] Initializing built-in extension Present 
[*]    [ 548.021] Initializing built-in extension DRI3 
[*]    [ 548.036] Initializing built-in extension X-Resource 
[*]    [ 548.050] Initializing built-in extension XVideo 
[*]    [ 548.064] Initializing built-in extension XVideo-MotionCompensation 
[*]    [ 548.076] Initializing built-in extension SELinux 
[*]    [ 548.088] Initializing built-in extension XFree86-VidModeExtension 
[*]    [ 548.099] Initializing built-in extension XFree86-DGA 
[*]    [ 548.109] Initializing built-in extension XFree86-DRI 
[*]    [ 548.118] Initializing built-in extension DRI2 
[*]    [ 548.118] (II) LoadModule: "glx" 
[*]    [ 548.137] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so 
[*]    [ 548.713] (II) Module glx: vendor="NVIDIA Corporation" 
[*]    [ 548.713] compiled for 4.0.2, module version = 1.0.0 
[*]    [ 548.713] Module class: X.Org Server Extension 
[*]    [ 548.713] (II) NVIDIA GLX Module 331.67 Fri Apr 4 11:46:43 PDT 2014 
[*]    [ 548.722] Loading extension GLX 
[*]    [ 548.722] (II) LoadModule: "nvidia" 
[*]    [ 548.722] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so 
[*]    [ 548.776] (II) Module nvidia: vendor="NVIDIA Corporation" 
[*]    [ 548.776] compiled for 4.0.2, module version = 1.0.0 
[*]    [ 548.776] Module class: X.Org Video Driver 
[*]    [ 548.791] (II) NVIDIA dlloader X Driver 331.67 Fri Apr 4 11:25:22 PDT 2014 
[*]    [ 548.791] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs 
[*]    [ 548.792] (--) using VT number 8 
[*]    [ 548.848] (II) Loading sub module "fb" 
[*]    [ 548.848] (II) LoadModule: "fb" 
[*]    [ 548.854] (II) Loading /usr/lib/xorg/modules/libfb.so 
[*]    [ 548.861] (II) Module fb: vendor="X.Org Foundation" 
[*]    [ 548.861] compiled for 1.15.1, module version = 1.0.0 
[*]    [ 548.861] ABI class: X.Org ANSI C Emulation, version 0.4 
[*]    [ 548.861] (WW) Unresolved symbol: fbGetGCPrivateKey 
[*]    [ 548.861] (II) Loading sub module "wfb" 
[*]    [ 548.861] (II) LoadModule: "wfb" 
[*]    [ 548.862] (II) Loading /usr/lib/xorg/modules/libwfb.so 
[*]    [ 548.867] (II) Module wfb: vendor="X.Org Foundation" 
[*]    [ 548.867] compiled for 1.15.1, module version = 1.0.0 
[*]    [ 548.867] ABI class: X.Org ANSI C Emulation, version 0.4 
[*]    [ 548.867] (II) Loading sub module "ramdac" 
[*]    [ 548.867] (II) LoadModule: "ramdac" 
[*]    [ 548.867] (II) Module "ramdac" already built-in 
[*]    [ 548.880] (**) NVIDIA(0): Depth 16, (--) framebuffer bpp 16 
[*]    [ 548.880] (==) NVIDIA(0): RGB weight 565 
[*]    [ 548.880] (==) NVIDIA(0): Default visual is TrueColor 
[*]    [ 548.880] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0) 
[*]    [ 548.881] (**) NVIDIA(0): Option "Stereo" "0" 
[*]    [ 548.881] (**) NVIDIA(0): Stereo disabled by request 
[*]    [ 548.881] (**) NVIDIA(0): Option "MetaModes" "640x480 +0+0" 
[*]    [ 548.881] (**) NVIDIA(1): Option "MetaModes" "640x480 +0+0" 
[*]    [ 548.881] (**) NVIDIA(0): Enabling 2D acceleration 
[*]    [ 549.655] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102) 
[*]    [ 549.657] (II) NVIDIA(0): NVIDIA GPU Quadro NVS 450 (G98) at PCI:5:0:0 (GPU-0) 
[*]    [ 549.657] (--) NVIDIA(0): Memory: 262144 kBytes 
[*]    [ 549.657] (--) NVIDIA(0): VideoBIOS: 62.98.77.00.05 
[*]    [ 549.657] (II) NVIDIA(0): Detected PCI Express Link width: 16X 
[*]    [ 549.783] (II) NVIDIA(GPU-0): Display (DELL 1905FP (DFP-2)) does not support NVIDIA 3D 
[*]    [ 549.783] (II) NVIDIA(GPU-0): Vision stereo. 
[*]    [ 549.783] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (DFP-3)) does not support NVIDIA 
[*]    [ 549.783] (II) NVIDIA(GPU-0): 3D Vision stereo. 
[*]    [ 549.783] (--) NVIDIA(0): Valid display device(s) on Quadro NVS 450 at PCI:5:0:0 
[*]    [ 549.783] (--) NVIDIA(0): DFP-0 
[*]    [ 549.783] (--) NVIDIA(0): DFP-1 
[*]    [ 549.783] (--) NVIDIA(0): DELL 1905FP (DFP-2) (boot, connected) 
[*]    [ 549.783] (--) NVIDIA(0): Samsung SyncMaster (DFP-3) (connected) 
[*]    [ 549.783] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS 
[*]    [ 549.783] (--) NVIDIA(0): DFP-0: 165.0 MHz maximum pixel clock 
[*]    [ 549.783] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS 
[*]    [ 549.783] (--) NVIDIA(0): DFP-1: 165.0 MHz maximum pixel clock 
[*]    [ 549.783] (--) NVIDIA(0): DELL 1905FP (DFP-2): Internal DisplayPort 
[*]    [ 549.783] (--) NVIDIA(0): DELL 1905FP (DFP-2): 480.0 MHz maximum pixel clock 
[*]    [ 549.783] (--) NVIDIA(0): Samsung SyncMaster (DFP-3): Internal DisplayPort 
[*]    [ 549.783] (--) NVIDIA(0): Samsung SyncMaster (DFP-3): 480.0 MHz maximum pixel clock 
[*]    [ 549.783] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display 
[*]    [ 549.783] (**) NVIDIA(0): device DELL 1905FP (DFP-2) (Using EDID frequencies has 
[*]    [ 549.783] (**) NVIDIA(0): been enabled on all display devices.) 
[*]    [ 549.785] (II) NVIDIA(0): Validated MetaModes: 
[*]    [ 549.785] (II) NVIDIA(0): "640x480+0+0" 
[*]    [ 549.786] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480 
[*]    [ 549.791] (--) NVIDIA(0): DPI set to (42, 39); computed from "UseEdidDpi" X config 
[*]    [ 549.791] (--) NVIDIA(0): option 
[*]    [ 549.791] (**) NVIDIA(1): Depth 16, (--) framebuffer bpp 16 
[*]    [ 549.791] (==) NVIDIA(1): RGB weight 565 
[*]    [ 549.791] (==) NVIDIA(1): Default visual is TrueColor 
[*]    [ 549.791] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0) 
[*]    [ 549.791] (**) NVIDIA(1): Option "Stereo" "0" 
[*]    [ 549.791] (**) NVIDIA(1): Stereo disabled by request 
[*]    [ 549.791] (II) NVIDIA(1): NVIDIA GPU Quadro NVS 450 (G98) at PCI:5:0:0 (GPU-0) 
[*]    [ 549.791] (--) NVIDIA(1): Memory: 262144 kBytes 
[*]    [ 549.791] (--) NVIDIA(1): VideoBIOS: 62.98.77.00.05 
[*]    [ 549.791] (II) NVIDIA(1): Detected PCI Express Link width: 16X 
[*]    [ 549.911] (--) NVIDIA(1): Valid display device(s) on Quadro NVS 450 at PCI:5:0:0 
[*]    [ 549.911] (--) NVIDIA(1): DFP-0 
[*]    [ 549.911] (--) NVIDIA(1): DFP-1 
[*]    [ 549.911] (--) NVIDIA(1): DELL 1905FP (DFP-2) (boot, connected) 
[*]    [ 549.911] (--) NVIDIA(1): Samsung SyncMaster (DFP-3) (connected) 
[*]    [ 549.911] (--) NVIDIA(1): DFP-0: Internal Single Link TMDS 
[*]    [ 549.911] (--) NVIDIA(1): DFP-0: 165.0 MHz maximum pixel clock 
[*]    [ 549.911] (--) NVIDIA(1): DFP-1: Internal Single Link TMDS 
[*]    [ 549.911] (--) NVIDIA(1): DFP-1: 165.0 MHz maximum pixel clock 
[*]    [ 549.911] (--) NVIDIA(1): DELL 1905FP (DFP-2): Internal DisplayPort 
[*]    [ 549.911] (--) NVIDIA(1): DELL 1905FP (DFP-2): 480.0 MHz maximum pixel clock 
[*]    [ 549.911] (--) NVIDIA(1): Samsung SyncMaster (DFP-3): Internal DisplayPort 
[*]    [ 549.911] (--) NVIDIA(1): Samsung SyncMaster (DFP-3): 480.0 MHz maximum pixel clock 
[*]    [ 549.912] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display 
[*]    [ 549.912] (**) NVIDIA(1): device Samsung SyncMaster (DFP-3) (Using EDID frequencies 
[*]    [ 549.912] (**) NVIDIA(1): has been enabled on all display devices.) 
[*]    [ 549.915] (II) NVIDIA(1): Validated MetaModes: 
[*]    [ 549.915] (II) NVIDIA(1): "640x480+0+0" 
[*]    [ 549.915] (II) NVIDIA(1): Virtual screen size determined to be 640 x 480 
[*]    [ 549.921] (--) NVIDIA(1): DPI set to (42, 40); computed from "UseEdidDpi" X config 
[*]    [ 549.921] (--) NVIDIA(1): option 
[*]    [ 549.921] (**) NVIDIA(2): Depth 16, (--) framebuffer bpp 16 
[*]    [ 549.921] (==) NVIDIA(2): RGB weight 565 
[*]    [ 549.921] (==) NVIDIA(2): Default visual is TrueColor 
[*]    [ 549.921] (==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0) 
[*]    [ 549.921] (**) NVIDIA(2): Option "Stereo" "0" 
[*]    [ 549.921] (**) NVIDIA(2): Stereo disabled by request 
[*]    [ 549.921] (**) NVIDIA(2): Option "MetaModes" "640x480 +0+0" 
[*]    [ 549.921] (**) NVIDIA(3): Option "MetaModes" "640x480 +0+0" 
[*]    [ 549.921] (**) NVIDIA(2): Enabling 2D acceleration 
[*]    [ 550.682] (II) NVIDIA(GPU-1): Found DRM driver nvidia-drm (20130102) 
[*]    [ 550.684] (II) NVIDIA(2): NVIDIA GPU Quadro NVS 450 (G98) at PCI:6:0:0 (GPU-1) 
[*]    [ 550.684] (--) NVIDIA(2): Memory: 262144 kBytes 
[*]    [ 550.684] (--) NVIDIA(2): VideoBIOS: 62.98.77.00.05 
[*]    [ 550.684] (II) NVIDIA(2): Detected PCI Express Link width: 16X 
[*]    [ 550.790] (II) NVIDIA(GPU-1): Display (DELL E172FP (DFP-2)) does not support NVIDIA 3D 
[*]    [ 550.790] (II) NVIDIA(GPU-1): Vision stereo. 
[*]    [ 550.790] (II) NVIDIA(GPU-1): Display (DELL 1908FP (DFP-3)) does not support NVIDIA 3D 
[*]    [ 550.790] (II) NVIDIA(GPU-1): Vision stereo. 
[*]    [ 550.815] (--) NVIDIA(2): Valid display device(s) on Quadro NVS 450 at PCI:6:0:0 
[*]    [ 550.815] (--) NVIDIA(2): DFP-0 
[*]    [ 550.815] (--) NVIDIA(2): DFP-1 
[*]    [ 550.815] (--) NVIDIA(2): DELL E172FP (DFP-2) (boot, connected) 
[*]    [ 550.815] (--) NVIDIA(2): DELL 1908FP (DFP-3) (connected) 
[*]    [ 550.815] (--) NVIDIA(2): DFP-0: Internal Single Link TMDS 
[*]    [ 550.815] (--) NVIDIA(2): DFP-0: 165.0 MHz maximum pixel clock 
[*]    [ 550.815] (--) NVIDIA(2): DFP-1: Internal Single Link TMDS 
[*]    [ 550.815] (--) NVIDIA(2): DFP-1: 165.0 MHz maximum pixel clock 
[*]    [ 550.815] (--) NVIDIA(2): DELL E172FP (DFP-2): Internal DisplayPort 
[*]    [ 550.815] (--) NVIDIA(2): DELL E172FP (DFP-2): 480.0 MHz maximum pixel clock 
[*]    [ 550.815] (--) NVIDIA(2): DELL 1908FP (DFP-3): Internal DisplayPort 
[*]    [ 550.815] (--) NVIDIA(2): DELL 1908FP (DFP-3): 480.0 MHz maximum pixel clock 
[*]    [ 550.815] (**) NVIDIA(2): Using HorizSync/VertRefresh ranges from the EDID for display 
[*]    [ 550.815] (**) NVIDIA(2): device DELL E172FP (DFP-2) (Using EDID frequencies has 
[*]    [ 550.815] (**) NVIDIA(2): been enabled on all display devices.) 
[*]    [ 550.838] (II) NVIDIA(2): Validated MetaModes: 
[*]    [ 550.838] (II) NVIDIA(2): "640x480+0+0" 
[*]    [ 550.838] (II) NVIDIA(2): Virtual screen size determined to be 640 x 480 
[*]    [ 550.844] (--) NVIDIA(2): DPI set to (47, 45); computed from "UseEdidDpi" X config 
[*]    [ 550.844] (--) NVIDIA(2): option 
[*]    [ 550.844] (**) NVIDIA(3): Depth 16, (--) framebuffer bpp 16 
[*]    [ 550.844] (==) NVIDIA(3): RGB weight 565 
[*]    [ 550.844] (==) NVIDIA(3): Default visual is TrueColor 
[*]    [ 550.844] (==) NVIDIA(3): Using gamma correction (1.0, 1.0, 1.0) 
[*]    [ 550.844] (**) NVIDIA(3): Option "Stereo" "0" 
[*]    [ 550.844] (**) NVIDIA(3): Stereo disabled by request 
[*]    [ 550.844] (II) NVIDIA(3): NVIDIA GPU Quadro NVS 450 (G98) at PCI:6:0:0 (GPU-1) 
[*]    [ 550.844] (--) NVIDIA(3): Memory: 262144 kBytes 
[*]    [ 550.844] (--) NVIDIA(3): VideoBIOS: 62.98.77.00.05 
[*]    [ 550.844] (II) NVIDIA(3): Detected PCI Express Link width: 16X 
[*]    [ 550.965] (--) NVIDIA(3): Valid display device(s) on Quadro NVS 450 at PCI:6:0:0 
[*]    [ 550.965] (--) NVIDIA(3): DFP-0 
[*]    [ 550.965] (--) NVIDIA(3): DFP-1 
[*]    [ 550.965] (--) NVIDIA(3): DELL E172FP (DFP-2) (boot, connected) 
[*]    [ 550.965] (--) NVIDIA(3): DELL 1908FP (DFP-3) (connected) 
[*]    [ 550.965] (--) NVIDIA(3): DFP-0: Internal Single Link TMDS 
[*]    [ 550.965] (--) NVIDIA(3): DFP-0: 165.0 MHz maximum pixel clock 
[*]    [ 550.965] (--) NVIDIA(3): DFP-1: Internal Single Link TMDS 
[*]    [ 550.965] (--) NVIDIA(3): DFP-1: 165.0 MHz maximum pixel clock 
[*]    [ 550.965] (--) NVIDIA(3): DELL E172FP (DFP-2): Internal DisplayPort 
[*]    [ 550.965] (--) NVIDIA(3): DELL E172FP (DFP-2): 480.0 MHz maximum pixel clock 
[*]    [ 550.965] (--) NVIDIA(3): DELL 1908FP (DFP-3): Internal DisplayPort 
[*]    [ 550.965] (--) NVIDIA(3): DELL 1908FP (DFP-3): 480.0 MHz maximum pixel clock 
[*]    [ 550.965] (**) NVIDIA(3): Using HorizSync/VertRefresh ranges from the EDID for display 
[*]    [ 550.965] (**) NVIDIA(3): device DELL 1908FP (DFP-3) (Using EDID frequencies has 
[*]    [ 550.965] (**) NVIDIA(3): been enabled on all display devices.) 
[*]    [ 550.967] (II) NVIDIA(3): Validated MetaModes: 
[*]    [ 550.967] (II) NVIDIA(3): "640x480+0+0" 
[*]    [ 550.967] (II) NVIDIA(3): Virtual screen size determined to be 640 x 480 
[*]    [ 550.973] (--) NVIDIA(3): DPI set to (42, 40); computed from "UseEdidDpi" X config 
[*]    [ 550.973] (--) NVIDIA(3): option 
[*]    [ 550.973] (**) NVIDIA(4): Depth 16, (--) framebuffer bpp 16 
[*]    [ 550.973] (==) NVIDIA(4): RGB weight 565 
[*]    [ 550.973] (==) NVIDIA(4): Default visual is TrueColor 
[*]    [ 550.973] (==) NVIDIA(4): Using gamma correction (1.0, 1.0, 1.0) 
[*]    [ 550.973] (**) NVIDIA(4): Option "Stereo" "0" 
[*]    [ 550.973] (**) NVIDIA(4): Stereo disabled by request 
[*]    [ 550.973] (**) NVIDIA(4): Option "MetaModes" "640x480 +0+0" 
[*]    [ 550.973] (**) NVIDIA(4): Enabling 2D acceleration 
[*]    [ 550.974] (EE) NVIDIA(GPU-2): Failed to initialize the NVIDIA GPU at PCI:9:0:0. Please 
[*]    [ 550.974] (EE) NVIDIA(GPU-2): check your system's kernel log for additional error 
[*]    [ 550.974] (EE) NVIDIA(GPU-2): messages and refer to Chapter 8: Common Problems in the 
[*]    [ 550.974] (EE) NVIDIA(GPU-2): README for additional information. 
[*]    [ 550.974] (EE) NVIDIA(GPU-2): Failed to initialize the NVIDIA graphics device! 
[*]    [ 550.974] (EE) NVIDIA(4): Failing initialization of X screen 4 
[*]    [ 550.974] (II) UnloadModule: "nvidia" 
[*]    [ 550.974] (II) UnloadSubModule: "wfb" 
[*]    [ 550.974] (II) UnloadSubModule: "fb" 
[*]    [ 550.975] (EE) NVIDIA(GPU-3): Failed to initialize the NVIDIA GPU at PCI:10:0:0. Please 
[*]    [ 550.975] (EE) NVIDIA(GPU-3): check your system's kernel log for additional error 
[*]    [ 550.975] (EE) NVIDIA(GPU-3): messages and refer to Chapter 8: Common Problems in the 
[*]    [ 550.975] (EE) NVIDIA(GPU-3): README for additional information. 
[*]    [ 550.975] (EE) NVIDIA(GPU-3): Failed to initialize the NVIDIA graphics device! 
[*]    [ 550.976] (EE) NVIDIA(GPU-2): Failed to initialize the NVIDIA GPU at PCI:9:0:0. Please 
[*]    [ 550.976] (EE) NVIDIA(GPU-2): check your system's kernel log for additional error 
[*]    [ 550.976] (EE) NVIDIA(GPU-2): messages and refer to Chapter 8: Common Problems in the 
[*]    [ 550.976] (EE) NVIDIA(GPU-2): README for additional information. 
[*]    [ 550.976] (EE) NVIDIA(GPU-2): Failed to initialize the NVIDIA graphics device! 
[*]    [ 550.976] (II) NVIDIA(GPU-3): Deleting GPU-3 
[*]    [ 550.976] (II) NVIDIA(GPU-2): Deleting GPU-2 
[*]    [ 550.976] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access. 
[*]    [ 551.103] (II) NVIDIA(0): Setting mode "640x480+0+0" 
[*]    [ 551.153] Loading extension NV-GLX 
[*]    [ 551.195] (==) NVIDIA(0): Disabling shared memory pixmaps 
[*]    [ 551.195] (==) NVIDIA(0): Backing store enabled 
[*]    [ 551.195] (==) NVIDIA(0): Silken mouse enabled 
[*]    [ 551.196] (**) NVIDIA(0): DPMS enabled 
[*]    [ 551.196] Loading extension NV-CONTROL 
[*]    [ 551.196] (II) Loading sub module "dri2" 
[*]    [ 551.196] (II) LoadModule: "dri2" 
[*]    [ 551.196] (II) Module "dri2" already built-in 
[*]    [ 551.196] (II) NVIDIA(0): [DRI2] Setup complete 
[*]    [ 551.196] (II) NVIDIA(0): [DRI2] VDPAU driver: nvidia 
[*]    [ 551.196] (--) RandR disabled 
[*]    [ 551.201] (II) NVIDIA(1): Setting mode "640x480+0+0" 
[*]    [ 551.341] (==) NVIDIA(1): Disabling shared memory pixmaps 
[*]    [ 551.341] (==) NVIDIA(1): Backing store enabled 
[*]    [ 551.341] (==) NVIDIA(1): Silken mouse enabled 
[*]    [ 551.342] (**) NVIDIA(1): DPMS enabled 
[*]    [ 551.342] (II) Loading sub module "dri2" 
[*]    [ 551.342] (II) LoadModule: "dri2" 
[*]    [ 551.342] (II) Module "dri2" already built-in 
[*]    [ 551.342] (II) NVIDIA(1): [DRI2] Setup complete 
[*]    [ 551.342] (II) NVIDIA(1): [DRI2] VDPAU driver: nvidia 
[*]    [ 551.342] (--) RandR disabled 
[*]    [ 551.470] (II) NVIDIA(2): Setting mode "640x480+0+0" 
[*]    [ 551.536] (==) NVIDIA(2): Disabling shared memory pixmaps 
[*]    [ 551.536] (==) NVIDIA(2): Backing store enabled 
[*]    [ 551.536] (==) NVIDIA(2): Silken mouse enabled 
[*]    [ 551.537] (**) NVIDIA(2): DPMS enabled 
[*]    [ 551.537] (II) Loading sub module "dri2" 
[*]    [ 551.537] (II) LoadModule: "dri2" 
[*]    [ 551.537] (II) Module "dri2" already built-in 
[*]    [ 551.537] (II) NVIDIA(2): [DRI2] Setup complete 
[*]    [ 551.537] (II) NVIDIA(2): [DRI2] VDPAU driver: nvidia 
[*]    [ 551.537] (--) RandR disabled 
[*]    [ 551.542] (II) NVIDIA(3): Setting mode "640x480+0+0" 
[*]    [ 551.682] (==) NVIDIA(3): Disabling shared memory pixmaps 
[*]    [ 551.682] (==) NVIDIA(3): Backing store enabled 
[*]    [ 551.682] (==) NVIDIA(3): Silken mouse enabled 
[*]    [ 551.682] (**) NVIDIA(3): DPMS enabled 
[*]    [ 551.682] (II) Loading sub module "dri2" 
[*]    [ 551.682] (II) LoadModule: "dri2" 
[*]    [ 551.682] (II) Module "dri2" already built-in 
[*]    [ 551.682] (II) NVIDIA(3): [DRI2] Setup complete 
[*]    [ 551.682] (II) NVIDIA(3): [DRI2] VDPAU driver: nvidia 
[*]    [ 551.682] (--) RandR disabled 
[*]    [ 551.688] (II) SELinux: Disabled on system 
[*]    [ 551.689] (II) Initializing extension GLX 
[*]    [ 551.763] (II) XKB: generating xkmfile /tmp/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm 
[*]    [ 551.918] (II) config/udev: Adding input device Power Button (/dev/input/event1) 
[*]    [ 551.918] (**) Power Button: Applying InputClass "evdev keyboard catchall" 
[*]    [ 551.918] (II) LoadModule: "evdev" 
[*]    [ 551.918] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so 
[*]    [ 551.928] (II) Module evdev: vendor="X.Org Foundation" 
[*]    [ 551.928] compiled for 1.15.0, module version = 2.8.2 
[*]    [ 551.928] Module class: X.Org XInput Driver 
[*]    [ 551.928] ABI class: X.Org XInput driver, version 20.0 
[*]    [ 551.928] (II) Using input driver 'evdev' for 'Power Button' 
[*]    [ 551.928] (**) Power Button: always reports core events 
[*]    [ 551.928] (**) evdev: Power Button: Device: "/dev/input/event1" 
[*]    [ 551.928] (--) evdev: Power Button: Vendor 0 Product 0x1 
[*]    [ 551.928] (--) evdev: Power Button: Found keys 
[*]    [ 551.928] (II) evdev: Power Button: Configuring as keyboard 
[*]    [ 551.928] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1" 
[*]    [ 551.928] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6) 
[*]    [ 551.928] (**) Option "xkb_rules" "evdev" 
[*]    [ 551.928] (**) Option "xkb_model" "pc105" 
[*]    [ 551.928] (**) Option "xkb_layout" "ch" 
[*]    [ 551.928] (**) Option "xkb_variant" "fr" 
[*]    [ 551.929] (II) XKB: generating xkmfile /tmp/server-53A4CFD27CBE694B87E57086754C176B71A8EEB5.xkm 
[*]    [ 551.959] (II) config/udev: Adding input device Power Button (/dev/input/event0) 
[*]    [ 551.960] (**) Power Button: Applying InputClass "evdev keyboard catchall" 
[*]    [ 551.960] (II) Using input driver 'evdev' for 'Power Button' 
[*]    [ 551.960] (**) Power Button: always reports core events 
[*]    [ 551.960] (**) evdev: Power Button: Device: "/dev/input/event0" 
[*]    [ 551.960] (--) evdev: Power Button: Vendor 0 Product 0x1 
[*]    [ 551.960] (--) evdev: Power Button: Found keys 
[*]    [ 551.960] (II) evdev: Power Button: Configuring as keyboard 
[*]    [ 551.960] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0" 
[*]    [ 551.960] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7) 
[*]    [ 551.960] (**) Option "xkb_rules" "evdev" 
[*]    [ 551.960] (**) Option "xkb_model" "pc105" 
[*]    [ 551.960] (**) Option "xkb_layout" "ch" 
[*]    [ 551.960] (**) Option "xkb_variant" "fr" 
[*]    [ 551.960] (II) config/udev: Adding drm device (/dev/dri/card2) 
[*]    [ 551.960] (II) config/udev: Ignoring already known drm device (/dev/dri/card2) 
[*]    [ 551.960] (II) config/udev: Adding drm device (/dev/dri/card0) 
[*]    [ 551.960] (II) config/udev: Ignoring already known drm device (/dev/dri/card0) 
[*]    [ 551.960] (II) config/udev: Adding drm device (/dev/dri/card3) 
[*]    [ 551.960] (II) config/udev: Ignoring already known drm device (/dev/dri/card3) 
[*]    [ 551.960] (II) config/udev: Adding drm device (/dev/dri/card1) 
[*]    [ 551.960] (II) config/udev: Ignoring already known drm device (/dev/dri/card1) 
[*]    [ 551.960] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event2) 
[*]    [ 551.960] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall" 
[*]    [ 551.960] (II) Using input driver 'evdev' for 'Logitech USB-PS/2 Optical Mouse' 
[*]    [ 551.960] (**) Logitech USB-PS/2 Optical Mouse: always reports core events 
[*]    [ 551.960] (**) evdev: Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2" 
[*]    [ 551.960] (--) evdev: Logitech USB-PS/2 Optical Mouse: Vendor 0x46d Product 0xc03e 
[*]    [ 551.960] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons 
[*]    [ 551.960] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s) 
[*]    [ 551.960] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found relative axes 
[*]    [ 551.960] (--) evdev: Logitech USB-PS/2 Optical Mouse: Found x and y relative axes 
[*]    [ 551.960] (II) evdev: Logitech USB-PS/2 Optical Mouse: Configuring as mouse 
[*]    [ 551.960] (II) evdev: Logitech USB-PS/2 Optical Mouse: Adding scrollwheel support 
[*]    [ 551.960] (**) evdev: Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5 
[*]    [ 551.960] (**) evdev: Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200 
[*]    [ 551.960] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input3/event2" 
[*]    [ 551.960] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE, id 8) 
[*]    [ 551.960] (II) evdev: Logitech USB-PS/2 Optical Mouse: initialized for relative axes. 
[*]    [ 551.961] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1 
[*]    [ 551.961] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0 
[*]    [ 551.961] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000 
[*]    [ 551.961] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4 
[*]    [ 551.961] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0) 
[*]    [ 551.961] (II) No input driver specified, ignoring this device. 
[*]    [ 551.961] (II) This device may have been added with another device file. 
[*]    [ 551.961] (II) config/udev: Adding input device Dell Dell QuietKey Keyboard (/dev/input/event3) 
[*]    [ 551.961] (**) Dell Dell QuietKey Keyboard: Applying InputClass "evdev keyboard catchall" 
[*]    [ 551.961] (II) Using input driver 'evdev' for 'Dell Dell QuietKey Keyboard' 
[*]    [ 551.961] (**) Dell Dell QuietKey Keyboard: always reports core events 
[*]    [ 551.961] (**) evdev: Dell Dell QuietKey Keyboard: Device: "/dev/input/event3" 
[*]    [ 551.961] (--) evdev: Dell Dell QuietKey Keyboard: Vendor 0x413c Product 0x2106 
[*]    [ 551.961] (--) evdev: Dell Dell QuietKey Keyboard: Found keys 
[*]    [ 551.961] (II) evdev: Dell Dell QuietKey Keyboard: Configuring as keyboard 
[*]    [ 551.961] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input4/event3" 
[*]    [ 551.961] (II) XINPUT: Adding extended input device "Dell Dell QuietKey Keyboard" (type: KEYBOARD, id 9) 
[*]    [ 551.961] (**) Option "xkb_rules" "evdev" 
[*]    [ 551.961] (**) Option "xkb_model" "pc105" 
[*]    [ 551.961] (**) Option "xkb_layout" "ch" 
[*]    [ 551.961] (**) Option "xkb_variant" "fr" 
[*]    [ 551.961] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6) 
[*]    [ 551.961] (II) No input driver specified, ignoring this device. 
[*]    [ 551.961] (II) This device may have been added with another device file. 
[*]    [ 551.962] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5) 
[*]    [ 551.962] (II) No input driver specified, ignoring this device. 
[*]    [ 551.962] (II) This device may have been added with another device file. 
[*]    [ 551.962] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4) 
[*]    [ 551.962] (II) No input driver specified, ignoring this device. 
[*]    [ 551.962] (II) This device may have been added with another device file. 
[*]    [ 551.962] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11) 
[*]    [ 551.962] (II) No input driver specified, ignoring this device. 
[*]    [ 551.962] (II) This device may have been added with another device file. 
[*]    [ 551.962] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10) 
[*]    [ 551.962] (II) No input driver specified, ignoring this device. 
[*]    [ 551.962] (II) This device may have been added with another device file. 
[*]    [ 551.962] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9) 
[*]    [ 551.962] (II) No input driver specified, ignoring this device. 
[*]    [ 551.962] (II) This device may have been added with another device file. 
[*]    [ 551.962] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8) 
[*]    [ 551.962] (II) No input driver specified, ignoring this device. 
[*]    [ 551.962] (II) This device may have been added with another device file. 
[*]    [ 551.963] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7) 
[*]    [ 551.963] (II) No input driver specified, ignoring this device. 
[*]    [ 551.963] (II) This device may have been added with another device file. 
[/LIST]

```

kern.log
```
May 16 14:35:37 toto-av-display kernel: [ 548.748257] nvidia 0000:05:00.0: irq 55 for MSI/MSI-X

    May 16 14:35:38 toto-av-display kernel: [ 549.781739] nvidia 0000:06:00.0: irq 56 for MSI/MSI-X

    May 16 14:35:39 toto-av-display kernel: [ 550.833812] nvidia 0000:09:00.0: irq 57 for MSI/MSI-X

    May 16 14:35:39 toto-av-display kernel: [ 550.834355] NVRM: nvidia_frontend_open: minor 2, module->open() failed, error -5

    May 16 14:35:39 toto-av-display kernel: [ 550.834541] nvidia 0000:0a:00.0: irq 57 for MSI/MSI-X

    May 16 14:35:39 toto-av-display kernel: [ 550.835061] NVRM: nvidia_frontend_open: minor 3, module->open() failed, error -5

    May 16 14:35:39 toto-av-display kernel: [ 550.835163] nvidia 0000:09:00.0: irq 57 for MSI/MSI-X

    May 16 14:35:39 toto-av-display kernel: [ 550.835719] NVRM: nvidia_frontend_open: minor 2, module->open() failed, error -5


```

---

