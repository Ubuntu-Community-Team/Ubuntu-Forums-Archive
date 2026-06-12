---
title: "Six monitors under Ubuntu with NVidia and Intel"
date: 2012-06-01
forum: Multimedia Software
---

### Post by adw3345 on 2012-06-01
So I have a project that requires spanning a desktop across six monitors - I know, I know, the real question is not "How to get six monitors working" but actually "Why do you need six monitors?" Sadly the reasons are out of my hands, and I have been tasked to get six monitors working under Ubuntu 12. I am very close to success, my problem probably isn't a Ubuntu problem but hopefully some kind person will be able to point me to the right direction.
 
I am using a NVIDIA Quadra NVS 450 quad DisplayPort card to drive 4 monitors. By itself, this works flawlessly. No complaints here. My workspace spans 4 monitors and I can drag windows across screens. Perfect!
 
For the other two, I am using an Intel 3770k with Asus Sabertooth Z77 motherboard using the Intel drivers, which covers the i915 on-chip video. Using only this setup, I get a dual head workspace with my workspace spanning across both screens, using the on-motherboard DisplayPort and HDMI port. Excellent!
 
However, when I combine the two for a total of six screens, the NVIDIA displays work fine, but my Intel displays are cloned. Instead of my desktop spanning across 6 monitors, it spans across 5, with the 6th a clone of the 5th - Monitors 5 and 6 are driven by the Intel chip.
 
I know that there is some kind of cross-interference between the two graphics chips, but I've done a lot of experimentation and don't seem to be any closer to getting the tricky 6th monitor not to clone the 5th one.
 
I'm using Xinerama, mostly because it seems to work for the most part and I honestly don't know any better. If there's a better approach definitely would like to hear about it.
 
I'm attaching my xorg.conf file, as well as the Xorg.0.log file. No doubt I'm overlooking the obvious, so any hints are greatly appreciated!
 
Thanks-
 
Derrick
 
Xorg.conf file:
 
[FONT=Courier New]# nvidia-settings: version 295.53 (buildd@sandpaperfig) Wed May 16 23:15:27 UTC 2012[/FONT]
 
 
[FONT=Courier New]Section "ServerLayout"[/FONT]
[FONT=Courier New]Identifier "Layout0"[/FONT]
[FONT=Courier New]Screen 0 "Screen0" 0 0[/FONT]
[FONT=Courier New]Screen 1 "Screen1" RightOf "Screen0"[/FONT]
[FONT=Courier New]Screen 2 "Screen2" RightOf "Screen1"[/FONT]
[FONT=Courier New]Screen 3 "Screen3" Below "Screen0"[/FONT]
[FONT=Courier New]Screen 4 "Screen4" RightOf "Screen3"[/FONT]
[FONT=Courier New]Screen 5 "Screen5" RightOf "Screen4"[/FONT]
[FONT=Courier New]InputDevice "Keyboard0" "CoreKeyboard"[/FONT]
[FONT=Courier New]InputDevice "Mouse0" "CorePointer"[/FONT]
[FONT=Courier New]Option "Xinerama" "1"[/FONT]
[FONT=Courier New]Option "Clone" "off"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Files"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "ServerFlags"[/FONT]
[FONT=Courier New]Option "AIGLX" "off"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "InputDevice"[/FONT]
 
[FONT=Courier New]# generated from default[/FONT]
[FONT=Courier New]Identifier "Mouse0"[/FONT]
[FONT=Courier New]Driver "mouse"[/FONT]
[FONT=Courier New]Option "Protocol" "auto"[/FONT]
[FONT=Courier New]Option "Device" "/dev/psaux"[/FONT]
[FONT=Courier New]Option "Emulate3Buttons" "no"[/FONT]
[FONT=Courier New]Option "ZAxisMapping" "4 5"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "InputDevice"[/FONT]
 
[FONT=Courier New]# generated from default[/FONT]
[FONT=Courier New]Identifier "Keyboard0"[/FONT]
[FONT=Courier New]Driver "kbd"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Monitor"[/FONT]
[FONT=Courier New]Identifier "Monitor0"[/FONT]
[FONT=Courier New]VendorName "HP"[/FONT]
[FONT=Courier New]ModelName "HP LA2405"[/FONT]
[FONT=Courier New]HorizSync 24.0 - 76.0[/FONT]
[FONT=Courier New]VertRefresh 50.0 - 63.0[/FONT]
[FONT=Courier New]Option "DPMS"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Monitor"[/FONT]
[FONT=Courier New]Identifier "Monitor1"[/FONT]
[FONT=Courier New]VendorName "HP"[/FONT]
[FONT=Courier New]ModelName "HP LA2405"[/FONT]
[FONT=Courier New]HorizSync 24.0 - 76.0[/FONT]
[FONT=Courier New]VertRefresh 50.0 - 63.0[/FONT]
[FONT=Courier New]Option "DPMS"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Monitor"[/FONT]
[FONT=Courier New]Identifier "Monitor2"[/FONT]
[FONT=Courier New]VendorName "HP"[/FONT]
[FONT=Courier New]ModelName "HP LA2405"[/FONT]
[FONT=Courier New]HorizSync 24.0 - 76.0[/FONT]
[FONT=Courier New]VertRefresh 50.0 - 63.0[/FONT]
[FONT=Courier New]Option "DPMS"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Monitor"[/FONT]
[FONT=Courier New]Identifier "Monitor3"[/FONT]
[FONT=Courier New]VendorName "HP"[/FONT]
[FONT=Courier New]ModelName "HP LA2405"[/FONT]
[FONT=Courier New]HorizSync 24.0 - 76.0[/FONT]
[FONT=Courier New]VertRefresh 50.0 - 63.0[/FONT]
[FONT=Courier New]Option "DPMS"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Monitor"[/FONT]
[FONT=Courier New]Identifier "Monitor4"[/FONT]
[FONT=Courier New]VendorName "HP"[/FONT]
[FONT=Courier New]ModelName "HP LA2405"[/FONT]
[FONT=Courier New]HorizSync 24.0 - 76.0[/FONT]
[FONT=Courier New]VertRefresh 50.0 - 63.0[/FONT]
[FONT=Courier New]Option "DPMS"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Monitor"[/FONT]
[FONT=Courier New]Identifier "Monitor5"[/FONT]
[FONT=Courier New]VendorName "HP"[/FONT]
[FONT=Courier New]ModelName "HP LA2405"[/FONT]
[FONT=Courier New]HorizSync 24.0 - 76.0[/FONT]
[FONT=Courier New]VertRefresh 50.0 - 63.0[/FONT]
[FONT=Courier New]Option "DPMS"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Device"[/FONT]
[FONT=Courier New]Identifier "Device0"[/FONT]
[FONT=Courier New]Driver "nvidia"[/FONT]
[FONT=Courier New]VendorName "NVIDIA Corporation"[/FONT]
[FONT=Courier New]BoardName "Quadro NVS 450"[/FONT]
[FONT=Courier New]BusID "PCI:4:0:0"[/FONT]
[FONT=Courier New]Screen 0[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Device"[/FONT]
[FONT=Courier New]Identifier "Device1"[/FONT]
[FONT=Courier New]Driver "nvidia"[/FONT]
[FONT=Courier New]VendorName "NVIDIA Corporation"[/FONT]
[FONT=Courier New]BoardName "Quadro NVS 450"[/FONT]
[FONT=Courier New]BusID "PCI:4:0:0"[/FONT]
[FONT=Courier New]Screen 1[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Device"[/FONT]
[FONT=Courier New]Identifier "Device2"[/FONT]
[FONT=Courier New]Driver "nvidia"[/FONT]
[FONT=Courier New]VendorName "NVIDIA Corporation"[/FONT]
[FONT=Courier New]BoardName "Quadro NVS 450"[/FONT]
[FONT=Courier New]BusID "PCI:3:0:0"[/FONT]
[FONT=Courier New]Screen 0[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Device"[/FONT]
[FONT=Courier New]Identifier "Device3"[/FONT]
[FONT=Courier New]Driver "nvidia"[/FONT]
[FONT=Courier New]VendorName "NVIDIA Corporation"[/FONT]
[FONT=Courier New]BoardName "Quadro NVS 450"[/FONT]
[FONT=Courier New]BusID "PCI:3:0:0"[/FONT]
[FONT=Courier New]Screen 1[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Device"[/FONT]
[FONT=Courier New]Identifier "Device4"[/FONT]
[FONT=Courier New]Driver "intel"[/FONT]
[FONT=Courier New]VendorName "intel"[/FONT]
[FONT=Courier New]BoardName "intel"[/FONT]
[FONT=Courier New]BusID "PCI:0:2:0"[/FONT]
[FONT=Courier New]Option "monitor-HDMI2" "Monitor4"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Device"[/FONT]
[FONT=Courier New]Identifier "Device5"[/FONT]
[FONT=Courier New]Driver "intel"[/FONT]
[FONT=Courier New]VendorName "intel"[/FONT]
[FONT=Courier New]BoardName "intel"[/FONT]
[FONT=Courier New]BusID "PCI:0:2:0"[/FONT]
[FONT=Courier New]Option "monitor-DP1" "Monitor5"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Screen"[/FONT]
[FONT=Courier New]Identifier "Screen0"[/FONT]
[FONT=Courier New]Device "Device0"[/FONT]
[FONT=Courier New]Monitor "Monitor0"[/FONT]
[FONT=Courier New]DefaultDepth 24[/FONT]
[FONT=Courier New]Option "TwinView" "0"[/FONT]
[FONT=Courier New]Option "metamodes" "DFP-0: 1920x1200 +0+0"[/FONT]
[FONT=Courier New]SubSection "Display"[/FONT]
[FONT=Courier New]Depth 24[/FONT]
[FONT=Courier New]EndSubSection[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Screen"[/FONT]
[FONT=Courier New]Identifier "Screen1"[/FONT]
[FONT=Courier New]Device "Device1"[/FONT]
[FONT=Courier New]Monitor "Monitor1"[/FONT]
[FONT=Courier New]DefaultDepth 24[/FONT]
[FONT=Courier New]Option "TwinView" "0"[/FONT]
[FONT=Courier New]Option "metamodes" "DFP-1: 1920x1200 +0+0"[/FONT]
[FONT=Courier New]SubSection "Display"[/FONT]
[FONT=Courier New]Depth 24[/FONT]
[FONT=Courier New]EndSubSection[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Screen"[/FONT]
[FONT=Courier New]Identifier "Screen2"[/FONT]
[FONT=Courier New]Device "Device2"[/FONT]
[FONT=Courier New]Monitor "Monitor2"[/FONT]
[FONT=Courier New]DefaultDepth 24[/FONT]
[FONT=Courier New]Option "TwinView" "0"[/FONT]
[FONT=Courier New]Option "metamodes" "DFP-2: 1920x1200 +0+0"[/FONT]
[FONT=Courier New]SubSection "Display"[/FONT]
[FONT=Courier New]Depth 24[/FONT]
[FONT=Courier New]EndSubSection[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Screen"[/FONT]
[FONT=Courier New]Identifier "Screen3"[/FONT]
[FONT=Courier New]Device "Device3"[/FONT]
[FONT=Courier New]Monitor "Monitor3"[/FONT]
[FONT=Courier New]DefaultDepth 24[/FONT]
[FONT=Courier New]Option "TwinView" "0"[/FONT]
[FONT=Courier New]Option "metamodes" "DFP-3: 1920x1200 +0+0"[/FONT]
[FONT=Courier New]SubSection "Display"[/FONT]
[FONT=Courier New]Depth 24[/FONT]
[FONT=Courier New]EndSubSection[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
 
[FONT=Courier New]Section "Screen"[/FONT]
[FONT=Courier New]Identifier "Screen4"[/FONT]
[FONT=Courier New]Device "Device4"[/FONT]
[FONT=Courier New]Monitor "Monitor4"[/FONT]
[FONT=Courier New]DefaultDepth 24[/FONT]
[FONT=Courier New]Option "metamodes" "HDMI2: 1920x1200 +0+0"[/FONT]
[FONT=Courier New]SubSection "Display"[/FONT]
[FONT=Courier New]Depth 24[/FONT]
[FONT=Courier New]EndSubSection[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Screen"[/FONT]
[FONT=Courier New]Identifier "Screen5"[/FONT]
[FONT=Courier New]Device "Device5"[/FONT]
[FONT=Courier New]Monitor "Monitor5"[/FONT]
[FONT=Courier New]DefaultDepth 24[/FONT]
[FONT=Courier New]Option "metamodes" "DP1: 1920x1200 +0+0"[/FONT]
[FONT=Courier New]SubSection "Display"[/FONT]
[FONT=Courier New]Depth 24[/FONT]
[FONT=Courier New]EndSubSection[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
[FONT=Courier New]Section "Extensions"[/FONT]
[FONT=Courier New]Option "Composite" "Disable"[/FONT]
[FONT=Courier New]EndSection[/FONT]
 
 
Xorg.0.log file
 
[ 20.695] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[ 20.695] X Protocol Version 11, Revision 0
[ 20.695] Build Operating System: Linux 2.6.24-31-server i686 Ubuntu
[ 20.695] Current Operating System: Linux in-theroy-yes 3.2.0-24-generic-pae #39-Ubuntu SMP Mon May 21 18:54:21 UTC 2012 i686
[ 20.695] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-24-generic-pae root=UUID=b16d4611-ef14-4906-a8d6-a9d8e61f071c ro quiet splash vmalloc=192MB vt.handoff=7
[ 20.695] Build Date: 07 May 2012 11:39:37PM
[ 20.695] xorg-server 2:1.11.4-0ubuntu10.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[ 20.695] Current version of pixman: 0.24.4
[ 20.695] Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
[ 20.695] Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 20.695] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May 30 23:05:47 2012
[ 20.696] (==) Using config file: "/etc/X11/xorg.conf"
[ 20.696] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 20.696] (==) ServerLayout "Layout0"
[ 20.696] (**) |-->Screen "Screen0" (0)
[ 20.696] (**) | |-->Monitor "Monitor0"
[ 20.696] (**) | |-->Device "Device0"
[ 20.696] (**) |-->Screen "Screen1" (1)
[ 20.696] (**) | |-->Monitor "Monitor1"
[ 20.696] (**) | |-->Device "Device1"
[ 20.696] (**) |-->Screen "Screen2" (2)
[ 20.696] (**) | |-->Monitor "Monitor2"
[ 20.696] (**) | |-->Device "Device2"
[ 20.696] (**) |-->Screen "Screen3" (3)
[ 20.696] (**) | |-->Monitor "Monitor3"
[ 20.697] (**) | |-->Device "Device3"
[ 20.697] (**) |-->Screen "Screen4" (4)
[ 20.697] (**) | |-->Monitor "Monitor4"
[ 20.697] (**) | |-->Device "Device4"
[ 20.697] (**) |-->Screen "Screen5" (5)
[ 20.697] (**) | |-->Monitor "Monitor5"
[ 20.697] (**) | |-->Device "Device5"
[ 20.697] (**) |-->Input Device "Keyboard0"
[ 20.697] (**) |-->Input Device "Mouse0"
[ 20.697] (**) Option "Xinerama" "1"
[ 20.697] (**) Option "AIGLX" "off"
[ 20.697] (==) Automatically adding devices
[ 20.697] (==) Automatically enabling devices
[ 20.697] (**) Xinerama: enabled
[ 20.697] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 20.697] Entry deleted from font path.
[ 20.697] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 20.697] Entry deleted from font path.
[ 20.697] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 20.697] Entry deleted from font path.
[ 20.697] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 20.697] Entry deleted from font path.
[ 20.697] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 20.697] Entry deleted from font path.
[ 20.697] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[ 20.697] Entry deleted from font path.
[ 20.697] (==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/Type1,
built-ins
[ 20.697] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/
extra-modules,/usr/lib/xorg/modules"
[ 20.697] (**) Extension "Composite" is disabled
[ 20.697] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 20.697] (WW) Disabling Keyboard0
[ 20.697] (WW) Disabling Mouse0
[ 20.697] (II) Loader magic: 0xb77e65a0
[ 20.697] (II) Module ABI versions:
[ 20.697] X.Org ANSI C Emulation: 0.4
[ 20.697] X.Org Video Driver: 11.0
[ 20.697] X.Org XInput driver : 16.0
[ 20.697] X.Org Server Extension : 6.0
[ 20.698] (--) PCI: (0:0:2:0) 8086:0162:1043:84ca rev 9, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[ 20.698] (--) PCI: (0:3:0:0) 10de:06fa:10de:0619 rev 161, Mem @ 0xf6000000/16777216, 0xe4000000/67108864, 0xf4000000/33554432, I/O @ 0x0000c000/128, BIOS @ 0x????????/131072
[ 20.698] (--) PCI:*(0:4:0:0) 10de:06fa:10de:0619 rev 161, Mem @ 0xf2000000/16777216, 0xe0000000/67108864, 0xf0000000/33554432, I/O @ 0x0000b000/128, BIOS @ 0x????????/131072
[ 20.698] (II) Open ACPI successful (/var/run/acpid.socket)
[ 20.698] (II) LoadModule: "extmod"
[ 20.698] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[ 20.698] (II) Module extmod: vendor="X.Org Foundation"
[ 20.698] compiled for 1.11.3, module version = 1.0.0
[ 20.698] Module class: X.Org Server Extension
[ 20.698] ABI class: X.Org Server Extension, version 6.0
[ 20.698] (II) Loading extension MIT-SCREEN-SAVER
[ 20.698] (II) Loading extension XFree86-VidModeExtension
[ 20.698] (II) Loading extension XFree86-DGA
[ 20.698] (II) Loading extension DPMS
[ 20.698] (II) Loading extension XVideo
[ 20.698] (II) Loading extension XVideo-MotionCompensation
[ 20.698] (II) Loading extension X-Resource
[ 20.698] (II) LoadModule: "dbe"
[ 20.698] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[ 20.698] (II) Module dbe: vendor="X.Org Foundation"
[ 20.698] compiled for 1.11.3, module version = 1.0.0
[ 20.698] Module class: X.Org Server Extension
[ 20.698] ABI class: X.Org Server Extension, version 6.0
[ 20.698] (II) Loading extension DOUBLE-BUFFER
[ 20.698] (II) LoadModule: "glx"
[ 20.698] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[ 20.711] (II) Module glx: vendor="NVIDIA Corporation"
[ 20.711] compiled for 4.0.2, module version = 1.0.0
[ 20.711] Module class: X.Org Server Extension
[ 20.711] (II) NVIDIA GLX Module 295.53 Fri May 11 23:34:50 PDT 2012
[ 20.711] (II) Loading extension GLX
[ 20.711] (II) LoadModule: "record"
[ 20.711] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[ 20.711] (II) Module record: vendor="X.Org Foundation"
[ 20.711] compiled for 1.11.3, module version = 1.13.0
[ 20.711] Module class: X.Org Server Extension
[ 20.711] ABI class: X.Org Server Extension, version 6.0
[ 20.711] (II) Loading extension RECORD
[ 20.711] (II) LoadModule: "dri"
[ 20.711] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[ 20.711] (II) Module dri: vendor="X.Org Foundation"
[ 20.711] compiled for 1.11.3, module version = 1.0.0
[ 20.711] ABI class: X.Org Server Extension, version 6.0
[ 20.711] (II) Loading extension XFree86-DRI
[ 20.711] (II) LoadModule: "dri2"
[ 20.712] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 20.712] (II) Module dri2: vendor="X.Org Foundation"
[ 20.712] compiled for 1.11.3, module version = 1.2.0
[ 20.712] ABI class: X.Org Server Extension, version 6.0
[ 20.712] (II) Loading extension DRI2
[ 20.712] (II) LoadModule: "nvidia"
[ 20.712] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[ 20.712] (II) Module nvidia: vendor="NVIDIA Corporation"
[ 20.712] compiled for 4.0.2, module version = 1.0.0
[ 20.712] Module class: X.Org Video Driver
[ 20.712] (II) LoadModule: "intel"
[ 20.712] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 20.712] (II) Module intel: vendor="X.Org Foundation"
[ 20.712] compiled for 1.11.3, module version = 2.19.0
[ 20.712] Module class: X.Org Video Driver
[ 20.712] ABI class: X.Org Video Driver, version 11.0
[ 20.712] (II) NVIDIA dlloader X Driver 295.53 Fri May 11 23:14:53 PDT 2012
[ 20.712] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[ 20.712] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
Ivybridge Server (GT2)
[ 20.713] (++) using VT number 7
 
[ 20.713] (II) Loading sub module "fb"
[ 20.713] (II) LoadModule: "fb"
[ 20.713] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 20.713] (II) Module fb: vendor="X.Org Foundation"
[ 20.713] compiled for 1.11.3, module version = 1.0.0
[ 20.713] ABI class: X.Org ANSI C Emulation, version 0.4
[ 20.713] (II) Loading sub module "wfb"
[ 20.713] (II) LoadModule: "wfb"
[ 20.713] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 20.713] (II) Module wfb: vendor="X.Org Foundation"
[ 20.713] compiled for 1.11.3, module version = 1.0.0
[ 20.713] ABI class: X.Org ANSI C Emulation, version 0.4
[ 20.713] (II) Loading sub module "ramdac"
[ 20.713] (II) LoadModule: "ramdac"
[ 20.713] (II) Module "ramdac" already built-in
[ 20.713] (WW) NVIDIA: Xinerama is enabled, so RandR has likely been disabled by the
[ 20.713] (WW) NVIDIA: X server.
[ 20.713] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 20.713] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 20.713] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 20.713] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libwfb.so
[ 20.713] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 20.715] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 20.715] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[ 20.715] (==) NVIDIA(0): RGB weight 888
[ 20.715] (==) NVIDIA(0): Default visual is TrueColor
[ 20.715] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[ 20.715] (**) NVIDIA(0): Option "TwinView" "0"
[ 20.715] (**) NVIDIA(0): Option "MetaModes" "DFP-0: 1920x1200 +0+0"
[ 20.715] (**) NVIDIA(0): Enabling 2D acceleration
[ 21.491] (WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-2
[ 21.493] (II) NVIDIA(GPU-0): Display (HP LA2405 (DFP-2)) does not support NVIDIA 3D Vision
[ 21.493] (II) NVIDIA(GPU-0): stereo.
[ 21.494] (WW) NVIDIA(GPU-0): Unable to read EDID for display device DFP-3
[ 21.496] (II) NVIDIA(GPU-0): Display (HP LA2405 (DFP-3)) does not support NVIDIA 3D Vision
[ 21.496] (II) NVIDIA(GPU-0): stereo.
[ 21.498] (II) NVIDIA(0): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:4:0:0 (GPU-0)
[ 21.498] (--) NVIDIA(0): Memory: 262144 kBytes
[ 21.498] (--) NVIDIA(0): VideoBIOS: 62.98.77.00.05
[ 21.498] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[ 21.498] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[ 21.524] (--) NVIDIA(0): Connected display device(s) on Quadro NVS 450 at PCI:4:0:0
[ 21.524] (--) NVIDIA(0): HP LA2405 (DFP-2)
[ 21.524] (--) NVIDIA(0): HP LA2405 (DFP-3)
[ 21.524] (--) NVIDIA(0): HP LA2405 (DFP-2): 480.0 MHz maximum pixel clock
[ 21.524] (--) NVIDIA(0): HP LA2405 (DFP-2): Internal DisplayPort
[ 21.524] (--) NVIDIA(0): HP LA2405 (DFP-3): 480.0 MHz maximum pixel clock
[ 21.524] (--) NVIDIA(0): HP LA2405 (DFP-3): Internal DisplayPort
[ 21.524] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[ 21.524] (**) NVIDIA(0): device HP LA2405 (DFP-2) (Using EDID frequencies has been
[ 21.524] (**) NVIDIA(0): enabled on all display devices.)
[ 21.598] (II) NVIDIA(0): Assigned Display Device: DFP-2
[ 21.598] (WW) NVIDIA(0): Invalid display device in Mode Description
[ 21.598] (WW) NVIDIA(0): "DFP-0:1920x1200+0+0"
[ 21.598] (WW) NVIDIA(0): Not using mode description "DFP-0:1920x1200+0+0"; unable to
[ 21.598] (WW) NVIDIA(0): map to display device
[ 21.598] (==) NVIDIA(0): 
[ 21.598] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[ 21.598] (==) NVIDIA(0): will be used as the requested mode.
[ 21.598] (==) NVIDIA(0): 
[ 21.598] (II) NVIDIA(0): Validated modes:
[ 21.598] (II) NVIDIA(0): "nvidia-auto-select"
[ 21.598] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[ 21.603] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[ 21.603] (--) NVIDIA(0): option
[ 21.603] (**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
[ 21.603] (==) NVIDIA(1): RGB weight 888
[ 21.603] (==) NVIDIA(1): Default visual is TrueColor
[ 21.603] (==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
[ 21.603] (**) NVIDIA(1): Option "TwinView" "0"
[ 21.603] (**) NVIDIA(1): Option "MetaModes" "DFP-1: 1920x1200 +0+0"
[ 21.603] (II) NVIDIA(1): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:4:0:0 (GPU-0)
[ 21.603] (--) NVIDIA(1): Memory: 262144 kBytes
[ 21.603] (--) NVIDIA(1): VideoBIOS: 62.98.77.00.05
[ 21.603] (II) NVIDIA(1): Detected PCI Express Link width: 16X
[ 21.603] (--) NVIDIA(1): Interlaced video modes are supported on this GPU
[ 21.626] (--) NVIDIA(1): Connected display device(s) on Quadro NVS 450 at PCI:4:0:0
[ 21.626] (--) NVIDIA(1): HP LA2405 (DFP-2)
[ 21.626] (--) NVIDIA(1): HP LA2405 (DFP-3)
[ 21.626] (--) NVIDIA(1): HP LA2405 (DFP-2): 480.0 MHz maximum pixel clock
[ 21.626] (--) NVIDIA(1): HP LA2405 (DFP-2): Internal DisplayPort
[ 21.626] (--) NVIDIA(1): HP LA2405 (DFP-3): 480.0 MHz maximum pixel clock
[ 21.626] (--) NVIDIA(1): HP LA2405 (DFP-3): Internal DisplayPort
[ 21.627] (**) NVIDIA(1): Using HorizSync/VertRefresh ranges from the EDID for display
[ 21.627] (**) NVIDIA(1): device HP LA2405 (DFP-3) (Using EDID frequencies has been
[ 21.627] (**) NVIDIA(1): enabled on all display devices.)
[ 21.690] (II) NVIDIA(1): Assigned Display Device: DFP-3
[ 21.690] (WW) NVIDIA(1): Invalid display device in Mode Description
[ 21.690] (WW) NVIDIA(1): "DFP-1:1920x1200+0+0"
[ 21.690] (WW) NVIDIA(1): Not using mode description "DFP-1:1920x1200+0+0"; unable to
[ 21.690] (WW) NVIDIA(1): map to display device
[ 21.690] (==) NVIDIA(1): 
[ 21.690] (==) NVIDIA(1): No modes were requested; the default mode "nvidia-auto-select"
[ 21.690] (==) NVIDIA(1): will be used as the requested mode.
[ 21.690] (==) NVIDIA(1): 
[ 21.690] (II) NVIDIA(1): Validated modes:
[ 21.690] (II) NVIDIA(1): "nvidia-auto-select"
[ 21.690] (II) NVIDIA(1): Virtual screen size determined to be 1920 x 1200
[ 21.695] (WW) NVIDIA(1): Cannot find size of first mode for HP LA2405 (DFP-2); cannot
[ 21.695] (WW) NVIDIA(1): compute DPI from HP LA2405 (DFP-2)'s EDID.
[ 21.695] (==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
[ 21.695] (**) NVIDIA(2): Depth 24, (--) framebuffer bpp 32
[ 21.695] (==) NVIDIA(2): RGB weight 888
[ 21.695] (==) NVIDIA(2): Default visual is TrueColor
[ 21.695] (==) NVIDIA(2): Using gamma correction (1.0, 1.0, 1.0)
[ 21.695] (**) NVIDIA(2): Option "TwinView" "0"
[ 21.695] (**) NVIDIA(2): Option "MetaModes" "DFP-2: 1920x1200 +0+0"
[ 21.695] (**) NVIDIA(2): Enabling 2D acceleration
[ 21.977] (WW) NVIDIA(GPU-1): Unable to read EDID for display device DFP-2
[ 21.980] (II) NVIDIA(GPU-1): Display (HP LA2405 (DFP-2)) does not support NVIDIA 3D Vision
[ 21.980] (II) NVIDIA(GPU-1): stereo.
[ 21.980] (WW) NVIDIA(GPU-1): Unable to read EDID for display device DFP-3
[ 21.983] (II) NVIDIA(GPU-1): Display (HP LA2405 (DFP-3)) does not support NVIDIA 3D Vision
[ 21.983] (II) NVIDIA(GPU-1): stereo.
[ 21.985] (II) NVIDIA(2): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:3:0:0 (GPU-1)
[ 21.985] (--) NVIDIA(2): Memory: 262144 kBytes
[ 21.985] (--) NVIDIA(2): VideoBIOS: 62.98.77.00.05
[ 21.985] (II) NVIDIA(2): Detected PCI Express Link width: 16X
[ 21.985] (--) NVIDIA(2): Interlaced video modes are supported on this GPU
[ 22.011] (--) NVIDIA(2): Connected display device(s) on Quadro NVS 450 at PCI:3:0:0
[ 22.011] (--) NVIDIA(2): HP LA2405 (DFP-2)
[ 22.011] (--) NVIDIA(2): HP LA2405 (DFP-3)
[ 22.011] (--) NVIDIA(2): HP LA2405 (DFP-2): 480.0 MHz maximum pixel clock
[ 22.011] (--) NVIDIA(2): HP LA2405 (DFP-2): Internal DisplayPort
[ 22.011] (--) NVIDIA(2): HP LA2405 (DFP-3): 480.0 MHz maximum pixel clock
[ 22.011] (--) NVIDIA(2): HP LA2405 (DFP-3): Internal DisplayPort
[ 22.011] (II) NVIDIA(2): Display Device found referenced in MetaMode: DFP-2
[ 22.011] (**) NVIDIA(2): Using HorizSync/VertRefresh ranges from the EDID for display
[ 22.011] (**) NVIDIA(2): device HP LA2405 (DFP-2) (Using EDID frequencies has been
[ 22.011] (**) NVIDIA(2): enabled on all display devices.)
[ 22.079] (II) NVIDIA(2): Assigned Display Device: DFP-2
[ 22.079] (II) NVIDIA(2): Validated modes:
[ 22.079] (II) NVIDIA(2): "DFP-2:1920x1200+0+0"
[ 22.079] (II) NVIDIA(2): Virtual screen size determined to be 1920 x 1200
[ 22.084] (--) NVIDIA(2): DPI set to (93, 95); computed from "UseEdidDpi" X config
[ 22.084] (--) NVIDIA(2): option
[ 22.084] (**) NVIDIA(3): Depth 24, (--) framebuffer bpp 32
[ 22.084] (==) NVIDIA(3): RGB weight 888
[ 22.084] (==) NVIDIA(3): Default visual is TrueColor
[ 22.084] (==) NVIDIA(3): Using gamma correction (1.0, 1.0, 1.0)
[ 22.084] (**) NVIDIA(3): Option "TwinView" "0"
[ 22.084] (**) NVIDIA(3): Option "MetaModes" "DFP-3: 1920x1200 +0+0"
[ 22.084] (II) NVIDIA(3): NVIDIA GPU Quadro NVS 450 (G98GL) at PCI:3:0:0 (GPU-1)
[ 22.084] (--) NVIDIA(3): Memory: 262144 kBytes
[ 22.084] (--) NVIDIA(3): VideoBIOS: 62.98.77.00.05
[ 22.084] (II) NVIDIA(3): Detected PCI Express Link width: 16X
[ 22.084] (--) NVIDIA(3): Interlaced video modes are supported on this GPU
[ 22.107] (--) NVIDIA(3): Connected display device(s) on Quadro NVS 450 at PCI:3:0:0
[ 22.107] (--) NVIDIA(3): HP LA2405 (DFP-2)
[ 22.107] (--) NVIDIA(3): HP LA2405 (DFP-3)
[ 22.107] (--) NVIDIA(3): HP LA2405 (DFP-2): 480.0 MHz maximum pixel clock
[ 22.107] (--) NVIDIA(3): HP LA2405 (DFP-2): Internal DisplayPort
[ 22.107] (--) NVIDIA(3): HP LA2405 (DFP-3): 480.0 MHz maximum pixel clock
[ 22.107] (--) NVIDIA(3): HP LA2405 (DFP-3): Internal DisplayPort
[ 22.107] (II) NVIDIA(3): Display Device found referenced in MetaMode: DFP-3
[ 22.107] (**) NVIDIA(3): Using HorizSync/VertRefresh ranges from the EDID for display
[ 22.107] (**) NVIDIA(3): device HP LA2405 (DFP-3) (Using EDID frequencies has been
[ 22.107] (**) NVIDIA(3): enabled on all display devices.)
[ 22.175] (II) NVIDIA(3): Assigned Display Device: DFP-3
[ 22.175] (II) NVIDIA(3): Validated modes:
[ 22.175] (II) NVIDIA(3): "DFP-3:1920x1200+0+0"
[ 22.175] (II) NVIDIA(3): Virtual screen size determined to be 1920 x 1200
[ 22.181] (WW) NVIDIA(3): Cannot find size of first mode for HP LA2405 (DFP-2); cannot
[ 22.181] (WW) NVIDIA(3): compute DPI from HP LA2405 (DFP-2)'s EDID.
[ 22.181] (==) NVIDIA(3): DPI set to (75, 75); computed from built-in default
[ 22.181] drmOpenDevice: node name is /dev/dri/card0
[ 22.181] drmOpenDevice: open result is 20, (OK)
[ 22.181] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[ 22.181] drmOpenDevice: node name is /dev/dri/card0
[ 22.181] drmOpenDevice: open result is 20, (OK)
[ 22.181] drmOpenByBusid: drmOpenMinor returns 20
[ 22.181] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[ 22.181] (**) intel(4): Depth 24, (--) framebuffer bpp 32
[ 22.181] (==) intel(4): RGB weight 888
[ 22.181] (==) intel(4): Default visual is TrueColor
[ 22.181] (II) intel(4): Integrated Graphics Chipset: Intel(R) Ivybridge Desktop (GT2)
[ 22.181] (--) intel(4): Chipset: "Ivybridge Desktop (GT2)"
[ 22.181] (**) intel(4): Relaxed fencing enabled
[ 22.181] (**) intel(4): Wait on SwapBuffers? enabled
[ 22.181] (**) intel(4): Triple buffering? enabled
[ 22.181] (**) intel(4): Framebuffer tiled
[ 22.181] (**) intel(4): Pixmaps tiled
[ 22.181] (**) intel(4): 3D buffers tiled
[ 22.181] (**) intel(4): SwapBuffers wait enabled
[ 22.181] (==) intel(4): video overlay key set to 0x101fe
[ 22.181] (II) intel(4): Output VGA1 using monitor section Monitor4
[ 22.186] (II) intel(4): Output HDMI1 has no monitor section
[ 22.302] (II) intel(4): Output HDMI2 using monitor section Monitor4
[ 22.358] (II) intel(4): Output DP1 has no monitor section
[ 22.404] (II) intel(4): Output DP2 has no monitor section
[ 22.404] (II) intel(4): EDID for output VGA1
[ 22.408] (II) intel(4): EDID for output HDMI1
[ 22.525] (II) intel(4): EDID for output HDMI2
[ 22.525] (II) intel(4): Manufacturer: HWP Model: 284b Serial#: 16843009
[ 22.525] (II) intel(4): Year: 2012 Week: 4
[ 22.525] (II) intel(4): EDID Version: 1.3
[ 22.525] (II) intel(4): Digital Display Input
[ 22.525] (II) intel(4): Max Image Size [cm]: horiz.: 52 vert.: 32
[ 22.525] (II) intel(4): Gamma: 2.20
[ 22.525] (II) intel(4): DPMS capabilities: StandBy Suspend Off
[ 22.525] (II) intel(4): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[ 22.525] (II) intel(4): Default color space is primary color space
[ 22.525] (II) intel(4): First detailed timing is preferred mode
[ 22.525] (II) intel(4): redX: 0.650 redY: 0.337 greenX: 0.296 greenY: 0.604
[ 22.525] (II) intel(4): blueX: 0.147 blueY: 0.074 whiteX: 0.313 whiteY: 0.329
[ 22.525] (II) intel(4): Supported established timings:
[ 22.525] (II) intel(4): 640x480@60Hz
[ 22.525] (II) intel(4): 800x600@60Hz
[ 22.525] (II) intel(4): 1024x768@60Hz
[ 22.525] (II) intel(4): Manufacturer's mask: 0
[ 22.525] (II) intel(4): Supported standard timings:
[ 22.525] (II) intel(4): #0: hsize: 1280 vsize 960 refresh: 60 vid: 16513
[ 22.525] (II) intel(4): #1: hsize: 1280 vsize 1024 refresh: 60 vid: 32897
[ 22.525] (II) intel(4): #2: hsize: 1440 vsize 900 refresh: 60 vid: 149
[ 22.525] (II) intel(4): #3: hsize: 1600 vsize 1200 refresh: 60 vid: 16553
[ 22.525] (II) intel(4): #4: hsize: 1680 vsize 1050 refresh: 60 vid: 179
[ 22.525] (II) intel(4): #5: hsize: 1920 vsize 1080 refresh: 60 vid: 49361
[ 22.525] (II) intel(4): Supported detailed timing:
[ 22.525] (II) intel(4): clock: 154.0 MHz Image Size: 518 x 324 mm
[ 22.525] (II) intel(4): h_active: 1920 h_sync: 1968 h_sync_end 2000 h_blank_end 2080 h_border: 0
[ 22.525] (II) intel(4): v_active: 1200 v_sync: 1203 v_sync_end 1209 v_blanking: 1235 v_border: 0
[ 22.525] (II) intel(4): Ranges: V min: 50 V max: 63 Hz, H min: 24 H max: 76 kHz, PixClock max 175 MHz
[ 22.525] (II) intel(4): Monitor name: LA2405
[ 22.525] (II) intel(4): Serial No: CN420401Z7
[ 22.525] (II) intel(4): EDID (in hex):
[ 22.525] (II) intel(4): 00ffffffffffff0022f04b2801010101
[ 22.525] (II) intel(4): 0416010380342078ee9ec5a6564b9a25
[ 22.525] (II) intel(4): 135054210800814081809500a940b300
[ 22.525] (II) intel(4): d1c001010101283c80a070b023403020
[ 22.525] (II) intel(4): 360006442100001a000000fd00323f18
[ 22.525] (II) intel(4): 4c11000a202020202020000000fc004c
[ 22.525] (II) intel(4): 41323430350a202020202020000000ff
[ 22.525] (II) intel(4): 00434e3432303430315a370a202000e1
[ 22.525] (II) intel(4): Printing probed modes for output HDMI2
[ 22.525] (II) intel(4): Modeline "1920x1200"x60.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[ 22.525] (II) intel(4): Modeline "1600x1200"x60.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[ 22.525] (II) intel(4): Modeline "1680x1050"x60.0 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[ 22.525] (II) intel(4): Modeline "1280x1024"x60.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 22.525] (II) intel(4): Modeline "1440x900"x59.9 106.50 1440 1520 1672 1904 900 903 909 934 -hsync +vsync (55.9 kHz)
[ 22.525] (II) intel(4): Modeline "1280x960"x60.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)
[ 22.525] (II) intel(4): Modeline "1024x768"x60.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)
[ 22.525] (II) intel(4): Modeline "800x600"x60.3 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)
[ 22.525] (II) intel(4): Modeline "640x480"x60.0 25.20 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
[ 22.581] (II) intel(4): EDID for output DP1
[ 22.581] (II) intel(4): Manufacturer: HWP Model: 284c Serial#: 16843009
[ 22.581] (II) intel(4): Year: 2012 Week: 4
[ 22.581] (II) intel(4): EDID Version: 1.4
[ 22.581] (II) intel(4): Digital Display Input
[ 22.581] (II) intel(4): 8 bits per channel
[ 22.581] (II) intel(4): Digital interface is DisplayPort
[ 22.581] (II) intel(4): Max Image Size [cm]: horiz.: 52 vert.: 32
[ 22.581] (II) intel(4): Gamma: 2.20
[ 22.581] (II) intel(4): DPMS capabilities: Off
[ 22.581] (II) intel(4): Supported color encodings: RGB 4:4:4 
[ 22.581] (II) intel(4): First detailed timing is preferred mode
[ 22.581] (II) intel(4): Preferred mode is native pixel format and refresh rate
[ 22.581] (II) intel(4): redX: 0.650 redY: 0.337 greenX: 0.296 greenY: 0.604
[ 22.581] (II) intel(4): blueX: 0.147 blueY: 0.074 whiteX: 0.313 whiteY: 0.329
[ 22.581] (II) intel(4): Supported established timings:
[ 22.581] (II) intel(4): 640x480@60Hz
[ 22.581] (II) intel(4): 800x600@60Hz
[ 22.581] (II) intel(4): 1024x768@60Hz
[ 22.581] (II) intel(4): Manufacturer's mask: 0
[ 22.581] (II) intel(4): Supported standard timings:
[ 22.581] (II) intel(4): #0: hsize: 1280 vsize 960 refresh: 60 vid: 16513
[ 22.581] (II) intel(4): #1: hsize: 1280 vsize 1024 refresh: 60 vid: 32897
[ 22.581] (II) intel(4): #2: hsize: 1440 vsize 900 refresh: 60 vid: 149
[ 22.581] (II) intel(4): #3: hsize: 1600 vsize 1200 refresh: 60 vid: 16553
[ 22.581] (II) intel(4): #4: hsize: 1680 vsize 1050 refresh: 60 vid: 179
[ 22.581] (II) intel(4): #5: hsize: 1920 vsize 1080 refresh: 60 vid: 49361
[ 22.581] (II) intel(4): Supported detailed timing:
[ 22.581] (II) intel(4): clock: 154.0 MHz Image Size: 518 x 324 mm
[ 22.581] (II) intel(4): h_active: 1920 h_sync: 1968 h_sync_end 2000 h_blank_end 2080 h_border: 0
[ 22.581] (II) intel(4): v_active: 1200 v_sync: 1203 v_sync_end 1209 v_blanking: 1235 v_border: 0
[ 22.581] (II) intel(4): Ranges: V min: 50 V max: 63 Hz, H min: 24 H max: 76 kHz, PixClock max 175 MHz
[ 22.581] (II) intel(4): Monitor name: LA2405
[ 22.581] (II) intel(4): Serial No: CN420401YL
[ 22.581] (II) intel(4): EDID (in hex):
[ 22.581] (II) intel(4): 00ffffffffffff0022f04c2801010101
[ 22.581] (II) intel(4): 04160104a5342078229ec5a6564b9a25
[ 22.581] (II) intel(4): 135054210800814081809500a940b300
[ 22.581] (II) intel(4): d1c001010101283c80a070b023403020
[ 22.581] (II) intel(4): 360006442100001a000000fd00323f18
[ 22.581] (II) intel(4): 4c11000a202020202020000000fc004c
[ 22.581] (II) intel(4): 41323430350a202020202020000000ff
[ 22.581] (II) intel(4): 00434e343230343031594c0a20200072
[ 22.581] (II) intel(4): Printing probed modes for output DP1
[ 22.581] (II) intel(4): Modeline "1920x1200"x60.0 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[ 22.581] (II) intel(4): Modeline "1920x1080"x60.0 172.78 1920 2040 2248 2576 1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[ 22.581] (II) intel(4): Modeline "1600x1200"x60.0 162.00 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[ 22.581] (II) intel(4): Modeline "1680x1050"x60.0 146.25 1680 1784 1960 2240 1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[ 22.581] (II) intel(4): Modeline "1280x1024"x60.0 108.00 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[ 22.581] (II) intel(4): Modeline "1440x900"x59.9 106.50 1440 1520 1672 1904 900 903 909 934 -hsync +vsync (55.9 kHz)
[ 22.581] (II) intel(4): Modeline "1280x960"x60.0 108.00 1280 1376 1488 1800 960 961 964 1000 +hsync +vsync (60.0 kHz)
[ 22.581] (II) intel(4): Modeline "1024x768"x60.0 65.00 1024 1048 1184 1344 768 771 777 806 -hsync -vsync (48.4 kHz)
[ 22.581] (II) intel(4): Modeline "800x600"x60.3 40.00 800 840 968 1056 600 601 605 628 +hsync +vsync (37.9 kHz)
[ 22.581] (II) intel(4): Modeline "640x480"x60.0 25.20 640 656 752 800 480 490 492 525 -hsync -vsync (31.5 kHz)
[ 22.628] (II) intel(4): EDID for output DP2
[ 22.628] (II) intel(4): Output VGA1 disconnected
[ 22.628] (II) intel(4): Output HDMI1 disconnected
[ 22.628] (II) intel(4): Output HDMI2 connected
[ 22.628] (II) intel(4): Output DP1 connected
[ 22.628] (II) intel(4): Output DP2 disconnected
[ 22.628] (II) intel(4): Using exact sizes for initial modes
[ 22.628] (II) intel(4): Output HDMI2 using initial mode 1920x1200
[ 22.628] (II) intel(4): Output DP1 using initial mode 1920x1200
[ 22.628] (II) intel(4): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[ 22.628] (II) intel(4): Kernel page flipping support detected, enabling
[ 22.628] (==) intel(4): DPI set to (96, 96)
[ 22.628] (II) Loading sub module "fb"
[ 22.628] (II) LoadModule: "fb"
[ 22.628] (II) Loading /usr/lib/xorg/modules/libfb.so
[ 22.628] (II) Module fb: vendor="X.Org Foundation"
[ 22.628] compiled for 1.11.3, module version = 1.0.0
[ 22.628] ABI class: X.Org ANSI C Emulation, version 0.4
[ 22.628] (II) Loading sub module "dri2"
[ 22.628] (II) LoadModule: "dri2"
[ 22.628] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 22.628] (II) Module dri2: vendor="X.Org Foundation"
[ 22.628] compiled for 1.11.3, module version = 1.2.0
[ 22.628] ABI class: X.Org Server Extension, version 6.0
[ 22.628] (--) Depth 24 pixmap format is 32 bpp
[ 22.628] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[ 22.655] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[ 22.695] (II) Loading extension NV-GLX
[ 22.723] (==) NVIDIA(0): Disabling shared memory pixmaps
[ 22.723] (==) NVIDIA(0): Backing store disabled
[ 22.723] (==) NVIDIA(0): Silken mouse enabled
[ 22.723] (**) NVIDIA(0): DPMS enabled
[ 22.723] (II) Loading extension NV-CONTROL
[ 22.724] (II) Loading sub module "dri2"
[ 22.724] (II) LoadModule: "dri2"
[ 22.724] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 22.724] (II) Module dri2: vendor="X.Org Foundation"
[ 22.724] compiled for 1.11.3, module version = 1.2.0
[ 22.724] ABI class: X.Org Server Extension, version 6.0
[ 22.724] (II) NVIDIA(0): [DRI2] Setup complete
[ 22.724] (II) NVIDIA(0): [DRI2] VDPAU driver: nvidia
[ 22.724] (==) RandR enabled
[ 22.728] (II) NVIDIA(1): Setting mode "nvidia-auto-select"
[ 22.821] (==) NVIDIA(1): Disabling shared memory pixmaps
[ 22.821] (==) NVIDIA(1): Backing store disabled
[ 22.821] (==) NVIDIA(1): Silken mouse enabled
[ 22.821] (**) NVIDIA(1): DPMS enabled
[ 22.821] (II) Loading sub module "dri2"
[ 22.821] (II) LoadModule: "dri2"
[ 22.821] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 22.821] (II) Module dri2: vendor="X.Org Foundation"
[ 22.821] compiled for 1.11.3, module version = 1.2.0
[ 22.821] ABI class: X.Org Server Extension, version 6.0
[ 22.821] (II) NVIDIA(1): [DRI2] Setup complete
[ 22.821] (II) NVIDIA(1): [DRI2] VDPAU driver: nvidia
[ 22.821] (==) RandR enabled
[ 22.849] (II) NVIDIA(2): Setting mode "DFP-2:1920x1200+0+0"
[ 22.915] (==) NVIDIA(2): Disabling shared memory pixmaps
[ 22.915] (==) NVIDIA(2): Backing store disabled
[ 22.915] (==) NVIDIA(2): Silken mouse enabled
[ 22.915] (**) NVIDIA(2): DPMS enabled
[ 22.915] (II) Loading sub module "dri2"
[ 22.915] (II) LoadModule: "dri2"
[ 22.915] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 22.915] (II) Module dri2: vendor="X.Org Foundation"
[ 22.915] compiled for 1.11.3, module version = 1.2.0
[ 22.915] ABI class: X.Org Server Extension, version 6.0
[ 22.916] (II) NVIDIA(2): [DRI2] Setup complete
[ 22.916] (II) NVIDIA(2): [DRI2] VDPAU driver: nvidia
[ 22.916] (==) RandR enabled
[ 22.920] (II) NVIDIA(3): Setting mode "DFP-3:1920x1200+0+0"
[ 23.015] (==) NVIDIA(3): Disabling shared memory pixmaps
[ 23.015] (==) NVIDIA(3): Backing store disabled
[ 23.015] (==) NVIDIA(3): Silken mouse enabled
[ 23.015] (**) NVIDIA(3): DPMS enabled
[ 23.015] (II) Loading sub module "dri2"
[ 23.015] (II) LoadModule: "dri2"
[ 23.015] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[ 23.015] (II) Module dri2: vendor="X.Org Foundation"
[ 23.015] compiled for 1.11.3, module version = 1.2.0
[ 23.015] ABI class: X.Org Server Extension, version 6.0
[ 23.015] (II) NVIDIA(3): [DRI2] Setup complete
[ 23.015] (II) NVIDIA(3): [DRI2] VDPAU driver: nvidia
[ 23.015] (==) RandR enabled
[ 23.015] (II) intel(4): [DRI2] Setup complete
[ 23.015] (II) intel(4): [DRI2] DRI driver: i965
[ 23.015] (II) intel(4): Allocated new frame buffer 1920x1200 stride 7680, tiled
[ 23.016] (II) UXA(4): Driver registered support for the following operations:
[ 23.016] (II) solid
[ 23.016] (II) copy
[ 23.016] (II) composite (RENDER acceleration)
[ 23.016] (II) put_image
[ 23.016] (II) get_image
[ 23.016] (==) intel(4): Backing store disabled
[ 23.016] (==) intel(4): Silken mouse enabled
[ 23.016] (II) intel(4): Initializing HW Cursor
[ 23.016] (II) intel(4): RandR 1.2 enabled, ignore the following RandR disabled message.
[ 23.016] (**) intel(4): DPMS enabled
[ 23.016] (==) intel(4): Intel XvMC decoder enabled
[ 23.016] (II) intel(4): Set up textured video
[ 23.016] (II) intel(4): [XvMC] xvmc_vld driver initialized.
[ 23.016] (II) intel(4): direct rendering: DRI2 Enabled
[ 23.016] (WW) intel(4): Option "metamodes" is not used
[ 23.016] (==) intel(4): hotplug detection: "enabled"
[ 23.136] (--) RandR disabled
[ 23.136] (II) Initializing built-in extension Generic Event Extension
[ 23.136] (II) Initializing built-in extension SHAPE
[ 23.136] (II) Initializing built-in extension MIT-SHM
[ 23.136] (II) Initializing built-in extension XInputExtension
[ 23.136] (II) Initializing built-in extension XTEST
[ 23.136] (II) Initializing built-in extension BIG-REQUESTS
[ 23.136] (II) Initializing built-in extension SYNC
[ 23.136] (II) Initializing built-in extension XKEYBOARD
[ 23.136] (II) Initializing built-in extension XC-MISC
[ 23.136] (II) Initializing built-in extension SECURITY
[ 23.136] (II) Initializing built-in extension XINERAMA
[ 23.136] (II) Initializing built-in extension XFIXES
[ 23.136] (II) Initializing built-in extension RENDER
[ 23.136] (II) Initializing built-in extension RANDR
[ 23.136] (II) Initializing built-in extension COMPOSITE
[ 23.136] (II) Initializing built-in extension DAMAGE
[ 23.137] (II) Initializing extension GLX
[ 23.169] (WW) NVIDIA: Xinerama and GLX are enabled, but some X screens are not being
[ 23.169] (WW) NVIDIA: driven by the NVIDIA X driver. OpenGL rendering will be
[ 23.169] (WW) NVIDIA: disabled on these screens:
[ 23.169] (WW) NVIDIA: - Screen 4: intel
[ 23.259] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.
xkm
[ 23.261] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[ 23.261] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 23.261] (II) LoadModule: "evdev"
[ 23.261] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.261] (II) Module evdev: vendor="X.Org Foundation"
[ 23.261] compiled for 1.11.3, module version = 2.7.0
[ 23.261] Module class: X.Org XInput Driver
[ 23.261] ABI class: X.Org XInput driver, version 16.0
[ 23.261] (II) Using input driver 'evdev' for 'Power Button'
[ 23.261] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.261] (**) Power Button: always reports core events
[ 23.261] (**) evdev: Power Button: Device: "/dev/input/event1"
[ 23.261] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 23.261] (--) evdev: Power Button: Found keys
[ 23.261] (II) evdev: Power Button: Configuring as keyboard
[ 23.261] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/
event1"
[ 23.261] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[ 23.261] (**) Option "xkb_rules" "evdev"
[ 23.261] (**) Option "xkb_model" "pc105"
[ 23.261] (**) Option "xkb_layout" "us"
[ 23.261] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[ 23.261] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[ 23.261] (II) Using input driver 'evdev' for 'Video Bus'
[ 23.261] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.261] (**) Video Bus: always reports core events
[ 23.261] (**) evdev: Video Bus: Device: "/dev/input/event6"
[ 23.261] (--) evdev: Video Bus: Vendor 0 Product 0x6
[ 23.261] (--) evdev: Video Bus: Found keys
[ 23.261] (II) evdev: Video Bus: Configuring as keyboard
[ 23.261] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:
00/input/input6/event6"
[ 23.261] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[ 23.261] (**) Option "xkb_rules" "evdev"
[ 23.261] (**) Option "xkb_model" "pc105"
[ 23.261] (**) Option "xkb_layout" "us"
[ 23.262] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[ 23.262] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[ 23.262] (II) Using input driver 'evdev' for 'Power Button'
[ 23.262] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.262] (**) Power Button: always reports core events
[ 23.262] (**) evdev: Power Button: Device: "/dev/input/event0"
[ 23.262] (--) evdev: Power Button: Vendor 0 Product 0x1
[ 23.262] (--) evdev: Power Button: Found keys
[ 23.262] (II) evdev: Power Button: Configuring as keyboard
[ 23.262] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/
input0/event0"
[ 23.262] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[ 23.262] (**) Option "xkb_rules" "evdev"
[ 23.262] (**) Option "xkb_model" "pc105"
[ 23.262] (**) Option "xkb_layout" "us"
[ 23.262] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[ 23.262] (II) No input driver specified, ignoring this device.
[ 23.262] (II) This device may have been added with another device file.
[ 23.262] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event11)
[ 23.262] (II) No input driver specified, ignoring this device.
[ 23.262] (II) This device may have been added with another device file.
[ 23.262] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[ 23.262] (II) No input driver specified, ignoring this device.
[ 23.262] (II) This device may have been added with another device file.
[ 23.262] (II) config/udev: Adding input device HDA Intel PCH Line-Out Side (/dev/input/event13)
[ 23.262] (II) No input driver specified, ignoring this device.
[ 23.262] (II) This device may have been added with another device file.
[ 23.263] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event14)
[ 23.263] (II) No input driver specified, ignoring this device.
[ 23.263] (II) This device may have been added with another device file.
[ 23.263] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/event15)
[ 23.263] (II) No input driver specified, ignoring this device.
[ 23.263] (II) This device may have been added with another device file.
[ 23.263] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event16)
[ 23.263] (II) No input driver specified, ignoring this device.
[ 23.263] (II) This device may have been added with another device file.
[ 23.263] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event7)
[ 23.263] (II) No input driver specified, ignoring this device.
[ 23.263] (II) This device may have been added with another device file.
[ 23.263] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[ 23.263] (II) No input driver specified, ignoring this device.
[ 23.263] (II) This device may have been added with another device file.
[ 23.263] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event9)
[ 23.263] (II) No input driver specified, ignoring this device.
[ 23.263] (II) This device may have been added with another device file.
[ 23.263] (II) config/udev: Adding input device daskeyboard (/dev/input/event2)
[ 23.263] (**) daskeyboard: Applying InputClass "evdev keyboard catchall"
[ 23.263] (II) Using input driver 'evdev' for 'daskeyboard'
[ 23.263] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.263] (**) daskeyboard: always reports core events
[ 23.263] (**) evdev: daskeyboard: Device: "/dev/input/event2"
[ 23.263] (--) evdev: daskeyboard: Vendor 0x4d9 Product 0x2013
[ 23.263] (--) evdev: daskeyboard: Found keys
[ 23.263] (II) evdev: daskeyboard: Configuring as keyboard
[ 23.263] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.
5/2-1.5:1.0/input/input2/event2"
[ 23.263] (II) XINPUT: Adding extended input device "daskeyboard" (type: KEYBOARD, id 9)
[ 23.263] (**) Option "xkb_rules" "evdev"
[ 23.263] (**) Option "xkb_model" "pc105"
[ 23.263] (**) Option "xkb_layout" "us"
[ 23.264] (II) config/udev: Adding input device daskeyboard (/dev/input/event3)
[ 23.264] (**) daskeyboard: Applying InputClass "evdev keyboard catchall"
[ 23.264] (II) Using input driver 'evdev' for 'daskeyboard'
[ 23.264] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.264] (**) daskeyboard: always reports core events
[ 23.264] (**) evdev: daskeyboard: Device: "/dev/input/event3"
[ 23.264] (--) evdev: daskeyboard: Vendor 0x4d9 Product 0x2013
[ 23.264] (--) evdev: daskeyboard: Found keys
[ 23.264] (II) evdev: daskeyboard: Configuring as keyboard
[ 23.264] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.
5/2-1.5:1.1/input/input3/event3"
[ 23.264] (II) XINPUT: Adding extended input device "daskeyboard" (type: KEYBOARD, id 10)
[ 23.264] (**) Option "xkb_rules" "evdev"
[ 23.264] (**) Option "xkb_model" "pc105"
[ 23.264] (**) Option "xkb_layout" "us"
[ 23.264] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/event4)
[ 23.264] (**) Logitech Unifying Device. Wireless PID:101a: Applying InputClass "evdev pointer catchall"
[ 23.264] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:101a'
[ 23.264] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.264] (**) Logitech Unifying Device. Wireless PID:101a: always reports core events
[ 23.264] (**) evdev: Logitech Unifying Device. Wireless PID:101a: Device: "/dev/input/event4"
[ 23.264] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Vendor 0x46d Product 0xc52b
[ 23.264] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found 20 mouse buttons
[ 23.264] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found scroll wheel(s)
[ 23.264] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found relative axes
[ 23.264] (--) evdev: Logitech Unifying Device. Wireless PID:101a: Found x and y relative axes
[ 23.264] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Configuring as mouse
[ 23.264] (II) evdev: Logitech Unifying Device. Wireless PID:101a: Adding scrollwheel support
[ 23.264] (**) evdev: Logitech Unifying Device. Wireless PID:101a: YAxisMapping: buttons 4 and 5
[ 23.264] (**) evdev: Logitech Unifying Device. Wireless PID:101a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[ 23.264] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.
6/2-1.6.1/2-1.6.1:1.2/0003:046D:C52B.0005/input/input4/event4"
 
[ 23.264] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:101a" (type: MOUSE, id 11)
[ 23.264] (II) evdev: Logitech Unifying Device. Wireless PID:101a: initialized for relative axes.
[ 23.264] (**) Logitech Unifying Device. Wireless PID:101a: (accel) keeping acceleration scheme 1
[ 23.264] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration profile 0
[ 23.264] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration factor: 2.000
[ 23.264] (**) Logitech Unifying Device. Wireless PID:101a: (accel) acceleration threshold: 4
[ 23.264] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:101a (/dev/input/mouse0)
[ 23.264] (II) No input driver specified, ignoring this device.
[ 23.264] (II) This device may have been added with another device file.
[ 23.265] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event5)
[ 23.265] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[ 23.265] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[ 23.265] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[ 23.265] (**) Eee PC WMI hotkeys: always reports core events
[ 23.265] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event5"
[ 23.265] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[ 23.265] (--) evdev: Eee PC WMI hotkeys: Found keys
[ 23.265] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[ 23.265] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input5/event5"
 
[ 23.265] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 12)
[ 23.265] (**) Option "xkb_rules" "evdev"
[ 23.265] (**) Option "xkb_model" "pc105"
[ 23.265] (**) Option "xkb_layout" "us"
[ 26.934] [mi] Increasing EQ size to 512 to prevent dropped events.
[ 37.707] (II) XKB: reuse xkmfile /var/lib/xkb/server-03AF3717FF3AB439A4BAABA686CCB40771CDF520.
xkm

---

