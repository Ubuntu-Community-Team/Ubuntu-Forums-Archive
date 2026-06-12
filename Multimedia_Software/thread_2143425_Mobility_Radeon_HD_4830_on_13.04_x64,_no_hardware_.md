---
title: "Mobility Radeon HD 4830 on 13.04 x64, no hardware acceleration"
date: 2013-05-09
forum: Multimedia Software
---

### Post by ironyCurtain on 2013-05-09
Hi all,

I have been struggling to get hardware acceleration to work with the ATI card in my laptop: 
```
~$ lspci | grep -i VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV740/M97 [Mobility Radeon HD 4830]
```

In order to get Ubuntu 13.04 to even install I had to press the down arrow while booting from the install media and set the nomodeset kernel boot parameter--otherwise i wound up getting a black screen. Unity is pretty laggy when it uses effects (like the expose-like effect especially). The card is old enough that proprietary drivers no longer support it, so I have been trying to get it to work on the open source radeon driver. As far as I can tell, while the radeon kernel module is loaded, it's the VESA driver that eventually winds up being used. 

```
~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
dm_crypt               22820  1 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
arc4                   12615  2 
snd_hda_codec_hdmi     36913  1 
coretemp               13355  0 
snd_hda_codec_idt      70256  1 
iwldvm                241834  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
kvm_intel             132891  0 
mac80211              606457  1 iwldvm
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
kvm                   443165  1 kvm_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
joydev                 17377  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
uvcvideo               80847  0 
iwlwifi               173477  1 iwldvm
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
psmouse                95870  0 
snd_timer              29425  2 snd_pcm,snd_seq
videobuf2_vmalloc      13056  1 uvcvideo
cfg80211              510937  3 iwlwifi,mac80211,iwldvm
videobuf2_memops       13202  1 videobuf2_vmalloc
mac_hid                13205  0 
i7core_edac            24169  0 
edac_core              62003  1 i7core_edac
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
hp_accel               26012  0 
serio_raw              13215  0 
lis3lv02d              20111  1 hp_accel
hp_wmi                 18048  0 
intel_ips              17978  0 
input_polldev          13896  1 lis3lv02d
videobuf2_core         40513  1 uvcvideo
sparse_keymap          13890  1 hp_wmi
videodev              129260  2 uvcvideo,videobuf2_core
lpc_ich                17061  0 
microcode              22881  0 
radeon                937749  0 
video                  19390  0 
wmi                    19070  1 hp_wmi
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
drm                   286313  3 ttm,drm_kms_helper,radeon
atl1c                  41071  0 
ahci                   25731  3 
libahci                31364  1 ahci

```

```
~$ cat /var/log/Xorg.0.log
[    80.361] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    80.361] X Protocol Version 11, Revision 0
[    80.361] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    80.361] Current Operating System: Linux condor 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64
[    80.361] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=d3bfedd5-18e7-473f-8142-b514cd183984 ro recovery nomodeset nomodeset
[    80.361] Build Date: 17 April 2013  10:43:13PM
[    80.361] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[    80.361] Current version of pixman: 0.28.2
[    80.361] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    80.361] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    80.361] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May  8 23:06:24 2013
[    80.380] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    80.380] (==) No Layout section.  Using the first Screen section.
[    80.380] (==) No screen section available. Using defaults.
[    80.380] (**) |-->Screen "Default Screen Section" (0)
[    80.380] (**) |   |-->Monitor "<default monitor>"
[    80.381] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    80.381] (==) Automatically adding devices
[    80.381] (==) Automatically enabling devices
[    80.381] (==) Automatically adding GPU devices
[    80.381] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    80.381] 	Entry deleted from font path.
[    80.381] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    80.381] 	Entry deleted from font path.
[    80.381] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    80.381] 	Entry deleted from font path.
[    80.381] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    80.381] 	Entry deleted from font path.
[    80.381] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    80.381] 	Entry deleted from font path.
[    80.381] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    80.381] 	Entry deleted from font path.
[    80.381] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    80.381] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    80.381] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    80.381] (II) Loader magic: 0x7f00d31ecd20
[    80.381] (II) Module ABI versions:
[    80.381] 	X.Org ANSI C Emulation: 0.4
[    80.381] 	X.Org Video Driver: 13.1
[    80.381] 	X.Org XInput driver : 18.0
[    80.381] 	X.Org Server Extension : 7.0
[    80.381] (II) config/udev: Adding drm device (/dev/dri/card0)
[    80.383] (--) PCI:*(0:1:0:0) 1002:94a0:103c:7009 rev 0, Mem @ 0xc0000000/268435456, 0xd4000000/65536, I/O @ 0x00004000/256, BIOS @ 0x????????/131072
[    80.383] (II) Open ACPI successful (/var/run/acpid.socket)
[    80.383] Initializing built-in extension Generic Event Extension
[    80.383] Initializing built-in extension SHAPE
[    80.383] Initializing built-in extension MIT-SHM
[    80.383] Initializing built-in extension XInputExtension
[    80.383] Initializing built-in extension XTEST
[    80.383] Initializing built-in extension BIG-REQUESTS
[    80.383] Initializing built-in extension SYNC
[    80.383] Initializing built-in extension XKEYBOARD
[    80.383] Initializing built-in extension XC-MISC
[    80.383] Initializing built-in extension SECURITY
[    80.383] Initializing built-in extension XINERAMA
[    80.383] Initializing built-in extension XFIXES
[    80.383] Initializing built-in extension RENDER
[    80.383] Initializing built-in extension RANDR
[    80.383] Initializing built-in extension COMPOSITE
[    80.383] Initializing built-in extension DAMAGE
[    80.383] Initializing built-in extension MIT-SCREEN-SAVER
[    80.383] Initializing built-in extension DOUBLE-BUFFER
[    80.383] Initializing built-in extension RECORD
[    80.383] Initializing built-in extension DPMS
[    80.383] Initializing built-in extension X-Resource
[    80.383] Initializing built-in extension XVideo
[    80.383] Initializing built-in extension XVideo-MotionCompensation
[    80.383] Initializing built-in extension SELinux
[    80.383] Initializing built-in extension XFree86-VidModeExtension
[    80.383] Initializing built-in extension XFree86-DGA
[    80.383] Initializing built-in extension XFree86-DRI
[    80.383] Initializing built-in extension DRI2
[    80.383] (II) LoadModule: "glx"
[    80.431] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    80.431] (II) Module glx: vendor="X.Org Foundation"
[    80.431] 	compiled for 1.13.3, module version = 1.0.0
[    80.431] 	ABI class: X.Org Server Extension, version 7.0
[    80.431] (==) AIGLX enabled
[    80.431] Loading extension GLX
[    80.431] (==) Matched fglrx as autoconfigured driver 0
[    80.431] (==) Matched ati as autoconfigured driver 1
[    80.431] (==) Matched fglrx as autoconfigured driver 2
[    80.431] (==) Matched ati as autoconfigured driver 3
[    80.431] (==) Matched vesa as autoconfigured driver 4
[    80.431] (==) Matched modesetting as autoconfigured driver 5
[    80.431] (==) Matched fbdev as autoconfigured driver 6
[    80.431] (==) Assigned the driver to the xf86ConfigLayout
[    80.431] (II) LoadModule: "fglrx"
[    80.431] (WW) Warning, couldn't open module fglrx
[    80.431] (II) UnloadModule: "fglrx"
[    80.431] (II) Unloading fglrx
[    80.431] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    80.431] (II) LoadModule: "ati"
[    80.431] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    80.431] (II) Module ati: vendor="X.Org Foundation"
[    80.431] 	compiled for 1.13.3, module version = 7.1.0
[    80.431] 	Module class: X.Org Video Driver
[    80.431] 	ABI class: X.Org Video Driver, version 13.1
[    80.431] (II) LoadModule: "radeon"
[    80.432] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    80.522] (II) Module radeon: vendor="X.Org Foundation"
[    80.523] 	compiled for 1.13.3, module version = 7.1.0
[    80.523] 	Module class: X.Org Video Driver
[    80.523] 	ABI class: X.Org Video Driver, version 13.1
[    80.523] (II) LoadModule: "vesa"
[    80.523] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    80.523] (II) Module vesa: vendor="X.Org Foundation"
[    80.523] 	compiled for 1.12.99.902, module version = 2.3.2
[    80.523] 	Module class: X.Org Video Driver
[    80.523] 	ABI class: X.Org Video Driver, version 13.0
[    80.523] (II) LoadModule: "modesetting"
[    80.523] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    80.523] (II) Module modesetting: vendor="X.Org Foundation"
[    80.523] 	compiled for 1.13.3, module version = 0.7.0
[    80.523] 	Module class: X.Org Video Driver
[    80.523] 	ABI class: X.Org Video Driver, version 13.1
[    80.523] (II) LoadModule: "fbdev"
[    80.523] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    80.523] (II) Module fbdev: vendor="X.Org Foundation"
[    80.523] 	compiled for 1.12.99.902, module version = 0.4.3
[    80.523] 	Module class: X.Org Video Driver
[    80.523] 	ABI class: X.Org Video Driver, version 13.0
[    80.523] (==) Matched fglrx as autoconfigured driver 0
[    80.523] (==) Matched ati as autoconfigured driver 1
[    80.523] (==) Matched fglrx as autoconfigured driver 2
[    80.523] (==) Matched ati as autoconfigured driver 3
[    80.523] (==) Matched vesa as autoconfigured driver 4
[    80.523] (==) Matched modesetting as autoconfigured driver 5
[    80.523] (==) Matched fbdev as autoconfigured driver 6
[    80.523] (==) Assigned the driver to the xf86ConfigLayout
[    80.523] (II) LoadModule: "fglrx"
[    80.524] (WW) Warning, couldn't open module fglrx
[    80.524] (II) UnloadModule: "fglrx"
[    80.524] (II) Unloading fglrx
[    80.524] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    80.524] (II) LoadModule: "ati"
[    80.524] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    80.524] (II) Module ati: vendor="X.Org Foundation"
[    80.524] 	compiled for 1.13.3, module version = 7.1.0
[    80.524] 	Module class: X.Org Video Driver
[    80.524] 	ABI class: X.Org Video Driver, version 13.1
[    80.524] (II) LoadModule: "vesa"
[    80.525] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    80.525] (II) Module vesa: vendor="X.Org Foundation"
[    80.525] 	compiled for 1.12.99.902, module version = 2.3.2
[    80.525] 	Module class: X.Org Video Driver
[    80.525] 	ABI class: X.Org Video Driver, version 13.0
[    80.525] (II) UnloadModule: "vesa"
[    80.525] (II) Unloading vesa
[    80.525] (II) Failed to load module "vesa" (already loaded, 0)
[    80.525] (II) LoadModule: "modesetting"
[    80.525] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    80.525] (II) Module modesetting: vendor="X.Org Foundation"
[    80.525] 	compiled for 1.13.3, module version = 0.7.0
[    80.525] 	Module class: X.Org Video Driver
[    80.525] 	ABI class: X.Org Video Driver, version 13.1
[    80.525] (II) UnloadModule: "modesetting"
[    80.525] (II) Unloading modesetting
[    80.525] (II) Failed to load module "modesetting" (already loaded, 0)
[    80.525] (II) LoadModule: "fbdev"
[    80.525] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    80.525] (II) Module fbdev: vendor="X.Org Foundation"
[    80.525] 	compiled for 1.12.99.902, module version = 0.4.3
[    80.525] 	Module class: X.Org Video Driver
[    80.525] 	ABI class: X.Org Video Driver, version 13.0
[    80.525] (II) UnloadModule: "fbdev"
[    80.525] (II) Unloading fbdev
[    80.525] (II) Failed to load module "fbdev" (already loaded, 0)
[    80.525] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
	ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
	ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	AMD FireStream 9250, ATI FirePro V8700 (FireGL),
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
	ATI Radeon 4100, ATI Mobility Radeon HD 4200,
	ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI FirePro (FireGL) Graphics Adapter,
	ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
	ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
	CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
	BARTS, BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
	CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
	ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
	TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
	PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
	VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[    80.529] (II) VESA: driver for VESA chipsets: vesa
[    80.529] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    80.529] (II) FBDEV: driver for framebuffer: fbdev
[    80.529] (++) using VT number 7

[    80.530] (II) [KMS] drm report modesetting isn't supported.
[    80.530] (II) [KMS] drm report modesetting isn't supported.
[    80.530] (II) [KMS] drm report modesetting isn't supported.
[    80.530] (II) [KMS] drm report modesetting isn't supported.
[    80.530] (II) [KMS] drm report modesetting isn't supported.
[    80.530] (WW) Falling back to old probe method for modesetting
[    80.547] (WW) Falling back to old probe method for fbdev
[    80.547] (II) Loading sub module "fbdevhw"
[    80.547] (II) LoadModule: "fbdevhw"
[    80.547] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    80.548] (II) Module fbdevhw: vendor="X.Org Foundation"
[    80.548] 	compiled for 1.13.3, module version = 0.0.2
[    80.548] 	ABI class: X.Org Video Driver, version 13.1
[    80.548] (EE) open /dev/fb0: No such file or directory
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"
[    80.548] (II) Loading sub module "vbe"
[    80.548] (II) LoadModule: "vbe"
[    80.548] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    80.548] (II) Module vbe: vendor="X.Org Foundation"
[    80.548] 	compiled for 1.13.3, module version = 1.1.0
[    80.548] 	ABI class: X.Org Video Driver, version 13.1
[    80.548] (II) Loading sub module "int10"
[    80.548] (II) LoadModule: "int10"
[    80.549] (II) Loading /usr/lib/xorg/modules/libint10.so
[    80.549] (II) Module int10: vendor="X.Org Foundation"
[    80.549] 	compiled for 1.13.3, module version = 1.0.0
[    80.549] 	ABI class: X.Org Video Driver, version 13.1
[    80.549] (II) VESA(0): initializing int10
[    83.444] (II) VESA(0): VESA BIOS detected
[    83.444] (II) VESA(0): VESA VBE Version 3.0
[    83.444] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    83.444] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    83.444] (II) VESA(0): VESA VBE OEM Software Rev: 11.22
[    83.444] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    83.444] (II) VESA(0): VESA VBE OEM Product: M97
[    83.444] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    83.458] (II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    83.458] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    83.458] (==) VESA(0): RGB weight 888
[    83.458] (==) VESA(0): Default visual is TrueColor
[    83.458] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    83.458] (II) Loading sub module "ddc"
[    83.458] (II) LoadModule: "ddc"
[    83.458] (II) Module "ddc" already built-in
[    83.458] (II) VESA(0): VESA VBE DDC supported
[    83.458] (II) VESA(0): VESA VBE DDC Level 2
[    83.458] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    83.511] (II) VESA(0): VESA VBE DDC read successfully
[    83.511] (II) VESA(0): Manufacturer: LGD  Model: 1fb  Serial#: 0
[    83.511] (II) VESA(0): Year: 2009  Week: 0
[    83.511] (II) VESA(0): EDID Version: 1.3
[    83.511] (II) VESA(0): Digital Display Input
[    83.511] (II) VESA(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    83.511] (II) VESA(0): Gamma: 2.20
[    83.511] (II) VESA(0): No DPMS capabilities specified
[    83.511] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    83.511] (II) VESA(0): First detailed timing is preferred mode
[    83.511] (II) VESA(0): redX: 0.621 redY: 0.352   greenX: 0.314 greenY: 0.586
[    83.511] (II) VESA(0): blueX: 0.147 blueY: 0.118   whiteX: 0.313 whiteY: 0.329
[    83.511] (II) VESA(0): Manufacturer's mask: 0
[    83.511] (II) VESA(0): Supported detailed timing:
[    83.511] (II) VESA(0): clock: 138.5 MHz   Image Size:  345 x 194 mm
[    83.511] (II) VESA(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    83.511] (II) VESA(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    83.511] (II) VESA(0):  LG Display
[    83.511] (II) VESA(0):  LP156WF1-TLE1
[    83.511] (II) VESA(0): EDID (in hex):
[    83.511] (II) VESA(0): 	00ffffffffffff0030e4fb0100000000
[    83.511] (II) VESA(0): 	00130103802313780a08d59f5a509625
[    83.511] (II) VESA(0): 	1e505400000001010101010101010101
[    83.511] (II) VESA(0): 	0101010101011a3680a070381f403020
[    83.511] (II) VESA(0): 	350059c2100000190000000000000000
[    83.511] (II) VESA(0): 	00000000000000000000000000fe004c
[    83.511] (II) VESA(0): 	4720446973706c61790a2020000000fe
[    83.511] (II) VESA(0): 	004c503135365746312d544c4531009c
[    83.512] (II) VESA(0): EDID vendor "LGD", prod id 507
[    83.512] (II) VESA(0): Printing DDC gathered Modelines:
[    83.512] (II) VESA(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 -hsync -vsync (66.6 kHz eP)
[    83.512] (II) VESA(0): Searching for matching VESA mode(s):
[    83.512] Mode: 100 (640x400)
[    83.512] 	ModeAttributes: 0xbb
[    83.512] 	WinAAttributes: 0x7
[    83.512] 	WinBAttributes: 0x0
[    83.512] 	WinGranularity: 64
[    83.512] 	WinSize: 64
[    83.512] 	WinASegment: 0xa000
[    83.512] 	WinBSegment: 0x0
[    83.512] 	WinFuncPtr: 0xc000545d
[    83.512] 	BytesPerScanline: 640
[    83.512] 	XResolution: 640
[    83.512] 	YResolution: 400
[    83.512] 	XCharSize: 8
[    83.512] 	YCharSize: 16
[    83.512] 	NumberOfPlanes: 1
[    83.512] 	BitsPerPixel: 8
[    83.512] 	NumberOfBanks: 1
[    83.512] 	MemoryModel: 4
[    83.512] 	BankSize: 0
[    83.512] 	NumberOfImages: 63
[    83.512] 	RedMaskSize: 0
[    83.512] 	RedFieldPosition: 0
[    83.512] 	GreenMaskSize: 0
[    83.512] 	GreenFieldPosition: 0
[    83.512] 	BlueMaskSize: 0
[    83.512] 	BlueFieldPosition: 0
[    83.512] 	RsvdMaskSize: 0
[    83.512] 	RsvdFieldPosition: 0
[    83.512] 	DirectColorModeInfo: 0
[    83.512] 	PhysBasePtr: 0xc0000000
[    83.512] 	LinBytesPerScanLine: 640
[    83.512] 	BnkNumberOfImagePages: 63
[    83.512] 	LinNumberOfImagePages: 63
[    83.512] 	LinRedMaskSize: 0
[    83.512] 	LinRedFieldPosition: 0
[    83.512] 	LinGreenMaskSize: 0
[    83.512] 	LinGreenFieldPosition: 0
[    83.512] 	LinBlueMaskSize: 0
[    83.512] 	LinBlueFieldPosition: 0
[    83.512] 	LinRsvdMaskSize: 0
[    83.512] 	LinRsvdFieldPosition: 0
[    83.512] 	MaxPixelClock: 400000000
[    83.512] Mode: 101 (640x480)
[    83.512] 	ModeAttributes: 0xbb
[    83.512] 	WinAAttributes: 0x7
[    83.512] 	WinBAttributes: 0x0
[    83.512] 	WinGranularity: 64
[    83.512] 	WinSize: 64
[    83.512] 	WinASegment: 0xa000
[    83.512] 	WinBSegment: 0x0
[    83.512] 	WinFuncPtr: 0xc000545d
[    83.512] 	BytesPerScanline: 640
[    83.512] 	XResolution: 640
[    83.512] 	YResolution: 480
[    83.512] 	XCharSize: 8
[    83.512] 	YCharSize: 16
[    83.512] 	NumberOfPlanes: 1
[    83.512] 	BitsPerPixel: 8
[    83.512] 	NumberOfBanks: 1
[    83.512] 	MemoryModel: 4
[    83.512] 	BankSize: 0
[    83.512] 	NumberOfImages: 50
[    83.512] 	RedMaskSize: 0
[    83.512] 	RedFieldPosition: 0
[    83.512] 	GreenMaskSize: 0
[    83.512] 	GreenFieldPosition: 0
[    83.512] 	BlueMaskSize: 0
[    83.512] 	BlueFieldPosition: 0
[    83.512] 	RsvdMaskSize: 0
[    83.512] 	RsvdFieldPosition: 0
[    83.512] 	DirectColorModeInfo: 0
[    83.512] 	PhysBasePtr: 0xc0000000
[    83.512] 	LinBytesPerScanLine: 640
[    83.512] 	BnkNumberOfImagePages: 50
[    83.512] 	LinNumberOfImagePages: 50
[    83.512] 	LinRedMaskSize: 0
[    83.512] 	LinRedFieldPosition: 0
[    83.512] 	LinGreenMaskSize: 0
[    83.512] 	LinGreenFieldPosition: 0
[    83.512] 	LinBlueMaskSize: 0
[    83.512] 	LinBlueFieldPosition: 0
[    83.512] 	LinRsvdMaskSize: 0
[    83.512] 	LinRsvdFieldPosition: 0
[    83.512] 	MaxPixelClock: 400000000
[    83.513] Mode: 103 (800x600)
[    83.513] 	ModeAttributes: 0xbb
[    83.513] 	WinAAttributes: 0x7
[    83.513] 	WinBAttributes: 0x0
[    83.513] 	WinGranularity: 64
[    83.513] 	WinSize: 64
[    83.513] 	WinASegment: 0xa000
[    83.513] 	WinBSegment: 0x0
[    83.513] 	WinFuncPtr: 0xc000545d
[    83.513] 	BytesPerScanline: 832
[    83.513] 	XResolution: 800
[    83.513] 	YResolution: 600
[    83.513] 	XCharSize: 8
[    83.513] 	YCharSize: 14
[    83.513] 	NumberOfPlanes: 1
[    83.513] 	BitsPerPixel: 8
[    83.513] 	NumberOfBanks: 1
[    83.513] 	MemoryModel: 4
[    83.513] 	BankSize: 0
[    83.513] 	NumberOfImages: 31
[    83.513] 	RedMaskSize: 0
[    83.513] 	RedFieldPosition: 0
[    83.513] 	GreenMaskSize: 0
[    83.513] 	GreenFieldPosition: 0
[    83.513] 	BlueMaskSize: 0
[    83.513] 	BlueFieldPosition: 0
[    83.513] 	RsvdMaskSize: 0
[    83.513] 	RsvdFieldPosition: 0
[    83.513] 	DirectColorModeInfo: 0
[    83.513] 	PhysBasePtr: 0xc0000000
[    83.513] 	LinBytesPerScanLine: 832
[    83.513] 	BnkNumberOfImagePages: 31
[    83.513] 	LinNumberOfImagePages: 31
[    83.513] 	LinRedMaskSize: 0
[    83.513] 	LinRedFieldPosition: 0
[    83.513] 	LinGreenMaskSize: 0
[    83.513] 	LinGreenFieldPosition: 0
[    83.513] 	LinBlueMaskSize: 0
[    83.513] 	LinBlueFieldPosition: 0
[    83.513] 	LinRsvdMaskSize: 0
[    83.513] 	LinRsvdFieldPosition: 0
[    83.513] 	MaxPixelClock: 400000000
[    83.513] Mode: 105 (1024x768)
[    83.513] 	ModeAttributes: 0xbb
[    83.513] 	WinAAttributes: 0x7
[    83.513] 	WinBAttributes: 0x0
[    83.513] 	WinGranularity: 64
[    83.513] 	WinSize: 64
[    83.513] 	WinASegment: 0xa000
[    83.513] 	WinBSegment: 0x0
[    83.513] 	WinFuncPtr: 0xc000545d
[    83.513] 	BytesPerScanline: 1024
[    83.513] 	XResolution: 1024
[    83.513] 	YResolution: 768
[    83.513] 	XCharSize: 8
[    83.513] 	YCharSize: 16
[    83.513] 	NumberOfPlanes: 1
[    83.513] 	BitsPerPixel: 8
[    83.513] 	NumberOfBanks: 1
[    83.513] 	MemoryModel: 4
[    83.513] 	BankSize: 0
[    83.513] 	NumberOfImages: 18
[    83.513] 	RedMaskSize: 0
[    83.513] 	RedFieldPosition: 0
[    83.513] 	GreenMaskSize: 0
[    83.513] 	GreenFieldPosition: 0
[    83.513] 	BlueMaskSize: 0
[    83.513] 	BlueFieldPosition: 0
[    83.513] 	RsvdMaskSize: 0
[    83.513] 	RsvdFieldPosition: 0
[    83.513] 	DirectColorModeInfo: 0
[    83.513] 	PhysBasePtr: 0xc0000000
[    83.513] 	LinBytesPerScanLine: 1024
[    83.513] 	BnkNumberOfImagePages: 18
[    83.513] 	LinNumberOfImagePages: 18
[    83.513] 	LinRedMaskSize: 0
[    83.513] 	LinRedFieldPosition: 0
[    83.513] 	LinGreenMaskSize: 0
[    83.513] 	LinGreenFieldPosition: 0
[    83.513] 	LinBlueMaskSize: 0
[    83.513] 	LinBlueFieldPosition: 0
[    83.513] 	LinRsvdMaskSize: 0
[    83.513] 	LinRsvdFieldPosition: 0
[    83.513] 	MaxPixelClock: 400000000
[    83.513] Mode: 107 (1280x1024)
[    83.513] 	ModeAttributes: 0xbb
[    83.513] 	WinAAttributes: 0x7
[    83.513] 	WinBAttributes: 0x0
[    83.513] 	WinGranularity: 64
[    83.513] 	WinSize: 64
[    83.514] 	WinASegment: 0xa000
[    83.514] 	WinBSegment: 0x0
[    83.514] 	WinFuncPtr: 0xc000545d
[    83.514] 	BytesPerScanline: 1280
[    83.514] 	XResolution: 1280
[    83.514] 	YResolution: 1024
[    83.514] 	XCharSize: 8
[    83.514] 	YCharSize: 16
[    83.514] 	NumberOfPlanes: 1
[    83.514] 	BitsPerPixel: 8
[    83.514] 	NumberOfBanks: 1
[    83.514] 	MemoryModel: 4
[    83.514] 	BankSize: 0
[    83.514] 	NumberOfImages: 11
[    83.514] 	RedMaskSize: 0
[    83.514] 	RedFieldPosition: 0
[    83.514] 	GreenMaskSize: 0
[    83.514] 	GreenFieldPosition: 0
[    83.514] 	BlueMaskSize: 0
[    83.514] 	BlueFieldPosition: 0
[    83.514] 	RsvdMaskSize: 0
[    83.514] 	RsvdFieldPosition: 0
[    83.514] 	DirectColorModeInfo: 0
[    83.514] 	PhysBasePtr: 0xc0000000
[    83.514] 	LinBytesPerScanLine: 1280
[    83.514] 	BnkNumberOfImagePages: 11
[    83.514] 	LinNumberOfImagePages: 11
[    83.514] 	LinRedMaskSize: 0
[    83.514] 	LinRedFieldPosition: 0
[    83.514] 	LinGreenMaskSize: 0
[    83.514] 	LinGreenFieldPosition: 0
[    83.514] 	LinBlueMaskSize: 0
[    83.514] 	LinBlueFieldPosition: 0
[    83.514] 	LinRsvdMaskSize: 0
[    83.514] 	LinRsvdFieldPosition: 0
[    83.514] 	MaxPixelClock: 400000000
[    83.514] Mode: 109 (132x25)
[    83.514] 	ModeAttributes: 0xa
[    83.514] 	WinAAttributes: 0x7
[    83.514] 	WinBAttributes: 0x0
[    83.514] 	WinGranularity: 64
[    83.514] 	WinSize: 64
[    83.514] 	WinASegment: 0xb000
[    83.514] 	WinBSegment: 0x0
[    83.514] 	WinFuncPtr: 0xc000545d
[    83.514] 	BytesPerScanline: 160
[    83.514] 	XResolution: 132
[    83.514] 	YResolution: 25
[    83.514] 	XCharSize: 8
[    83.514] 	YCharSize: 16
[    83.514] 	NumberOfPlanes: 1
[    83.514] 	BitsPerPixel: 4
[    83.514] 	NumberOfBanks: 1
[    83.514] 	MemoryModel: 0
[    83.514] 	BankSize: 0
[    83.514] 	NumberOfImages: 2
[    83.514] 	RedMaskSize: 8
[    83.514] 	RedFieldPosition: 16
[    83.514] 	GreenMaskSize: 8
[    83.514] 	GreenFieldPosition: 8
[    83.514] 	BlueMaskSize: 8
[    83.514] 	BlueFieldPosition: 0
[    83.514] 	RsvdMaskSize: 0
[    83.514] 	RsvdFieldPosition: 0
[    83.514] 	DirectColorModeInfo: 0
[    83.514] 	PhysBasePtr: 0xc0000000
[    83.514] 	LinBytesPerScanLine: 160
[    83.514] 	BnkNumberOfImagePages: 2
[    83.514] 	LinNumberOfImagePages: 2
[    83.514] 	LinRedMaskSize: 8
[    83.514] 	LinRedFieldPosition: 16
[    83.514] 	LinGreenMaskSize: 8
[    83.514] 	LinGreenFieldPosition: 8
[    83.514] 	LinBlueMaskSize: 8
[    83.514] 	LinBlueFieldPosition: 0
[    83.514] 	LinRsvdMaskSize: 0
[    83.514] 	LinRsvdFieldPosition: 0
[    83.514] 	MaxPixelClock: 400000000
[    83.514] Mode: 10a (132x43)
[    83.514] 	ModeAttributes: 0xa
[    83.514] 	WinAAttributes: 0x7
[    83.514] 	WinBAttributes: 0x0
[    83.514] 	WinGranularity: 64
[    83.514] 	WinSize: 64
[    83.514] 	WinASegment: 0xb000
[    83.514] 	WinBSegment: 0x0
[    83.514] 	WinFuncPtr: 0xc000545d
[    83.514] 	BytesPerScanline: 160
[    83.514] 	XResolution: 132
[    83.514] 	YResolution: 43
[    83.514] 	XCharSize: 8
[    83.514] 	YCharSize: 16
[    83.514] 	NumberOfPlanes: 1
[    83.514] 	BitsPerPixel: 4
[    83.514] 	NumberOfBanks: 1
[    83.514] 	MemoryModel: 0
[    83.514] 	BankSize: 0
[    83.514] 	NumberOfImages: 2
[    83.514] 	RedMaskSize: 8
[    83.514] 	RedFieldPosition: 16
[    83.514] 	GreenMaskSize: 8
[    83.514] 	GreenFieldPosition: 8
[    83.514] 	BlueMaskSize: 8
[    83.514] 	BlueFieldPosition: 0
[    83.514] 	RsvdMaskSize: 0
[    83.514] 	RsvdFieldPosition: 0
[    83.514] 	DirectColorModeInfo: 0
[    83.514] 	PhysBasePtr: 0xc0000000
[    83.514] 	LinBytesPerScanLine: 160
[    83.514] 	BnkNumberOfImagePages: 2
[    83.514] 	LinNumberOfImagePages: 2
[    83.514] 	LinRedMaskSize: 8
[    83.514] 	LinRedFieldPosition: 16
[    83.514] 	LinGreenMaskSize: 8
[    83.514] 	LinGreenFieldPosition: 8
[    83.514] 	LinBlueMaskSize: 8
[    83.514] 	LinBlueFieldPosition: 0
[    83.514] 	LinRsvdMaskSize: 0
[    83.514] 	LinRsvdFieldPosition: 0
[    83.514] 	MaxPixelClock: 400000000
[    83.514] Mode: 130 (132x44)
[    83.514] 	ModeAttributes: 0xa
[    83.514] 	WinAAttributes: 0x7
[    83.514] 	WinBAttributes: 0x0
[    83.514] 	WinGranularity: 64
[    83.514] 	WinSize: 64
[    83.514] 	WinASegment: 0xb000
[    83.514] 	WinBSegment: 0x0
[    83.514] 	WinFuncPtr: 0xc000545d
[    83.514] 	BytesPerScanline: 160
[    83.514] 	XResolution: 132
[    83.514] 	YResolution: 44
[    83.514] 	XCharSize: 8
[    83.514] 	YCharSize: 16
[    83.514] 	NumberOfPlanes: 1
[    83.514] 	BitsPerPixel: 4
[    83.514] 	NumberOfBanks: 1
[    83.514] 	MemoryModel: 0
[    83.514] 	BankSize: 0
[    83.514] 	NumberOfImages: 2
[    83.514] 	RedMaskSize: 8
[    83.514] 	RedFieldPosition: 16
[    83.514] 	GreenMaskSize: 8
[    83.514] 	GreenFieldPosition: 8
[    83.514] 	BlueMaskSize: 8
[    83.514] 	BlueFieldPosition: 0
[    83.514] 	RsvdMaskSize: 0
[    83.514] 	RsvdFieldPosition: 0
[    83.514] 	DirectColorModeInfo: 0
[    83.514] 	PhysBasePtr: 0xc0000000
[    83.514] 	LinBytesPerScanLine: 160
[    83.514] 	BnkNumberOfImagePages: 2
[    83.514] 	LinNumberOfImagePages: 2
[    83.514] 	LinRedMaskSize: 8
[    83.514] 	LinRedFieldPosition: 16
[    83.514] 	LinGreenMaskSize: 8
[    83.514] 	LinGreenFieldPosition: 8
[    83.514] 	LinBlueMaskSize: 8
[    83.514] 	LinBlueFieldPosition: 0
[    83.514] 	LinRsvdMaskSize: 0
[    83.514] 	LinRsvdFieldPosition: 0
[    83.514] 	MaxPixelClock: 400000000
[    83.515] Mode: 110 (640x480)
[    83.515] 	ModeAttributes: 0xbb
[    83.515] 	WinAAttributes: 0x7
[    83.515] 	WinBAttributes: 0x0
[    83.515] 	WinGranularity: 64
[    83.515] 	WinSize: 64
[    83.515] 	WinASegment: 0xa000
[    83.515] 	WinBSegment: 0x0
[    83.515] 	WinFuncPtr: 0xc000545d
[    83.515] 	BytesPerScanline: 1280
[    83.515] 	XResolution: 640
[    83.515] 	YResolution: 480
[    83.515] 	XCharSize: 8
[    83.515] 	YCharSize: 16
[    83.515] 	NumberOfPlanes: 1
[    83.515] 	BitsPerPixel: 16
[    83.515] 	NumberOfBanks: 1
[    83.515] 	MemoryModel: 6
[    83.515] 	BankSize: 0
[    83.515] 	NumberOfImages: 24
[    83.515] 	RedMaskSize: 5
[    83.515] 	RedFieldPosition: 10
[    83.515] 	GreenMaskSize: 5
[    83.515] 	GreenFieldPosition: 5
[    83.515] 	BlueMaskSize: 5
[    83.515] 	BlueFieldPosition: 0
[    83.515] 	RsvdMaskSize: 0
[    83.515] 	RsvdFieldPosition: 0
[    83.515] 	DirectColorModeInfo: 0
[    83.515] 	PhysBasePtr: 0xc0000000
[    83.515] 	LinBytesPerScanLine: 1280
[    83.515] 	BnkNumberOfImagePages: 24
[    83.515] 	LinNumberOfImagePages: 24
[    83.515] 	LinRedMaskSize: 5
[    83.515] 	LinRedFieldPosition: 10
[    83.515] 	LinGreenMaskSize: 5
[    83.515] 	LinGreenFieldPosition: 5
[    83.515] 	LinBlueMaskSize: 5
[    83.515] 	LinBlueFieldPosition: 0
[    83.515] 	LinRsvdMaskSize: 0
[    83.515] 	LinRsvdFieldPosition: 0
[    83.515] 	MaxPixelClock: 400000000
[    83.515] Mode: 111 (640x480)
[    83.515] 	ModeAttributes: 0xbb
[    83.515] 	WinAAttributes: 0x7
[    83.515] 	WinBAttributes: 0x0
[    83.515] 	WinGranularity: 64
[    83.515] 	WinSize: 64
[    83.515] 	WinASegment: 0xa000
[    83.515] 	WinBSegment: 0x0
[    83.515] 	WinFuncPtr: 0xc000545d
[    83.515] 	BytesPerScanline: 1280
[    83.515] 	XResolution: 640
[    83.515] 	YResolution: 480
[    83.515] 	XCharSize: 8
[    83.515] 	YCharSize: 16
[    83.515] 	NumberOfPlanes: 1
[    83.515] 	BitsPerPixel: 16
[    83.515] 	NumberOfBanks: 1
[    83.515] 	MemoryModel: 6
[    83.515] 	BankSize: 0
[    83.515] 	NumberOfImages: 24
[    83.515] 	RedMaskSize: 5
[    83.515] 	RedFieldPosition: 11
[    83.515] 	GreenMaskSize: 6
[    83.515] 	GreenFieldPosition: 5
[    83.515] 	BlueMaskSize: 5
[    83.515] 	BlueFieldPosition: 0
[    83.515] 	RsvdMaskSize: 0
[    83.515] 	RsvdFieldPosition: 0
[    83.515] 	DirectColorModeInfo: 0
[    83.515] 	PhysBasePtr: 0xc0000000
[    83.515] 	LinBytesPerScanLine: 1280
[    83.515] 	BnkNumberOfImagePages: 24
[    83.515] 	LinNumberOfImagePages: 24
[    83.515] 	LinRedMaskSize: 5
[    83.515] 	LinRedFieldPosition: 11
[    83.515] 	LinGreenMaskSize: 6
[    83.515] 	LinGreenFieldPosition: 5
[    83.515] 	LinBlueMaskSize: 5
[    83.515] 	LinBlueFieldPosition: 0
[    83.515] 	LinRsvdMaskSize: 0
[    83.515] 	LinRsvdFieldPosition: 0
[    83.515] 	MaxPixelClock: 400000000
[    83.515] Mode: 113 (800x600)
[    83.515] 	ModeAttributes: 0xbb
[    83.515] 	WinAAttributes: 0x7
[    83.515] 	WinBAttributes: 0x0
[    83.515] 	WinGranularity: 64
[    83.515] 	WinSize: 64
[    83.515] 	WinASegment: 0xa000
[    83.515] 	WinBSegment: 0x0
[    83.515] 	WinFuncPtr: 0xc000545d
[    83.515] 	BytesPerScanline: 1600
[    83.515] 	XResolution: 800
[    83.515] 	YResolution: 600
[    83.515] 	XCharSize: 8
[    83.515] 	YCharSize: 14
[    83.515] 	NumberOfPlanes: 1
[    83.515] 	BitsPerPixel: 16
[    83.516] 	NumberOfBanks: 1
[    83.516] 	MemoryModel: 6
[    83.516] 	BankSize: 0
[    83.516] 	NumberOfImages: 16
[    83.516] 	RedMaskSize: 5
[    83.516] 	RedFieldPosition: 10
[    83.516] 	GreenMaskSize: 5
[    83.516] 	GreenFieldPosition: 5
[    83.516] 	BlueMaskSize: 5
[    83.516] 	BlueFieldPosition: 0
[    83.516] 	RsvdMaskSize: 0
[    83.516] 	RsvdFieldPosition: 0
[    83.516] 	DirectColorModeInfo: 0
[    83.516] 	PhysBasePtr: 0xc0000000
[    83.516] 	LinBytesPerScanLine: 1600
[    83.516] 	BnkNumberOfImagePages: 16
[    83.516] 	LinNumberOfImagePages: 16
[    83.516] 	LinRedMaskSize: 5
[    83.516] 	LinRedFieldPosition: 10
[    83.516] 	LinGreenMaskSize: 5
[    83.516] 	LinGreenFieldPosition: 5
[    83.516] 	LinBlueMaskSize: 5
[    83.516] 	LinBlueFieldPosition: 0
[    83.516] 	LinRsvdMaskSize: 0
[    83.516] 	LinRsvdFieldPosition: 0
[    83.516] 	MaxPixelClock: 400000000
[    83.516] Mode: 114 (800x600)
[    83.516] 	ModeAttributes: 0xbb
[    83.516] 	WinAAttributes: 0x7
[    83.516] 	WinBAttributes: 0x0
[    83.516] 	WinGranularity: 64
[    83.516] 	WinSize: 64
[    83.516] 	WinASegment: 0xa000
[    83.516] 	WinBSegment: 0x0
[    83.516] 	WinFuncPtr: 0xc000545d
[    83.516] 	BytesPerScanline: 1600
[    83.516] 	XResolution: 800
[    83.516] 	YResolution: 600
[    83.516] 	XCharSize: 8
[    83.516] 	YCharSize: 14
[    83.516] 	NumberOfPlanes: 1
[    83.516] 	BitsPerPixel: 16
[    83.516] 	NumberOfBanks: 1
[    83.516] 	MemoryModel: 6
[    83.516] 	BankSize: 0
[    83.516] 	NumberOfImages: 16
[    83.516] 	RedMaskSize: 5
[    83.516] 	RedFieldPosition: 11
[    83.516] 	GreenMaskSize: 6
[    83.516] 	GreenFieldPosition: 5
[    83.516] 	BlueMaskSize: 5
[    83.516] 	BlueFieldPosition: 0
[    83.516] 	RsvdMaskSize: 0
[    83.516] 	RsvdFieldPosition: 0
[    83.516] 	DirectColorModeInfo: 0
[    83.516] 	PhysBasePtr: 0xc0000000
[    83.516] 	LinBytesPerScanLine: 1600
[    83.516] 	BnkNumberOfImagePages: 16
[    83.516] 	LinNumberOfImagePages: 16
[    83.516] 	LinRedMaskSize: 5
[    83.516] 	LinRedFieldPosition: 11
[    83.516] 	LinGreenMaskSize: 6
[    83.516] 	LinGreenFieldPosition: 5
[    83.516] 	LinBlueMaskSize: 5
[    83.516] 	LinBlueFieldPosition: 0
[    83.516] 	LinRsvdMaskSize: 0
[    83.516] 	LinRsvdFieldPosition: 0
[    83.516] 	MaxPixelClock: 400000000
[    83.516] Mode: 116 (1024x768)
[    83.516] 	ModeAttributes: 0xbb
[    83.516] 	WinAAttributes: 0x7
[    83.516] 	WinBAttributes: 0x0
[    83.516] 	WinGranularity: 64
[    83.516] 	WinSize: 64
[    83.516] 	WinASegment: 0xa000
[    83.516] 	WinBSegment: 0x0
[    83.516] 	WinFuncPtr: 0xc000545d
[    83.516] 	BytesPerScanline: 2048
[    83.516] 	XResolution: 1024
[    83.516] 	YResolution: 768
[    83.516] 	XCharSize: 8
[    83.516] 	YCharSize: 16
[    83.516] 	NumberOfPlanes: 1
[    83.516] 	BitsPerPixel: 16
[    83.516] 	NumberOfBanks: 1
[    83.516] 	MemoryModel: 6
[    83.516] 	BankSize: 0
[    83.516] 	NumberOfImages: 9
[    83.516] 	RedMaskSize: 5
[    83.516] 	RedFieldPosition: 10
[    83.516] 	GreenMaskSize: 5
[    83.516] 	GreenFieldPosition: 5
[    83.516] 	BlueMaskSize: 5
[    83.516] 	BlueFieldPosition: 0
[    83.516] 	RsvdMaskSize: 0
[    83.516] 	RsvdFieldPosition: 0
[    83.516] 	DirectColorModeInfo: 0
[    83.516] 	PhysBasePtr: 0xc0000000
[    83.516] 	LinBytesPerScanLine: 2048
[    83.516] 	BnkNumberOfImagePages: 9
[    83.516] 	LinNumberOfImagePages: 9
[    83.516] 	LinRedMaskSize: 5
[    83.516] 	LinRedFieldPosition: 10
[    83.516] 	LinGreenMaskSize: 5
[    83.516] 	LinGreenFieldPosition: 5
[    83.516] 	LinBlueMaskSize: 5
[    83.516] 	LinBlueFieldPosition: 0
[    83.516] 	LinRsvdMaskSize: 0
[    83.516] 	LinRsvdFieldPosition: 0
[    83.516] 	MaxPixelClock: 400000000
[    83.517] Mode: 117 (1024x768)
[    83.517] 	ModeAttributes: 0xbb
[    83.517] 	WinAAttributes: 0x7
[    83.517] 	WinBAttributes: 0x0
[    83.517] 	WinGranularity: 64
[    83.517] 	WinSize: 64
[    83.517] 	WinASegment: 0xa000
[    83.517] 	WinBSegment: 0x0
[    83.517] 	WinFuncPtr: 0xc000545d
[    83.517] 	BytesPerScanline: 2048
[    83.517] 	XResolution: 1024
[    83.517] 	YResolution: 768
[    83.517] 	XCharSize: 8
[    83.517] 	YCharSize: 16
[    83.517] 	NumberOfPlanes: 1
[    83.517] 	BitsPerPixel: 16
[    83.517] 	NumberOfBanks: 1
[    83.517] 	MemoryModel: 6
[    83.517] 	BankSize: 0
[    83.517] 	NumberOfImages: 9
[    83.517] 	RedMaskSize: 5
[    83.517] 	RedFieldPosition: 11
[    83.517] 	GreenMaskSize: 6
[    83.517] 	GreenFieldPosition: 5
[    83.517] 	BlueMaskSize: 5
[    83.517] 	BlueFieldPosition: 0
[    83.517] 	RsvdMaskSize: 0
[    83.517] 	RsvdFieldPosition: 0
[    83.517] 	DirectColorModeInfo: 0
[    83.517] 	PhysBasePtr: 0xc0000000
[    83.517] 	LinBytesPerScanLine: 2048
[    83.517] 	BnkNumberOfImagePages: 9
[    83.517] 	LinNumberOfImagePages: 9
[    83.517] 	LinRedMaskSize: 5
[    83.517] 	LinRedFieldPosition: 11
[    83.517] 	LinGreenMaskSize: 6
[    83.517] 	LinGreenFieldPosition: 5
[    83.517] 	LinBlueMaskSize: 5
[    83.517] 	LinBlueFieldPosition: 0
[    83.517] 	LinRsvdMaskSize: 0
[    83.517] 	LinRsvdFieldPosition: 0
[    83.517] 	MaxPixelClock: 400000000
[    83.517] Mode: 119 (1280x1024)
[    83.517] 	ModeAttributes: 0xbb
[    83.517] 	WinAAttributes: 0x7
[    83.517] 	WinBAttributes: 0x0
[    83.517] 	WinGranularity: 64
[    83.517] 	WinSize: 64
[    83.517] 	WinASegment: 0xa000
[    83.517] 	WinBSegment: 0x0
[    83.517] 	WinFuncPtr: 0xc000545d
[    83.517] 	BytesPerScanline: 2560
[    83.517] 	XResolution: 1280
[    83.517] 	YResolution: 1024
[    83.517] 	XCharSize: 8
[    83.517] 	YCharSize: 16
[    83.517] 	NumberOfPlanes: 1
[    83.517] 	BitsPerPixel: 16
[    83.517] 	NumberOfBanks: 1
[    83.517] 	MemoryModel: 6
[    83.517] 	BankSize: 0
[    83.517] 	NumberOfImages: 5
[    83.517] 	RedMaskSize: 5
[    83.517] 	RedFieldPosition: 10
[    83.517] 	GreenMaskSize: 5
[    83.517] 	GreenFieldPosition: 5
[    83.517] 	BlueMaskSize: 5
[    83.517] 	BlueFieldPosition: 0
[    83.517] 	RsvdMaskSize: 0
[    83.517] 	RsvdFieldPosition: 0
[    83.517] 	DirectColorModeInfo: 0
[    83.517] 	PhysBasePtr: 0xc0000000
[    83.517] 	LinBytesPerScanLine: 2560
[    83.517] 	BnkNumberOfImagePages: 5
[    83.517] 	LinNumberOfImagePages: 5
[    83.517] 	LinRedMaskSize: 5
[    83.517] 	LinRedFieldPosition: 10
[    83.517] 	LinGreenMaskSize: 5
[    83.517] 	LinGreenFieldPosition: 5
[    83.517] 	LinBlueMaskSize: 5
[    83.517] 	LinBlueFieldPosition: 0
[    83.517] 	LinRsvdMaskSize: 0
[    83.517] 	LinRsvdFieldPosition: 0
[    83.517] 	MaxPixelClock: 400000000
[    83.518] Mode: 11a (1280x1024)
[    83.518] 	ModeAttributes: 0xbb
[    83.518] 	WinAAttributes: 0x7
[    83.518] 	WinBAttributes: 0x0
[    83.518] 	WinGranularity: 64
[    83.518] 	WinSize: 64
[    83.518] 	WinASegment: 0xa000
[    83.518] 	WinBSegment: 0x0
[    83.518] 	WinFuncPtr: 0xc000545d
[    83.518] 	BytesPerScanline: 2560
[    83.518] 	XResolution: 1280
[    83.518] 	YResolution: 1024
[    83.518] 	XCharSize: 8
[    83.518] 	YCharSize: 16
[    83.518] 	NumberOfPlanes: 1
[    83.518] 	BitsPerPixel: 16
[    83.518] 	NumberOfBanks: 1
[    83.518] 	MemoryModel: 6
[    83.518] 	BankSize: 0
[    83.518] 	NumberOfImages: 5
[    83.518] 	RedMaskSize: 5
[    83.518] 	RedFieldPosition: 11
[    83.518] 	GreenMaskSize: 6
[    83.518] 	GreenFieldPosition: 5
[    83.518] 	BlueMaskSize: 5
[    83.518] 	BlueFieldPosition: 0
[    83.518] 	RsvdMaskSize: 0
[    83.518] 	RsvdFieldPosition: 0
[    83.518] 	DirectColorModeInfo: 0
[    83.518] 	PhysBasePtr: 0xc0000000
[    83.518] 	LinBytesPerScanLine: 2560
[    83.518] 	BnkNumberOfImagePages: 5
[    83.518] 	LinNumberOfImagePages: 5
[    83.518] 	LinRedMaskSize: 5
[    83.518] 	LinRedFieldPosition: 11
[    83.518] 	LinGreenMaskSize: 6
[    83.518] 	LinGreenFieldPosition: 5
[    83.518] 	LinBlueMaskSize: 5
[    83.518] 	LinBlueFieldPosition: 0
[    83.518] 	LinRsvdMaskSize: 0
[    83.518] 	LinRsvdFieldPosition: 0
[    83.518] 	MaxPixelClock: 400000000
[    83.518] Mode: 10d (320x200)
[    83.518] 	ModeAttributes: 0xbb
[    83.518] 	WinAAttributes: 0x7
[    83.518] 	WinBAttributes: 0x0
[    83.518] 	WinGranularity: 64
[    83.518] 	WinSize: 64
[    83.518] 	WinASegment: 0xa000
[    83.518] 	WinBSegment: 0x0
[    83.518] 	WinFuncPtr: 0xc000545d
[    83.518] 	BytesPerScanline: 640
[    83.518] 	XResolution: 320
[    83.518] 	YResolution: 200
[    83.518] 	XCharSize: 8
[    83.518] 	YCharSize: 8
[    83.518] 	NumberOfPlanes: 1
[    83.518] 	BitsPerPixel: 16
[    83.518] 	NumberOfBanks: 1
[    83.518] 	MemoryModel: 6
[    83.518] 	BankSize: 0
[    83.518] 	NumberOfImages: 127
[    83.518] 	RedMaskSize: 5
[    83.518] 	RedFieldPosition: 10
[    83.518] 	GreenMaskSize: 5
[    83.518] 	GreenFieldPosition: 5
[    83.518] 	BlueMaskSize: 5
[    83.518] 	BlueFieldPosition: 0
[    83.518] 	RsvdMaskSize: 0
[    83.518] 	RsvdFieldPosition: 0
[    83.518] 	DirectColorModeInfo: 0
[    83.518] 	PhysBasePtr: 0xc0000000
[    83.518] 	LinBytesPerScanLine: 640
[    83.518] 	BnkNumberOfImagePages: 127
[    83.518] 	LinNumberOfImagePages: 127
[    83.518] 	LinRedMaskSize: 5
[    83.518] 	LinRedFieldPosition: 10
[    83.518] 	LinGreenMaskSize: 5
[    83.518] 	LinGreenFieldPosition: 5
[    83.518] 	LinBlueMaskSize: 5
[    83.518] 	LinBlueFieldPosition: 0
[    83.518] 	LinRsvdMaskSize: 0
[    83.518] 	LinRsvdFieldPosition: 0
[    83.518] 	MaxPixelClock: 400000000
[    83.518] Mode: 10e (320x200)
[    83.518] 	ModeAttributes: 0xbb
[    83.518] 	WinAAttributes: 0x7
[    83.518] 	WinBAttributes: 0x0
[    83.518] 	WinGranularity: 64
[    83.518] 	WinSize: 64
[    83.518] 	WinASegment: 0xa000
[    83.518] 	WinBSegment: 0x0
[    83.518] 	WinFuncPtr: 0xc000545d
[    83.518] 	BytesPerScanline: 640
[    83.518] 	XResolution: 320
[    83.518] 	YResolution: 200
[    83.518] 	XCharSize: 8
[    83.518] 	YCharSize: 8
[    83.518] 	NumberOfPlanes: 1
[    83.518] 	BitsPerPixel: 16
[    83.518] 	NumberOfBanks: 1
[    83.518] 	MemoryModel: 6
[    83.518] 	BankSize: 0
[    83.518] 	NumberOfImages: 127
[    83.518] 	RedMaskSize: 5
[    83.518] 	RedFieldPosition: 11
[    83.518] 	GreenMaskSize: 6
[    83.518] 	GreenFieldPosition: 5
[    83.518] 	BlueMaskSize: 5
[    83.518] 	BlueFieldPosition: 0
[    83.518] 	RsvdMaskSize: 0
[    83.518] 	RsvdFieldPosition: 0
[    83.518] 	DirectColorModeInfo: 0
[    83.518] 	PhysBasePtr: 0xc0000000
[    83.518] 	LinBytesPerScanLine: 640
[    83.518] 	BnkNumberOfImagePages: 127
[    83.518] 	LinNumberOfImagePages: 127
[    83.518] 	LinRedMaskSize: 5
[    83.518] 	LinRedFieldPosition: 11
[    83.518] 	LinGreenMaskSize: 6
[    83.518] 	LinGreenFieldPosition: 5
[    83.518] 	LinBlueMaskSize: 5
[    83.518] 	LinBlueFieldPosition: 0
[    83.518] 	LinRsvdMaskSize: 0
[    83.518] 	LinRsvdFieldPosition: 0
[    83.518] 	MaxPixelClock: 400000000
[    83.519] *Mode: 120 (320x200)
[    83.519] 	ModeAttributes: 0xbb
[    83.519] 	WinAAttributes: 0x7
[    83.519] 	WinBAttributes: 0x0
[    83.519] 	WinGranularity: 64
[    83.519] 	WinSize: 64
[    83.519] 	WinASegment: 0xa000
[    83.519] 	WinBSegment: 0x0
[    83.519] 	WinFuncPtr: 0xc000545d
[    83.519] 	BytesPerScanline: 1280
[    83.519] 	XResolution: 320
[    83.519] 	YResolution: 200
[    83.519] 	XCharSize: 8
[    83.519] 	YCharSize: 8
[    83.519] 	NumberOfPlanes: 1
[    83.519] 	BitsPerPixel: 32
[    83.519] 	NumberOfBanks: 1
[    83.519] 	MemoryModel: 6
[    83.519] 	BankSize: 0
[    83.519] 	NumberOfImages: 63
[    83.519] 	RedMaskSize: 8
[    83.519] 	RedFieldPosition: 16
[    83.519] 	GreenMaskSize: 8
[    83.519] 	GreenFieldPosition: 8
[    83.519] 	BlueMaskSize: 8
[    83.519] 	BlueFieldPosition: 0
[    83.519] 	RsvdMaskSize: 0
[    83.519] 	RsvdFieldPosition: 0
[    83.519] 	DirectColorModeInfo: 0
[    83.519] 	PhysBasePtr: 0xc0000000
[    83.519] 	LinBytesPerScanLine: 1280
[    83.519] 	BnkNumberOfImagePages: 63
[    83.519] 	LinNumberOfImagePages: 63
[    83.519] 	LinRedMaskSize: 8
[    83.519] 	LinRedFieldPosition: 16
[    83.519] 	LinGreenMaskSize: 8
[    83.519] 	LinGreenFieldPosition: 8
[    83.519] 	LinBlueMaskSize: 8
[    83.519] 	LinBlueFieldPosition: 0
[    83.519] 	LinRsvdMaskSize: 0
[    83.519] 	LinRsvdFieldPosition: 0
[    83.519] 	MaxPixelClock: 400000000
[    83.519] Mode: 193 (320x240)
[    83.519] 	ModeAttributes: 0xbb
[    83.519] 	WinAAttributes: 0x7
[    83.519] 	WinBAttributes: 0x0
[    83.519] 	WinGranularity: 64
[    83.519] 	WinSize: 64
[    83.519] 	WinASegment: 0xa000
[    83.519] 	WinBSegment: 0x0
[    83.519] 	WinFuncPtr: 0xc000545d
[    83.519] 	BytesPerScanline: 320
[    83.519] 	XResolution: 320
[    83.519] 	YResolution: 240
[    83.519] 	XCharSize: 8
[    83.519] 	YCharSize: 8
[    83.519] 	NumberOfPlanes: 1
[    83.519] 	BitsPerPixel: 8
[    83.519] 	NumberOfBanks: 1
[    83.519] 	MemoryModel: 4
[    83.519] 	BankSize: 0
[    83.519] 	NumberOfImages: 127
[    83.519] 	RedMaskSize: 0
[    83.519] 	RedFieldPosition: 0
[    83.519] 	GreenMaskSize: 0
[    83.519] 	GreenFieldPosition: 0
[    83.519] 	BlueMaskSize: 0
[    83.519] 	BlueFieldPosition: 0
[    83.519] 	RsvdMaskSize: 0
[    83.519] 	RsvdFieldPosition: 0
[    83.519] 	DirectColorModeInfo: 0
[    83.519] 	PhysBasePtr: 0xc0000000
[    83.519] 	LinBytesPerScanLine: 320
[    83.519] 	BnkNumberOfImagePages: 127
[    83.519] 	LinNumberOfImagePages: 127
[    83.519] 	LinRedMaskSize: 0
[    83.519] 	LinRedFieldPosition: 0
[    83.519] 	LinGreenMaskSize: 0
[    83.519] 	LinGreenFieldPosition: 0
[    83.519] 	LinBlueMaskSize: 0
[    83.519] 	LinBlueFieldPosition: 0
[    83.519] 	LinRsvdMaskSize: 0
[    83.519] 	LinRsvdFieldPosition: 0
[    83.519] 	MaxPixelClock: 400000000
[    83.520] Mode: 195 (320x240)
[    83.520] 	ModeAttributes: 0xbb
[    83.520] 	WinAAttributes: 0x7
[    83.520] 	WinBAttributes: 0x0
[    83.520] 	WinGranularity: 64
[    83.520] 	WinSize: 64
[    83.520] 	WinASegment: 0xa000
[    83.520] 	WinBSegment: 0x0
[    83.520] 	WinFuncPtr: 0xc000545d
[    83.520] 	BytesPerScanline: 640
[    83.520] 	XResolution: 320
[    83.520] 	YResolution: 240
[    83.520] 	XCharSize: 8
[    83.520] 	YCharSize: 8
[    83.520] 	NumberOfPlanes: 1
[    83.520] 	BitsPerPixel: 16
[    83.520] 	NumberOfBanks: 1
[    83.520] 	MemoryModel: 6
[    83.520] 	BankSize: 0
[    83.520] 	NumberOfImages: 84
[    83.520] 	RedMaskSize: 5
[    83.520] 	RedFieldPosition: 11
[    83.520] 	GreenMaskSize: 6
[    83.520] 	GreenFieldPosition: 5
[    83.520] 	BlueMaskSize: 5
[    83.520] 	BlueFieldPosition: 0
[    83.520] 	RsvdMaskSize: 0
[    83.520] 	RsvdFieldPosition: 0
[    83.520] 	DirectColorModeInfo: 0
[    83.520] 	PhysBasePtr: 0xc0000000
[    83.520] 	LinBytesPerScanLine: 640
[    83.520] 	BnkNumberOfImagePages: 84
[    83.520] 	LinNumberOfImagePages: 84
[    83.520] 	LinRedMaskSize: 5
[    83.520] 	LinRedFieldPosition: 11
[    83.520] 	LinGreenMaskSize: 6
[    83.520] 	LinGreenFieldPosition: 5
[    83.520] 	LinBlueMaskSize: 5
[    83.520] 	LinBlueFieldPosition: 0
[    83.520] 	LinRsvdMaskSize: 0
[    83.520] 	LinRsvdFieldPosition: 0
[    83.520] 	MaxPixelClock: 400000000
[    83.520] *Mode: 196 (320x240)
[    83.520] 	ModeAttributes: 0xbb
[    83.520] 	WinAAttributes: 0x7
[    83.520] 	WinBAttributes: 0x0
[    83.520] 	WinGranularity: 64
[    83.520] 	WinSize: 64
[    83.520] 	WinASegment: 0xa000
[    83.520] 	WinBSegment: 0x0
[    83.520] 	WinFuncPtr: 0xc000545d
[    83.520] 	BytesPerScanline: 1280
[    83.520] 	XResolution: 320
[    83.520] 	YResolution: 240
[    83.520] 	XCharSize: 8
[    83.520] 	YCharSize: 8
[    83.520] 	NumberOfPlanes: 1
[    83.520] 	BitsPerPixel: 32
[    83.520] 	NumberOfBanks: 1
[    83.520] 	MemoryModel: 6
[    83.520] 	BankSize: 0
[    83.520] 	NumberOfImages: 50
[    83.520] 	RedMaskSize: 8
[    83.520] 	RedFieldPosition: 16
[    83.520] 	GreenMaskSize: 8
[    83.520] 	GreenFieldPosition: 8
[    83.520] 	BlueMaskSize: 8
[    83.520] 	BlueFieldPosition: 0
[    83.520] 	RsvdMaskSize: 0
[    83.520] 	RsvdFieldPosition: 0
[    83.520] 	DirectColorModeInfo: 0
[    83.520] 	PhysBasePtr: 0xc0000000
[    83.520] 	LinBytesPerScanLine: 1280
[    83.520] 	BnkNumberOfImagePages: 50
[    83.520] 	LinNumberOfImagePages: 50
[    83.520] 	LinRedMaskSize: 8
[    83.520] 	LinRedFieldPosition: 16
[    83.520] 	LinGreenMaskSize: 8
[    83.520] 	LinGreenFieldPosition: 8
[    83.520] 	LinBlueMaskSize: 8
[    83.520] 	LinBlueFieldPosition: 0
[    83.520] 	LinRsvdMaskSize: 0
[    83.520] 	LinRsvdFieldPosition: 0
[    83.520] 	MaxPixelClock: 400000000
[    83.520] Mode: 1b3 (512x384)
[    83.520] 	ModeAttributes: 0xbb
[    83.520] 	WinAAttributes: 0x7
[    83.520] 	WinBAttributes: 0x0
[    83.520] 	WinGranularity: 64
[    83.520] 	WinSize: 64
[    83.520] 	WinASegment: 0xa000
[    83.520] 	WinBSegment: 0x0
[    83.520] 	WinFuncPtr: 0xc000545d
[    83.520] 	BytesPerScanline: 512
[    83.520] 	XResolution: 512
[    83.520] 	YResolution: 384
[    83.520] 	XCharSize: 8
[    83.520] 	YCharSize: 16
[    83.520] 	NumberOfPlanes: 1
[    83.520] 	BitsPerPixel: 8
[    83.520] 	NumberOfBanks: 1
[    83.520] 	MemoryModel: 4
[    83.520] 	BankSize: 0
[    83.520] 	NumberOfImages: 63
[    83.520] 	RedMaskSize: 0
[    83.520] 	RedFieldPosition: 0
[    83.520] 	GreenMaskSize: 0
[    83.520] 	GreenFieldPosition: 0
[    83.520] 	BlueMaskSize: 0
[    83.520] 	BlueFieldPosition: 0
[    83.520] 	RsvdMaskSize: 0
[    83.521] 	RsvdFieldPosition: 0
[    83.521] 	DirectColorModeInfo: 0
[    83.521] 	PhysBasePtr: 0xc0000000
[    83.521] 	LinBytesPerScanLine: 512
[    83.521] 	BnkNumberOfImagePages: 63
[    83.521] 	LinNumberOfImagePages: 63
[    83.521] 	LinRedMaskSize: 0
[    83.521] 	LinRedFieldPosition: 0
[    83.521] 	LinGreenMaskSize: 0
[    83.521] 	LinGreenFieldPosition: 0
[    83.521] 	LinBlueMaskSize: 0
[    83.521] 	LinBlueFieldPosition: 0
[    83.521] 	LinRsvdMaskSize: 0
[    83.521] 	LinRsvdFieldPosition: 0
[    83.521] 	MaxPixelClock: 400000000
[    83.521] Mode: 1b5 (512x384)
[    83.521] 	ModeAttributes: 0xbb
[    83.521] 	WinAAttributes: 0x7
[    83.521] 	WinBAttributes: 0x0
[    83.521] 	WinGranularity: 64
[    83.521] 	WinSize: 64
[    83.521] 	WinASegment: 0xa000
[    83.521] 	WinBSegment: 0x0
[    83.521] 	WinFuncPtr: 0xc000545d
[    83.521] 	BytesPerScanline: 1024
[    83.521] 	XResolution: 512
[    83.521] 	YResolution: 384
[    83.521] 	XCharSize: 8
[    83.521] 	YCharSize: 16
[    83.521] 	NumberOfPlanes: 1
[    83.521] 	BitsPerPixel: 16
[    83.521] 	NumberOfBanks: 1
[    83.521] 	MemoryModel: 6
[    83.521] 	BankSize: 0
[    83.521] 	NumberOfImages: 35
[    83.521] 	RedMaskSize: 5
[    83.521] 	RedFieldPosition: 11
[    83.521] 	GreenMaskSize: 6
[    83.521] 	GreenFieldPosition: 5
[    83.521] 	BlueMaskSize: 5
[    83.521] 	BlueFieldPosition: 0
[    83.521] 	RsvdMaskSize: 0
[    83.521] 	RsvdFieldPosition: 0
[    83.521] 	DirectColorModeInfo: 0
[    83.521] 	PhysBasePtr: 0xc0000000
[    83.521] 	LinBytesPerScanLine: 1024
[    83.521] 	BnkNumberOfImagePages: 35
[    83.521] 	LinNumberOfImagePages: 35
[    83.521] 	LinRedMaskSize: 5
[    83.521] 	LinRedFieldPosition: 11
[    83.521] 	LinGreenMaskSize: 6
[    83.521] 	LinGreenFieldPosition: 5
[    83.521] 	LinBlueMaskSize: 5
[    83.521] 	LinBlueFieldPosition: 0
[    83.521] 	LinRsvdMaskSize: 0
[    83.521] 	LinRsvdFieldPosition: 0
[    83.521] 	MaxPixelClock: 400000000
[    83.521] *Mode: 1b6 (512x384)
[    83.521] 	ModeAttributes: 0xbb
[    83.521] 	WinAAttributes: 0x7
[    83.521] 	WinBAttributes: 0x0
[    83.521] 	WinGranularity: 64
[    83.521] 	WinSize: 64
[    83.521] 	WinASegment: 0xa000
[    83.521] 	WinBSegment: 0x0
[    83.521] 	WinFuncPtr: 0xc000545d
[    83.521] 	BytesPerScanline: 2048
[    83.521] 	XResolution: 512
[    83.521] 	YResolution: 384
[    83.521] 	XCharSize: 8
[    83.521] 	YCharSize: 16
[    83.521] 	NumberOfPlanes: 1
[    83.521] 	BitsPerPixel: 32
[    83.521] 	NumberOfBanks: 1
[    83.521] 	MemoryModel: 6
[    83.521] 	BankSize: 0
[    83.521] 	NumberOfImages: 18
[    83.521] 	RedMaskSize: 8
[    83.521] 	RedFieldPosition: 16
[    83.521] 	GreenMaskSize: 8
[    83.521] 	GreenFieldPosition: 8
[    83.521] 	BlueMaskSize: 8
[    83.521] 	BlueFieldPosition: 0
[    83.521] 	RsvdMaskSize: 0
[    83.521] 	RsvdFieldPosition: 0
[    83.521] 	DirectColorModeInfo: 0
[    83.521] 	PhysBasePtr: 0xc0000000
[    83.521] 	LinBytesPerScanLine: 2048
[    83.521] 	BnkNumberOfImagePages: 18
[    83.521] 	LinNumberOfImagePages: 18
[    83.521] 	LinRedMaskSize: 8
[    83.521] 	LinRedFieldPosition: 16
[    83.521] 	LinGreenMaskSize: 8
[    83.521] 	LinGreenFieldPosition: 8
[    83.521] 	LinBlueMaskSize: 8
[    83.521] 	LinBlueFieldPosition: 0
[    83.521] 	LinRsvdMaskSize: 0
[    83.521] 	LinRsvdFieldPosition: 0
[    83.521] 	MaxPixelClock: 400000000
[    83.522] Mode: 1c3 (640x350)
[    83.522] 	ModeAttributes: 0xbb
[    83.522] 	WinAAttributes: 0x7
[    83.522] 	WinBAttributes: 0x0
[    83.522] 	WinGranularity: 64
[    83.522] 	WinSize: 64
[    83.522] 	WinASegment: 0xa000
[    83.522] 	WinBSegment: 0x0
[    83.522] 	WinFuncPtr: 0xc000545d
[    83.522] 	BytesPerScanline: 640
[    83.522] 	XResolution: 640
[    83.522] 	YResolution: 350
[    83.522] 	XCharSize: 8
[    83.522] 	YCharSize: 14
[    83.522] 	NumberOfPlanes: 1
[    83.522] 	BitsPerPixel: 8
[    83.522] 	NumberOfBanks: 1
[    83.522] 	MemoryModel: 4
[    83.522] 	BankSize: 0
[    83.522] 	NumberOfImages: 63
[    83.522] 	RedMaskSize: 0
[    83.522] 	RedFieldPosition: 0
[    83.522] 	GreenMaskSize: 0
[    83.522] 	GreenFieldPosition: 0
[    83.522] 	BlueMaskSize: 0
[    83.522] 	BlueFieldPosition: 0
[    83.522] 	RsvdMaskSize: 0
[    83.522] 	RsvdFieldPosition: 0
[    83.522] 	DirectColorModeInfo: 0
[    83.522] 	PhysBasePtr: 0xc0000000
[    83.522] 	LinBytesPerScanLine: 640
[    83.522] 	BnkNumberOfImagePages: 63
[    83.522] 	LinNumberOfImagePages: 63
[    83.522] 	LinRedMaskSize: 0
[    83.522] 	LinRedFieldPosition: 0
[    83.522] 	LinGreenMaskSize: 0
[    83.522] 	LinGreenFieldPosition: 0
[    83.522] 	LinBlueMaskSize: 0
[    83.522] 	LinBlueFieldPosition: 0
[    83.522] 	LinRsvdMaskSize: 0
[    83.522] 	LinRsvdFieldPosition: 0
[    83.522] 	MaxPixelClock: 400000000
[    83.522] Mode: 1c5 (640x350)
[    83.522] 	ModeAttributes: 0xbb
[    83.522] 	WinAAttributes: 0x7
[    83.522] 	WinBAttributes: 0x0
[    83.522] 	WinGranularity: 64
[    83.522] 	WinSize: 64
[    83.522] 	WinASegment: 0xa000
[    83.522] 	WinBSegment: 0x0
[    83.522] 	WinFuncPtr: 0xc000545d
[    83.522] 	BytesPerScanline: 1280
[    83.522] 	XResolution: 640
[    83.522] 	YResolution: 350
[    83.522] 	XCharSize: 8
[    83.522] 	YCharSize: 14
[    83.522] 	NumberOfPlanes: 1
[    83.522] 	BitsPerPixel: 16
[    83.522] 	NumberOfBanks: 1
[    83.522] 	MemoryModel: 6
[    83.522] 	BankSize: 0
[    83.522] 	NumberOfImages: 35
[    83.522] 	RedMaskSize: 5
[    83.522] 	RedFieldPosition: 11
[    83.522] 	GreenMaskSize: 6
[    83.522] 	GreenFieldPosition: 5
[    83.522] 	BlueMaskSize: 5
[    83.522] 	BlueFieldPosition: 0
[    83.522] 	RsvdMaskSize: 0
[    83.522] 	RsvdFieldPosition: 0
[    83.522] 	DirectColorModeInfo: 0
[    83.522] 	PhysBasePtr: 0xc0000000
[    83.522] 	LinBytesPerScanLine: 1280
[    83.522] 	BnkNumberOfImagePages: 35
[    83.522] 	LinNumberOfImagePages: 35
[    83.522] 	LinRedMaskSize: 5
[    83.522] 	LinRedFieldPosition: 11
[    83.522] 	LinGreenMaskSize: 6
[    83.522] 	LinGreenFieldPosition: 5
[    83.522] 	LinBlueMaskSize: 5
[    83.522] 	LinBlueFieldPosition: 0
[    83.522] 	LinRsvdMaskSize: 0
[    83.522] 	LinRsvdFieldPosition: 0
[    83.522] 	MaxPixelClock: 400000000
[    83.522] *Mode: 1c6 (640x350)
[    83.522] 	ModeAttributes: 0xbb
[    83.522] 	WinAAttributes: 0x7
[    83.522] 	WinBAttributes: 0x0
[    83.522] 	WinGranularity: 64
[    83.522] 	WinSize: 64
[    83.522] 	WinASegment: 0xa000
[    83.522] 	WinBSegment: 0x0
[    83.522] 	WinFuncPtr: 0xc000545d
[    83.522] 	BytesPerScanline: 2560
[    83.522] 	XResolution: 640
[    83.522] 	YResolution: 350
[    83.522] 	XCharSize: 8
[    83.523] 	YCharSize: 14
[    83.523] 	NumberOfPlanes: 1
[    83.523] 	BitsPerPixel: 32
[    83.523] 	NumberOfBanks: 1
[    83.523] 	MemoryModel: 6
[    83.523] 	BankSize: 0
[    83.523] 	NumberOfImages: 17
[    83.523] 	RedMaskSize: 8
[    83.523] 	RedFieldPosition: 16
[    83.523] 	GreenMaskSize: 8
[    83.523] 	GreenFieldPosition: 8
[    83.523] 	BlueMaskSize: 8
[    83.523] 	BlueFieldPosition: 0
[    83.523] 	RsvdMaskSize: 0
[    83.523] 	RsvdFieldPosition: 0
[    83.523] 	DirectColorModeInfo: 0
[    83.523] 	PhysBasePtr: 0xc0000000
[    83.523] 	LinBytesPerScanLine: 2560
[    83.523] 	BnkNumberOfImagePages: 17
[    83.523] 	LinNumberOfImagePages: 17
[    83.523] 	LinRedMaskSize: 8
[    83.523] 	LinRedFieldPosition: 16
[    83.523] 	LinGreenMaskSize: 8
[    83.523] 	LinGreenFieldPosition: 8
[    83.523] 	LinBlueMaskSize: 8
[    83.523] 	LinBlueFieldPosition: 0
[    83.523] 	LinRsvdMaskSize: 0
[    83.523] 	LinRsvdFieldPosition: 0
[    83.523] 	MaxPixelClock: 400000000
[    83.523] Mode: 133 (720x400)
[    83.523] 	ModeAttributes: 0xbb
[    83.523] 	WinAAttributes: 0x7
[    83.523] 	WinBAttributes: 0x0
[    83.523] 	WinGranularity: 64
[    83.523] 	WinSize: 64
[    83.523] 	WinASegment: 0xa000
[    83.523] 	WinBSegment: 0x0
[    83.523] 	WinFuncPtr: 0xc000545d
[    83.523] 	BytesPerScanline: 768
[    83.523] 	XResolution: 720
[    83.523] 	YResolution: 400
[    83.523] 	XCharSize: 8
[    83.523] 	YCharSize: 16
[    83.523] 	NumberOfPlanes: 1
[    83.523] 	BitsPerPixel: 8
[    83.523] 	NumberOfBanks: 1
[    83.523] 	MemoryModel: 4
[    83.523] 	BankSize: 0
[    83.523] 	NumberOfImages: 50
[    83.523] 	RedMaskSize: 0
[    83.523] 	RedFieldPosition: 0
[    83.523] 	GreenMaskSize: 0
[    83.523] 	GreenFieldPosition: 0
[    83.523] 	BlueMaskSize: 0
[    83.523] 	BlueFieldPosition: 0
[    83.523] 	RsvdMaskSize: 0
[    83.523] 	RsvdFieldPosition: 0
[    83.523] 	DirectColorModeInfo: 0
[    83.523] 	PhysBasePtr: 0xc0000000
[    83.523] 	LinBytesPerScanLine: 768
[    83.523] 	BnkNumberOfImagePages: 50
[    83.523] 	LinNumberOfImagePages: 50
[    83.523] 	LinRedMaskSize: 0
[    83.523] 	LinRedFieldPosition: 0
[    83.523] 	LinGreenMaskSize: 0
[    83.523] 	LinGreenFieldPosition: 0
[    83.523] 	LinBlueMaskSize: 0
[    83.523] 	LinBlueFieldPosition: 0
[    83.523] 	LinRsvdMaskSize: 0
[    83.523] 	LinRsvdFieldPosition: 0
[    83.523] 	MaxPixelClock: 400000000
[    83.523] Mode: 135 (720x400)
[    83.523] 	ModeAttributes: 0xbb
[    83.523] 	WinAAttributes: 0x7
[    83.523] 	WinBAttributes: 0x0
[    83.523] 	WinGranularity: 64
[    83.523] 	WinSize: 64
[    83.523] 	WinASegment: 0xa000
[    83.523] 	WinBSegment: 0x0
[    83.523] 	WinFuncPtr: 0xc000545d
[    83.523] 	BytesPerScanline: 1472
[    83.523] 	XResolution: 720
[    83.523] 	YResolution: 400
[    83.523] 	XCharSize: 8
[    83.523] 	YCharSize: 16
[    83.523] 	NumberOfPlanes: 1
[    83.523] 	BitsPerPixel: 16
[    83.523] 	NumberOfBanks: 1
[    83.523] 	MemoryModel: 6
[    83.523] 	BankSize: 0
[    83.523] 	NumberOfImages: 27
[    83.523] 	RedMaskSize: 5
[    83.523] 	RedFieldPosition: 11
[    83.523] 	GreenMaskSize: 6
[    83.523] 	GreenFieldPosition: 5
[    83.523] 	BlueMaskSize: 5
[    83.523] 	BlueFieldPosition: 0
[    83.523] 	RsvdMaskSize: 0
[    83.523] 	RsvdFieldPosition: 0
[    83.523] 	DirectColorModeInfo: 0
[    83.523] 	PhysBasePtr: 0xc0000000
[    83.523] 	LinBytesPerScanLine: 1472
[    83.523] 	BnkNumberOfImagePages: 27
[    83.523] 	LinNumberOfImagePages: 27
[    83.523] 	LinRedMaskSize: 5
[    83.523] 	LinRedFieldPosition: 11
[    83.523] 	LinGreenMaskSize: 6
[    83.523] 	LinGreenFieldPosition: 5
[    83.523] 	LinBlueMaskSize: 5
[    83.523] 	LinBlueFieldPosition: 0
[    83.523] 	LinRsvdMaskSize: 0
[    83.523] 	LinRsvdFieldPosition: 0
[    83.523] 	MaxPixelClock: 400000000
[    83.524] *Mode: 136 (720x400)
[    83.524] 	ModeAttributes: 0xbb
[    83.524] 	WinAAttributes: 0x7
[    83.524] 	WinBAttributes: 0x0
[    83.524] 	WinGranularity: 64
[    83.524] 	WinSize: 64
[    83.524] 	WinASegment: 0xa000
[    83.524] 	WinBSegment: 0x0
[    83.524] 	WinFuncPtr: 0xc000545d
[    83.524] 	BytesPerScanline: 2944
[    83.524] 	XResolution: 720
[    83.524] 	YResolution: 400
[    83.524] 	XCharSize: 8
[    83.524] 	YCharSize: 16
[    83.524] 	NumberOfPlanes: 1
[    83.524] 	BitsPerPixel: 32
[    83.524] 	NumberOfBanks: 1
[    83.524] 	MemoryModel: 6
[    83.524] 	BankSize: 0
[    83.524] 	NumberOfImages: 13
[    83.524] 	RedMaskSize: 8
[    83.524] 	RedFieldPosition: 16
[    83.524] 	GreenMaskSize: 8
[    83.524] 	GreenFieldPosition: 8
[    83.524] 	BlueMaskSize: 8
[    83.524] 	BlueFieldPosition: 0
[    83.524] 	RsvdMaskSize: 0
[    83.524] 	RsvdFieldPosition: 0
[    83.524] 	DirectColorModeInfo: 0
[    83.524] 	PhysBasePtr: 0xc0000000
[    83.524] 	LinBytesPerScanLine: 2944
[    83.524] 	BnkNumberOfImagePages: 13
[    83.524] 	LinNumberOfImagePages: 13
[    83.524] 	LinRedMaskSize: 8
[    83.524] 	LinRedFieldPosition: 16
[    83.524] 	LinGreenMaskSize: 8
[    83.524] 	LinGreenFieldPosition: 8
[    83.524] 	LinBlueMaskSize: 8
[    83.524] 	LinBlueFieldPosition: 0
[    83.524] 	LinRsvdMaskSize: 0
[    83.524] 	LinRsvdFieldPosition: 0
[    83.524] 	MaxPixelClock: 400000000
[    83.524] Mode: 153 (1152x864)
[    83.524] 	ModeAttributes: 0xbb
[    83.524] 	WinAAttributes: 0x7
[    83.524] 	WinBAttributes: 0x0
[    83.524] 	WinGranularity: 64
[    83.524] 	WinSize: 64
[    83.524] 	WinASegment: 0xa000
[    83.524] 	WinBSegment: 0x0
[    83.524] 	WinFuncPtr: 0xc000545d
[    83.524] 	BytesPerScanline: 1152
[    83.524] 	XResolution: 1152
[    83.524] 	YResolution: 864
[    83.524] 	XCharSize: 8
[    83.524] 	YCharSize: 16
[    83.524] 	NumberOfPlanes: 1
[    83.524] 	BitsPerPixel: 8
[    83.524] 	NumberOfBanks: 1
[    83.524] 	MemoryModel: 4
[    83.524] 	BankSize: 0
[    83.524] 	NumberOfImages: 15
[    83.524] 	RedMaskSize: 0
[    83.524] 	RedFieldPosition: 0
[    83.524] 	GreenMaskSize: 0
[    83.524] 	GreenFieldPosition: 0
[    83.524] 	BlueMaskSize: 0
[    83.524] 	BlueFieldPosition: 0
[    83.524] 	RsvdMaskSize: 0
[    83.524] 	RsvdFieldPosition: 0
[    83.524] 	DirectColorModeInfo: 0
[    83.524] 	PhysBasePtr: 0xc0000000
[    83.524] 	LinBytesPerScanLine: 1152
[    83.524] 	BnkNumberOfImagePages: 15
[    83.524] 	LinNumberOfImagePages: 15
[    83.524] 	LinRedMaskSize: 0
[    83.524] 	LinRedFieldPosition: 0
[    83.524] 	LinGreenMaskSize: 0
[    83.524] 	LinGreenFieldPosition: 0
[    83.524] 	LinBlueMaskSize: 0
[    83.524] 	LinBlueFieldPosition: 0
[    83.524] 	LinRsvdMaskSize: 0
[    83.524] 	LinRsvdFieldPosition: 0
[    83.524] 	MaxPixelClock: 400000000
[    83.525] Mode: 155 (1152x864)
[    83.525] 	ModeAttributes: 0xbb
[    83.525] 	WinAAttributes: 0x7
[    83.525] 	WinBAttributes: 0x0
[    83.525] 	WinGranularity: 64
[    83.525] 	WinSize: 64
[    83.525] 	WinASegment: 0xa000
[    83.525] 	WinBSegment: 0x0
[    83.525] 	WinFuncPtr: 0xc000545d
[    83.525] 	BytesPerScanline: 2304
[    83.525] 	XResolution: 1152
[    83.525] 	YResolution: 864
[    83.525] 	XCharSize: 8
[    83.525] 	YCharSize: 16
[    83.525] 	NumberOfPlanes: 1
[    83.525] 	BitsPerPixel: 16
[    83.525] 	NumberOfBanks: 1
[    83.525] 	MemoryModel: 6
[    83.525] 	BankSize: 0
[    83.525] 	NumberOfImages: 7
[    83.525] 	RedMaskSize: 5
[    83.525] 	RedFieldPosition: 11
[    83.525] 	GreenMaskSize: 6
[    83.525] 	GreenFieldPosition: 5
[    83.525] 	BlueMaskSize: 5
[    83.525] 	BlueFieldPosition: 0
[    83.525] 	RsvdMaskSize: 0
[    83.525] 	RsvdFieldPosition: 0
[    83.525] 	DirectColorModeInfo: 0
[    83.525] 	PhysBasePtr: 0xc0000000
[    83.525] 	LinBytesPerScanLine: 2304
[    83.525] 	BnkNumberOfImagePages: 7
[    83.525] 	LinNumberOfImagePages: 7
[    83.525] 	LinRedMaskSize: 5
[    83.525] 	LinRedFieldPosition: 11
[    83.525] 	LinGreenMaskSize: 6
[    83.525] 	LinGreenFieldPosition: 5
[    83.525] 	LinBlueMaskSize: 5
[    83.525] 	LinBlueFieldPosition: 0
[    83.525] 	LinRsvdMaskSize: 0
[    83.525] 	LinRsvdFieldPosition: 0
[    83.525] 	MaxPixelClock: 400000000
[    83.525] *Mode: 156 (1152x864)
[    83.525] 	ModeAttributes: 0xbb
[    83.525] 	WinAAttributes: 0x7
[    83.525] 	WinBAttributes: 0x0
[    83.525] 	WinGranularity: 64
[    83.525] 	WinSize: 64
[    83.525] 	WinASegment: 0xa000
[    83.525] 	WinBSegment: 0x0
[    83.525] 	WinFuncPtr: 0xc000545d
[    83.525] 	BytesPerScanline: 4608
[    83.525] 	XResolution: 1152
[    83.525] 	YResolution: 864
[    83.525] 	XCharSize: 8
[    83.525] 	YCharSize: 16
[    83.525] 	NumberOfPlanes: 1
[    83.525] 	BitsPerPixel: 32
[    83.525] 	NumberOfBanks: 1
[    83.525] 	MemoryModel: 6
[    83.525] 	BankSize: 0
[    83.525] 	NumberOfImages: 3
[    83.525] 	RedMaskSize: 8
[    83.525] 	RedFieldPosition: 16
[    83.525] 	GreenMaskSize: 8
[    83.525] 	GreenFieldPosition: 8
[    83.525] 	BlueMaskSize: 8
[    83.525] 	BlueFieldPosition: 0
[    83.525] 	RsvdMaskSize: 0
[    83.525] 	RsvdFieldPosition: 0
[    83.525] 	DirectColorModeInfo: 0
[    83.525] 	PhysBasePtr: 0xc0000000
[    83.525] 	LinBytesPerScanLine: 4608
[    83.525] 	BnkNumberOfImagePages: 3
[    83.525] 	LinNumberOfImagePages: 3
[    83.525] 	LinRedMaskSize: 8
[    83.525] 	LinRedFieldPosition: 16
[    83.525] 	LinGreenMaskSize: 8
[    83.525] 	LinGreenFieldPosition: 8
[    83.525] 	LinBlueMaskSize: 8
[    83.525] 	LinBlueFieldPosition: 0
[    83.525] 	LinRsvdMaskSize: 0
[    83.525] 	LinRsvdFieldPosition: 0
[    83.525] 	MaxPixelClock: 400000000
[    83.525] Mode: 163 (1280x960)
[    83.525] 	ModeAttributes: 0xbb
[    83.525] 	WinAAttributes: 0x7
[    83.525] 	WinBAttributes: 0x0
[    83.525] 	WinGranularity: 64
[    83.525] 	WinSize: 64
[    83.525] 	WinASegment: 0xa000
[    83.525] 	WinBSegment: 0x0
[    83.526] 	WinFuncPtr: 0xc000545d
[    83.526] 	BytesPerScanline: 1280
[    83.526] 	XResolution: 1280
[    83.526] 	YResolution: 960
[    83.526] 	XCharSize: 8
[    83.526] 	YCharSize: 16
[    83.526] 	NumberOfPlanes: 1
[    83.526] 	BitsPerPixel: 8
[    83.526] 	NumberOfBanks: 1
[    83.526] 	MemoryModel: 4
[    83.526] 	BankSize: 0
[    83.526] 	NumberOfImages: 12
[    83.526] 	RedMaskSize: 0
[    83.526] 	RedFieldPosition: 0
[    83.526] 	GreenMaskSize: 0
[    83.526] 	GreenFieldPosition: 0
[    83.526] 	BlueMaskSize: 0
[    83.526] 	BlueFieldPosition: 0
[    83.526] 	RsvdMaskSize: 0
[    83.526] 	RsvdFieldPosition: 0
[    83.526] 	DirectColorModeInfo: 0
[    83.526] 	PhysBasePtr: 0xc0000000
[    83.526] 	LinBytesPerScanLine: 1280
[    83.526] 	BnkNumberOfImagePages: 12
[    83.526] 	LinNumberOfImagePages: 12
[    83.526] 	LinRedMaskSize: 0
[    83.526] 	LinRedFieldPosition: 0
[    83.526] 	LinGreenMaskSize: 0
[    83.526] 	LinGreenFieldPosition: 0
[    83.526] 	LinBlueMaskSize: 0
[    83.526] 	LinBlueFieldPosition: 0
[    83.526] 	LinRsvdMaskSize: 0
[    83.526] 	LinRsvdFieldPosition: 0
[    83.526] 	MaxPixelClock: 400000000
[    83.526] Mode: 165 (1280x960)
[    83.526] 	ModeAttributes: 0xbb
[    83.526] 	WinAAttributes: 0x7
[    83.526] 	WinBAttributes: 0x0
[    83.526] 	WinGranularity: 64
[    83.526] 	WinSize: 64
[    83.526] 	WinASegment: 0xa000
[    83.526] 	WinBSegment: 0x0
[    83.526] 	WinFuncPtr: 0xc000545d
[    83.526] 	BytesPerScanline: 2560
[    83.526] 	XResolution: 1280
[    83.526] 	YResolution: 960
[    83.526] 	XCharSize: 8
[    83.526] 	YCharSize: 16
[    83.526] 	NumberOfPlanes: 1
[    83.526] 	BitsPerPixel: 16
[    83.526] 	NumberOfBanks: 1
[    83.526] 	MemoryModel: 6
[    83.526] 	BankSize: 0
[    83.526] 	NumberOfImages: 5
[    83.526] 	RedMaskSize: 5
[    83.526] 	RedFieldPosition: 11
[    83.526] 	GreenMaskSize: 6
[    83.526] 	GreenFieldPosition: 5
[    83.526] 	BlueMaskSize: 5
[    83.526] 	BlueFieldPosition: 0
[    83.526] 	RsvdMaskSize: 0
[    83.526] 	RsvdFieldPosition: 0
[    83.526] 	DirectColorModeInfo: 0
[    83.526] 	PhysBasePtr: 0xc0000000
[    83.526] 	LinBytesPerScanLine: 2560
[    83.526] 	BnkNumberOfImagePages: 5
[    83.526] 	LinNumberOfImagePages: 5
[    83.526] 	LinRedMaskSize: 5
[    83.526] 	LinRedFieldPosition: 11
[    83.526] 	LinGreenMaskSize: 6
[    83.526] 	LinGreenFieldPosition: 5
[    83.526] 	LinBlueMaskSize: 5
[    83.526] 	LinBlueFieldPosition: 0
[    83.526] 	LinRsvdMaskSize: 0
[    83.526] 	LinRsvdFieldPosition: 0
[    83.526] 	MaxPixelClock: 400000000
[    83.526] *Mode: 166 (1280x960)
[    83.526] 	ModeAttributes: 0xbb
[    83.526] 	WinAAttributes: 0x7
[    83.526] 	WinBAttributes: 0x0
[    83.526] 	WinGranularity: 64
[    83.526] 	WinSize: 64
[    83.526] 	WinASegment: 0xa000
[    83.526] 	WinBSegment: 0x0
[    83.526] 	WinFuncPtr: 0xc000545d
[    83.526] 	BytesPerScanline: 5120
[    83.526] 	XResolution: 1280
[    83.526] 	YResolution: 960
[    83.526] 	XCharSize: 8
[    83.526] 	YCharSize: 16
[    83.526] 	NumberOfPlanes: 1
[    83.526] 	BitsPerPixel: 32
[    83.526] 	NumberOfBanks: 1
[    83.526] 	MemoryModel: 6
[    83.526] 	BankSize: 0
[    83.526] 	NumberOfImages: 2
[    83.526] 	RedMaskSize: 8
[    83.526] 	RedFieldPosition: 16
[    83.526] 	GreenMaskSize: 8
[    83.526] 	GreenFieldPosition: 8
[    83.526] 	BlueMaskSize: 8
[    83.526] 	BlueFieldPosition: 0
[    83.526] 	RsvdMaskSize: 0
[    83.526] 	RsvdFieldPosition: 0
[    83.526] 	DirectColorModeInfo: 0
[    83.526] 	PhysBasePtr: 0xc0000000
[    83.526] 	LinBytesPerScanLine: 5120
[    83.526] 	BnkNumberOfImagePages: 2
[    83.526] 	LinNumberOfImagePages: 2
[    83.526] 	LinRedMaskSize: 8
[    83.526] 	LinRedFieldPosition: 16
[    83.526] 	LinGreenMaskSize: 8
[    83.526] 	LinGreenFieldPosition: 8
[    83.526] 	LinBlueMaskSize: 8
[    83.526] 	LinBlueFieldPosition: 0
[    83.526] 	LinRsvdMaskSize: 0
[    83.526] 	LinRsvdFieldPosition: 0
[    83.526] 	MaxPixelClock: 400000000
[    83.527] *Mode: 121 (640x480)
[    83.527] 	ModeAttributes: 0xbb
[    83.527] 	WinAAttributes: 0x7
[    83.527] 	WinBAttributes: 0x0
[    83.527] 	WinGranularity: 64
[    83.527] 	WinSize: 64
[    83.527] 	WinASegment: 0xa000
[    83.527] 	WinBSegment: 0x0
[    83.527] 	WinFuncPtr: 0xc000545d
[    83.527] 	BytesPerScanline: 2560
[    83.527] 	XResolution: 640
[    83.527] 	YResolution: 480
[    83.527] 	XCharSize: 8
[    83.527] 	YCharSize: 16
[    83.527] 	NumberOfPlanes: 1
[    83.527] 	BitsPerPixel: 32
[    83.527] 	NumberOfBanks: 1
[    83.527] 	MemoryModel: 6
[    83.527] 	BankSize: 0
[    83.527] 	NumberOfImages: 12
[    83.527] 	RedMaskSize: 8
[    83.527] 	RedFieldPosition: 16
[    83.527] 	GreenMaskSize: 8
[    83.527] 	GreenFieldPosition: 8
[    83.527] 	BlueMaskSize: 8
[    83.527] 	BlueFieldPosition: 0
[    83.527] 	RsvdMaskSize: 0
[    83.527] 	RsvdFieldPosition: 0
[    83.527] 	DirectColorModeInfo: 0
[    83.527] 	PhysBasePtr: 0xc0000000
[    83.527] 	LinBytesPerScanLine: 2560
[    83.527] 	BnkNumberOfImagePages: 12
[    83.527] 	LinNumberOfImagePages: 12
[    83.527] 	LinRedMaskSize: 8
[    83.527] 	LinRedFieldPosition: 16
[    83.527] 	LinGreenMaskSize: 8
[    83.527] 	LinGreenFieldPosition: 8
[    83.527] 	LinBlueMaskSize: 8
[    83.527] 	LinBlueFieldPosition: 0
[    83.527] 	LinRsvdMaskSize: 0
[    83.527] 	LinRsvdFieldPosition: 0
[    83.527] 	MaxPixelClock: 400000000
[    83.527] *Mode: 122 (800x600)
[    83.527] 	ModeAttributes: 0xbb
[    83.527] 	WinAAttributes: 0x7
[    83.527] 	WinBAttributes: 0x0
[    83.527] 	WinGranularity: 64
[    83.527] 	WinSize: 64
[    83.527] 	WinASegment: 0xa000
[    83.527] 	WinBSegment: 0x0
[    83.527] 	WinFuncPtr: 0xc000545d
[    83.527] 	BytesPerScanline: 3200
[    83.527] 	XResolution: 800
[    83.527] 	YResolution: 600
[    83.527] 	XCharSize: 8
[    83.527] 	YCharSize: 14
[    83.527] 	NumberOfPlanes: 1
[    83.527] 	BitsPerPixel: 32
[    83.527] 	NumberOfBanks: 1
[    83.527] 	MemoryModel: 6
[    83.527] 	BankSize: 0
[    83.527] 	NumberOfImages: 7
[    83.527] 	RedMaskSize: 8
[    83.527] 	RedFieldPosition: 16
[    83.527] 	GreenMaskSize: 8
[    83.527] 	GreenFieldPosition: 8
[    83.527] 	BlueMaskSize: 8
[    83.527] 	BlueFieldPosition: 0
[    83.527] 	RsvdMaskSize: 0
[    83.527] 	RsvdFieldPosition: 0
[    83.527] 	DirectColorModeInfo: 0
[    83.527] 	PhysBasePtr: 0xc0000000
[    83.527] 	LinBytesPerScanLine: 3200
[    83.527] 	BnkNumberOfImagePages: 7
[    83.527] 	LinNumberOfImagePages: 7
[    83.527] 	LinRedMaskSize: 8
[    83.527] 	LinRedFieldPosition: 16
[    83.527] 	LinGreenMaskSize: 8
[    83.527] 	LinGreenFieldPosition: 8
[    83.527] 	LinBlueMaskSize: 8
[    83.527] 	LinBlueFieldPosition: 0
[    83.527] 	LinRsvdMaskSize: 0
[    83.527] 	LinRsvdFieldPosition: 0
[    83.527] 	MaxPixelClock: 400000000
[    83.528] *Mode: 123 (1024x768)
[    83.528] 	ModeAttributes: 0xbb
[    83.528] 	WinAAttributes: 0x7
[    83.528] 	WinBAttributes: 0x0
[    83.528] 	WinGranularity: 64
[    83.528] 	WinSize: 64
[    83.528] 	WinASegment: 0xa000
[    83.528] 	WinBSegment: 0x0
[    83.528] 	WinFuncPtr: 0xc000545d
[    83.528] 	BytesPerScanline: 4096
[    83.528] 	XResolution: 1024
[    83.528] 	YResolution: 768
[    83.528] 	XCharSize: 8
[    83.528] 	YCharSize: 16
[    83.528] 	NumberOfPlanes: 1
[    83.528] 	BitsPerPixel: 32
[    83.528] 	NumberOfBanks: 1
[    83.528] 	MemoryModel: 6
[    83.528] 	BankSize: 0
[    83.528] 	NumberOfImages: 4
[    83.528] 	RedMaskSize: 8
[    83.528] 	RedFieldPosition: 16
[    83.528] 	GreenMaskSize: 8
[    83.528] 	GreenFieldPosition: 8
[    83.528] 	BlueMaskSize: 8
[    83.528] 	BlueFieldPosition: 0
[    83.528] 	RsvdMaskSize: 0
[    83.528] 	RsvdFieldPosition: 0
[    83.528] 	DirectColorModeInfo: 0
[    83.528] 	PhysBasePtr: 0xc0000000
[    83.528] 	LinBytesPerScanLine: 4096
[    83.528] 	BnkNumberOfImagePages: 4
[    83.528] 	LinNumberOfImagePages: 4
[    83.528] 	LinRedMaskSize: 8
[    83.528] 	LinRedFieldPosition: 16
[    83.528] 	LinGreenMaskSize: 8
[    83.528] 	LinGreenFieldPosition: 8
[    83.528] 	LinBlueMaskSize: 8
[    83.528] 	LinBlueFieldPosition: 0
[    83.528] 	LinRsvdMaskSize: 0
[    83.528] 	LinRsvdFieldPosition: 0
[    83.528] 	MaxPixelClock: 400000000
[    83.528] *Mode: 124 (1280x1024)
[    83.528] 	ModeAttributes: 0xbb
[    83.528] 	WinAAttributes: 0x7
[    83.528] 	WinBAttributes: 0x0
[    83.528] 	WinGranularity: 64
[    83.528] 	WinSize: 64
[    83.528] 	WinASegment: 0xa000
[    83.528] 	WinBSegment: 0x0
[    83.528] 	WinFuncPtr: 0xc000545d
[    83.528] 	BytesPerScanline: 5120
[    83.528] 	XResolution: 1280
[    83.528] 	YResolution: 1024
[    83.528] 	XCharSize: 8
[    83.528] 	YCharSize: 16
[    83.528] 	NumberOfPlanes: 1
[    83.528] 	BitsPerPixel: 32
[    83.528] 	NumberOfBanks: 1
[    83.528] 	MemoryModel: 6
[    83.528] 	BankSize: 0
[    83.528] 	NumberOfImages: 2
[    83.528] 	RedMaskSize: 8
[    83.528] 	RedFieldPosition: 16
[    83.528] 	GreenMaskSize: 8
[    83.528] 	GreenFieldPosition: 8
[    83.528] 	BlueMaskSize: 8
[    83.528] 	BlueFieldPosition: 0
[    83.528] 	RsvdMaskSize: 0
[    83.528] 	RsvdFieldPosition: 0
[    83.528] 	DirectColorModeInfo: 0
[    83.528] 	PhysBasePtr: 0xc0000000
[    83.528] 	LinBytesPerScanLine: 5120
[    83.528] 	BnkNumberOfImagePages: 2
[    83.528] 	LinNumberOfImagePages: 2
[    83.528] 	LinRedMaskSize: 8
[    83.528] 	LinRedFieldPosition: 16
[    83.528] 	LinGreenMaskSize: 8
[    83.528] 	LinGreenFieldPosition: 8
[    83.528] 	LinBlueMaskSize: 8
[    83.528] 	LinBlueFieldPosition: 0
[    83.528] 	LinRsvdMaskSize: 0
[    83.528] 	LinRsvdFieldPosition: 0
[    83.528] 	MaxPixelClock: 400000000
[    83.528] Mode: 143 (1400x1050)
[    83.528] 	ModeAttributes: 0xbb
[    83.528] 	WinAAttributes: 0x7
[    83.528] 	WinBAttributes: 0x0
[    83.529] 	WinGranularity: 64
[    83.529] 	WinSize: 64
[    83.529] 	WinASegment: 0xa000
[    83.529] 	WinBSegment: 0x0
[    83.529] 	WinFuncPtr: 0xc000545d
[    83.529] 	BytesPerScanline: 1408
[    83.529] 	XResolution: 1400
[    83.529] 	YResolution: 1050
[    83.529] 	XCharSize: 8
[    83.529] 	YCharSize: 16
[    83.529] 	NumberOfPlanes: 1
[    83.529] 	BitsPerPixel: 8
[    83.529] 	NumberOfBanks: 1
[    83.529] 	MemoryModel: 4
[    83.529] 	BankSize: 0
[    83.529] 	NumberOfImages: 10
[    83.529] 	RedMaskSize: 0
[    83.529] 	RedFieldPosition: 0
[    83.529] 	GreenMaskSize: 0
[    83.529] 	GreenFieldPosition: 0
[    83.529] 	BlueMaskSize: 0
[    83.529] 	BlueFieldPosition: 0
[    83.529] 	RsvdMaskSize: 0
[    83.529] 	RsvdFieldPosition: 0
[    83.529] 	DirectColorModeInfo: 0
[    83.529] 	PhysBasePtr: 0xc0000000
[    83.529] 	LinBytesPerScanLine: 1408
[    83.529] 	BnkNumberOfImagePages: 10
[    83.529] 	LinNumberOfImagePages: 10
[    83.529] 	LinRedMaskSize: 0
[    83.529] 	LinRedFieldPosition: 0
[    83.529] 	LinGreenMaskSize: 0
[    83.529] 	LinGreenFieldPosition: 0
[    83.529] 	LinBlueMaskSize: 0
[    83.529] 	LinBlueFieldPosition: 0
[    83.529] 	LinRsvdMaskSize: 0
[    83.529] 	LinRsvdFieldPosition: 0
[    83.529] 	MaxPixelClock: 400000000
[    83.529] Mode: 145 (1400x1050)
[    83.529] 	ModeAttributes: 0xbb
[    83.529] 	WinAAttributes: 0x7
[    83.529] 	WinBAttributes: 0x0
[    83.529] 	WinGranularity: 64
[    83.529] 	WinSize: 64
[    83.529] 	WinASegment: 0xa000
[    83.529] 	WinBSegment: 0x0
[    83.529] 	WinFuncPtr: 0xc000545d
[    83.529] 	BytesPerScanline: 2816
[    83.529] 	XResolution: 1400
[    83.529] 	YResolution: 1050
[    83.529] 	XCharSize: 8
[    83.529] 	YCharSize: 16
[    83.529] 	NumberOfPlanes: 1
[    83.529] 	BitsPerPixel: 16
[    83.529] 	NumberOfBanks: 1
[    83.529] 	MemoryModel: 6
[    83.529] 	BankSize: 0
[    83.529] 	NumberOfImages: 4
[    83.529] 	RedMaskSize: 5
[    83.529] 	RedFieldPosition: 11
[    83.529] 	GreenMaskSize: 6
[    83.529] 	GreenFieldPosition: 5
[    83.529] 	BlueMaskSize: 5
[    83.529] 	BlueFieldPosition: 0
[    83.529] 	RsvdMaskSize: 0
[    83.529] 	RsvdFieldPosition: 0
[    83.529] 	DirectColorModeInfo: 0
[    83.529] 	PhysBasePtr: 0xc0000000
[    83.529] 	LinBytesPerScanLine: 2816
[    83.529] 	BnkNumberOfImagePages: 4
[    83.529] 	LinNumberOfImagePages: 4
[    83.529] 	LinRedMaskSize: 5
[    83.529] 	LinRedFieldPosition: 11
[    83.529] 	LinGreenMaskSize: 6
[    83.529] 	LinGreenFieldPosition: 5
[    83.529] 	LinBlueMaskSize: 5
[    83.529] 	LinBlueFieldPosition: 0
[    83.529] 	LinRsvdMaskSize: 0
[    83.529] 	LinRsvdFieldPosition: 0
[    83.529] 	MaxPixelClock: 400000000
[    83.529] *Mode: 146 (1400x1050)
[    83.529] 	ModeAttributes: 0xbb
[    83.529] 	WinAAttributes: 0x7
[    83.529] 	WinBAttributes: 0x0
[    83.529] 	WinGranularity: 64
[    83.529] 	WinSize: 64
[    83.529] 	WinASegment: 0xa000
[    83.529] 	WinBSegment: 0x0
[    83.529] 	WinFuncPtr: 0xc000545d
[    83.529] 	BytesPerScanline: 5632
[    83.529] 	XResolution: 1400
[    83.529] 	YResolution: 1050
[    83.529] 	XCharSize: 8
[    83.529] 	YCharSize: 16
[    83.529] 	NumberOfPlanes: 1
[    83.529] 	BitsPerPixel: 32
[    83.529] 	NumberOfBanks: 1
[    83.529] 	MemoryModel: 6
[    83.529] 	BankSize: 0
[    83.529] 	NumberOfImages: 1
[    83.529] 	RedMaskSize: 8
[    83.529] 	RedFieldPosition: 16
[    83.529] 	GreenMaskSize: 8
[    83.529] 	GreenFieldPosition: 8
[    83.529] 	BlueMaskSize: 8
[    83.529] 	BlueFieldPosition: 0
[    83.529] 	RsvdMaskSize: 0
[    83.529] 	RsvdFieldPosition: 0
[    83.529] 	DirectColorModeInfo: 0
[    83.529] 	PhysBasePtr: 0xc0000000
[    83.529] 	LinBytesPerScanLine: 5632
[    83.529] 	BnkNumberOfImagePages: 1
[    83.529] 	LinNumberOfImagePages: 1
[    83.529] 	LinRedMaskSize: 8
[    83.529] 	LinRedFieldPosition: 16
[    83.530] 	LinGreenMaskSize: 8
[    83.530] 	LinGreenFieldPosition: 8
[    83.530] 	LinBlueMaskSize: 8
[    83.530] 	LinBlueFieldPosition: 0
[    83.530] 	LinRsvdMaskSize: 0
[    83.530] 	LinRsvdFieldPosition: 0
[    83.530] 	MaxPixelClock: 400000000
[    83.530] Mode: 173 (1600x1200)
[    83.530] 	ModeAttributes: 0xba
[    83.530] 	WinAAttributes: 0x7
[    83.530] 	WinBAttributes: 0x0
[    83.530] 	WinGranularity: 64
[    83.530] 	WinSize: 64
[    83.530] 	WinASegment: 0xa000
[    83.530] 	WinBSegment: 0x0
[    83.530] 	WinFuncPtr: 0xc000545d
[    83.530] 	BytesPerScanline: 1600
[    83.530] 	XResolution: 1600
[    83.530] 	YResolution: 1200
[    83.530] 	XCharSize: 8
[    83.530] 	YCharSize: 16
[    83.530] 	NumberOfPlanes: 1
[    83.530] 	BitsPerPixel: 8
[    83.530] 	NumberOfBanks: 1
[    83.530] 	MemoryModel: 4
[    83.530] 	BankSize: 0
[    83.530] 	NumberOfImages: 7
[    83.530] 	RedMaskSize: 0
[    83.530] 	RedFieldPosition: 0
[    83.530] 	GreenMaskSize: 0
[    83.530] 	GreenFieldPosition: 0
[    83.530] 	BlueMaskSize: 0
[    83.530] 	BlueFieldPosition: 0
[    83.530] 	RsvdMaskSize: 0
[    83.530] 	RsvdFieldPosition: 0
[    83.530] 	DirectColorModeInfo: 0
[    83.530] 	PhysBasePtr: 0xc0000000
[    83.530] 	LinBytesPerScanLine: 1600
[    83.530] 	BnkNumberOfImagePages: 7
[    83.530] 	LinNumberOfImagePages: 7
[    83.530] 	LinRedMaskSize: 0
[    83.530] 	LinRedFieldPosition: 0
[    83.530] 	LinGreenMaskSize: 0
[    83.530] 	LinGreenFieldPosition: 0
[    83.530] 	LinBlueMaskSize: 0
[    83.530] 	LinBlueFieldPosition: 0
[    83.530] 	LinRsvdMaskSize: 0
[    83.530] 	LinRsvdFieldPosition: 0
[    83.530] 	MaxPixelClock: 400000000
[    83.530] Mode: 175 (1600x1200)
[    83.530] 	ModeAttributes: 0xba
[    83.530] 	WinAAttributes: 0x7
[    83.530] 	WinBAttributes: 0x0
[    83.530] 	WinGranularity: 64
[    83.530] 	WinSize: 64
[    83.530] 	WinASegment: 0xa000
[    83.530] 	WinBSegment: 0x0
[    83.530] 	WinFuncPtr: 0xc000545d
[    83.530] 	BytesPerScanline: 3200
[    83.530] 	XResolution: 1600
[    83.530] 	YResolution: 1200
[    83.530] 	XCharSize: 8
[    83.530] 	YCharSize: 16
[    83.530] 	NumberOfPlanes: 1
[    83.530] 	BitsPerPixel: 16
[    83.530] 	NumberOfBanks: 1
[    83.530] 	MemoryModel: 6
[    83.530] 	BankSize: 0
[    83.530] 	NumberOfImages: 3
[    83.530] 	RedMaskSize: 5
[    83.530] 	RedFieldPosition: 11
[    83.530] 	GreenMaskSize: 6
[    83.530] 	GreenFieldPosition: 5
[    83.530] 	BlueMaskSize: 5
[    83.530] 	BlueFieldPosition: 0
[    83.530] 	RsvdMaskSize: 0
[    83.530] 	RsvdFieldPosition: 0
[    83.530] 	DirectColorModeInfo: 0
[    83.530] 	PhysBasePtr: 0xc0000000
[    83.530] 	LinBytesPerScanLine: 3200
[    83.530] 	BnkNumberOfImagePages: 3
[    83.530] 	LinNumberOfImagePages: 3
[    83.530] 	LinRedMaskSize: 5
[    83.530] 	LinRedFieldPosition: 11
[    83.530] 	LinGreenMaskSize: 6
[    83.530] 	LinGreenFieldPosition: 5
[    83.530] 	LinBlueMaskSize: 5
[    83.530] 	LinBlueFieldPosition: 0
[    83.530] 	LinRsvdMaskSize: 0
[    83.530] 	LinRsvdFieldPosition: 0
[    83.530] 	MaxPixelClock: 400000000
[    83.531] Mode: 176 (1600x1200)
[    83.531] 	ModeAttributes: 0xba
[    83.531] 	WinAAttributes: 0x7
[    83.531] 	WinBAttributes: 0x0
[    83.531] 	WinGranularity: 64
[    83.531] 	WinSize: 64
[    83.531] 	WinASegment: 0xa000
[    83.531] 	WinBSegment: 0x0
[    83.531] 	WinFuncPtr: 0xc000545d
[    83.531] 	BytesPerScanline: 6400
[    83.531] 	XResolution: 1600
[    83.531] 	YResolution: 1200
[    83.531] 	XCharSize: 8
[    83.531] 	YCharSize: 16
[    83.531] 	NumberOfPlanes: 1
[    83.531] 	BitsPerPixel: 32
[    83.531] 	NumberOfBanks: 1
[    83.531] 	MemoryModel: 6
[    83.531] 	BankSize: 0
[    83.531] 	NumberOfImages: 1
[    83.531] 	RedMaskSize: 8
[    83.531] 	RedFieldPosition: 16
[    83.531] 	GreenMaskSize: 8
[    83.531] 	GreenFieldPosition: 8
[    83.531] 	BlueMaskSize: 8
[    83.531] 	BlueFieldPosition: 0
[    83.531] 	RsvdMaskSize: 0
[    83.531] 	RsvdFieldPosition: 0
[    83.531] 	DirectColorModeInfo: 0
[    83.531] 	PhysBasePtr: 0xc0000000
[    83.531] 	LinBytesPerScanLine: 6400
[    83.531] 	BnkNumberOfImagePages: 1
[    83.531] 	LinNumberOfImagePages: 1
[    83.531] 	LinRedMaskSize: 8
[    83.531] 	LinRedFieldPosition: 16
[    83.531] 	LinGreenMaskSize: 8
[    83.531] 	LinGreenFieldPosition: 8
[    83.531] 	LinBlueMaskSize: 8
[    83.531] 	LinBlueFieldPosition: 0
[    83.531] 	LinRsvdMaskSize: 0
[    83.531] 	LinRsvdFieldPosition: 0
[    83.531] 	MaxPixelClock: 400000000
[    83.531] Mode: 183 (1792x1344)
[    83.531] 	ModeAttributes: 0xba
[    83.531] 	WinAAttributes: 0x7
[    83.531] 	WinBAttributes: 0x0
[    83.531] 	WinGranularity: 64
[    83.531] 	WinSize: 64
[    83.531] 	WinASegment: 0xa000
[    83.531] 	WinBSegment: 0x0
[    83.531] 	WinFuncPtr: 0xc000545d
[    83.531] 	BytesPerScanline: 1792
[    83.531] 	XResolution: 1792
[    83.531] 	YResolution: 1344
[    83.531] 	XCharSize: 8
[    83.531] 	YCharSize: 16
[    83.531] 	NumberOfPlanes: 1
[    83.531] 	BitsPerPixel: 8
[    83.531] 	NumberOfBanks: 1
[    83.531] 	MemoryModel: 4
[    83.531] 	BankSize: 0
[    83.531] 	NumberOfImages: 5
[    83.531] 	RedMaskSize: 0
[    83.531] 	RedFieldPosition: 0
[    83.531] 	GreenMaskSize: 0
[    83.531] 	GreenFieldPosition: 0
[    83.531] 	BlueMaskSize: 0
[    83.531] 	BlueFieldPosition: 0
[    83.531] 	RsvdMaskSize: 0
[    83.531] 	RsvdFieldPosition: 0
[    83.531] 	DirectColorModeInfo: 0
[    83.531] 	PhysBasePtr: 0xc0000000
[    83.531] 	LinBytesPerScanLine: 1792
[    83.531] 	BnkNumberOfImagePages: 5
[    83.531] 	LinNumberOfImagePages: 5
[    83.531] 	LinRedMaskSize: 0
[    83.531] 	LinRedFieldPosition: 0
[    83.531] 	LinGreenMaskSize: 0
[    83.531] 	LinGreenFieldPosition: 0
[    83.531] 	LinBlueMaskSize: 0
[    83.531] 	LinBlueFieldPosition: 0
[    83.531] 	LinRsvdMaskSize: 0
[    83.531] 	LinRsvdFieldPosition: 0
[    83.531] 	MaxPixelClock: 400000000
[    83.532] Mode: 185 (1792x1344)
[    83.532] 	ModeAttributes: 0xba
[    83.532] 	WinAAttributes: 0x7
[    83.532] 	WinBAttributes: 0x0
[    83.532] 	WinGranularity: 64
[    83.532] 	WinSize: 64
[    83.532] 	WinASegment: 0xa000
[    83.532] 	WinBSegment: 0x0
[    83.532] 	WinFuncPtr: 0xc000545d
[    83.532] 	BytesPerScanline: 3584
[    83.532] 	XResolution: 1792
[    83.532] 	YResolution: 1344
[    83.532] 	XCharSize: 8
[    83.532] 	YCharSize: 16
[    83.532] 	NumberOfPlanes: 1
[    83.532] 	BitsPerPixel: 16
[    83.532] 	NumberOfBanks: 1
[    83.532] 	MemoryModel: 6
[    83.532] 	BankSize: 0
[    83.532] 	NumberOfImages: 2
[    83.532] 	RedMaskSize: 5
[    83.532] 	RedFieldPosition: 11
[    83.532] 	GreenMaskSize: 6
[    83.532] 	GreenFieldPosition: 5
[    83.532] 	BlueMaskSize: 5
[    83.532] 	BlueFieldPosition: 0
[    83.532] 	RsvdMaskSize: 0
[    83.532] 	RsvdFieldPosition: 0
[    83.532] 	DirectColorModeInfo: 0
[    83.532] 	PhysBasePtr: 0xc0000000
[    83.532] 	LinBytesPerScanLine: 3584
[    83.532] 	BnkNumberOfImagePages: 2
[    83.532] 	LinNumberOfImagePages: 2
[    83.532] 	LinRedMaskSize: 5
[    83.532] 	LinRedFieldPosition: 11
[    83.532] 	LinGreenMaskSize: 6
[    83.532] 	LinGreenFieldPosition: 5
[    83.532] 	LinBlueMaskSize: 5
[    83.532] 	LinBlueFieldPosition: 0
[    83.532] 	LinRsvdMaskSize: 0
[    83.532] 	LinRsvdFieldPosition: 0
[    83.532] 	MaxPixelClock: 400000000
[    83.532] Mode: 186 (1792x1344)
[    83.532] 	ModeAttributes: 0xba
[    83.532] 	WinAAttributes: 0x7
[    83.532] 	WinBAttributes: 0x0
[    83.532] 	WinGranularity: 64
[    83.532] 	WinSize: 64
[    83.532] 	WinASegment: 0xa000
[    83.532] 	WinBSegment: 0x0
[    83.532] 	WinFuncPtr: 0xc000545d
[    83.532] 	BytesPerScanline: 7168
[    83.532] 	XResolution: 1792
[    83.532] 	YResolution: 1344
[    83.532] 	XCharSize: 8
[    83.532] 	YCharSize: 16
[    83.532] 	NumberOfPlanes: 1
[    83.532] 	BitsPerPixel: 32
[    83.532] 	NumberOfBanks: 1
[    83.532] 	MemoryModel: 6
[    83.532] 	BankSize: 0
[    83.532] 	NumberOfImages: 1
[    83.532] 	RedMaskSize: 8
[    83.532] 	RedFieldPosition: 16
[    83.532] 	GreenMaskSize: 8
[    83.532] 	GreenFieldPosition: 8
[    83.532] 	BlueMaskSize: 8
[    83.532] 	BlueFieldPosition: 0
[    83.532] 	RsvdMaskSize: 0
[    83.532] 	RsvdFieldPosition: 0
[    83.532] 	DirectColorModeInfo: 0
[    83.532] 	PhysBasePtr: 0xc0000000
[    83.532] 	LinBytesPerScanLine: 7168
[    83.532] 	BnkNumberOfImagePages: 1
[    83.532] 	LinNumberOfImagePages: 1
[    83.532] 	LinRedMaskSize: 8
[    83.532] 	LinRedFieldPosition: 16
[    83.532] 	LinGreenMaskSize: 8
[    83.532] 	LinGreenFieldPosition: 8
[    83.532] 	LinBlueMaskSize: 8
[    83.532] 	LinBlueFieldPosition: 0
[    83.532] 	LinRsvdMaskSize: 0
[    83.532] 	LinRsvdFieldPosition: 0
[    83.532] 	MaxPixelClock: 400000000
[    83.532] Mode: 1d3 (1856x1392)
[    83.532] 	ModeAttributes: 0xba
[    83.532] 	WinAAttributes: 0x7
[    83.532] 	WinBAttributes: 0x0
[    83.532] 	WinGranularity: 64
[    83.532] 	WinSize: 64
[    83.532] 	WinASegment: 0xa000
[    83.532] 	WinBSegment: 0x0
[    83.532] 	WinFuncPtr: 0xc000545d
[    83.532] 	BytesPerScanline: 1856
[    83.532] 	XResolution: 1856
[    83.532] 	YResolution: 1392
[    83.532] 	XCharSize: 8
[    83.532] 	YCharSize: 16
[    83.532] 	NumberOfPlanes: 1
[    83.533] 	BitsPerPixel: 8
[    83.533] 	NumberOfBanks: 1
[    83.533] 	MemoryModel: 4
[    83.533] 	BankSize: 0
[    83.533] 	NumberOfImages: 5
[    83.533] 	RedMaskSize: 0
[    83.533] 	RedFieldPosition: 0
[    83.533] 	GreenMaskSize: 0
[    83.533] 	GreenFieldPosition: 0
[    83.533] 	BlueMaskSize: 0
[    83.533] 	BlueFieldPosition: 0
[    83.533] 	RsvdMaskSize: 0
[    83.533] 	RsvdFieldPosition: 0
[    83.533] 	DirectColorModeInfo: 0
[    83.533] 	PhysBasePtr: 0xc0000000
[    83.533] 	LinBytesPerScanLine: 1856
[    83.533] 	BnkNumberOfImagePages: 5
[    83.533] 	LinNumberOfImagePages: 5
[    83.533] 	LinRedMaskSize: 0
[    83.533] 	LinRedFieldPosition: 0
[    83.533] 	LinGreenMaskSize: 0
[    83.533] 	LinGreenFieldPosition: 0
[    83.533] 	LinBlueMaskSize: 0
[    83.533] 	LinBlueFieldPosition: 0
[    83.533] 	LinRsvdMaskSize: 0
[    83.533] 	LinRsvdFieldPosition: 0
[    83.533] 	MaxPixelClock: 400000000
[    83.533] Mode: 1d5 (1856x1392)
[    83.533] 	ModeAttributes: 0xba
[    83.533] 	WinAAttributes: 0x7
[    83.533] 	WinBAttributes: 0x0
[    83.533] 	WinGranularity: 64
[    83.533] 	WinSize: 64
[    83.533] 	WinASegment: 0xa000
[    83.533] 	WinBSegment: 0x0
[    83.533] 	WinFuncPtr: 0xc000545d
[    83.533] 	BytesPerScanline: 3712
[    83.533] 	XResolution: 1856
[    83.533] 	YResolution: 1392
[    83.533] 	XCharSize: 8
[    83.533] 	YCharSize: 16
[    83.533] 	NumberOfPlanes: 1
[    83.533] 	BitsPerPixel: 16
[    83.533] 	NumberOfBanks: 1
[    83.533] 	MemoryModel: 6
[    83.533] 	BankSize: 0
[    83.533] 	NumberOfImages: 2
[    83.533] 	RedMaskSize: 5
[    83.533] 	RedFieldPosition: 11
[    83.533] 	GreenMaskSize: 6
[    83.533] 	GreenFieldPosition: 5
[    83.533] 	BlueMaskSize: 5
[    83.533] 	BlueFieldPosition: 0
[    83.533] 	RsvdMaskSize: 0
[    83.533] 	RsvdFieldPosition: 0
[    83.533] 	DirectColorModeInfo: 0
[    83.533] 	PhysBasePtr: 0xc0000000
[    83.533] 	LinBytesPerScanLine: 3712
[    83.533] 	BnkNumberOfImagePages: 2
[    83.533] 	LinNumberOfImagePages: 2
[    83.533] 	LinRedMaskSize: 5
[    83.533] 	LinRedFieldPosition: 11
[    83.533] 	LinGreenMaskSize: 6
[    83.533] 	LinGreenFieldPosition: 5
[    83.533] 	LinBlueMaskSize: 5
[    83.533] 	LinBlueFieldPosition: 0
[    83.533] 	LinRsvdMaskSize: 0
[    83.533] 	LinRsvdFieldPosition: 0
[    83.533] 	MaxPixelClock: 400000000
[    83.533] Mode: 1d6 (1856x1392)
[    83.533] 	ModeAttributes: 0xba
[    83.533] 	WinAAttributes: 0x7
[    83.533] 	WinBAttributes: 0x0
[    83.533] 	WinGranularity: 64
[    83.533] 	WinSize: 64
[    83.533] 	WinASegment: 0xa000
[    83.533] 	WinBSegment: 0x0
[    83.533] 	WinFuncPtr: 0xc000545d
[    83.533] 	BytesPerScanline: 7424
[    83.533] 	XResolution: 1856
[    83.533] 	YResolution: 1392
[    83.533] 	XCharSize: 8
[    83.533] 	YCharSize: 16
[    83.533] 	NumberOfPlanes: 1
[    83.533] 	BitsPerPixel: 32
[    83.533] 	NumberOfBanks: 1
[    83.533] 	MemoryModel: 6
[    83.533] 	BankSize: 0
[    83.533] 	NumberOfImages: 1
[    83.533] 	RedMaskSize: 8
[    83.533] 	RedFieldPosition: 16
[    83.533] 	GreenMaskSize: 8
[    83.533] 	GreenFieldPosition: 8
[    83.533] 	BlueMaskSize: 8
[    83.533] 	BlueFieldPosition: 0
[    83.533] 	RsvdMaskSize: 0
[    83.533] 	RsvdFieldPosition: 0
[    83.533] 	DirectColorModeInfo: 0
[    83.533] 	PhysBasePtr: 0xc0000000
[    83.533] 	LinBytesPerScanLine: 7424
[    83.533] 	BnkNumberOfImagePages: 1
[    83.533] 	LinNumberOfImagePages: 1
[    83.533] 	LinRedMaskSize: 8
[    83.533] 	LinRedFieldPosition: 16
[    83.533] 	LinGreenMaskSize: 8
[    83.533] 	LinGreenFieldPosition: 8
[    83.533] 	LinBlueMaskSize: 8
[    83.533] 	LinBlueFieldPosition: 0
[    83.533] 	LinRsvdMaskSize: 0
[    83.533] 	LinRsvdFieldPosition: 0
[    83.534] 	MaxPixelClock: 400000000
[    83.534] Mode: 1e3 (1920x1440)
[    83.534] 	ModeAttributes: 0xba
[    83.534] 	WinAAttributes: 0x7
[    83.534] 	WinBAttributes: 0x0
[    83.534] 	WinGranularity: 64
[    83.534] 	WinSize: 64
[    83.534] 	WinASegment: 0xa000
[    83.534] 	WinBSegment: 0x0
[    83.534] 	WinFuncPtr: 0xc000545d
[    83.534] 	BytesPerScanline: 1920
[    83.534] 	XResolution: 1920
[    83.534] 	YResolution: 1440
[    83.534] 	XCharSize: 8
[    83.534] 	YCharSize: 16
[    83.534] 	NumberOfPlanes: 1
[    83.534] 	BitsPerPixel: 8
[    83.534] 	NumberOfBanks: 1
[    83.534] 	MemoryModel: 4
[    83.534] 	BankSize: 0
[    83.534] 	NumberOfImages: 4
[    83.534] 	RedMaskSize: 0
[    83.534] 	RedFieldPosition: 0
[    83.534] 	GreenMaskSize: 0
[    83.534] 	GreenFieldPosition: 0
[    83.534] 	BlueMaskSize: 0
[    83.534] 	BlueFieldPosition: 0
[    83.534] 	RsvdMaskSize: 0
[    83.534] 	RsvdFieldPosition: 0
[    83.534] 	DirectColorModeInfo: 0
[    83.534] 	PhysBasePtr: 0xc0000000
[    83.534] 	LinBytesPerScanLine: 1920
[    83.534] 	BnkNumberOfImagePages: 4
[    83.534] 	LinNumberOfImagePages: 4
[    83.534] 	LinRedMaskSize: 0
[    83.534] 	LinRedFieldPosition: 0
[    83.534] 	LinGreenMaskSize: 0
[    83.534] 	LinGreenFieldPosition: 0
[    83.534] 	LinBlueMaskSize: 0
[    83.534] 	LinBlueFieldPosition: 0
[    83.534] 	LinRsvdMaskSize: 0
[    83.534] 	LinRsvdFieldPosition: 0
[    83.534] 	MaxPixelClock: 400000000
[    83.534] Mode: 1e5 (1920x1440)
[    83.534] 	ModeAttributes: 0xba
[    83.534] 	WinAAttributes: 0x7
[    83.534] 	WinBAttributes: 0x0
[    83.534] 	WinGranularity: 64
[    83.534] 	WinSize: 64
[    83.534] 	WinASegment: 0xa000
[    83.534] 	WinBSegment: 0x0
[    83.534] 	WinFuncPtr: 0xc000545d
[    83.534] 	BytesPerScanline: 3840
[    83.534] 	XResolution: 1920
[    83.534] 	YResolution: 1440
[    83.534] 	XCharSize: 8
[    83.534] 	YCharSize: 16
[    83.534] 	NumberOfPlanes: 1
[    83.534] 	BitsPerPixel: 16
[    83.534] 	NumberOfBanks: 1
[    83.534] 	MemoryModel: 6
[    83.534] 	BankSize: 0
[    83.534] 	NumberOfImages: 2
[    83.534] 	RedMaskSize: 5
[    83.534] 	RedFieldPosition: 11
[    83.534] 	GreenMaskSize: 6
[    83.534] 	GreenFieldPosition: 5
[    83.534] 	BlueMaskSize: 5
[    83.534] 	BlueFieldPosition: 0
[    83.534] 	RsvdMaskSize: 0
[    83.534] 	RsvdFieldPosition: 0
[    83.534] 	DirectColorModeInfo: 0
[    83.534] 	PhysBasePtr: 0xc0000000
[    83.534] 	LinBytesPerScanLine: 3840
[    83.534] 	BnkNumberOfImagePages: 2
[    83.534] 	LinNumberOfImagePages: 2
[    83.534] 	LinRedMaskSize: 5
[    83.534] 	LinRedFieldPosition: 11
[    83.534] 	LinGreenMaskSize: 6
[    83.534] 	LinGreenFieldPosition: 5
[    83.534] 	LinBlueMaskSize: 5
[    83.534] 	LinBlueFieldPosition: 0
[    83.534] 	LinRsvdMaskSize: 0
[    83.534] 	LinRsvdFieldPosition: 0
[    83.534] 	MaxPixelClock: 400000000
[    83.535] Mode: 1e6 (1920x1440)
[    83.535] 	ModeAttributes: 0xba
[    83.535] 	WinAAttributes: 0x7
[    83.535] 	WinBAttributes: 0x0
[    83.535] 	WinGranularity: 64
[    83.535] 	WinSize: 64
[    83.535] 	WinASegment: 0xa000
[    83.535] 	WinBSegment: 0x0
[    83.535] 	WinFuncPtr: 0xc000545d
[    83.535] 	BytesPerScanline: 7680
[    83.535] 	XResolution: 1920
[    83.535] 	YResolution: 1440
[    83.535] 	XCharSize: 8
[    83.535] 	YCharSize: 16
[    83.535] 	NumberOfPlanes: 1
[    83.535] 	BitsPerPixel: 32
[    83.535] 	NumberOfBanks: 1
[    83.535] 	MemoryModel: 6
[    83.535] 	BankSize: 0
[    83.535] 	NumberOfImages: 1
[    83.535] 	RedMaskSize: 8
[    83.535] 	RedFieldPosition: 16
[    83.535] 	GreenMaskSize: 8
[    83.535] 	GreenFieldPosition: 8
[    83.535] 	BlueMaskSize: 8
[    83.535] 	BlueFieldPosition: 0
[    83.535] 	RsvdMaskSize: 0
[    83.535] 	RsvdFieldPosition: 0
[    83.535] 	DirectColorModeInfo: 0
[    83.535] 	PhysBasePtr: 0xc0000000
[    83.535] 	LinBytesPerScanLine: 7680
[    83.535] 	BnkNumberOfImagePages: 1
[    83.535] 	LinNumberOfImagePages: 1
[    83.535] 	LinRedMaskSize: 8
[    83.535] 	LinRedFieldPosition: 16
[    83.535] 	LinGreenMaskSize: 8
[    83.535] 	LinGreenFieldPosition: 8
[    83.535] 	LinBlueMaskSize: 8
[    83.535] 	LinBlueFieldPosition: 0
[    83.535] 	LinRsvdMaskSize: 0
[    83.535] 	LinRsvdFieldPosition: 0
[    83.535] 	MaxPixelClock: 400000000
[    83.535] Mode: 1ee (1920x1080)
[    83.535] 	ModeAttributes: 0xbb
[    83.535] 	WinAAttributes: 0x7
[    83.535] 	WinBAttributes: 0x0
[    83.535] 	WinGranularity: 64
[    83.535] 	WinSize: 64
[    83.535] 	WinASegment: 0xa000
[    83.535] 	WinBSegment: 0x0
[    83.535] 	WinFuncPtr: 0xc000545d
[    83.535] 	BytesPerScanline: 1920
[    83.535] 	XResolution: 1920
[    83.535] 	YResolution: 1080
[    83.535] 	XCharSize: 8
[    83.535] 	YCharSize: 16
[    83.535] 	NumberOfPlanes: 1
[    83.535] 	BitsPerPixel: 8
[    83.535] 	NumberOfBanks: 1
[    83.535] 	MemoryModel: 4
[    83.535] 	BankSize: 0
[    83.535] 	NumberOfImages: 7
[    83.535] 	RedMaskSize: 0
[    83.535] 	RedFieldPosition: 0
[    83.535] 	GreenMaskSize: 0
[    83.535] 	GreenFieldPosition: 0
[    83.535] 	BlueMaskSize: 0
[    83.535] 	BlueFieldPosition: 0
[    83.535] 	RsvdMaskSize: 0
[    83.535] 	RsvdFieldPosition: 0
[    83.535] 	DirectColorModeInfo: 0
[    83.535] 	PhysBasePtr: 0xc0000000
[    83.535] 	LinBytesPerScanLine: 1920
[    83.535] 	BnkNumberOfImagePages: 7
[    83.535] 	LinNumberOfImagePages: 7
[    83.535] 	LinRedMaskSize: 0
[    83.535] 	LinRedFieldPosition: 0
[    83.535] 	LinGreenMaskSize: 0
[    83.535] 	LinGreenFieldPosition: 0
[    83.535] 	LinBlueMaskSize: 0
[    83.535] 	LinBlueFieldPosition: 0
[    83.535] 	LinRsvdMaskSize: 0
[    83.535] 	LinRsvdFieldPosition: 0
[    83.535] 	MaxPixelClock: 400000000
[    83.536] Mode: 1ef (1920x1080)
[    83.536] 	ModeAttributes: 0xbb
[    83.536] 	WinAAttributes: 0x7
[    83.536] 	WinBAttributes: 0x0
[    83.536] 	WinGranularity: 64
[    83.536] 	WinSize: 64
[    83.536] 	WinASegment: 0xa000
[    83.536] 	WinBSegment: 0x0
[    83.536] 	WinFuncPtr: 0xc000545d
[    83.536] 	BytesPerScanline: 3840
[    83.536] 	XResolution: 1920
[    83.536] 	YResolution: 1080
[    83.536] 	XCharSize: 8
[    83.536] 	YCharSize: 16
[    83.536] 	NumberOfPlanes: 1
[    83.536] 	BitsPerPixel: 16
[    83.536] 	NumberOfBanks: 1
[    83.536] 	MemoryModel: 6
[    83.536] 	BankSize: 0
[    83.536] 	NumberOfImages: 3
[    83.536] 	RedMaskSize: 5
[    83.536] 	RedFieldPosition: 11
[    83.536] 	GreenMaskSize: 6
[    83.536] 	GreenFieldPosition: 5
[    83.536] 	BlueMaskSize: 5
[    83.536] 	BlueFieldPosition: 0
[    83.536] 	RsvdMaskSize: 0
[    83.536] 	RsvdFieldPosition: 0
[    83.536] 	DirectColorModeInfo: 0
[    83.536] 	PhysBasePtr: 0xc0000000
[    83.536] 	LinBytesPerScanLine: 3840
[    83.536] 	BnkNumberOfImagePages: 3
[    83.536] 	LinNumberOfImagePages: 3
[    83.536] 	LinRedMaskSize: 5
[    83.536] 	LinRedFieldPosition: 11
[    83.536] 	LinGreenMaskSize: 6
[    83.536] 	LinGreenFieldPosition: 5
[    83.536] 	LinBlueMaskSize: 5
[    83.536] 	LinBlueFieldPosition: 0
[    83.536] 	LinRsvdMaskSize: 0
[    83.536] 	LinRsvdFieldPosition: 0
[    83.536] 	MaxPixelClock: 400000000
[    83.536] *Mode: 1f0 (1920x1080)
[    83.536] 	ModeAttributes: 0xbb
[    83.536] 	WinAAttributes: 0x7
[    83.536] 	WinBAttributes: 0x0
[    83.536] 	WinGranularity: 64
[    83.536] 	WinSize: 64
[    83.536] 	WinASegment: 0xa000
[    83.536] 	WinBSegment: 0x0
[    83.536] 	WinFuncPtr: 0xc000545d
[    83.536] 	BytesPerScanline: 7680
[    83.536] 	XResolution: 1920
[    83.536] 	YResolution: 1080
[    83.536] 	XCharSize: 8
[    83.536] 	YCharSize: 16
[    83.536] 	NumberOfPlanes: 1
[    83.536] 	BitsPerPixel: 32
[    83.536] 	NumberOfBanks: 1
[    83.536] 	MemoryModel: 6
[    83.536] 	BankSize: 0
[    83.536] 	NumberOfImages: 1
[    83.536] 	RedMaskSize: 8
[    83.536] 	RedFieldPosition: 16
[    83.536] 	GreenMaskSize: 8
[    83.536] 	GreenFieldPosition: 8
[    83.536] 	BlueMaskSize: 8
[    83.536] 	BlueFieldPosition: 0
[    83.536] 	RsvdMaskSize: 0
[    83.536] 	RsvdFieldPosition: 0
[    83.536] 	DirectColorModeInfo: 0
[    83.536] 	PhysBasePtr: 0xc0000000
[    83.536] 	LinBytesPerScanLine: 7680
[    83.536] 	BnkNumberOfImagePages: 1
[    83.536] 	LinNumberOfImagePages: 1
[    83.536] 	LinRedMaskSize: 8
[    83.536] 	LinRedFieldPosition: 16
[    83.536] 	LinGreenMaskSize: 8
[    83.536] 	LinGreenFieldPosition: 8
[    83.536] 	LinBlueMaskSize: 8
[    83.536] 	LinBlueFieldPosition: 0
[    83.536] 	LinRsvdMaskSize: 0
[    83.536] 	LinRsvdFieldPosition: 0
[    83.536] 	MaxPixelClock: 400000000
[    83.536] 
[    83.536] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    83.536] (II) VESA(0): <default monitor>: Using hsync value of 66.59 kHz
[    83.536] (II) VESA(0): <default monitor>: Using vrefresh value of 59.93 Hz
[    83.536] (WW) VESA(0): Unable to estimate virtual size
[    83.536] (II) VESA(0): Not using built-in mode "1400x1050" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "1280x960" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "1152x864" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    83.536] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    83.536] (--) VESA(0): Virtual size is 1920x1080 (pitch 1920)
[    83.536] (**) VESA(0): *Built-in mode "1920x1080"
[    83.536] (**) VESA(0): Display dimensions: (350, 190) mm
[    83.536] (**) VESA(0): DPI set to (139, 144)
[    83.536] (**) VESA(0): Using "Shadow Framebuffer"
[    83.536] (II) Loading sub module "shadow"
[    83.536] (II) LoadModule: "shadow"
[    83.537] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    83.537] (II) Module shadow: vendor="X.Org Foundation"
[    83.537] 	compiled for 1.13.3, module version = 1.1.0
[    83.537] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    83.537] (II) Loading sub module "fb"
[    83.537] (II) LoadModule: "fb"
[    83.537] (II) Loading /usr/lib/xorg/modules/libfb.so
[    83.537] (II) Module fb: vendor="X.Org Foundation"
[    83.537] 	compiled for 1.13.3, module version = 1.0.0
[    83.537] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    83.537] (II) UnloadModule: "radeon"
[    83.537] (II) UnloadModule: "modesetting"
[    83.537] (II) Unloading modesetting
[    83.537] (II) UnloadModule: "fbdev"
[    83.537] (II) Unloading fbdev
[    83.537] (II) UnloadSubModule: "fbdevhw"
[    83.537] (II) Unloading fbdevhw
[    83.537] (==) Depth 24 pixmap format is 32 bpp
[    83.537] (II) Loading sub module "int10"
[    83.537] (II) LoadModule: "int10"
[    83.537] (II) Loading /usr/lib/xorg/modules/libint10.so
[    83.537] (II) Module int10: vendor="X.Org Foundation"
[    83.537] 	compiled for 1.13.3, module version = 1.0.0
[    83.537] 	ABI class: X.Org Video Driver, version 13.1
[    83.537] (II) VESA(0): initializing int10
[    86.381] (II) VESA(0): VESA BIOS detected
[    86.381] (II) VESA(0): VESA VBE Version 3.0
[    86.381] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    86.381] (II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
[    86.381] (II) VESA(0): VESA VBE OEM Software Rev: 11.22
[    86.381] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
[    86.381] (II) VESA(0): VESA VBE OEM Product: M97
[    86.381] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    86.381] (II) VESA(0): virtual address = 0x7f00cd2b8000,
	physical address = 0xc0000000, size = 16777216
[    86.396] (II) VESA(0): Setting up VESA Mode 0x1F0 (1920x1080)
[    86.396] (II) VESA(0): VBESetVBEMode failed, mode set without customized refresh.
[    86.443] (==) VESA(0): Default visual is TrueColor
[    86.443] (==) VESA(0): Backing store disabled
[    86.443] (==) VESA(0): DPMS enabled
[    86.443] (==) RandR enabled
[    86.446] (II) SELinux: Disabled on system
[    86.447] (II) AIGLX: Screen 0 is not DRI2 capable
[    86.447] (II) AIGLX: Screen 0 is not DRI capable
[    86.606] (II) AIGLX: Loaded and initialized swrast
[    86.606] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    86.615] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    86.616] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    86.616] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    86.616] (II) LoadModule: "evdev"
[    86.617] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    86.620] (II) Module evdev: vendor="X.Org Foundation"
[    86.620] 	compiled for 1.13.3, module version = 2.7.3
[    86.620] 	Module class: X.Org XInput Driver
[    86.620] 	ABI class: X.Org XInput driver, version 18.0
[    86.620] (II) Using input driver 'evdev' for 'Power Button'
[    86.620] (**) Power Button: always reports core events
[    86.620] (**) evdev: Power Button: Device: "/dev/input/event2"
[    86.620] (--) evdev: Power Button: Vendor 0 Product 0x1
[    86.621] (--) evdev: Power Button: Found keys
[    86.621] (II) evdev: Power Button: Configuring as keyboard
[    86.621] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    86.621] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    86.621] (**) Option "xkb_rules" "evdev"
[    86.621] (**) Option "xkb_model" "pc105"
[    86.621] (**) Option "xkb_layout" "us"
[    86.621] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    86.621] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    86.621] (II) Using input driver 'evdev' for 'Video Bus'
[    86.621] (**) Video Bus: always reports core events
[    86.621] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    86.621] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    86.621] (--) evdev: Video Bus: Found keys
[    86.621] (II) evdev: Video Bus: Configuring as keyboard
[    86.621] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:24/LNXVIDEO:01/input/input4/event4"
[    86.621] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    86.621] (**) Option "xkb_rules" "evdev"
[    86.621] (**) Option "xkb_model" "pc105"
[    86.621] (**) Option "xkb_layout" "us"
[    86.621] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    86.621] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    86.621] (II) Using input driver 'evdev' for 'Power Button'
[    86.621] (**) Power Button: always reports core events
[    86.621] (**) evdev: Power Button: Device: "/dev/input/event0"
[    86.621] (--) evdev: Power Button: Vendor 0 Product 0x1
[    86.621] (--) evdev: Power Button: Found keys
[    86.621] (II) evdev: Power Button: Configuring as keyboard
[    86.621] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    86.621] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    86.621] (**) Option "xkb_rules" "evdev"
[    86.621] (**) Option "xkb_model" "pc105"
[    86.621] (**) Option "xkb_layout" "us"
[    86.622] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    86.622] (II) No input driver specified, ignoring this device.
[    86.622] (II) This device may have been added with another device file.
[    86.622] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0/drm/card0
[    86.622] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    86.622] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event10)
[    86.622] (II) No input driver specified, ignoring this device.
[    86.622] (II) This device may have been added with another device file.
[    86.622] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event8)
[    86.622] (II) No input driver specified, ignoring this device.
[    86.622] (II) This device may have been added with another device file.
[    86.622] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event9)
[    86.622] (II) No input driver specified, ignoring this device.
[    86.622] (II) This device may have been added with another device file.
[    86.623] (II) config/udev: Adding input device HP Webcam (/dev/input/event7)
[    86.623] (**) HP Webcam: Applying InputClass "evdev keyboard catchall"
[    86.623] (II) Using input driver 'evdev' for 'HP Webcam'
[    86.623] (**) HP Webcam: always reports core events
[    86.623] (**) evdev: HP Webcam: Device: "/dev/input/event7"
[    86.623] (--) evdev: HP Webcam: Vendor 0x4f2 Product 0xb16c
[    86.623] (--) evdev: HP Webcam: Found keys
[    86.623] (II) evdev: HP Webcam: Configuring as keyboard
[    86.623] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7/event7"
[    86.623] (II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD, id 9)
[    86.623] (**) Option "xkb_rules" "evdev"
[    86.623] (**) Option "xkb_model" "pc105"
[    86.623] (**) Option "xkb_layout" "us"
[    86.623] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    86.623] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    86.623] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    86.623] (**) AT Translated Set 2 keyboard: always reports core events
[    86.623] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    86.623] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    86.623] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    86.623] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    86.623] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    86.623] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[    86.623] (**) Option "xkb_rules" "evdev"
[    86.623] (**) Option "xkb_model" "pc105"
[    86.623] (**) Option "xkb_layout" "us"
[    86.623] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event11)
[    86.623] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    86.623] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    86.623] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    86.623] (II) LoadModule: "synaptics"
[    86.624] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    86.624] (II) Module synaptics: vendor="X.Org Foundation"
[    86.624] 	compiled for 1.13.1.901, module version = 1.6.2
[    86.624] 	Module class: X.Org XInput Driver
[    86.624] 	ABI class: X.Org XInput driver, version 18.0
[    86.624] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    86.624] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    86.624] (**) Option "Device" "/dev/input/event11"
[    86.652] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    86.652] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    86.652] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5458
[    86.652] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4514
[    86.652] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    86.652] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    86.652] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    86.652] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    86.652] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    86.652] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    86.652] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    86.658] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input11/event11"
[    86.658] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 11)
[    86.658] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    86.658] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    86.658] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[    86.658] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    86.658] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    86.658] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    86.658] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    86.658] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    86.658] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    86.658] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    86.658] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[    86.658] (II) No input driver specified, ignoring this device.
[    86.658] (II) This device may have been added with another device file.
[    86.658] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    86.658] (II) No input driver specified, ignoring this device.
[    86.658] (II) This device may have been added with another device file.
[    86.660] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event5)
[    86.660] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    86.660] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    86.660] (**) HP WMI hotkeys: always reports core events
[    86.660] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event5"
[    86.660] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    86.660] (--) evdev: HP WMI hotkeys: Found keys
[    86.660] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    86.660] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[    86.660] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[    86.660] (**) Option "xkb_rules" "evdev"
[    86.660] (**) Option "xkb_model" "pc105"
[    86.660] (**) Option "xkb_layout" "us"
```

```
~$ glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_MESA_copy_sub_buffer
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_create_context_robustness, GLX_ARB_framebuffer_sRGB, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_framebuffer_sRGB, 
    GLX_EXT_create_context_es2_profile, GLX_MESA_copy_sub_buffer, 
    GLX_MESA_multithread_makecurrent, GLX_MESA_swap_control, 
    GLX_OML_swap_method, GLX_OML_sync_control, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_INTEL_swap_event
GLX version: 1.4
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_multithread_makecurrent, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_EXT_texture_from_pixmap
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string: 2.1 Mesa 9.1.1
OpenGL shading language version string: 1.20
OpenGL extensions:
    GL_ARB_multisample, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_copy_texture, 
    GL_EXT_polygon_offset, GL_EXT_subtexture, GL_EXT_texture_object, 
    GL_EXT_vertex_array, GL_EXT_compiled_vertex_array, GL_EXT_texture, 
    GL_EXT_texture3D, GL_IBM_rasterpos_clip, GL_ARB_point_parameters, 
    GL_EXT_draw_range_elements, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_separate_specular_color, 
    GL_EXT_texture_edge_clamp, GL_SGIS_generate_mipmap, 
    GL_SGIS_texture_border_clamp, GL_SGIS_texture_edge_clamp, 
    GL_SGIS_texture_lod, GL_ARB_multitexture, GL_IBM_multimode_draw_arrays, 
    GL_IBM_texture_mirrored_repeat, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_transpose_matrix, 
    GL_EXT_blend_func_separate, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_secondary_color, GL_EXT_texture_env_add, GL_EXT_texture_lod_bias, 
    GL_INGR_blend_func_separate, GL_NV_blend_square, GL_NV_light_max_exponent, 
    GL_NV_texgen_reflection, GL_NV_texture_env_combine4, GL_S3_s3tc, 
    GL_SUN_multi_draw_arrays, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_EXT_framebuffer_object, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_MESA_window_pos, GL_NV_packed_depth_stencil, 
    GL_NV_texture_rectangle, GL_ARB_depth_texture, GL_ARB_occlusion_query, 
    GL_ARB_shadow, GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar, 
    GL_ARB_texture_env_dot3, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_window_pos, GL_EXT_stencil_two_side, GL_EXT_texture_cube_map, 
    GL_NV_fog_distance, GL_APPLE_packed_pixels, GL_APPLE_vertex_array_object, 
    GL_ARB_draw_buffers, GL_ARB_fragment_program, GL_ARB_fragment_shader, 
    GL_ARB_shader_objects, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, GL_MESA_pack_invert, 
    GL_MESA_ycbcr_texture, GL_NV_primitive_restart, 
    GL_ARB_fragment_program_shadow, GL_ARB_half_float_pixel, 
    GL_ARB_occlusion_query2, GL_ARB_point_sprite, GL_ARB_shading_language_100, 
    GL_ARB_sync, GL_ARB_texture_non_power_of_two, GL_ARB_vertex_buffer_object, 
    GL_ATI_blend_equation_separate, GL_EXT_blend_equation_separate, 
    GL_OES_read_format, GL_ARB_color_buffer_float, GL_ARB_pixel_buffer_object, 
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_float, 
    GL_ARB_texture_rectangle, GL_ATI_texture_compression_3dc, 
    GL_EXT_pixel_buffer_object, GL_EXT_texture_compression_dxt1, 
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, 
    GL_EXT_texture_shared_exponent, GL_ARB_framebuffer_object, 
    GL_EXT_framebuffer_blit, GL_EXT_packed_depth_stencil, 
    GL_ARB_vertex_array_object, GL_ATI_separate_stencil, 
    GL_ATI_texture_mirror_once, GL_EXT_draw_buffers2, GL_EXT_draw_instanced, 
    GL_EXT_gpu_program_parameters, GL_EXT_texture_array, 
    GL_EXT_texture_compression_latc, GL_EXT_texture_integer, 
    GL_EXT_texture_sRGB_decode, GL_EXT_timer_query, GL_OES_EGL_image, 
    GL_MESA_texture_array, GL_ARB_copy_buffer, GL_ARB_draw_instanced, 
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays, 
    GL_ARB_map_buffer_range, GL_ARB_texture_rg, GL_ARB_texture_swizzle, 
    GL_ARB_vertex_array_bgra, GL_EXT_separate_shader_objects, 
    GL_EXT_texture_swizzle, GL_EXT_vertex_array_bgra, 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
    GL_ARB_ES2_compatibility, GL_ARB_debug_output, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_explicit_attrib_location, 
    GL_ARB_fragment_coord_conventions, GL_ARB_provoking_vertex, 
    GL_ARB_sampler_objects, GL_ARB_shader_texture_lod, 
    GL_ARB_texture_rgb10_a2ui, GL_ARB_uniform_buffer_object, 
    GL_ARB_vertex_type_2_10_10_10_rev, GL_EXT_provoking_vertex, 
    GL_EXT_texture_snorm, GL_MESA_texture_signed_rgba, 
    GL_ARB_get_program_binary, GL_ARB_robustness, GL_ARB_timer_query, 
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3, 
    GL_ANGLE_texture_compression_dxt3, GL_ANGLE_texture_compression_dxt5, 
    GL_ARB_internalformat_query, GL_ARB_texture_storage, 
    GL_ARB_transform_feedback_instanced, GL_EXT_transform_feedback, 
    GL_ARB_invalidate_subdata

96 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x021 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0d2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x0d7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x0d8 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0d9 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0da 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0db 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0dc 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x0dd 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x0de 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x0df 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e0 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e1 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x0e2 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e3 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e4 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e5 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e6 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0e7 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0e8 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0e9 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ea 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0eb 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ec 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0ed 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0ee 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ef 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f0 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f1 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f2 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0f3 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0f4 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f5 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f6 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f7 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0f8 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0f9 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0fa 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fb 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fc 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0fd 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0fe 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0ff 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x100 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x101 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x102 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x103 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x104 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x105 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x106 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x107 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x108 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x109 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x10b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x10c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x10d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x10e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x10f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x110 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x111 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x112 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x113 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x114 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x115 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x116 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x117 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x118 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x119 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11a 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11b 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x11d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x11e 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x11f 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x120 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x121 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x122 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x123 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x124 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x125 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x126 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x127 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x128 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x129 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x12a 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12b 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12c 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12d 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x12e 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x12f 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x041 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

144 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x042 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x043 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x044 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x045 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x046 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x047 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x048 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x049 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04a 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04b 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04c 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x04d 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x04e 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x04f 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x050 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x051 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x052 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x053 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x054 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x055 24 tc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x056 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x057 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x058 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x059 24 tc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x05a 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05b 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05c 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05d 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x05e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x05f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x060 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x061 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x062 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x063 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x064 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x065 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x066 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x067 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x068 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x069 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06a 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x06b 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x06c 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x06d 24 tc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x06e 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x06f 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x070 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x071 24 tc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x072  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x073  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x074  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x075  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x076  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x077  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x078  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x079  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07a  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x07b  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07c  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x07d  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x07e  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x07f  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x080  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x081  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x082  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x083  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x084  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x085  0 tc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x086  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x087  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x088  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x089  0 tc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x08a 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08b 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08c 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08d 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x08e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0  0  0  0  0  0 0 None
0x08f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0  0  0 16 16 16 16  0 0 Slow
0x090 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x091 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x092 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x093 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x094 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0  0  0  0  0  0 0 None
0x095 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  0 16 16 16 16  0 0 Slow
0x096 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x097 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x098 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x099 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09a 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x09b 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8 16 16 16 16  0 0 Slow
0x09c 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x09d 24 dc  0  32  0 r  . .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x09e 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x09f 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0a0 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0  0  0  0  0  0 0 None
0x0a1 24 dc  0  32  0 r  y .   8  8  8  8 .  .  0 32  0 16 16 16 16  0 0 Slow
0x0a2 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a3 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a4 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a5 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0a7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0a8 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0a9 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0aa 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ab 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ac 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0ad 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0ae 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0af 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b0 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b1 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b2 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0b3 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0b4 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b5 24 dc  0  24  0 r  . .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b6 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b7 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0b8 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0b9 24 dc  0  24  0 r  y .   8  8  8  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0ba  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bb  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0bc  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bd  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0be  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0  0  0  0  0  0 0 None
0x0bf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0  0  0 16 16 16  0  0 0 Slow
0x0c0  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c1  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c2  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c3  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c4  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0  0  0  0  0  0 0 None
0x0c5  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  0 16 16 16  0  0 0 Slow
0x0c6  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c7  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0c8  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0c9  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0ca  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8  0  0  0  0  0 0 None
0x0cb  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 24  8 16 16 16  0  0 0 Slow
0x0cc  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0cd  0 dc  0  16  0 r  . .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0ce  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0cf  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
0x0d0  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0  0  0  0  0  0 0 None
0x0d1  0 dc  0  16  0 r  y .   5  6  5  0 .  .  0 32  0 16 16 16  0  0 0 Slow
```

My other major concern is that Xorg doesn't appear to be detecting the proper display modes for the laptop screen.

```
~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080       0.0* 

```

And just for fun:
```
~$ LIBGL_DEBUG=verbose glxgears
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
2004 frames in 5.0 seconds = 400.596 FPS
2107 frames in 5.0 seconds = 421.346 FPS
2096 frames in 5.0 seconds = 419.178 FPS
2185 frames in 5.0 seconds = 436.810 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"
      after 29578 requests (29576 known processed) with 0 events remaining.

```

Any suggestions on how to proceed? I'd eventually like to be able to set things up so that I can hook up to a projector or second monitor at work, but right now I would be pretty happy if Unity wasn't so laggy.

Any advice would be much appreciated. Thanks!

EDIT: To be clear, I am trying to get the open source radeon driver for X to work. I have no interest in using the unsupported proprietary driver.

---

### Post by 2F4U on 2013-05-09
> [    80.548] (EE) open /dev/fb0: No such file or directory
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"
[    80.548] (EE) Screen 0 deleted because of no matching config section.
[    80.548] (II) UnloadModule: "radeon"

There are some errors in your Xorg log file, which may be the reason why the radeon driver isn't used. Do you have a custom configuration, for example, xorg.conf?

---

### Post by ironyCurtain on 2013-05-09
I do not have a customized xorg.conf file. I can generate an xorg.conf.new file in my home directory that looks like this (using `sudo Xorg :1 -configure`):
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	Screen      3  "Screen3" RightOf "Screen2"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor3"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "ColorTiling"        	# [<bool>]
        #Option     "ColorTiling2D"      	# [<bool>]
        #Option     "RenderAccel"        	# [<bool>]
        #Option     "SubPixelOrder"      	# [<str>]
        #Option     "AccelMethod"        	# <str>
        #Option     "EXAVSync"           	# [<bool>]
        #Option     "EXAPixmaps"         	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        #Option     "EnablePageFlip"     	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
	Identifier  "Card0"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "kmsdev"             	# <str>
        #Option     "ShadowFB"           	# [<bool>]
	Identifier  "Card1"
	Driver      "modesetting"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card2"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card3"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen3"
	Device     "Card3"
	Monitor    "Monitor3"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```
If I understand correctly this is equivalent to the xorg.conf that gets generated by Xorg each time I boot up. I got the same errors when I used it. It winds up using VESA instead of RADEON.

---

### Post by dadamia on 2013-05-09
I have a similar problem on an old Gateway laptop, which uses an ATI RV 350 Mobility Radeon 9600 M10.  I also see the radeon module loaded and later unloaded in my Xorg.0.log file and the radeon module does not show up in my lsmod output.  The laptop does not work at its native screen resolution of 1280x800, but instead comes up at 1024x768.  When used with a 1600x1200 external monitor, it does come up in the correct (1600x1200) resolution.

I also had this problem with Ubuntu 12.10, but not with 11.10 and earlier.

When I boot the  computer with a Knoppix live CD, the radeon driver is installed and the resolution is correct on both the laptop screen and the external monitor.

---

### Post by ironyCurtain on 2013-05-10
Interestingly enough the radeon module is still loaded, it is just using VESA instead.
```
@condor:~$ lsmod | grep -i radeon
radeon                937749  0 
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
drm_kms_helper         49394  1 radeon
drm                   286313  3 ttm,drm_kms_helper,radeon
``` 
I tried using the xorg.conf I generated earlier in #3 but it actually wouldn't successfully boot (it would eventually segfault). I am writing a simpler configuration in some files in /etc/X11/xorg.conf.d/*.conf that at least so far fall back to using vesa when using the radeon driver fails. If anyone has good ideas on what should go into an xorg.conf for the radeon driver I would love to hear them.

---

### Post by Mark Phelps on 2013-05-10
No amount of X.org modding is going to get you hardware acceleration.  

AMD dropped restricted driver support for their entire HD 2x/3x/4x series last Summer. The last Ubuntu version that provides that support was 12.04.1.  Starting with Ubuntu 12.04.2, the X-server was upgraded to a new version that is incompatible with the legacy HD 23x/3x/4x series drivers.

---

### Post by ironyCurtain on 2013-05-10
I am not trying to use the closed source drivers. I am trying to get the open source radeon driver to work. See here:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
and
[http://www.x.org/wiki/radeon](http://www.x.org/wiki/radeon).

They say that the open source driver supports my card with 3D hardware acceleration. It is just not in a working state right now. The radeon driver is getting unloaded for some reason and then X falls back to VESA. I think it might have something to do with kernel modesetting but I can't be sure (see the errors in the Xorg.0.log I posted above).

---

### Post by ironyCurtain on 2013-05-12
I thought I would post an update. I wound up installing Ubuntu 12.04 LTS. I was able to boot my HP Envy 15-1050nr laptop without any special kernel options, so I did not have any problems with having to have modesetting disable to even boot up. Hardware acceleration with the Xorg radeon driver just worked without any configuration. Unity is responsive and smooth with all the desktop effects. I am able to change to all the available resolutions on my monitor, whereas on 13.04 I was stuck at 1920x1080. I'm quite pleased with the stability and ease of setup of 12.04. I will probably be sticking with the LTS release at least until the next LTS release, at which point I will probably try it and make sure everything works before upgrading. This is an acceptable solution for me, although it would definitely be nice if the issues that I ran into were resolved in the next Ubuntu release.

One thing I thought it was curious was that lspci reported a different string for my video card on 12.04...
```
zach@condor:~$ lspci | grep -i VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Mobility Radeon HD 4830 [M97]
```
I'm not sure if that's significant or if it could be due to a different version of lspci.

---

### Post by pme 72 on 2013-05-12
Not sure why you are getting a black screen with KMS enabled. There is an Ubuntu Wiki page for trouble shooting Blank Screen. 

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

My /var/log/Xorg.0.log file with an HD4550 looks like yours up to your line: 

[   80.530] (II) [KMS] drm report modesetting isn't supported.

where mine reads:

(II) [KMS] Kernel modesetting enabled.

---

### Post by Yellow Pasque on 2013-05-12
> [KMS] drm report modesetting isn't supported.

Yeah, I've seen a few other radeon users struggle with that issue. If you hit it again, it would be worth trying newer kernels: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/)

---

### Post by ironyCurtain on 2013-05-15
> **Temüjin said:**
> Yeah, I've seen a few other radeon users struggle with that issue. If you hit it again, it would be worth trying newer kernels: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/)

Thank you so much for this idea! I was able to resolve these issues by installing the newest v3.9-raring kernel and then making a couple of changes to to /etc/default/grub.

[SIZE=4]Installing the mainline kernel[/SIZE]

You can install a new kernel without overwriting your old one. Often newer kernels will have fixes that aren't in the older one provided by the distribution.

Point your browser at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/). You'll need to download 3 files from here. Two are deb package files containing the kernel headers and kernel image for your architecture, respectively (in my case amd64 for a x86_64 cpu). The other one is architecture independent headers. If you follow these instructions be sure to download the files for the right architecture for your machine.

At this time v3.9-raring is the newest mainline kernel tested with raring so that is what I used, but others can be found at [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").

First download the three debs. You can either download with your browser or pull them down with wget at the terminal:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-headers-3.9.0-030900-generic_3.9.0-030900.201304291257_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-image-3.9.0-030900-generic_3.9.0-030900.201304291257_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.9-raring/linux-headers-3.9.0-030900_3.9.0-030900.201304291257_all.deb
```

Once they are downloaded, put the three files in a directory by themselves, cd to that directory in your terminal and install them with dpkg. For example:
```
cd ~/Downloads/v3.9-raring
sudo dpkg -i *.deb
# update the bootloader to know that the new kernel is installed
sudo update-grub

```

[SIZE=4]Testing the kernel[/SIZE]

At this point you could reboot and test the kernel. It might just work. On the other hand, like in my case, it might need additional kernel parameters to work correctly. The basics have been [discussed elsewhere]("http://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter").

I changed the following two lines in /etc/default/grub to read as follows:

```
GRUB_CMDLINE_LINUX_DEFAULT="modeset=0 acpi_osi=linux vesafb.nonsense=1"

[...]

GRUB_GFXPAYLOAD_LINUX=text
```

Then be sure to run ```
sudo update-grub
``` to install these settings to the bootloader. 

[SIZE=4]Reboot[/SIZE]

Reboot into grub and select your new kernel and press enter. Hopefully it works. If not, you may have to tweak some of the settings.

Note: Other have apparently had luck using just "acpi_osi=" in case the above doesn't work. If you have the same computer as me hopefully the above works fine.

[SIZE=4]Recap[/SIZE]

The 3.9.0 kernel works perfectly so far AND there is the added bonus of it fixing another bug that was causing the radeon driver to spam /var/log/syslog with 5 warnings or so per second. 

I intend to file a bug report for my kernel issues. The few times I was able to boot 3.8.0 without the "nomodeset" kernel parameter the system was extremely unstable and would often lock up completely while loading up lightdm, while logging in, or shortly after logging in. Most of the time it locked up before that, or I just got a black screen and had no idea what was going on. The 3.9.0 kernel seems to not have such issues, at least not with the kernel parameters I am using now.

Cheers!

---

### Post by ironyCurtain on 2013-05-15
I may have spoken too soon. The above worked for one boot, then I wasn't able to boot it again even with identical settings. The inconsistency is killing me. 

In the mean time I noticed 3.8.0-21-generic kernel was now available on apt so I installed that. I was able to boot that once with default grub settings --> literally just "quiet splash $vt_handoff" on the kernel line in the grub setup. I thought great, rebooted, tried the same exact thing and got a black screen.

I tried modeset=0 apci_osi=linux parameters: Worked fine with hardware acceleration
Rebooted and tried the exact same settings: Hung at loading the ramdisk forever

Later it worked with only "acpi_osi=linux vesafb.nonsense=1", but after putting that in GRUB_CMDLINE_LINUX_DEFAULT, running update-grub and rebooting it ALSO gave me a black screen.

Is it possible that grub is changing something the second time it boots a kernel with particular settings? If so, how do I stop it from doing that?

:confused:

---

### Post by Nisk on 2013-09-07
Have you found a solution?
I have the same problem.

```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV740/M97 [Mobility Radeon HD 4830] [1002:94a0]
```

LIBGL_DEBUG=verbose glxinfo:

[http://pastebin.com/vXrjT16E](http://pastebin.com/vXrjT16E)

```
lsb_release -a:

LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:qt4-3.1-amd64:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
```

Xorg.0.log:

[http://pastebin.com/UYVQk42Y](http://pastebin.com/UYVQk42Y)

It always works fine on a first boot. Can I force it to do what ever it does on the first boot?

---

