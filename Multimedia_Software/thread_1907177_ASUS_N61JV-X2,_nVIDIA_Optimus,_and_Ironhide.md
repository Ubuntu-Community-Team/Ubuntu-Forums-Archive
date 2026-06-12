---
title: "ASUS N61JV-X2, nVIDIA Optimus, and Ironhide"
date: 2012-01-10
forum: Multimedia Software
---

### Post by Welly Wu on 2012-01-10
I completely removed the Bumblebee PPA and files by following their instructions on their website to remove old versions. I installed Ironhide to replace it. This is my Ironhide log:

[   418.562] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   418.562] X Protocol Version 11, Revision 0
[   418.562] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   418.562] Current Operating System: Linux N61JV-X2 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64
[   418.562] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=add6445a-226d-4dd3-9e41-4a2f757c1cf8 ro quiet splash vt.handoff=7
[   418.562] Build Date: 19 October 2011  05:21:26AM
[   418.562] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   418.562] Current version of pixman: 0.22.2
[   418.562] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[   418.562] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   418.562] (==) Log file: "/var/log/Xorg.8.log", Time: Tue Jan 10 21:09:03 2012
[   418.563] (EE) Unable to locate/open config file: "/etc/X11/xorg.conf.nvidia"
[   418.563] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   418.563] (==) No Layout section.  Using the first Screen section.
[   418.563] (==) No screen section available. Using defaults.
[   418.563] (**) |-->Screen "Default Screen Section" (0)
[   418.563] (**) |   |-->Monitor "<default monitor>"
[   418.563] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   418.563] (==) Automatically adding devices
[   418.563] (==) Automatically enabling devices
[   418.563] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   418.563] 	Entry deleted from font path.
[   418.563] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   418.563] 	Entry deleted from font path.
[   418.563] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   418.563] 	Entry deleted from font path.
[   418.563] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   418.563] 	Entry deleted from font path.
[   418.563] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   418.564] 	Entry deleted from font path.
[   418.564] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   418.564] (++) ModulePath set to "/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules"
[   418.564] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   418.564] (II) Loader magic: 0x7e0220
[   418.564] (II) Module ABI versions:
[   418.564] 	X.Org ANSI C Emulation: 0.4
[   418.564] 	X.Org Video Driver: 10.0
[   418.564] 	X.Org XInput driver : 12.3
[   418.564] 	X.Org Server Extension : 5.0
[   418.565] (--) PCI:*(0:0:2:0) 8086:0046:1043:1252 rev 18, Mem @ 0xe3400000/4194304, 0xc0000000/268435456, I/O @ 0x0000e080/8
[   418.565] (--) PCI: (0:1:0:0) 10de:0a35:1043:1252 rev 162, Mem @ 0xe2000000/16777216, 0xd0000000/268435456, 0xe0000000/33554432, I/O @ 0x0000d000/128, BIOS @ 0x????????/524288
[   418.565] (II) Open ACPI successful (/var/run/acpid.socket)
[   418.565] (II) LoadModule: "extmod"
[   418.566] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   418.566] (II) Module extmod: vendor="X.Org Foundation"
[   418.566] 	compiled for 1.10.4, module version = 1.0.0
[   418.566] 	Module class: X.Org Server Extension
[   418.566] 	ABI class: X.Org Server Extension, version 5.0
[   418.566] (II) Loading extension MIT-SCREEN-SAVER
[   418.566] (II) Loading extension XFree86-VidModeExtension
[   418.566] (II) Loading extension XFree86-DGA
[   418.566] (II) Loading extension DPMS
[   418.566] (II) Loading extension XVideo
[   418.566] (II) Loading extension XVideo-MotionCompensation
[   418.566] (II) Loading extension X-Resource
[   418.566] (II) LoadModule: "dbe"
[   418.566] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   418.566] (II) Module dbe: vendor="X.Org Foundation"
[   418.566] 	compiled for 1.10.4, module version = 1.0.0
[   418.566] 	Module class: X.Org Server Extension
[   418.566] 	ABI class: X.Org Server Extension, version 5.0
[   418.566] (II) Loading extension DOUBLE-BUFFER
[   418.566] (II) LoadModule: "glx"
[   418.566] (II) Loading /usr/lib/nvidia-current/xorg/libglx.so
[   418.581] (II) Module glx: vendor="NVIDIA Corporation"
[   418.581] 	compiled for 4.0.2, module version = 1.0.0
[   418.581] 	Module class: X.Org Server Extension
[   418.581] (II) NVIDIA GLX Module  290.10  Wed Nov 16 18:01:24 PST 2011
[   418.581] (II) Loading extension GLX
[   418.581] (II) LoadModule: "record"
[   418.582] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   418.582] (II) Module record: vendor="X.Org Foundation"
[   418.582] 	compiled for 1.10.4, module version = 1.13.0
[   418.582] 	Module class: X.Org Server Extension
[   418.582] 	ABI class: X.Org Server Extension, version 5.0
[   418.582] (II) Loading extension RECORD
[   418.582] (II) LoadModule: "dri"
[   418.582] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   418.582] (II) Module dri: vendor="X.Org Foundation"
[   418.582] 	compiled for 1.10.4, module version = 1.0.0
[   418.582] 	ABI class: X.Org Server Extension, version 5.0
[   418.582] (II) Loading extension XFree86-DRI
[   418.582] (II) LoadModule: "dri2"
[   418.582] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   418.582] (II) Module dri2: vendor="X.Org Foundation"
[   418.582] 	compiled for 1.10.4, module version = 1.2.0
[   418.582] 	ABI class: X.Org Server Extension, version 5.0
[   418.582] (II) Loading extension DRI2
[   418.582] (==) Matched intel as autoconfigured driver 0
[   418.582] (==) Matched vesa as autoconfigured driver 1
[   418.582] (==) Matched fbdev as autoconfigured driver 2
[   418.582] (==) Assigned the driver to the xf86ConfigLayout
[   418.582] (II) LoadModule: "intel"
[   418.582] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   418.583] (II) Module intel: vendor="X.Org Foundation"
[   418.583] 	compiled for 1.10.4, module version = 2.15.901
[   418.583] 	Module class: X.Org Video Driver
[   418.583] 	ABI class: X.Org Video Driver, version 10.0
[   418.583] (II) LoadModule: "vesa"
[   418.583] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   418.583] (II) Module vesa: vendor="X.Org Foundation"
[   418.583] 	compiled for 1.10.2, module version = 2.3.0
[   418.583] 	Module class: X.Org Video Driver
[   418.583] 	ABI class: X.Org Video Driver, version 10.0
[   418.583] (II) LoadModule: "fbdev"
[   418.583] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   418.583] (II) Module fbdev: vendor="X.Org Foundation"
[   418.583] 	compiled for 1.10.0, module version = 0.4.2
[   418.583] 	ABI class: X.Org Video Driver, version 10.0
[   418.583] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
	Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
	Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
	Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
	Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[   418.583] (II) VESA: driver for VESA chipsets: vesa
[   418.583] (II) FBDEV: driver for framebuffer: fbdev
[   418.583] (--) using VT number 7

[   418.583] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[   418.586] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   418.586] (WW) Falling back to old probe method for vesa
[   418.586] (WW) Falling back to old probe method for fbdev
[   418.586] (II) Loading sub module "fbdevhw"
[   418.586] (II) LoadModule: "fbdevhw"
[   418.586] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   418.587] (II) Module fbdevhw: vendor="X.Org Foundation"
[   418.587] 	compiled for 1.10.4, module version = 0.0.2
[   418.587] 	ABI class: X.Org Video Driver, version 10.0
[   418.587] drmOpenDevice: node name is /dev/dri/card0
[   418.587] drmOpenDevice: open result is 9, (OK)
[   418.587] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   418.587] drmOpenDevice: node name is /dev/dri/card0
[   418.587] drmOpenDevice: open result is 9, (OK)
[   418.587] drmOpenByBusid: drmOpenMinor returns 9
[   418.587] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[   418.587] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   418.587] (EE) intel(0): [drm] failed to set drm interface version.
[   418.587] (EE) intel(0): Failed to become DRM master.
[   418.587] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   418.587] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   418.587] (==) intel(0): RGB weight 888
[   418.587] (==) intel(0): Default visual is TrueColor
[   418.587] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[   418.587] (--) intel(0): Chipset: "Arrandale"
[   418.587] (**) intel(0): Relaxed fencing disabled
[   418.587] (**) intel(0): Wait on SwapBuffers? enabled
[   418.587] (**) intel(0): Triple buffering? enabled
[   418.587] (**) intel(0): Framebuffer tiled
[   418.587] (**) intel(0): Pixmaps tiled
[   418.587] (**) intel(0): 3D buffers tiled
[   418.587] (**) intel(0): SwapBuffers wait enabled
[   418.587] (==) intel(0): video overlay key set to 0x101fe
[   418.587] (EE) intel(0): failed to get resources: Bad file descriptor
[   418.587] (II) UnloadModule: "intel"
[   418.587] (II) Unloading intel
[   418.587] (EE) Screen(s) found, but none have a usable configuration.
[   418.587] 
Fatal server error:
[   418.587] no screens found
[   418.587] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   418.587] Please also check the log file at "/var/log/Xorg.8.log" for additional information.
[   418.587] 
[   418.587]  ddxSigGiveUp: Closing log

I can not get optirun to display the glxspheres or anything else. What is the problem? How can I solve this problem?

Thanks.

---

