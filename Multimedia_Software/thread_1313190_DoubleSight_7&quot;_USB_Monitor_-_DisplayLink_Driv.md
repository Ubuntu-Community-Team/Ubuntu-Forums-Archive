---
title: "DoubleSight 7&quot; USB Monitor - DisplayLink Drivers - Extended Desktop"
date: 2009-11-03
forum: Multimedia Software
---

### Post by Calabraun on 2009-11-03
I recently bought a DoubleSight 7" USB Monitor [DS-70U]("http://www.doublesight.com/product/?idx=55"), trying to get it working as an extended desktop on Mythbuntu 9.10 and having some difficulty. It uses the DisplayLink technology.

It works in console mode, and also works fine as a standalone monitor with X windows. I can also get it working as the primary (Screen 0) monitor in an extended desktop setup. It just will not give me a screen if I set it up as the secondary monitor (Screen 1) using the config below.

```
Section "ServerLayout"                                              Identifier "Server Layout"
   Screen  0  "Default Screen" 0 0
   Screen  1  "DisplayLinkScreen" LeftOf "Default Screen"
EndSection                                                                 
####################################
  
Section "Files"                                                     ModulePath  "/usr/lib/xorg/modules"
   ModulePath  "/usr/local/lib/xorg/modules"
EndSection
    
########### Main Monitor ###########

Section "Monitor"
    Identifier     "Generic Monitor"
    Option         "DPMS"
EndSection   
   
Section "Device"                                                     Identifier "Generic Video Card"
    Driver     "nvidia"
    Option     "DPI" "100x100"               
    Option     "UseEvents" "1"                      
    Option     "AddARGBVisuals" "1"                         
    Option     "AddARGBGLXVisuals" "1"                      
    Option     "NoLogo" "1"                             
EndSection                                                         
Section "Screen"                                                     Identifier     "Default Screen"                         
    Device         "Generic Video Card"                   
    Monitor        "Generic Monitor"                           
    DefaultDepth    24
    SubSection     "Display"                              
        Depth   24                   
        Modes   "nvidia-auto-select" "1920x1080" "1280x720"
    EndSubSection                       
EndSection                                                                  
####### DisplayLink Stuff #######    
             
Section "Device"                                                    Identifier  "DisplayLinkDevice"  
   driver      "displaylink"                  
   Option      "fbdev" "/dev/fb0" 
EndSection
                                                       
Section "Monitor"                                                   Identifier  "DisplayLinkMonitor"    
EndSection                                                             
Section "Screen"                                                    Identifier  "DisplayLinkScreen"                 
   Device      "DisplayLinkDevice"      
   Monitor     "DisplayLinkMonitor"      
   SubSection "Display"                            
     Depth       24                         
     Modes       "800x480"  
   EndSubSection                                       
EndSection   
```                                                          

Here is the section of the Xorg.0.log file where the DisplayLink drivers get loaded...and then get unloaded! I don't see any errors that explain why they were unloaded.

```
(II) Module nvidia: vendor="NVIDIA Corporation"                                 
        compiled for 4.0.2, module version = 1.0.0                              
        Module class: X.Org Video Driver                                        
(II) LoadModule: "displaylink"                                                  
(II) Loading /usr/lib/xorg/modules/drivers//displaylink_drv.so                  
(II) Module displaylink: vendor="X.Org Foundation"                              
        compiled for 1.6.4, module version = 0.0.1                              
        ABI class: X.Org Video Driver, version 5.0                              
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009          
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs                        
(II) DL: driver for : displaylink                                               
(II) Primary Device is: PCI 01@00:00:0                                          
(II) Loading sub module "fb"
(II) LoadModule: "fb"                                                           
(II) Loading /usr/lib/xorg/modules//libfb.so                                    
(II) Module fb: vendor="X.Org Foundation"                                       
        compiled for 1.6.4, module version = 1.0.0                              
        ABI class: X.Org ANSI C Emulation, version 0.4                          
(II) Loading sub module "wfb"                                                   
(II) LoadModule: "wfb"                                                          
(II) Loading /usr/lib/xorg/modules//libwfb.so                                   
(II) Module wfb: vendor="X.Org Foundation"                                      
        compiled for 1.6.4, module version = 1.0.0                              
        ABI class: X.Org ANSI C Emulation, version 0.4                          
(II) Loading sub module "ramdac"                                                
(II) LoadModule: "ramdac"                                                       
(II) Module "ramdac" already built-in                                           
(WW) Falling back to old probe method for displaylink                           
(II) Loading sub module "fbdevhw"                                               
(II) LoadModule: "fbdevhw"                                                      
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"                                  
        compiled for 1.6.4, module version = 0.0.2                              
        ABI class: X.Org Video Driver, version 5.0                              
(II) resource ranges after probing:                                             
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]                     
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]                 
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]                 
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]                 
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]                     
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]                     
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32                               
(==) NVIDIA(0): RGB weight 888                                                  
(==) NVIDIA(0): Default visual is TrueColor                                     
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)                          
(**) NVIDIA(0): Option "NoLogo" "1"                                             
(**) NVIDIA(0): Option "DPI" "100x100"                                          
(**) NVIDIA(0): Option "UseEvents" "1"                                          
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "1"
(**) NVIDIA(0): Enabling RENDER acceleration                                    
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is   
(II) NVIDIA(0):     enabled.                                                    
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 GS (G72) at PCI:1:0:0 (GPU-0)           
(--) NVIDIA(0): Memory: 524288 kBytes                                           
(--) NVIDIA(0): VideoBIOS: 05.72.22.43.00                                       
(II) NVIDIA(0): Detected PCI Express Link width: 16X                            
(--) NVIDIA(0): Interlaced video modes are supported on this GPU                
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 GS at PCI:1:0:0:    
(--) NVIDIA(0):     SAMSUNG (DFP-0)                                             
(--) NVIDIA(0): SAMSUNG (DFP-0): 165.0 MHz maximum pixel clock                  
(--) NVIDIA(0): SAMSUNG (DFP-0): Internal Single Link TMDS                      
(II) NVIDIA(0): Assigned Display Device: DFP-0                                  
(II) NVIDIA(0): Validated modes:                                                
(II) NVIDIA(0):     "nvidia-auto-select"                                        
(II) NVIDIA(0):     "1920x1080"                                                 
(II) NVIDIA(0):     "1280x720"                                                  
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "1280x720"                                                  
(II) NVIDIA(0):     "1024x768"                                                  
(II) NVIDIA(0):     "720x480"                                                   
(II) NVIDIA(0):     "800x600"                                                   
(II) NVIDIA(0):     "640x480"                                                   
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080                
(**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option      
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.                               
(II) UnloadModule: "displaylink"                                                
(II) Unloading /usr/lib/xorg/modules/drivers//displaylink_drv.so                
(II) UnloadModule: "fbdevhw"                                                    
(II) Unloading /usr/lib/xorg/modules/linux//libfbdevhw.so                       
(--) Depth 24 pixmap format is 32 bpp                                           
(II) do I need RAC?  No, I don't.
```


By merely switching the two screens in the ServerLayout section, both monitors work in extended desktop mode. However, the tiny 7" screen does not really work well as a primary monitor!

```
Section "ServerLayout"                                              Identifier "Server Layout"
   Screen  0  "DisplayLinkScreen" 0 0
   Screen  1  "Default Screen" LeftOf "DisplayLinkScreen"
EndSection

```

I installed the DisplayLink drivers using the instructions [here]("http://libdlo.freedesktop.org/wiki/xf86-driver-displaylink") and [here]("http://libdlo.freedesktop.org/wiki/Ubuntu9.04").
Any help would be greatly appreciated!

-Cal

---

### Post by responder.member on 2009-11-11
Hi Cal.,

Had you tried to add
--
Option "Xinerama" "on"
--
into your ServerLayout part?

I found on some posts that mentioned Xinerama should be on to enable X11 recognized different graphic card at the same time.
Also there are people said the depth should be the same for all monitor which should be always 16 for displaylink driver.
Sorry I can't attach those posts' url right now.
I didn't save them into my bookmark.

I'm trying to get my displaylink devices work as an extended monitor but with no luck so far. (Under ubuntu 9.10 64bit)
When I set it as an standalone monitor, the X win will show without the login screen. Orz
Can you share that conf with me?

Thanks in advance.

FYI. I posted my questions on Libdlo mailing list which might come out a working solution later.
[http://lists.freedesktop.org/archives/libdlo/](http://lists.freedesktop.org/archives/libdlo/)

---

### Post by trubshac on 2009-12-02
Hi Cal

Did you ever solve this problem?  I'm having a similar problem myself.

---

### Post by Calabraun on 2009-12-22
I ended up starting a seperate X server for the USB monitor, and then using x2x ([http://x2x.dottedmag.net/](http://x2x.dottedmag.net/)) to allow moving the mouse between the screens. 

This scenario actually works quite well for me. x2x doesn't allow you to drag apps between both screens (just the pointer), which I don't really want anyway because mythtv runs full screen on the main monitor. It does allow me to easily get to the USB monitor for checking download statuses, and what not.

This is the quick script I made to start up the DoubleSight monitor.

> xinit -- /usr/bin/X :1 -xf86config xorg.conf.DS -novtswitch -sharevts -dpi 25 -audit 0 vt12 &
sleep 5
x2x -west -from :0 -to :1 &
export DISPLAY=":1"
exec startxfce4 &

And the xorg.conf.DS

> Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "Default Screen" 0 0
        Option     "AllowMouseOpenFail" "True"
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
    Option   "AllowEmptyInput"     "false"
    Option   "AutoAddDevices"      "false"
    Option   "AutoEnableDevices"   "false"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "void"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "void"
EndSection

#############################################                             

Section "Files"
        ModulePath      "/usr/lib/xorg/modules"
        ModulePath      "/usr/local/lib/xorg/modules"
EndSection

############### DisplayLink Monitor ###############

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
                Depth   24
                Modes   "800x480"
        EndSubSection
EndSection







Cal

---

### Post by Crath on 2009-12-24
Can you please maybe post information on where you learned more about xorg?

I have an external dvi to usb driver, and have it set up correctly, but it only runs the test on the external device (draws shapes) and I have no clue on how to add it as a second display device.

Thank you!

---

### Post by lkraav on 2011-08-11
> **Calabraun said:**
> I ended up starting a seperate X server for the 
This is the quick script I made to start up the DoubleSight monitor.


Instead of going through the trouble of definining void inputs, it seems that all I really needed in ServerFlags was:

```
Option "AutoAddDevices" "false"
```

Now none of the primary display's input devices are disturbing us.

About to take a look at differing keyboard layout on the x2x DS screen now.

---

### Post by NickD-NLUG on 2011-11-15
> **Calabraun said:**
> I ended up starting a seperate X server for the USB monitor, and then using x2x ([http://x2x.dottedmag.net/](http://x2x.dottedmag.net/)) to allow moving the mouse between the screens. 


Thank you very much for posting this - it's a neat way around a problem I was having getting my Lilliput screen to work.

One question - at the moment I can only use a modified version of your script as root; any tips on running it as a local user instead?

---

### Post by richardlxn on 2012-01-02
I recently bought a Doublesight DS90U display and tried to have it work under ubuntu 10.10. As I am totally a linux outsider, I installed displaylink from ubuntu software center, but the laptop just can not detect my Doublesight DS90U. Can you please tell me how to have the USB display work under ubuntu 10.10?

---

### Post by hondaman900 on 2012-01-18
Hey, richardlxn, did you find a solution/driver for this monitor on Ubuntu? I just got one and don't know how to make it work on Ubuntu 10.

Thx in advance

---

### Post by overdrank on 2012-01-18
Hi and please start a new thread with your issues. Back to sleep thread. Thread closed

---

