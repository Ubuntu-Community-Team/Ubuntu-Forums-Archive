---
title: "Dual panels with ATI Radeon 9600 (and Envy) missing direct/3D support?"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by pbannister on 2007-03-02
I have a dual Dell 24" panels connected to an ATI Radeon 9600 card with dual DVI output.  After installing the latest ATI binary drivers, from hints on this forum, and some xorg.conf editing, was able get both panels working (as one desktop with distinct screens).

This seems to get me everything but 3D support.

Output from **glxinfo** - ```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
name of display: :0.0
display: :0  screen: 0
**direct rendering: No**
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

Tried using the latest **envy** installer (from [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")).
```
       +-------------------------------------------------+
       |                                                 |
       |             Welcome to Envy 0.8.2               |
       |                                                 |
       |    Developed by Alberto Milone (aka tseliot)    |
       |                                                 |
       +-------------------------------------------------+


       +-----------------------------------------------------------+
       |    Envy Menu ver.0.8.2                                    |
       |                                                           |
       |    1 - Install the NVIDIA driver                          |
       |                                                           |
       |    2 - Uninstall the NVIDIA driver                        |
       |                                                           |
       |    3 - Install the ATI driver                             |
       |                                                           |
       |    4 - Uninstall the ATI driver                           |
       |                                                           |
       |    5 - Install the ATI/NVIDIA driver Manually             |
       |                                                           |
       |    6 - Restart the Xserver                                |
       |                                                           |
       |    7 - Exit                                               |
       |                                                           |
       |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
       +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

3
rm: cannot remove `*.deb': No such file or directory
Ubuntu Edgy 32bit
Your graphic card has been detected as a ATI Radeon 9600 Series
Your graphic card is supported by the latest driver
 * Stopping GNOME Display Manager...                                                                                                                                                           [ ok ]
sudo: /etc/init.d/kdm: command not found
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-2.6.17-11-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
xserver-xorg-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
pkg-config is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
gcc is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
module-assistant is already the newest version.
build-essential is already the newest version.
fakeroot is already the newest version.
dh-make is already the newest version.
debhelper is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package fglrx-control is not installed, so not removed
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 fglrx-kernel-2.6.17-11-generic fglrx-kernel-source xorg-driver-fglrx libssl0.9.7 xorg-driver-fglrx-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  fglrx-kernel-2.6.17-11-generic* fglrx-kernel-source* xorg-driver-fglrx* xorg-driver-fglrx-dev*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 29.3MB disk space will be freed.
(Reading database ... 132465 files and directories currently installed.)
Removing fglrx-kernel-2.6.17-11-generic ...
Purging configuration files for fglrx-kernel-2.6.17-11-generic ...
dpkg - warning: while removing fglrx-kernel-2.6.17-11-generic, directory `/lib/modules/2.6.17-11-generic/misc' not empty so not removed.
Removing fglrx-kernel-source ...
Removing xorg-driver-fglrx-dev ...
Removing xorg-driver-fglrx ...
Stopping atieventsd: done.
rmdir: /usr/lib/fglrx: Directory not empty
Purging configuration files for xorg-driver-fglrx ...
rmdir: /usr/lib/fglrx: Directory not empty
dpkg - warning: while removing xorg-driver-fglrx, directory `/etc/ati' not empty so not removed.
An installer has been detected
md5new: 5fbd42d666d467a904acbaeb600c1d5a
md5sumold: 5fbd42d666d467a904acbaeb600c1d5a
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.33.6...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/edgy
Package /usr/share/envy/xorg-driver-fglrx_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/xorg-driver-fglrx-dev_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/fglrx-kernel-source_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/fglrx-control_8.33.6-1_i386.deb has been successfully generated
Package /usr/share/envy/fglrx-sources_8.33.6-1_i386.deb has been successfully generated
Removing temporary directory: fglrx-install
(Reading database ... 132339 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.33.6-1_i386.deb) ...
Selecting previously deselected package fglrx-kernel-source.
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.33.6-1_i386.deb) ...
Preparing to replace fglrx-sources 8.33.6-1 (using fglrx-sources_8.33.6-1_i386.deb) ...
Unpacking replacement fglrx-sources ...
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.33.6-1_i386.deb) ...
Selecting previously deselected package xorg-driver-fglrx.
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.33.6-1_i386.deb) ...
Setting up fglrx-kernel-source (8.33.6-1) ...
Setting up fglrx-sources (8.33.6-1) ...
Setting up xorg-driver-fglrx (8.33.6-1) ...
Starting atieventsd: done.

Setting up fglrx-control (8.33.6-1) ...

Setting up xorg-driver-fglrx-dev (8.33.6-1) ...
Getting source for kernel version: 2.6.17-11-generic
Kernel headers available in /lib/modules/2.6.17-11-generic/build
apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  vmware-player-kernel-modules-2.6.17-10 libssl0.9.7
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!

Updated infos about 84 packages
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.17-11-generic_8.33.6-1+2.6.17.1-11.35_i386.deb .
Selecting previously deselected package fglrx-kernel-2.6.17-11-generic.
(Reading database ... 132469 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.17-11-generic (from .../fglrx-kernel-2.6.17-11-generic_8.33.6-1+2.6.17.1-11.35_i386.deb) ...
Setting up fglrx-kernel-2.6.17-11-generic (8.33.6-1+2.6.17.1-11.35) ...

Do you want your xorg.conf to be automatically configured? (y/n) \ "y" is the default answer

Found fglrx primary device section
Nothing to do, terminating.
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-4
Do you want to restart your computer now (Recommended)? (y/n) \ "y" is the default answer


Broadcast message from preston@mite
        (/dev/pts/0) at 0:22 ...

The system is going down for reboot NOW!
Operation Completed

```

The working **xorg.conf** file (minus direct/3D support) is as follows.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen       0 "Screen0" 0 0
        Screen         "Screen1" RightOf "Screen0"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        Option         "Xinerama" "On"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI video card 0"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "EnablePrivateBackZ" "yes"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI video card 1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "ATI video card 0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "ATI video card 1"
        Monitor    "Monitor1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

Output from **lspci**.
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0a.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

```

Output from **fglrxinfo**
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

There are some interesting messages in **Xorg.0.log** (too long to post here).  Possibly one of them (?) relevant.
```
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(1): board is an unknown third party board, chipset is supported
(WW) fglrx(0): ***********************************
(WW) fglrx(0): * DRI initialization disabled!    *
(WW) fglrx(0): * 2D acceleraton available (MMIO) *
(WW) fglrx(0): * no 3D acceleration available    *
(WW) fglrx(0): ***********************************
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(WW) fglrx(1): ***********************************
(WW) fglrx(1): * DRI initialization disabled!    *
(WW) fglrx(1): * 2D acceleraton available (MMIO) *
(WW) fglrx(1): * no 3D acceleration available    *
(WW) fglrx(1): ***********************************
(EE) AIGLX: Screen 0 is not DRI capable
(EE) AIGLX: Screen 1 is not DRI capable

```

---

