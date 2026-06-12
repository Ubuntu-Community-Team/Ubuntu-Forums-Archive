---
title: "Odd X -configure behaviour with intel cards."
date: 2011-05-03
forum: Multimedia Software
---

### Post by tjones00 on 2011-05-03
Installed Xubuntu 11.04 on two machines this week laptop/netbook both have integrated intel graphics.

Upon trying to create an xorg.conf via X -configure. This poped up.

```
(++) Using config file: "/home/user/xorg.conf.new"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
Number of created screens does not match number of detected devices.
  Configuration failed.
  ddxSigGiveUp: Closing log.
```So that xorg.conf.new seems to be something new to me. I went and examined it along with my Xorg.0.log and interestingly it contained triplicate Device/Monitor/Screen entries for each compatible driver intel, fbdev, and vesa. Each device definition had the same bus ID and the server layout section had relative positioning for the 2 extra screens.

I seriously doubt this behavior is intentional.

**Anybody know how to get new Xorg 1.10.1  X -configure to only make entries for the intel driver?** X --help didn't produce anything that seemed useful for this issue.

Yes I know I could manually edit the file removing the extra entries. However, turning off KMS and creating an xorg.conf is an issue that seems to come up with every release. It would be good to have a simple command for newer users to use without manually editing configuration files. Shutting down X and creating an xorg.conf with X -configure is daunting enough for most.

Edit: extra info for those who are interested.

xrandr -q

```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 222mm x 130mm
   1024x600       60.0*+
   800x600        60.3     56.2 
   640x480        59.9 
VGA1 disconnected (normal left inverted right x axis y axis)

```lspci -v

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device 361a
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc80 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fe940000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: intelfb, i915

```xorg.conf.new
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
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
    Load  "dbe"
    Load  "record"
    Load  "extmod"
    Load  "glx"
    Load  "dri"
    Load  "dri2"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
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

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "AccelMethod"            # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "VideoKey"               # <i>
        #Option     "FallbackDebug"          # [<bool>]
        #Option     "Tiling"                 # [<bool>]
        #Option     "Shadow"                 # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
        #Option     "XvMC"                   # [<bool>]
        #Option     "XvPreferOverlay"        # [<bool>]
        #Option     "DebugFlushBatches"      # [<bool>]
        #Option     "DebugFlushCaches"       # [<bool>]
        #Option     "DebugWait"              # [<bool>]
        #Option     "HotPlug"                # [<bool>]
        #Option     "RelaxedFencing"         # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "Rotate"                 # <str>
        #Option     "fbdev"                  # <str>
        #Option     "debug"                  # [<bool>]
    Identifier  "Card1"
    Driver      "fbdev"
    BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"               # [<bool>]
        #Option     "DefaultRefresh"         # [<bool>]
        #Option     "ModeSetClearScreen"     # [<bool>]
    Identifier  "Card2"
    Driver      "vesa"
    BusID       "PCI:0:2:0"
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

```Xorg.0.log from the X -configure attempt.

```
[ 13089.145]
X.Org X Server 1.10.1
Release Date: 2011-04-15
[ 13089.146] X Protocol Version 11, Revision 0
[ 13089.146] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[ 13089.147] Current Operating System: Linux casey-HP-Mini 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[ 13089.147] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=9d8d5daa-519c-4fb8-90de-1c2b8a0f890d ro quiet splash vt.handoff=7
[ 13089.148] Build Date: 19 April 2011  03:33:17PM
[ 13089.148] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support)
[ 13089.154] Current version of pixman: 0.20.2
[ 13089.157]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[ 13089.163] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[ 13089.172] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May  3 14:46:29 2011
[ 13089.175] (II) Loader magic: 0x81ffde0
[ 13089.175] (II) Module ABI versions:
[ 13089.175]     X.Org ANSI C Emulation: 0.4
[ 13089.175]     X.Org Video Driver: 10.0
[ 13089.175]     X.Org XInput driver : 12.3
[ 13089.175]     X.Org Server Extension : 5.0
[ 13089.178] (--) PCI:*(0:0:2:0) 8086:27ae:103c:361a rev 3, Mem @ 0xfe980000/524288, 0xd0000000/268435456, 0xfe940000/262144, I/O @ 0x0000dc80/8
[ 13089.178] (--) PCI: (0:0:2:1) 8086:27a6:103c:361a rev 3, Mem @ 0xfe880000/524288
[ 13089.185] List of video drivers:
[ 13089.187]     nouveau
[ 13089.190]     sisusb
[ 13089.193]     ztv
[ 13089.196]     i128
[ 13089.198]     intel
[ 13089.201]     voodoo
[ 13089.204]     ati
[ 13089.206]     openchrome
[ 13089.209]     mach64
[ 13089.211]     rendition
[ 13089.214]     mga
[ 13089.216]     neomagic
[ 13089.219]     tseng
[ 13089.221]     ark
[ 13089.223]     cirrus
[ 13089.226]     vmware
[ 13089.228]     radeon
[ 13089.230]     tdfx
[ 13089.232]     s3virge
[ 13089.234]     r128
[ 13089.236]     sis
[ 13089.238]     siliconmotion
[ 13089.240]     savage
[ 13089.242]     geode
[ 13089.244]     chips
[ 13089.246]     trident
[ 13089.248]     s3
[ 13089.249]     vmwlegacy
[ 13089.250]     apm
[ 13089.252]     qxl
[ 13089.253]     i740
[ 13089.254]     fbdev
[ 13089.255]     vesa
[ 13089.256] (II) LoadModule: "nouveau"
[ 13089.270] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[ 13089.316] (II) Module nouveau: vendor="X.Org Foundation"
[ 13089.316]     compiled for 1.10.0, module version = 0.0.16
[ 13089.316]     Module class: X.Org Video Driver
[ 13089.316]     ABI class: X.Org Video Driver, version 10.0
[ 13089.317] (II) LoadModule: "sisusb"
[ 13089.317] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
[ 13089.347] (II) Module sisusb: vendor="X.Org Foundation"
[ 13089.347]     compiled for 1.10.0, module version = 0.9.4
[ 13089.347]     Module class: X.Org Video Driver
[ 13089.347]     ABI class: X.Org Video Driver, version 10.0
[ 13089.347] (II) LoadModule: "ztv"
[ 13089.348] (II) Loading /usr/lib/xorg/modules/drivers/ztv_drv.so
[ 13089.359] (II) Module ztv: vendor="X.Org Foundation"
[ 13089.359]     compiled for 1.10.0, module version = 0.0.1
[ 13089.360]     ABI class: X.Org Video Driver, version 10.0
[ 13089.360] (II) LoadModule: "i128"
[ 13089.360] (II) Loading /usr/lib/xorg/modules/drivers/i128_drv.so
[ 13089.380] (II) Module i128: vendor="X.Org Foundation"
[ 13089.380]     compiled for 1.10.0, module version = 1.3.4
[ 13089.380]     Module class: X.Org Video Driver
[ 13089.380]     ABI class: X.Org Video Driver, version 10.0
[ 13089.380] (II) LoadModule: "intel"
[ 13089.382] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 13089.392] (II) Module intel: vendor="X.Org Foundation"
[ 13089.392]     compiled for 1.10.1, module version = 2.14.0
[ 13089.392]     Module class: X.Org Video Driver
[ 13089.392]     ABI class: X.Org Video Driver, version 10.0
[ 13089.392] (II) LoadModule: "voodoo"
[ 13089.393] (II) Loading /usr/lib/xorg/modules/drivers/voodoo_drv.so
[ 13089.395] (II) Module voodoo: vendor="X.Org Foundation"
[ 13089.395]     compiled for 1.10.0, module version = 1.1.0
[ 13089.395]     Module class: X.Org Video Driver
[ 13089.395]     ABI class: X.Org Video Driver, version 10.0
[ 13089.395] (II) LoadModule: "ati"
[ 13089.395] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[ 13089.404] (II) Module ati: vendor="X.Org Foundation"
[ 13089.404]     compiled for 1.10.0, module version = 6.14.0
[ 13089.404]     Module class: X.Org Video Driver
[ 13089.404]     ABI class: X.Org Video Driver, version 10.0
[ 13089.404] (II) LoadModule: "openchrome"
[ 13089.405] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[ 13089.427] (II) Module openchrome: vendor="http://openchrome.org/"
[ 13089.427]     compiled for 1.10.0, module version = 0.2.904
[ 13089.427]     Module class: X.Org Video Driver
[ 13089.427]     ABI class: X.Org Video Driver, version 10.0
[ 13089.427] (II) LoadModule: "mach64"
[ 13089.428] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
[ 13089.440] (II) Module mach64: vendor="X.Org Foundation"
[ 13089.441]     compiled for 1.10.0, module version = 6.8.2
[ 13089.441]     Module class: X.Org Video Driver
[ 13089.441]     ABI class: X.Org Video Driver, version 10.0
[ 13089.441] (II) LoadModule: "rendition"
[ 13089.441] (II) Loading /usr/lib/xorg/modules/drivers/rendition_drv.so
[ 13089.451] (II) Module rendition: vendor="X.Org Foundation"
[ 13089.451]     compiled for 1.10.0, module version = 4.2.4
[ 13089.451]     Module class: X.Org Video Driver
[ 13089.451]     ABI class: X.Org Video Driver, version 10.0
[ 13089.451] (II) LoadModule: "mga"
[ 13089.452] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
[ 13089.462] (II) Module mga: vendor="X.Org Foundation"
[ 13089.462]     compiled for 1.10.0, module version = 1.4.13
[ 13089.462]     Module class: X.Org Video Driver
[ 13089.462]     ABI class: X.Org Video Driver, version 10.0
[ 13089.472] (II) LoadModule: "neomagic"
[ 13089.473] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
[ 13089.479] (II) Module neomagic: vendor="X.Org Foundation"
[ 13089.479]     compiled for 1.10.0, module version = 1.2.5
[ 13089.479]     Module class: X.Org Video Driver
[ 13089.479]     ABI class: X.Org Video Driver, version 10.0
[ 13089.479] (II) LoadModule: "tseng"
[ 13089.480] (II) Loading /usr/lib/xorg/modules/drivers/tseng_drv.so
[ 13089.482] (II) Module tseng: vendor="X.Org Foundation"
[ 13089.482]     compiled for 1.10.0, module version = 1.1.0
[ 13089.482]     Module class: X.Org Video Driver
[ 13089.482]     ABI class: X.Org Video Driver, version 10.0
[ 13089.482] (II) LoadModule: "ark"
[ 13089.483] (II) Loading /usr/lib/xorg/modules/drivers/ark_drv.so
[ 13089.489] (II) Module ark: vendor="X.Org Foundation"
[ 13089.489]     compiled for 1.10.0, module version = 0.7.3
[ 13089.489]     Module class: X.Org Video Driver
[ 13089.489]     ABI class: X.Org Video Driver, version 10.0
[ 13089.489] (II) LoadModule: "cirrus"
[ 13089.489] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
[ 13089.494] (II) Module cirrus: vendor="X.Org Foundation"
[ 13089.494]     compiled for 1.10.0, module version = 1.3.2
[ 13089.494]     Module class: X.Org Video Driver
[ 13089.494]     ABI class: X.Org Video Driver, version 10.0
[ 13089.494] (II) LoadModule: "vmware"
[ 13089.495] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
[ 13089.504] (II) Module vmware: vendor="X.Org Foundation"
[ 13089.504]     compiled for 1.10.0, module version = 11.0.3
[ 13089.504]     Module class: X.Org Video Driver
[ 13089.504]     ABI class: X.Org Video Driver, version 10.0
[ 13089.504] (II) LoadModule: "vmwgfx"
[ 13089.506] (WW) Warning, couldn't open module vmwgfx
[ 13089.506] (II) UnloadModule: "vmwgfx"
[ 13089.506] (II) Unloading vmwgfx
[ 13089.506] (EE) Failed to load module "vmwgfx" (module does not exist, 0)
[ 13089.507] (EE) vmware: Please ignore the above warnings about not being able to to load module/driver vmwgfx
[ 13089.508] (II) vmware: Using vmwlegacy driver everything is fine.
[ 13089.508] (II) LoadModule: "vmwlegacy"
[ 13089.509] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[ 13089.511] (II) Module vmwlegacy: vendor="X.Org Foundation"
[ 13089.511]     compiled for 1.10.0, module version = 11.0.3
[ 13089.511]     Module class: X.Org Video Driver
[ 13089.511]     ABI class: X.Org Video Driver, version 10.0
[ 13089.511] (II) LoadModule: "radeon"
[ 13089.512] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[ 13089.561] (II) Module radeon: vendor="X.Org Foundation"
[ 13089.561]     compiled for 1.10.0, module version = 6.14.0
[ 13089.561]     Module class: X.Org Video Driver
[ 13089.561]     ABI class: X.Org Video Driver, version 10.0
[ 13089.569] (II) LoadModule: "tdfx"
[ 13089.570] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
[ 13089.572] (II) Module tdfx: vendor="X.Org Foundation"
[ 13089.572]     compiled for 1.10.0, module version = 1.4.3
[ 13089.572]     Module class: X.Org Video Driver
[ 13089.572]     ABI class: X.Org Video Driver, version 10.0
[ 13089.572] (II) LoadModule: "s3virge"
[ 13089.573] (II) Loading /usr/lib/xorg/modules/drivers/s3virge_drv.so
[ 13089.584] (II) Module s3virge: vendor="X.Org Foundation"
[ 13089.584]     compiled for 1.10.0, module version = 1.10.4
[ 13089.584]     Module class: X.Org Video Driver
[ 13089.584]     ABI class: X.Org Video Driver, version 10.0
[ 13089.584] (II) LoadModule: "r128"
[ 13089.585] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
[ 13089.587] (II) Module r128: vendor="X.Org Foundation"
[ 13089.587]     compiled for 1.10.0, module version = 6.8.1
[ 13089.587]     Module class: X.Org Video Driver
[ 13089.587]     ABI class: X.Org Video Driver, version 10.0
[ 13089.587] (II) LoadModule: "sis"
[ 13089.588] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[ 13089.603] (II) Module sis: vendor="X.Org Foundation"
[ 13089.603]     compiled for 1.10.0, module version = 0.10.3
[ 13089.603]     Module class: X.Org Video Driver
[ 13089.603]     ABI class: X.Org Video Driver, version 10.0
[ 13089.603] (II) LoadModule: "siliconmotion"
[ 13089.604] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
[ 13089.606] (II) Module siliconmotion: vendor="X.Org Foundation"
[ 13089.606]     compiled for 1.10.0, module version = 1.7.4
[ 13089.607]     Module class: X.Org Video Driver
[ 13089.607]     ABI class: X.Org Video Driver, version 10.0
[ 13089.607] (II) LoadModule: "savage"
[ 13089.608] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
[ 13089.610] (II) Module savage: vendor="X.Org Foundation"
[ 13089.610]     compiled for 1.10.0, module version = 2.3.2
[ 13089.610]     Module class: X.Org Video Driver
[ 13089.610]     ABI class: X.Org Video Driver, version 10.0
[ 13089.611] (II) LoadModule: "geode"
[ 13089.612] (II) Loading /usr/lib/xorg/modules/drivers/geode_drv.so
[ 13089.637] (II) Module geode: vendor="X.Org Foundation"
[ 13089.637]     compiled for 1.10.0, module version = 2.11.12
[ 13089.637]     Module class: X.Org Video Driver
[ 13089.637]     ABI class: X.Org Video Driver, version 10.0
[ 13089.637] (II) LoadModule: "chips"
[ 13089.638] (II) Loading /usr/lib/xorg/modules/drivers/chips_drv.so
[ 13089.640] (II) Module chips: vendor="X.Org Foundation"
[ 13089.641]     compiled for 1.10.0, module version = 1.2.3
[ 13089.641]     Module class: X.Org Video Driver
[ 13089.641]     ABI class: X.Org Video Driver, version 10.0
[ 13089.641] (II) LoadModule: "trident"
[ 13089.642] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
[ 13089.645] (II) Module trident: vendor="X.Org Foundation"
[ 13089.645]     compiled for 1.10.0, module version = 1.3.4
[ 13089.645]     Module class: X.Org Video Driver
[ 13089.645]     ABI class: X.Org Video Driver, version 10.0
[ 13089.645] (II) LoadModule: "s3"
[ 13089.646] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
[ 13089.648] (II) Module s3: vendor="X.Org Foundation"
[ 13089.648]     compiled for 1.10.0, module version = 0.6.3
[ 13089.648]     Module class: X.Org Video Driver
[ 13089.648]     ABI class: X.Org Video Driver, version 10.0
[ 13089.649] (II) LoadModule: "vmwlegacy"
[ 13089.649] (II) Loading /usr/lib/xorg/modules/drivers/vmwlegacy_drv.so
[ 13089.649] (II) Module vmwlegacy: vendor="X.Org Foundation"
[ 13089.649]     compiled for 1.10.0, module version = 11.0.3
[ 13089.650]     Module class: X.Org Video Driver
[ 13089.650]     ABI class: X.Org Video Driver, version 10.0
[ 13089.650] (II) UnloadModule: "vmwlegacy"
[ 13089.650] (II) Unloading vmwlegacy
[ 13089.650] (II) Failed to load module "vmwlegacy" (already loaded, -1076262632)
[ 13089.650] (II) LoadModule: "apm"
[ 13089.651] (II) Loading /usr/lib/xorg/modules/drivers/apm_drv.so
[ 13089.671] (II) Module apm: vendor="X.Org Foundation"
[ 13089.671]     compiled for 1.10.0, module version = 1.2.3
[ 13089.671]     Module class: X.Org Video Driver
[ 13089.671]     ABI class: X.Org Video Driver, version 10.0
[ 13089.671] (II) LoadModule: "qxl"
[ 13089.672] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
[ 13089.674] (II) Module qxl: vendor="X.Org Foundation"
[ 13089.674]     compiled for 1.10.0, module version = 0.0.0
[ 13089.674]     Module class: X.Org Video Driver
[ 13089.674]     ABI class: X.Org Video Driver, version 10.0
[ 13089.674] (II) LoadModule: "i740"
[ 13089.675] (II) Loading /usr/lib/xorg/modules/drivers/i740_drv.so
[ 13089.676] (II) Module i740: vendor="X.Org Foundation"
[ 13089.676]     compiled for 1.10.0, module version = 1.3.2
[ 13089.676]     Module class: X.Org Video Driver
[ 13089.676]     ABI class: X.Org Video Driver, version 10.0
[ 13089.677] (II) LoadModule: "fbdev"
[ 13089.677] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[ 13089.678] (II) Module fbdev: vendor="X.Org Foundation"
[ 13089.678]     compiled for 1.10.0, module version = 0.4.2
[ 13089.678]     ABI class: X.Org Video Driver, version 10.0
[ 13089.678] (II) LoadModule: "vesa"
[ 13089.678] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[ 13089.679] (II) Module vesa: vendor="X.Org Foundation"
[ 13089.679]     compiled for 1.10.0, module version = 2.3.0
[ 13089.679]     Module class: X.Org Video Driver
[ 13089.679]     ABI class: X.Org Video Driver, version 10.0
[ 13089.679] (WW) Falling back to old probe method for sisusb
[ 13089.679] (WW) Falling back to old probe method for z4l
[ 13089.679] (II) z4l driver for Video4Linux
[ 13089.679] (WW) Falling back to old probe method for i128
[ 13089.679] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
    Sandybridge, Sandybridge
[ 13089.681] (WW) Falling back to old probe method for voodoo
[ 13089.681] (WW) Falling back to old probe method for neomagic
[ 13089.681] (WW) Falling back to old probe method for tseng
[ 13089.681] (WW) Falling back to old probe method for ark
[ 13089.681] (WW) Falling back to old probe method for cirrus
[ 13089.681] (II) Loading sub module "cirrus_laguna"
[ 13089.681] (II) LoadModule: "cirrus_laguna"
[ 13089.682] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
[ 13089.683] (II) Module cirrus_laguna: vendor="X.Org Foundation"
[ 13089.683]     compiled for 1.10.0, module version = 1.0.0
[ 13089.683]     ABI class: X.Org Video Driver, version 10.0
[ 13089.683] (II) Loading sub module "cirrus_alpine"
[ 13089.683] (II) LoadModule: "cirrus_alpine"
[ 13089.684] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
[ 13089.686] (II) Module cirrus_alpine: vendor="X.Org Foundation"
[ 13089.686]     compiled for 1.10.0, module version = 1.0.0
[ 13089.686]     ABI class: X.Org Video Driver, version 10.0
[ 13089.686] (WW) Falling back to old probe method for s3virge
[ 13089.686] (WW) Falling back to old probe method for sis
[ 13089.686] (WW) Falling back to old probe method for siliconmotion
[ 13089.686] (WW) Falling back to old probe method for trident
[ 13089.686] (WW) Falling back to old probe method for s3
[ 13089.686] (WW) Falling back to old probe method for apm
[ 13089.686] (WW) Falling back to old probe method for i740
[ 13089.687] (II) FBDEV: driver for framebuffer: fbdev
[ 13089.687] (II) VESA: driver for VESA chipsets: vesa
[ 13089.694] (++) Using config file: "/home/casey/xorg.conf.new"
[ 13089.695] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[ 13089.705] (==) ServerLayout "X.org Configured"
[ 13089.705] (**) |-->Screen "Screen0" (0)
[ 13089.705] (**) |   |-->Monitor "Monitor0"
[ 13089.706] (**) |   |-->Device "Card0"
[ 13089.706] (**) |-->Screen "Screen1" (1)
[ 13089.706] (**) |   |-->Monitor "Monitor1"
[ 13089.707] (**) |   |-->Device "Card1"
[ 13089.707] (**) |-->Screen "Screen2" (2)
[ 13089.707] (**) |   |-->Monitor "Monitor2"
[ 13089.708] (**) |   |-->Device "Card2"
[ 13089.708] (**) |-->Input Device "Mouse0"
[ 13089.708] (**) |-->Input Device "Keyboard0"
[ 13089.708] (==) Automatically adding devices
[ 13089.708] (==) Automatically enabling devices
[ 13089.730] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 13089.730]     Entry deleted from font path.
[ 13089.731] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 13089.731]     Entry deleted from font path.
[ 13089.731] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 13089.731]     Entry deleted from font path.
[ 13089.731] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 13089.731]     Entry deleted from font path.
[ 13089.731] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 13089.731]     Entry deleted from font path.
[ 13089.754] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[ 13089.754]     Entry deleted from font path.
[ 13089.754] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[ 13089.754]     Entry deleted from font path.
[ 13089.754] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[ 13089.754]     Entry deleted from font path.
[ 13089.754] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[ 13089.754]     Entry deleted from font path.
[ 13089.754] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[ 13089.754]     Entry deleted from font path.
[ 13089.754] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[ 13089.754] (**) ModulePath set to "/usr/lib/xorg/modules"
[ 13089.754] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[ 13089.754] (WW) Disabling Mouse0
[ 13089.754] (WW) Disabling Keyboard0
[ 13089.951] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[ 13089.951] (WW) Falling back to old probe method for fbdev
[ 13089.951] (II) Loading sub module "fbdevhw"
[ 13089.951] (II) LoadModule: "fbdevhw"
[ 13089.952] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[ 13089.952] (II) Module fbdevhw: vendor="X.Org Foundation"
[ 13089.952]     compiled for 1.10.1, module version = 0.0.2
[ 13089.953]     ABI class: X.Org Video Driver, version 10.0
[ 13089.953] (WW) Falling back to old probe method for vesa
[ 13089.953] Number of created screens does not match number of detected devices.
  Configuration failed.

```

---

### Post by tjones00 on 2011-05-04
Well I guess this really doesn't matter since it looks like in Ubuntu 11.10 they will be dropping Xorg in favor of Wayland. I guess making sure any new Xorg features or changes are working properly isn't a priority.

[http://www.phoronix.com/scan.php?page=news_item&px=ODc1Nw](http://www.phoronix.com/scan.php?page=news_item&px=ODc1Nw)
[http://www.phoronix.com/scan.php?page=news_item&px=ODcyMg](http://www.phoronix.com/scan.php?page=news_item&px=ODcyMg)

---

### Post by cntrational on 2011-05-04
I have the exact same problem. I can't adjust my resolution without it, please find a solution soon.

---

### Post by BicyclerBoy on 2011-05-04
@tj
I have natty 11.04 unity 3d working okay on 945GME but only after adding a ppa..

I just used my xorg.conf from 10.10-netbook (simple & homemade).
I was never convinced that anything in my xorg.conf made any real difference.
I would just edit the cruft out or backup/delete it..

The big graphics performance lift was from using xorg-edgers ppa.
There is still no libva VA-API capability sadly...
The default natty 11.04 did not allow unity 3d because there was no 3d acceleration; i915 driver was in use..
My atom 330 945GME netbook (10.10 xorg-edgers ppa) can playback H264 576i in MythTV with acceptable performance for small LCD.
Have not got round to installing MythTV FE in 11.04..

KMS
The intel driver uses KMS (has a kernel module) so do not disable in grub.
The only "nomodeset" usage I (partly) understand is stopping the nouveau kernel module loading & preventing nvidia binary blob x-server from loading.

---

