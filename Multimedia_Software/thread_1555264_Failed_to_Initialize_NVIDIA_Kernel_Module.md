---
title: "Failed to Initialize NVIDIA Kernel Module"
date: 2010-08-17
forum: Multimedia Software
---

### Post by afbase on 2010-08-17
I have had this error for way too long.  This post will be done in parts.  I've had it for months now and I'd like to solve it.  Every suggestion on linux forums, ubuntu forums, or some XYZ-linux blog seems to either work for just one boot or none at all. Any Help is MUCH appreciated:
[LIST=1] Suggests that I've tried from other posts:
[LIST]
[*]since I have updated my kernel on several occasions, I have also re-installed my NVIDIA kernel module by downloading the run file from NVIDIA's website. It also follows instructions from this [post]("http://ubuntuforums.org/showpost.php?p=6297089&postcount=4").
[*]I have installed the linux header files and the xorg-dev files from [repository]("http://ubuntuforums.org/showpost.php?p=6332697&postcount=16")
[*]I have also tried [this]("https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/556736/comments/6").
[/LIST]
[/LIST]
[LIST=2] My hardware  (Alienway m17x - VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260M])
```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: bus master, 66MHz, fast devsel, latency 0

00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 1c00 [size=256]

00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: 66MHz, fast devsel

00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: 66MHz, fast devsel, IRQ 10
	I/O ports at 3080 [size=64]
	I/O ports at 3040 [size=64]
	I/O ports at 2000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
	Flags: 66MHz, fast devsel

00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	Memory at f0600000 (32-bit, non-prefetchable) [size=512K]
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current

00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: Dell Device 02a1
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at f0886000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: Dell Device 02a1
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f0889000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10)
	Subsystem: Dell Device 02a1
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f0887000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20)
	Subsystem: Dell Device 02a1
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
	Memory at f0889400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: nVidia Corporation Device cb79
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at f0880000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f0500000-f05fffff
	Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
	Subsystem: Dell Device 02a1
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f0888000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 30d0 [size=8]
	Memory at f0889c00 (32-bit, non-prefetchable) [size=256]
	Memory at f0889800 (32-bit, non-prefetchable) [size=16]
	Capabilities: <access denied>
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth

00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1) (prog-if 01)
	Subsystem: Dell Device 02a1
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 30
	I/O ports at 30e8 [size=8]
	I/O ports at 30dc [size=4]
	I/O ports at 30e0 [size=8]
	I/O ports at 30d8 [size=4]
	I/O ports at 30c0 [size=16]
	Memory at f0884000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: cc000000-ceffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:0d.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: f0200000-f03fffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: f0400000-f04fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: Dell Device 02a1
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f0500000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: Dell Device 02a1
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f0500800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: Dell Device 02a1
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f0500c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: Dell Device 02a1
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at f0501000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

02:00.0 VGA compatible controller: nVidia Corporation GT200 [GeForce GTX 260M] (rev a2)
	Subsystem: Dell Device 02a1
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 4000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau

06:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Broadcom Corporation Device 04b1
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, ssb

```
[/LIST]
[LIST=3]My configuration files:
Xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	# generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
[/LIST]
[LIST=4]My Error Logs:
syslog:
```
Aug 17 16:50:25 clinton-laptop kernel: [   24.570145] input: HDA NVidia Mic at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input11
Aug 17 16:50:25 clinton-laptop kernel: [   24.570222] input: HDA NVidia Line Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input12
Aug 17 16:50:25 clinton-laptop kernel: [   24.570273] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input13
Aug 17 16:50:25 clinton-laptop kernel: [   24.570329] input: HDA NVidia HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:08.0/sound/card0/input14
Aug 17 16:50:25 clinton-laptop kernel: [   24.650622] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 19
Aug 17 16:50:25 clinton-laptop kernel: [   24.650627] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 19 (level, low) -> IRQ 19
Aug 17 16:50:25 clinton-laptop kernel: [   24.650660] nvidia 0000:02:00.0: PCI INT A -> Link[Z003] -> GSI 23 (level, low) -> IRQ 23
Aug 17 16:50:25 clinton-laptop kernel: [   24.650667] nvidia 0000:02:00.0: setting latency timer to 64
Aug 17 16:50:25 clinton-laptop kernel: [   24.650673] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Aug 17 16:50:25 clinton-laptop kernel: [   24.650867] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
Aug 17 16:50:33 clinton-laptop kernel: [   32.570037] eth1: no IPv6 routers present
Aug 17 16:50:45 clinton-laptop gdm-binary[1734]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 17 16:50:45 clinton-laptop gdm-binary[1734]: WARNING: Unable to find users: no seat-id found
Aug 17 16:50:45 clinton-laptop gdm-simple-slave[1735]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 17 16:50:45 clinton-laptop gdm-binary[1734]: WARNING: GdmDisplay: display lasted 0.015315 seconds
Aug 17 16:50:45 clinton-laptop gdm-simple-slave[1740]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 17 16:50:46 clinton-laptop acpid: client 1625[0:0] has disconnected
Aug 17 16:50:46 clinton-laptop acpid: client connected from 1742[0:0]
Aug 17 16:50:46 clinton-laptop acpid: 1 client rule loaded
Aug 17 16:50:48 clinton-laptop wpa_supplicant[967]: WPS-AP-AVAILABLE 
Aug 17 16:50:48 clinton-laptop gdm-session-worker[1778]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Aug 17 16:50:49 clinton-laptop polkitd[1797]: started daemon version 0.96 using authority implementation `local' version `0.96'
Aug 17 16:50:49 clinton-laptop anacron[1834]: Anacron 2.3 started on 2010-08-17
Aug 17 16:50:49 clinton-laptop anacron[1834]: Normal exit (0 jobs run)
Aug 17 16:50:50 clinton-laptop gdm-simple-greeter[1777]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Aug 17 16:50:50 clinton-laptop acpid: client connected from 1899[108:114]
Aug 17 16:50:50 clinton-laptop acpid: 1 client rule loaded
Aug 17 16:51:17 clinton-laptop gdm-session-worker[1778]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Aug 17 16:51:18 clinton-laptop wpa_supplicant[967]: WPS-AP-AVAILABLE 

```
xorg log
```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux clinton-laptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-24-generic root=UUID=c2dc1101-3957-445e-baa9-63d7ceced4b9 ro quiet splash
Build Date: 21 July 2010  01:03:39PM
xorg-server 2:1.7.6-2ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 17 16:50:24 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI: (0:0:3:5) 10de:0aa3:10de:cb79 nVidia Corporation MCP79 Co-processor rev 177, Mem @ 0xf0600000/524288
(--) PCI:*(0:2:0:0) 10de:0618:1028:02a1 nVidia Corporation GT200 [GeForce GTX 260M] rev 162, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00004000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Aug 17 16:50:24 NVIDIA(0): Enabling RENDER acceleration
(II) Aug 17 16:50:24 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Aug 17 16:50:24 NVIDIA(0):     enabled.
(EE) Aug 17 16:50:24 NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) Aug 17 16:50:24 NVIDIA(0):     system's kernel log for additional error messages and
(EE) Aug 17 16:50:24 NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```
[/LIST]

---

### Post by sandroc70 on 2010-08-19
Hi all,

i have same problem on my notebook with NVdia GEForce 310.

Here's my xorg.log

sandro 


```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux capt-kirk 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=b6251c6f-64a0-4db1-85f5-726e6a01568f ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu Aug 19 08:53:48 2010
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 7

(--) PCI:*(0:0:2:0) 8086:0046:1043:1432 Intel Corporation Core Processor Integrated Graphics Controller rev 18, Mem @ 0xd3400000/4194304, 0xb0000000/268435456, I/O @ 0x0000e080/8
(--) PCI: (0:1:0:0) 10de:0a70:1043:1432 nVidia Corporation rev 162, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.4.1
    ABI class: X.Org Video Driver, version 6.0
(II) FBDEV: driver for framebuffer: fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.7.6, module version = 0.0.2
    ABI class: X.Org Video Driver, version 6.0
(**) FBDEV(0): claimed PCI slot 0@0:2:0
(II) FBDEV(0): using default device
(II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 4/4
(==) FBDEV(0): Depth 4, (==) framebuffer bpp 4
(==) FBDEV(0): Default visual is StaticColor
(==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) FBDEV(0): hardware: VGA16 VGA (video memory: 64kB)
(II) FBDEV(0): checking modes against framebuffer device...
(II) FBDEV(0): checking modes against monitor...
(--) FBDEV(0): Virtual size is 640x480 (pitch 640)
(**) FBDEV(0):  Built-in mode "current": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) FBDEV(0): Modeline "current"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync -csync (31.5 kHz)
(==) FBDEV(0): DPI set to (96, 96)
(EE) FBDEV(0): EGA/VGA planes are not yet supported by the fbdev driver

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3248]
1: /usr/bin/X (0x400000+0x655ad) [0x4655ad]
2: /lib/libpthread.so.0 (0x7f75028f6000+0xf8f0) [0x7f75029058f0]
3: /lib/libc.so.6 (cfree+0x40) [0x7f750164ce20]
4: /usr/bin/X (xf86DeleteMode+0x45) [0x47e4c5]
5: /usr/bin/X (xf86DeleteScreen+0xa0) [0x47bdb0]
6: /usr/bin/X (InitOutput+0x5ba) [0x473a1a]
7: /usr/bin/X (0x400000+0x26005) [0x426005]
8: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f75015edc4d]
9: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Segmentation fault at address 0x7f74fc000000

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by tjones00 on 2010-08-19
sandro

We'd need to see your /etc/X11/xorg.conf. Also the Xorg.0.log you posted is from failsafe graphics settings. To troubleshoot any error we'd need the Xorg log from when it crashed.

Notice: (++) Using config file: "/etc/X11/xorg.conf.failsafe"

We need Using config file: "/etc/X11/xorg.conf"



afbase

What procedure did you use to install the nvidia driver that generated those logs? The Nvidia .run file?

Did you receive any warnings or errors while installing it?

Have you blacklisted nouveau and it's buddys to prevent them from mucking things up? This is required in 10.04 if you install from the Nvidia.run method. It is not required if you did sudo apt-get install nvidia-current or used jockey. Nouveau is now built into the kernel so just uninstalling the xserver-xorg-video-nouveau as listed in the Ubuntu instructions is not enough.

sudo nano /etc/modprobe.d/blacklist.conf

add

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

save and exit

**If you want to try things again from the start this is the method I use.**

[B]
If you have a failed NVIDIA*.run install start at step 1. If you haven't installed NVIDIA*.run yet skip to step 2[/B].

1) Uninstall nvidia

sudo sh /path/to/NVIDIA*.run --uninstall

sudo sudo apt-get --purge remove nvidia-*

2) Make sure you have the dependencies to build and install the driver.

An easy way to make sure you have all the required  dependencies to build the nvidia proprietary driver is the following.

```
sudo apt-get install nvidia-current
sudo apt-get remove nvidia-current nvidia-settings
```It basically   builds and installs whatever proprietary driver is in the ubuntu   repositories and then you uninstall/remove it but the dependencies for   building and installing the driver will remain.


3) blacklist nouveau and the gang.

```
sudo nano /etc/modprobe.d/blacklist.conf
```add the following

```
blacklist vga16fb
 blacklist nouveau
 blacklist rivafb
 blacklist nvidiafb
 blacklist rivatv
```save and exit

reboot

```
sudo reboot
```

4) Install Nvidia
We need to reboot so that nouveau and anybody else is cleared out before installing NVIDIA*.run you could use modprobe -r but rebooting is easier.
-at grub edit the boot parameters (press e over the image you wish to boot) changing quiet splash to nomodeset then press ctrl-x to boot
-switch to a terminal if x doesn't start press ctrl+alt+f2
-login and stop x ```
sudo service gdm stop
```-install the nvidia proprietary driver ```
sudo sh /path/to/NVIDIA*.run
```-if NVIDIA*.run fails to execute via sudo sh try this
```
sudo chmod +x NVIDIA*.run
sudo ./NVIDIA*.run
```-allow it to make a xorg.conf or make your own after the install is complete

```
sudo nvidia-xconfig -s --no-logo --force-generate --output-xconfig=/etc/X11/xorg.conf

```

5) Reboot again.
```
sudo reboot
```

---

### Post by tmfries on 2010-11-24
tjones,

worked like a champ. Thank you sir!

---

