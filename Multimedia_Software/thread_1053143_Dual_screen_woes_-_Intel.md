---
title: "Dual screen woes - Intel"
date: 2009-01-28
forum: Multimedia Software
---

### Post by crypticedge on 2009-01-28
Problem description: Dual screen does not function on ubuntu 8.10

Attempted fixes: Redoing xorg from the default to something more specific as detailed below, default left no info on the alt monitor

Recent changes: Have you made any changes to your system/configuration recently that might have caused the problem? - No, never worked, this is a fresh install, and was part of the plan on the system. It functioned properly in windows, but is stuck in clone view on ubuntu.


Operating system: 32bit Ubuntu 8.10 

System specs: Dell 755, intel chipset and card

I've been bashing my head against this one for a day now, and come for help. 
I'm trying to get dual screen to work properly on ubuntu, 8.10, running KDE. When I start kdm up, it loads both screens properly, with the logon box on the proper side, but after logon I get a straight black screen on both making it unable to be used. 
This is my relivent lspci output
```

00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

```
Here is my xorg block

```

Section "Device"                                     
        Driver "intel"                                
        Identifier "Device[0]"                       
        VendorName "Intel"                           
        Option "NoAccel" "false"                     
        Option "XVideo" "on"                         
        Option "monitor-VGA" "Monitor[0]"            
        Option "monitor-TMDS-1" "Monitor[1]"         
        Option "AccelMethod" "exa"                   
        Option "MigrationHeuristic" "greedy"         
        Option "ExaNoComposite" "false"              
EndSection                                           

Section "Device"
        Driver "intel"   
        Identifier "Device[1]"
        VendorName "Intel"    
        Option "NoAccel" "false"
        Option "XVideo" "on"    
        Option "monitor-VGA" "Monitor[0]"
        Option "monitor-TMDS-1" "Monitor[1]"
        Option "AccelMethod" "exa"          
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "false"     
EndSection                                  

Section "Monitor"
        Identifier "Monitor[0]"
        Option "DPMS"
EndSection

Section "Monitor"
        Identifier "Monitor[1]"
        Option "DPMS"
        Option "RightOf" "Monitor[0]"
EndSection

Section "Screen"
        Device "Device[0]"
        Identifier "First"
        Monitor "Monitor[0]"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
                Virtual 2560 1024
        EndSubSection
EndSection

Section "Screen"
        Device "Device[1]"
        Identifier "Second"
        Monitor "Monitor[1]"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
                Virtual 2560 1024
        EndSubSection
EndSection

```

---

### Post by crypticedge on 2009-01-29
Nothing? I can't be the only one who wants to do dual monitor on ubuntu.

I have made tons of little tweaks yesterday, none of them fixed. Reverted to the default that comes with ubuntu, where you are stuck on perm clone view and unable to change it.

---

### Post by blackgr on 2009-01-29
[http://ubuntuforums.org/showthread.php?t=984185&page=4](http://ubuntuforums.org/showthread.php?t=984185&page=4)

---

### Post by crypticedge on 2009-01-29
Yeah, I've been over whats in there, and tried all that already. No help. I can't use it if my virtual is set over a specific amount (2048 ) as it just goes to a black screen. The kde tool for xrandr is useless and decides to merge the two monitors, so no changes ever take effect.

Edit - corrected resolution to a proper size, I had 2046, not 2048
Reedit - Form turned 8 ) into a smiley

---

### Post by crypticedge on 2009-01-29
I have changed my Xorg to use xinerama instead due to this issue with xrandr that seems to affect intel. As such, my new config (still not quite working) is below.
```

Section "Device"                                
        Driver "intel"                          
        Identifier "Intel 1"                    
        BusID       "PCI:0:2:0"                 
        VendorName "Intel"                      
        Option "DDCMode" "True"                 
        Option "NoAccel" "false"                
        Option "XVideo" "on"                    
#       Option "monitor-VGA" "Monitor[0]"       
#       Option "monitor-TMDS-1" "Monitor[1]"    
        Option "AccelMethod" "exa"              
        Option "MigrationHeuristic" "greedy"    
        Option "ExaNoComposite" "false"         
EndSection                                      

Section "Device"
        Driver "intel"
        Identifier "Intel 2"
        BusID       "PCI:0:2:1"
        VendorName "Intel"     
        Option "DDCMode" "True"
        Option "NoAccel" "false"
        Option "XVideo" "on"    
#       Option "monitor-VGA" "Monitor[0]"
#       Option "monitor-TMDS-1" "Monitor[1]"
        Option "AccelMethod" "exa"          
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "false"     
EndSection                                  

Section "Monitor"
        Identifier "Second Monitor"
#       Option "DPMS"              
EndSection                         

Section "Monitor"
        Identifier "Second Monitor"
#       Option "DPMS"
#       Option "RightOf" "Main Monitor"
EndSection

Section "Screen"
        Device "Intel 1"
        Identifier "First"
        Monitor "Main Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Device "Intel 2"
        Identifier "Second"
        Monitor "Second Monitor"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Main"
        Option  "Xinerama" "true"
        Screen  0       "First"
        Screen  1       "Second" RightOf "First"
EndSection

```
Now, it seems to start working, compared to xrandr, but xorg dumps, and quite harshly.

```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux IT-KYLE 2.6.27-11-generic #1 SMP Wed Jan 28 00:02:01 UTC 2009 i686                                                              
Build Date: 24 October 2008  08:00:16AM                                         
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)                            
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)                      
        to make sure that you have the latest version.                          
Module Loader present                                                           
Markers: (--) probed, (**) from config file, (==) default setting,              
        (++) from command line, (!!) notice, (II) informational,                
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.           
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 29 11:10:48 2009            
(==) Using config file: "/etc/X11/xorg.conf"                                    
(==) ServerLayout "Main"                                                        
(**) |-->Screen "First" (0)                                                     
(**) |   |-->Monitor "<default monitor>"                                        
(**) |   |-->Device "Intel 1"                                                   
(==) No monitor specified for screen "First".                                   
        Using a default monitor configuration.                                  
(**) |-->Screen "Second" (1)                                                    
(**) |   |-->Monitor "Second Monitor"                                           
(**) |   |-->Device "Intel 2"                                                   
(**) Option "Xinerama" "true"                                                   
(==) Automatically adding devices                                               
(==) Automatically enabling devices                                             
(**) Xinerama: enabled                                                          
(==) No FontPath specified.  Using compiled-in default.                         
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.              
        Entry deleted from font path.                                           
(==) FontPath set to:                                                           
        /usr/share/fonts/X11/misc,                                              
        /usr/share/fonts/X11/100dpi/:unscaled,                                  
        /usr/share/fonts/X11/75dpi/:unscaled,                                   
        /usr/share/fonts/X11/Type1,                                             
        /usr/share/fonts/X11/100dpi,                                            
        /usr/share/fonts/X11/75dpi,                                             
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType                        
(==) ModulePath set to "/usr/lib/xorg/modules"                                  
(II) Cannot locate a core pointer device.                                       
(II) Cannot locate a core keyboard device.                                      
(II) The server relies on HAL to provide the list of input devices.             
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.                                                                             
(II) Open ACPI successful (/var/run/acpid.socket)                               
(II) Loader magic: 0x81d9a40                                                    
(II) Module ABI versions:                                                       
        X.Org ANSI C Emulation: 0.4                                             
        X.Org Video Driver: 4.1                                                 
        X.Org XInput driver : 2.1                                               
        X.Org Server Extension : 1.1                                            
        X.Org Font Renderer : 0.6                                               
(II) Loader running on linux                                                    
(++) using VT number 7                                                          

(--) PCI:*(0@0:2:0) Intel Corporation 82Q35 Express Integrated Graphics Controller rev 2, Mem @ 0xfea00000/0, 0xd0000000/0, 0xfeb00000/0, I/O @ 0x0000ec90/0    
(--) PCI: (0@0:2:1) Intel Corporation 82Q35 Express Integrated Graphics Controller rev 2, Mem @ 0xfea80000/0                                                    
(II) System resource ranges:                                                    
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                     
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                 
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                 
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                 
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]                     
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]                     
(II) LoadModule: "extmod"                                                       

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.0.0         
        Module class: X.Org Server Extension               
        ABI class: X.Org Server Extension, version 1.1     
(II) Loading extension SHAPE                               
(II) Loading extension MIT-SUNDRY-NONSTANDARD              
(II) Loading extension BIG-REQUESTS                        
(II) Loading extension SYNC                                
(II) Loading extension MIT-SCREEN-SAVER                    
(II) Loading extension XC-MISC                             
(II) Loading extension XFree86-VidModeExtension            
(II) Loading extension XFree86-Misc                        
(II) Loading extension XFree86-DGA                         
(II) Loading extension DPMS                                
(II) Loading extension TOG-CUP                             
(II) Loading extension Extended-Visual-Information         
(II) Loading extension XVideo                              
(II) Loading extension XVideo-MotionCompensation           
(II) Loading extension X-Resource                          
(II) LoadModule: "dbe"                                     

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.0.0      
        Module class: X.Org Server Extension            
        ABI class: X.Org Server Extension, version 1.1  
(II) Loading extension DOUBLE-BUFFER                    
(II) LoadModule: "glx"                                  

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.0.0      
        ABI class: X.Org Server Extension, version 1.1  
(==) AIGLX enabled                                      
(==) Exporting typical set of GLX visuals               
(II) Loading extension GLX                              
(II) LoadModule: "freetype"                             

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.5.2, module version = 2.1.0                      
        Module class: X.Org Font Renderer                               
        ABI class: X.Org Font Renderer, version 0.6                     
(II) Loading font FreeType                                              
(II) LoadModule: "record"                                               

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.13.0        
        Module class: X.Org Server Extension               
        ABI class: X.Org Server Extension, version 1.1     
(II) Loading extension RECORD                              
(II) LoadModule: "dri"                                     

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"              
        compiled for 1.5.2, module version = 1.0.0      
        ABI class: X.Org Server Extension, version 1.1  
(II) Loading extension XFree86-DRI                      
(II) LoadModule: "intel"                                

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"            
        compiled for 1.5.2, module version = 2.5.1      
        Module class: X.Org Video Driver                
        ABI class: X.Org Video Driver, version 4.1      
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,                                
        Mobile Intel® GM45 Express Chipset,                              
        Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41          
(II) Primary Device is: PCI 00@00:02:0                                   
(II) resource ranges after xf86ClaimFixedResources() call:               
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]              
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]          
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]          
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]          
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]              
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]              
(II) resource ranges after probing:                                      
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]              
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]          
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]          
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]          
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]          
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]           
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]           
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]              
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]              
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B]              
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]             
(II) Loading sub module "vgahw"                                          
(II) LoadModule: "vgahw"                                                 

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"   
        compiled for 1.5.2, module version = 0.1.0
        ABI class: X.Org Video Driver, version 4.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32  
(==) intel(0): RGB weight 888                     
(==) intel(0): Default visual is TrueColor        
(**) intel(0): Option "AccelMethod" "exa"         
(**) intel(0): Option "NoAccel" "false"           
(**) intel(0): Option "XVideo" "on"               
(II) intel(0): Integrated Graphics Chipset: Intel(R) Q35
(--) intel(0): Chipset: "Q35"                           
(--) intel(0): Linear framebuffer at 0xD0000000         
(--) intel(0): IO registers at addr 0xFEA00000          
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(**) intel(0): Using EXA for acceleration                     
(II) intel(0): 2 display pipes available.                     
(II) Loading sub module "ddc"                                 
(II) LoadModule: "ddc"                                        
(II) Module "ddc" already built-in                            
(II) Loading sub module "i2c"                                 
(II) LoadModule: "i2c"                                        
(II) Module "i2c" already built-in                            
(II) intel(0): Output VGA has no monitor section              
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.    
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.                                                                  
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.                             
(II) intel(0): Output TMDS-1 has no monitor section                             
(II) intel(0): SDVOB: device VID/DID: 04:AA.03, clock range 25.0MHz - 165.0MHz  
(II) intel(0): SDVOB: 1 input channel                                           
(II) intel(0): SDVOB: TMDS0 output reported                                     
(II) intel(0): Current clock rate multiplier: 8                                 
(II) intel(0): I2C bus "CRTDDC_A" initialized.                                  
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.           
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.                              
(II) intel(0): I2C bus "CRTDDC_A" removed.                                      
(II) intel(0): EDID vendor "DEL", prod id 16419                                 
(II) intel(0): Using EDID range info for horizontal sync                        
(II) intel(0): Using EDID range info for vertical refresh                       
(II) intel(0): Printing DDC gathered Modelines:                                 
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)                                              
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)                                                       
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)                                                        
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)                                                        
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)                                                        
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)                                              
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)                                                   
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)                                                   
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)                                                       
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)                                                  
(II) intel(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)                                             
(II) intel(0): EDID vendor "DEL", prod id 16419                                 
(II) intel(0): I2C device "SDVOB DDC Bus:ddc2" registered at address 0xA0.      
(EE) intel(0): Unable to write to SDVOCTRL_E for SDVOB Slave 0x70.              
(II) intel(0): EDID vendor "DEL", prod id 16420                                 
(II) intel(0): Output VGA connected                                             
(II) intel(0): Output TMDS-1 connected                                          
(II) intel(0): Using user preference for initial modes                          
(II) intel(0): Output VGA using initial mode 1280x1024                          
(II) intel(0): Output TMDS-1 using initial mode 1280x1024                       
(II) intel(0): detected 1024 kB GTT.                                            
(II) intel(0): detected 7164 kB stolen memory.                                  
(==) intel(0): video overlay key set to 0x101fe                                 
(==) intel(0): Intel XvMC decoder disabled                                      
(==) intel(0): Will not try to enable page flipping                             
(==) intel(0): Triple buffering disabled                                        
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)                           
(**) intel(0): Display dimensions: (340, 270) mm                                
(**) intel(0): DPI set to (119, 150)                                            
(II) Loading sub module "fb"                                                    
(II) LoadModule: "fb"                                                           

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"   
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"                         
(II) LoadModule: "exa"                                

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"   
        compiled for 1.5.2, module version = 2.4.0
        ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"                  
(II) LoadModule: "ramdac"                         
(II) Module "ramdac" already built-in             
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x80020203 to 0x00020203                                                                               
(WW) intel(0): PIPEASTAT before: status: FIFO_UNDERRUN VBLANK_INT_ENABLE VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS                                  
(WW) intel(0): PIPEASTAT after: status: VBLANK_INT_ENABLE VSYNC_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS                                                 
(==) Depth 24 pixmap format is 32 bpp                                           
(II) do I need RAC?  No, I don't.                                               
(II) resource ranges after preInit:                                             
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                     
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                 
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                 
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                 
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)           
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)            
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)            
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]                     
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]                     
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)               
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)              
(II) intel(0): Kernel reported 484608 total, 1 used                             
(II) intel(0): I830CheckAvailableMemory: 1938428 kB available                   
(WW) intel(0): Direct rendering is not supported when Xinerama is enabled       
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.                       
(**) intel(0): Framebuffer compression disabled                                 
(**) intel(0): Tiling enabled                                                   
(==) intel(0): VideoRam: 262144 KB                                              
(II) intel(0): Attempting memory allocation with tiled buffers.                 
(II) intel(0): Tiled allocation successful.                                     
(II) intel(0): Page Flipping disabled                                           
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000  
(**) intel(0): Option "MigrationHeuristic" "greedy"                             
(**) intel(0): Option "EXANoComposite" "false"                                  
(II) EXA(0): Offscreen pixmap area of 39321600 bytes                            
(II) EXA(0): Driver registered support for the following operations:            
(II)         Solid                                                              
(II)         Copy                                                               
(II)         Composite (RENDER acceleration)                                    
(==) intel(0): Backing store disabled                                           
(==) intel(0): Silken mouse enabled                                             
(II) intel(0): Initializing HW Cursor                                           
(II) intel(0): Current clock rate multiplier: 8                                 
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01000000 (pgoffset 4096)     
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x02000000 (pgoffset 8192)     
(II) intel(0): Fixed memory allocation layout:                                  
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)                      
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00131fff: fake bufmgr (1024 kB)
(II) intel(0): 0x00132000-0x00132fff: overlay registers (4 kB)
(II) intel(0): 0x006ff000:            end of stolen memory
(II) intel(0): 0x01000000-0x01ffffff: front buffer (12800 kB) X tiled
(II) intel(0): 0x02000000-0x0457ffff: exa offscreen (38400 kB)
(II) intel(0): 0x10000000:            end of aperture
(WW) intel(0): ESR is 0x00000001, instruction error
(WW) intel(0): Existing errors found in hardware state.
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0):   Output TMDS-1 is connected to pipe B
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f4d400]
2: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb79b1fad]
3: /usr/bin/X [0x80caec4]
4: /usr/bin/X [0x80cb02a]
5: /usr/bin/X(xf86HandleColormaps+0x21a) [0x80cbf3a]
6: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb79b65f0]
7: /usr/bin/X(AddScreen+0x19f) [0x807137f]
8: /usr/bin/X(InitOutput+0x206) [0x80aa536]
9: /usr/bin/X(main+0x279) [0x8071b19]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b51685]
11: /usr/bin/X [0x8071101]
Saw signal 11.  Server aborting.
(II) intel(0): xf86UnbindGARTMemory: unbind key 0
(II) intel(0): xf86UnbindGARTMemory: unbind key 1

```

---

### Post by blackgr on 2009-01-29
> There is a known issue that DRI doesn't work on pre-965 if maximum is larger than 2048x2048.

This is propably intel's problem.

---

### Post by crypticedge on 2009-01-29
Ok, now is there any work around for this that I could try? I'm willing to do some experimentation to test these things to try to make it work.

---

### Post by jefco on 2009-02-04
I'm having the same problem with 8.10, a geforce card and via chipset, so it's not limited to intel. Loads in text mode on one monitor, then switches to the other one for the GUI login while the first monitor goes blank. I'm running the nvidia restricted driver and openchrome. I've made my own post about this, but hoping to find info here as well.

---

### Post by skoorbevad on 2009-02-05
> **crypticedge said:**
> Ok, now is there any work around for this that I could try? I'm willing to do some experimentation to test these things to try to make it work.

I actually don't think that it is Intel's problem, as an above poster suggests.  You need a patched version of DRI for the Intel video driver to properly display on screen resolutions (virtual or otherwise) larger than 2048 pixels on any one axis.

Conveniently, here's a .deb with the appropriate patch applied:
[http://rj45.org/stuff/misc/libgl1-mesa-dri_7.2-1ubuntu2_i386.deb](http://rj45.org/stuff/misc/libgl1-mesa-dri_7.2-1ubuntu2_i386.deb)

I managed to find that digging through a couple bug reports on this same issue that have been filed on Launchpad.  I've got this successfully working on a Dell D630, Intel GM965.  Two external monitors plugged into the docking station on VGA and DVI, virtual screen resolution of 2880x900.  Compiz is fully functional.

Install the patched .deb, open gnome-display-properties (or xrandr or whatever), and adjust your screens to your liking.

I still have some nags with the VGA-attached screen not firing up with the right resolution or horizontal sync when X starts, but it seems breaking out of X with CTRL-ALT-F1 and re-entering with ALT-F7 jolts it into the proper video mode.

Pre-GM965 MAY still have an issue, but from what I was reading it seemed like a few people were having success with this on those chipsets.

```

dbrooks@moo:~ $ sudo lspci -v | grep Display
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
dbrooks@moo:~ $ xrandr -q
Screen 0: minimum 320 x 200, current 2880 x 900, maximum 2880 x 900
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0*    59.9     60.0  
   1360x768       59.8  
   1280x800       60.0  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.0 +
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TMDS-1 connected 1440x900+1440+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0     59.9*    60.0  
   1360x768       59.8  
   1280x800       60.0  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
TV disconnected (normal left inverted right x axis y axis)

```

Additionally, in some situations (I've noticed this when running a window manager outside of gnome-session) you will need to disable any connected screens using xrandr that you aren't using, as for some reason having more than two display devices listed as "connected" in xrandr's output will hose things pretty good.  For instance, if you're running two external monitors and not using the built-in display, ake sure you use xrandr to turn the LVDS device off.  Likewise, do the same with the TV-out if you're using the internal screen and one external display.

I don't know why gnome-session seems to affect this, but it looks like it manages to.

---

### Post by Craig73 on 2009-02-10
> **skoorbevad said:**
> 
Conveniently, here's a .deb with the appropriate patch applied:
[http://rj45.org/stuff/misc/libgl1-mesa-dri_7.2-1ubuntu2_i386.deb](http://rj45.org/stuff/misc/libgl1-mesa-dri_7.2-1ubuntu2_i386.deb)


I tried this (briefly) on my Intel 855GM, and it didn't seem to work for me.

---

### Post by cmcginty on 2009-04-23
I thought this would be fixed in Jaunty ... but looks like it is not. What's the deal?

---

