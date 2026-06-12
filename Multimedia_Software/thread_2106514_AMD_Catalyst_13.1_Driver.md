---
title: "AMD Catalyst 13.1 Driver"
date: 2013-01-19
forum: Multimedia Software
---

### Post by KegHead on 2013-01-19
Hi!

Anyone with any luck with this yet?

KegHead

---

### Post by Thee on 2013-01-19
Didn't know they released a new driver. Now I'm tempted to try :)

Here are the relese notes:

```

New Features: 
The following section provides a summary of new features in this driver version.
XServer 1.13 support
Ubuntu 12.10 Production Support 
Resolved Issues:
This section provides information on resolved known issues in this release of the AMD Catalyst Linux software suite.

[368958]: Driver release version is added to GL_VERSION
[367282]: Bblank VGA display after resume from suspend
[367245]: X crash for AMD PowerXpress&#8482; A+I High-Performance mode on Ubuntu 12.10
[366820]  Performance of Valve Linux games
[366805]: Segmentation fault when exit QtOpenGL applications such as AMD CodeXL
[366425]: Xserver getting exit upon resume from suspend on RHEL 5.8
[364107]: VariBright not working when change AMD PowerPlay&#8482; settings in AMD Catalust Control Center:LE 
[363638]: VariBright doesn&#8217;t work after resume from suspend on "Trinity" platform
[350759]: Flickering cursor when run some full-screen OpenGL games with CrossFire enabled
[347895]: OpenGL performance on "Southern Islands" ASICs
[344996]: 16 re-frames doesn&#8217;t work for H.264 @Level 5.1
[337240]: Corruption when resize the Konsole window
[304016]: One display goes black after changing from multi-display desktop from single independent 
Known Issues:
The following section provides a summary of open issues that may be experienced with the AMD Catalyst Linux software suite.

[356966]: Tearing appears at the top/left corner with monitor rotation + Vsync is enabled
[350671]: Corruption may be experienced when running Unigine Tropics 1.3
[341497]: OpenGL Bitmap performance may be impacted in certain situations

```

[http://support.amd.com/us/kbarticles/Pages/AMDCatalyst131ProprietaryLinuxGraphicsDriverReleaseNotes.aspx](http://support.amd.com/us/kbarticles/Pages/AMDCatalyst131ProprietaryLinuxGraphicsDriverReleaseNotes.aspx)

---

### Post by KegHead on 2013-01-19
Hi!

I have the following AMD cpu:

AMD Athlon II X4 640...running 12.10 w/64..msi mobo.

Do I need the 13.1 driver?

Thanks!

KegHead

---

### Post by ZombieApocalypse on 2013-01-19
It works on my system (HD 5850) but some desktop effects don't appear to be working in KDE (Kubuntu 12.10 amd64, KDE 4.9.5), eg transluceny effects. 

It mentions in the release notes "performance of Valve Linux games" (a bit vague), but I certainly don't notice any performance improvement for Killing Floor through the Linux Steam beta client. Although technically this is not a Valve game.

I'm tempted to go back to the previous driver.

---

### Post by KegHead on 2013-01-19
Hi!

It looks like a lot of folks are not loading and or going back.

KegHead

---

### Post by Thee on 2013-01-19
Why is that? Something wrong with the driver?
Anyone can test the FPS before and after install?

---

### Post by KegHead on 2013-01-19
Hi!

Opinion is based on internet clutter.

I'll wait until more info is available.

KegHead

---

### Post by masuch on 2013-01-19
# --- my simple catalyst performance comparison on ubuntu 12.10 :
# installed by my own script, amd HD 6990
# I have always experienced performance degradation within very new catalyst driver (from catalyst 11.4 (ubuntu 11.4)). And always when installed from Ubuntu 3rd party repository quite later on - it is going to be faster. If somebody knows better performance tests, please share some information.



# --- catalyst 12.10 testing
./graphics.sh test
    # --- graphics action ...
   # 
   # --------------------------GRAPHICS test started ...............................
    # --- glxinfo |grep OpenGL
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.11903 Compatibility Profile Context
   # OpenGL shading language version string: 4.20
   # OpenGL extensions:
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.11903 Compatibility Profile Context
   # OpenGL shading language version string: 4.20
   # OpenGL extensions:
    # --- glxinfo |grep rendering
   # libGL: AtiGetClientDriverName: 9.0.2 fglrx (screen 0)
   # libGL: OpenDriver: trying /usr/lib/fglrx/dri/fglrx_dri.so
   # libGL: AtiGetClientDriverName: 9.0.2 fglrx (screen 1)
   # ukiDynamicMajor: found major device number 250
   # ukiDynamicMajor: found major device number 250
   # ukiOpenByBusid: Searching for BusID PCI:3:0:0
   # ukiOpenDevice: node name is /dev/ati/card0
   # ukiOpenDevice: open result is 6, (OK)
   # ukiOpenByBusid: ukiOpenMinor returns 6
   # ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
   # ukiDynamicMajor: found major device number 250
   # ukiDynamicMajor: found major device number 250
   # ukiOpenByBusid: Searching for BusID PCI:4:0:0
   # ukiOpenDevice: node name is /dev/ati/card0
   # ukiOpenDevice: open result is 7, (OK)
   # ukiOpenByBusid: ukiOpenMinor returns 7
   # ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
   # ukiOpenDevice: node name is /dev/ati/card1
   # ukiOpenDevice: open result is 7, (OK)
   # ukiOpenByBusid: ukiOpenMinor returns 7
   # ukiOpenByBusid: ukiGetBusid reports PCI:4:0:0
   # direct rendering: Yes
   # direct rendering: Yes
    # --- unity support test
   # OpenGL vendor string:   ATI Technologies Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string:  4.2.11903 Compatibility Profile Context
   # 
   # Not software rendered:    yes
   # Not blacklisted:          yes
   # GLX fbconfig:             yes
   # GLX texture from pixmap:  yes
   # GL npot or rect textures: yes
   # GL vertex program:        yes
   # GL fragment program:      yes
   # GL vertex buffer object:  yes
   # GL framebuffer object:    yes
   # GL version is 1.4+:       yes
   # 
   # Unity 3D supported:       yes
    # --- fglrx version
   # fglrx:
     # Installed: 2:9.000-0ubuntu3
     # Candidate: 2:9.000-0ubuntu3
     # Version table:
    # *** 2:9.000-0ubuntu3 0
           # 500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
           # 100 /var/lib/dpkg/status
    # --- fglrxinfo
   # display: :0.0  screen: 0
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.11903 Compatibility Profile Context
   # 
   # 
   # 
   # display: :0.0  screen: 1
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.11903 Compatibility Profile Context
   # 
    # --- Hardware Video Decode Acceleration (EXPERIMENTAL) 
   # libva: VA-API version 0.32.0
   # Xlib:  extension "XFree86-DRI" missing on display ":0.0".
   # libva: va_getDriverName() returns 0
   # libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
   # libva: va_openDriver() returns 0
   # vainfo: VA-API version: 0.32 (libva 1.0.15)
   # vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
   # vainfo: Supported profile and entrypoints
         # VAProfileH264High               :	VAEntrypointVLD
         # VAProfileVC1Advanced            :	VAEntrypointVLD
    # --- compiz 
   # compizconfig - Info: Backend     : ini
   # compizconfig - Info: Integration : true
   # compizconfig - Info: Profile     : default
   # Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
   # Loading icons...
   # ... try to run fgl_glxgears ...

> fgl_glxgears
Using GLX_SGIX_pbuffer
18434 frames in 5.0 seconds = 3686.800 FPS
18250 frames in 5.0 seconds = 3650.000 FPS
18807 frames in 5.0 seconds = 3761.400 FPS
18941 frames in 5.0 seconds = 3788.200 FPS
19091 frames in 5.0 seconds = 3818.200 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 201776 requests (201776 known processed) with 0 events remaining.

glxgears
48224 frames in 5.0 seconds = 9644.764 FPS
47054 frames in 5.0 seconds = 9410.666 FPS
45198 frames in 5.0 seconds = 9039.582 FPS
50051 frames in 5.0 seconds = 10010.148 FPS
48798 frames in 5.0 seconds = 9759.600 FPS
49961 frames in 5.0 seconds = 9992.015 FPS
41799 frames in 5.0 seconds = 8359.686 FPS
      
# - catalyst 13.1 in terminal
./graphics.sh install downloaded
    # --- graphics action ...
   # 
   # --------------------------SOFTWARE Preinstall started ...............................
   # Do you want to install  'software_preinstall'  (yes/no)?
   # n
   # NO
   # 
   # --------------------------GET Driver started ...............................
   # -------- I am now in directory:
   # /media/DATA.m/_software/linux.hardware/HD6990/catalyst.driver/catalyst-13.1
   # --------
   # /media/DATA.m/_software/linux.hardware/HD6990/catalyst.driver/catalyst-13.1
   # total 226052
   # -rwxr-xr-x 1 u1 u1 116617301 Jan 15 10:59 amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run
   # -rw-r--r-- 1 u1 u1 114850263 Jan 18 19:13 amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
   # --------/media/DATA.m/_software/linux.hardware/HD6990/catalyst.driver/catalyst-13.1/amd-driver-installer-catalyst-13.1-linux-x86.x86_64.zip
   # ls: cannot access *.deb: No such file or directory
   # Created directory fglrx-install.zGZt5k
   # Verifying archive integrity... All good.
   # Uncompressing AMD Catalyst(TM) Proprietary Driver-9.012.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
   # =====================================================================
    # AMD Catalyst(TM) Proprietary Driver Installer/Packager 
   # =====================================================================
   # Generating package: Ubuntu/quantal
   # Package /media/DATA.m/_software/linux.hardware/HD6990/catalyst.driver/catalyst-13.1/fglrx_9.012-0ubuntu1_amd64.deb has been successfully generated
   # Package /media/DATA.m/_software/linux.hardware/HD6990/catalyst.driver/catalyst-13.1/fglrx-dev_9.012-0ubuntu1_amd64.deb has been successfully generated
   # Package /media/DATA.m/_software/linux.hardware/HD6990/catalyst.driver/catalyst-13.1/fglrx-amdcccle_9.012-0ubuntu1_amd64.deb has been successfully generated
   # Removing temporary directory: fglrx-install.zGZt5k
   # 
   # --------------------------FGLRX remove started ...............................
    # --- fglrx UNINSTALL try --- START ...
    # --------------------------------
   # Reading package lists... Done
   # Building dependency tree       
   # Reading state information... Done
   # Package 'xorg-driver-fglrx' is not installed, so not removed
   # E: Unable to locate package fglrx_9.012-0ubuntu1_amd64.deb
   # E: Couldn't find any package by regex 'fglrx_9.012-0ubuntu1_amd64.deb'
   # E: Unable to locate package fglrx-amdcccle_9.012-0ubuntu1_amd64.deb
   # E: Couldn't find any package by regex 'fglrx-amdcccle_9.012-0ubuntu1_amd64.deb'
   # E: Unable to locate package fglrx-dev_9.012-0ubuntu1_amd64.deb
   # E: Couldn't find any package by regex 'fglrx-dev_9.012-0ubuntu1_amd64.deb'
   # Reading package lists... Done
   # Building dependency tree       
   # Reading state information... Done
   # E: Unable to locate package fglrx_9.012-0ubuntu1_amd64.deb
   # E: Couldn't find any package by regex 'fglrx_9.012-0ubuntu1_amd64.deb'
   # E: Unable to locate package fglrx-amdcccle_9.012-0ubuntu1_amd64.deb
   # E: Couldn't find any package by regex 'fglrx-amdcccle_9.012-0ubuntu1_amd64.deb'
   # E: Unable to locate package fglrx-dev_9.012-0ubuntu1_amd64.deb
   # E: Couldn't find any package by regex 'fglrx-dev_9.012-0ubuntu1_amd64.deb'
   # E: Unable to locate package fglrx-installer_9.012-0ubuntu1_amd64.changes
   # E: Couldn't find any package by regex 'fglrx-installer_9.012-0ubuntu1_amd64.changes'
    # --- rm /usr/lib*/fglrx ----------------
   # 
   # --------------------------CATALYST Installation started ...............................
    # --- fglrx INSTALL try --- START ...
    # --- installing downloaded ...
   # -------- I am now in directory:
   # /media/DATA.m/_software/linux.hardware/HD6990/catalyst.driver/catalyst-13.1
   # --------
   # (Reading database ... 1706505 files and directories currently installed.)
   # Preparing to replace fglrx 2:9.000-0ubuntu3 (using fglrx_9.012-0ubuntu1_amd64.deb) ...
   # Removing all DKMS Modules
   # Done.
   # Unpacking replacement fglrx ...
   # Preparing to replace fglrx-amdcccle 2:9.000-0ubuntu3 (using fglrx-amdcccle_9.012-0ubuntu1_amd64.deb) ...
   # Unpacking replacement fglrx-amdcccle ...
   # Preparing to replace fglrx-dev 2:9.000-0ubuntu3 (using fglrx-dev_9.012-0ubuntu1_amd64.deb) ...
   # Unpacking replacement fglrx-dev ...
   # Setting up fglrx (2:9.012-0ubuntu1) ...
   # update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
   # update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken
   # update-initramfs: deferring update (trigger activated)
   # update-initramfs: Generating /boot/initrd.img-3.5.0-22-generic
   # Loading new fglrx-9.012 DKMS files...
   # Building for 3.5.0-22-generic and 3.8.0-999-generic
   # Building for architecture x86_64
   # Building initial module for 3.5.0-22-generic
   # Done.
   # 
   # fglrx:
   # Running module version sanity check.
    # - Original module
      # - No original module exists within this kernel
    # - Installation
      # - Installing to /lib/modules/3.5.0-22-generic/updates/dkms/
   # 
   # depmod....
   # 
   # DKMS: install completed.
   # Building initial module for 3.8.0-999-generic
   # ERROR (dkms apport): kernel package linux-headers-3.8.0-999-generic is not supported
   # Error! Bad return status for module build on kernel: 3.8.0-999-generic (x86_64)
   # Consult /var/lib/dkms/fglrx/9.012/build/make.log for more information.
   # update-initramfs: deferring update (trigger activated)
   # Processing triggers for ureadahead ...
   # Processing triggers for bamfdaemon ...
   # Rebuilding /usr/share/applications/bamf.index...
   # Setting up fglrx-amdcccle (2:9.012-0ubuntu1) ...
   # Setting up fglrx-dev (2:9.012-0ubuntu1) ...
   # Processing triggers for initramfs-tools ...
   # update-initramfs: Generating /boot/initrd.img-3.8.0-999-generic
   # Processing triggers for libc-bin ...
   # ldconfig deferred processing now taking place
   # 
   # --------------------------CATALYST CONFIGURE started ...............................
    # --- configuring driver --- START
   # Uninitialised file found, configuring.
   # Using /etc/X11/xorg.conf
   # Saving back-up to /etc/X11/xorg.conf.fglrx-19
   # Check: Found fglrx section.
    # --- configuring driver --- END
   # --------show content of  /etc/X11/xorg.conf  ...
   # Section "ServerLayout"
      # Identifier     "aticonfig Layout"
      # Screen      0  "aticonfig-Screen[0]-0" 0 0
      # Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
   # EndSection
   # 
   # Section "Module"
   # EndSection
   # 
   # Section "Monitor"
      # Identifier   "aticonfig-Monitor[0]-0"
      # Option	    "VendorName" "ATI Proprietary Driver"
      # Option	    "ModelName" "Generic Autodetecting Monitor"
      # Option	    "DPMS" "true"
   # EndSection
   # 
   # Section "Monitor"
      # Identifier   "aticonfig-Monitor[1]-0"
      # Option	    "VendorName" "ATI Proprietary Driver"
      # Option	    "ModelName" "Generic Autodetecting Monitor"
      # Option	    "DPMS" "true"
   # EndSection
   # 
   # Section "Device"
      # Identifier  "aticonfig-Device[0]-0"
      # Driver      "fglrx"
      # BusID       "PCI:3:0:0"
   # EndSection
   # 
   # Section "Device"
      # Identifier  "aticonfig-Device[1]-0"
      # Driver      "fglrx"
      # BusID       "PCI:4:0:0"
   # EndSection
   # 
   # Section "Screen"
      # Identifier "aticonfig-Screen[0]-0"
      # Device     "aticonfig-Device[0]-0"
      # Monitor    "aticonfig-Monitor[0]-0"
      # DefaultDepth     24
      # SubSection "Display"
         # Viewport   0 0
         # Depth     24
      # EndSubSection
   # EndSection
   # 
   # Section "Screen"
      # Identifier "aticonfig-Screen[1]-0"
      # Device     "aticonfig-Device[1]-0"
      # Monitor    "aticonfig-Monitor[1]-0"
      # DefaultDepth     24
      # SubSection "Display"
         # Viewport   0 0
         # Depth     24
      # EndSubSection
   # EndSection
   # 
   # 
   # --- graphics action ...
   # 
   # --------------------------GRAPHICS test started ...............................
    # --- glxinfo |grep OpenGL
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012
   # OpenGL shading language version string: 4.20
   # OpenGL extensions:
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012
   # OpenGL shading language version string: 4.20
   # OpenGL extensions:
    # --- glxinfo |grep rendering
   # libGL: AtiGetClientDriverName: 9.1.11 fglrx (screen 0)
   # libGL: OpenDriver: trying /usr/lib/fglrx/dri/fglrx_dri.so
   # libGL: AtiGetClientDriverName: 9.1.11 fglrx (screen 1)
   # ukiDynamicMajor: found major device number 250
   # ukiDynamicMajor: found major device number 250
   # ukiOpenByBusid: Searching for BusID PCI:3:0:0
   # ukiOpenDevice: node name is /dev/ati/card0
   # ukiOpenDevice: open result is 6, (OK)
   # ukiOpenByBusid: ukiOpenMinor returns 6
   # ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
   # ukiDynamicMajor: found major device number 250
   # ukiDynamicMajor: found major device number 250
   # ukiOpenByBusid: Searching for BusID PCI:4:0:0
   # ukiOpenDevice: node name is /dev/ati/card0
   # ukiOpenDevice: open result is 7, (OK)
   # ukiOpenByBusid: ukiOpenMinor returns 7
   # ukiOpenByBusid: ukiGetBusid reports PCI:3:0:0
   # ukiOpenDevice: node name is /dev/ati/card1
   # ukiOpenDevice: open result is 7, (OK)
   # ukiOpenByBusid: ukiOpenMinor returns 7
   # ukiOpenByBusid: ukiGetBusid reports PCI:4:0:0
   # direct rendering: Yes
   # direct rendering: Yes
    # --- unity support test
   # OpenGL vendor string:   ATI Technologies Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string:  4.2.12002 Compatibility Profile Context 9.012
   # 
   # Not software rendered:    yes
   # Not blacklisted:          yes
   # GLX fbconfig:             yes
   # GLX texture from pixmap:  yes
   # GL npot or rect textures: yes
   # GL vertex program:        yes
   # GL fragment program:      yes
   # GL vertex buffer object:  yes
   # GL framebuffer object:    yes
   # GL version is 1.4+:       yes
   # 
   # Unity 3D supported:       yes
    # --- fglrx version
   # fglrx:
     # Installed: 2:9.012-0ubuntu1
     # Candidate: 2:9.012-0ubuntu1
     # Version table:
    # *** 2:9.012-0ubuntu1 0
           # 100 /var/lib/dpkg/status
        # 2:9.000-0ubuntu3 0
           # 500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/restricted amd64 Packages
    # --- fglrxinfo
   # display: :0.0  screen: 0
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012
   # 
   # 
   # 
   # display: :0.0  screen: 1
   # OpenGL vendor string: Advanced Micro Devices, Inc.
   # OpenGL renderer string: AMD Radeon HD 6900 Series  
   # OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012
   # 
    # --- Hardware Video Decode Acceleration (EXPERIMENTAL) 
   # libva: VA-API version 0.32.0
   # Xlib:  extension "XFree86-DRI" missing on display ":0.0".
   # libva: va_getDriverName() returns 0
   # libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
   # libva: va_openDriver() returns 0
   # vainfo: VA-API version: 0.32 (libva 1.0.15)
   # vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
   # vainfo: Supported profile and entrypoints
         # VAProfileH264High               :	VAEntrypointVLD
         # VAProfileVC1Advanced            :	VAEntrypointVLD
    # --- compiz 
   # compizconfig - Info: Backend     : ini
   # compizconfig - Info: Integration : true
   # compizconfig - Info: Profile     : default
   # Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
   # Loading icons...
   # ... try to run fgl_glxgears ...
> fgl_glxgears
Using GLX_SGIX_pbuffer
17666 frames in 5.0 seconds = 3533.200 FPS
18247 frames in 5.0 seconds = 3649.400 FPS
17870 frames in 5.0 seconds = 3574.000 FPS
18383 frames in 5.0 seconds = 3676.600 FPS
15395 frames in 5.0 seconds = 3079.000 FPS
18218 frames in 5.0 seconds = 3643.600 FPS

 glxgears
37288 frames in 5.0 seconds = 7457.476 FPS
37929 frames in 5.0 seconds = 7585.732 FPS
39720 frames in 5.0 seconds = 7943.992 FPS
37335 frames in 5.0 seconds = 7466.969 FPS
39400 frames in 5.0 seconds = 7879.915 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 193837 requests (193837 known processed) with 0 events remaining.

---

### Post by Thee on 2013-01-19
Well you seem to have gained 20-30fps on glxgears test. That's really nice.
I'm afraid to install it because I don't wanna screw up something and not know how to fix it :/

---

### Post by ZombieApocalypse on 2013-01-20
> **Thee said:**
> Well you seem to have gained 20-30fps on glxgears test. That's really nice.
I'm afraid to install it because I don't wanna screw up something and not know how to fix it :/

But does that translate into reality? I installed the 13.1 drivers and ran Killing Floor through the Linux Steam beta client and was getting the same fps (25-40fps) as with 12.11 beta and 12.9, and the same level of stuttering, which makes the game barely playable for me. 

And now some of the desktop effects in KDE don't work so I've reverted back to 12.9 for now.

---

### Post by KegHead on 2013-01-20
Hi!

Very interesting results.

I wonder if it's even worth waiting for the update to this driver or if Ubuntu will update?

KegHead

---

### Post by masuch on 2013-01-20
I believe Ubuntu will update fglrx driver but I would expect it in 13.04 version or maybe in some testing ubuntu "ppa" it will appear as usually did. 
Somebody mentioned here - I have as well the same experience with 12.9 catalyst version that is very fast:
To compare what I have written previously I had glxgears ~14.500,- and fgl_glxgears ~5.500,- in 12.9.
(Honestly, I had/have the same performance results even in Ubuntu 11.04 and catalyst 11.4 when I started to use linux for the first time - and continuously it is balancing between those mentioned performances results for the whole time :-) (catalyst, glxgears from 10.000,- to 14.600,-  , fgl_glxgears from 3.500,- to 5.500,- fps on HD6990 on catalyst from 11.4 to 13.1) - measured on Ubuntu from 11.4 to 12.10 version).
What is odd - I am experiencing - catalyst 12.10 has the similar performance results on another Ubuntu 12.10 instance (same computer). 
Well, I do not understand, how is it possible to have such big performance differences on the different Ubuntu 12.10 instances with the same catalyst 12.10 driver version, ~25% performance difference. So, I believe that I am messing regularly something up anyway.
So, according to my experience, if I play games, is always valuable to stay within older version/s of catalyst and do not use newer.
But as an developer on the other side, if I do some dev/run in opencl appls, or testing new opengl features than it is better to use the later/est catalyst version/s.

(( Installing newer catalyst driver leads very often to screw up to properly display desktop - usually blank) - but linux (as opposite to windows) has chroot or text mode to boot up into console in grub which is quite useful and easy to use.))

---

### Post by KegHead on 2013-01-20
Hi!

I look forward to Ubuntu doing something w/ fglrx. It would make it a lot easier for me.

On the other hand 13.04 is not that far away.

KegHead

---

### Post by vedrisha on 2013-01-21
Well considering that 12.9 didn't work at all on ubuntu 12.10 for me.
I'll have to try this one.
btw, I have AthlonII X4 , HD6770 and every time I install any driver I finished with black screen after restart. The sound is here, same as ctr+alt+1 but nothing else. 
So I'm trying this one right away, and letting you know did it work.

---

### Post by KegHead on 2013-01-21
hi!

there seems to be little interest in this topic.

closing out.

keghead

---

### Post by ZombieApocalypse on 2013-01-23
> **ZombieApocalypse said:**
> It works on my system (HD 5850) but some desktop effects don't appear to be working in KDE (Kubuntu 12.10 amd64, KDE 4.9.5), eg transluceny effects. 

It mentions in the release notes "performance of Valve Linux games" (a bit vague), but I certainly don't notice any performance improvement for Killing Floor through the Linux Steam beta client. Although technically this is not a Valve game.

I'm tempted to go back to the previous driver.

Turns out I hadn't installed the driver correctly. Reinstalled last night and all the KDE desktop effects are now working as expected. Still no noticeable difference in gaming performance (same frame rate and stuttering), though I've only tried Killing Floor so far.

---

### Post by vedrisha on 2013-01-23
Tried 13.1 and still getting the same result. Black screen after reboot.....
Seriously starting to thing to try to swap graphic card for some same rank Nvidia card...

---

### Post by ZombieApocalypse on 2013-01-23
> **vedrisha said:**
> Tried 13.1 and still getting the same result. Black screen after reboot.....
Seriously starting to thing to try to swap graphic card for some same rank Nvidia card...

What was your installation procedure?

---

### Post by badbod on 2013-02-23
RE 'Black screen on bootup'  - if you have 'memory hole remap' option in BIOS then disable it. I have to disable this in my bios or I get the same thing with proprietary drivers.

---

