---
title: "Dual Monitor - resolution mode not found"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by lenorin on 2007-02-21
Hi, I know this topic has been talked to death on these forums, and indeed I've read pretty much all the posts. I've read all the guides, blogs, tutorials, and manuals how to get dual screen set up, but I have a small problem I thought you guys could help me with. I know it has to be something simple. :-) I really appreciate the help, as I want to immerse myself into Ubuntu, and I can't if I can't have the two monitors on my docking station playing nicely together. Have to use Windows otherwise. I need you guys to save me from damnation.

Setup: I have an Dell Inspiron 6000, Intel 915GM integrated video graphics, and a 20.1” ViewSonic LCD screen connected via VGA cable. I am trying to get a dual-head system set up. 

Symptoms: I have the LCD monitor displaying an extension of the desktop, as it should be. So I know xinerama is working, all the mapping is working. Unfortunately the resolution on that screen is 640x480, and it should be 1680x1050. Below is the relevant section of my xorg.conf file, and then further down are two excerpts from my Xorg.0.log files. One showing the 1680x1050 mode for the “LFP” screen (the LCD), and the other showing that it can't seem to find the mode and that's why it's setting the resolution as it is. 

Needed solution: How do I make the XServer see the 1680x1050 mode?

Thanks ahead of time you guys! I really appreciate this.


------------------------------------------xorg.conf------------------------------------------
Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

Section "Device"
        Identifier      "External Video Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "laptop"
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "LCD"
        Option          "DPMS"
       # Modeline "1680x1050" 149.00  1680 1760 1944 2280  1050 1050 1052 1089
EndSection

Section "Screen"
        Identifier      "laptop-Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "laptop"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "LCD-Screen"
        Device          "External Video Card"
        Monitor         "LCD"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"     
        EndSubSection
EndSection
        
Section "ServerLayout"
        Identifier      "xinerama"
        Screen          0 "laptop-Screen" 0 0
        Screen          1 "LCD-Screen" RightOf "laptop-Screen"
        Option "Xinerama" "true"
        Option "Clone" "off"    
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

---------------------------------------/var/log/Xorg.0.log -------------------------------------
 (these guys are almost one after the other, I cut out irrelevant stuff for brevity, which is the soul of wit)
---------------------------------------------- Excerpt 1 ------------------------------------------
(**) I810(1): Depth 24, (--) framebuffer bpp 32
(==) I810(1): RGB weight 888
(==) I810(1): Default visual is TrueColor
(II) I810(1): Integrated Graphics Chipset: Intel(R) 915GM
(--) I810(1): Chipset: "915GM"
(--) I810(1): Linear framebuffer at 0xC0000000
(--) I810(1): IO registers at addr 0xDFF00000
(II) I810(1): 2 display pipes available.
(II) I810(1): detected 7932 kB stolen memory.
(WW) I810(1): Detected stolen memory (7872 kB) doesn't match what the BIOS reports (12288 kB)
(II) I810(1): Monitoring connected displays enabled
(--) I810(1): Pre-allocated VideoRAM: 7932 kByte
(==) I810(1): VideoRAM: 12288 kByte
(==) I810(1): video overlay key set to 0x101fe
(**) I810(1): page flipping disabled
(==) I810(1): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(1): BIOS Build: 1219
(==) I810(1): Device Presence: disabled.
(==) I810(1): Display Info: enabled.
(II) I810(1): Broken BIOSes cause the system to hang here.
              If you encounter this problem please add 
                 Option "DisplayInfo" "FALSE"
              to the Device section of your XF86Config file.
(II) I810(1): Display Info: CRT: attached: TRUE, present: TRUE, size: (720,400)
(II) I810(1): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(1): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Display Info: LFP (local flat panel): attached: TRUE, present: TRUE, size: (1680,1050)
(II) I810(1): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,2315)
(II) I810(1): Size of device LFP (local flat panel) is 1680 x 1050
(II) I810(1): Currently active displays on Pipe A:
(II) I810(1):   CRT
(II) I810(1): Currently active displays on Pipe B:
(II) I810(1):   LFP (local flat panel)
(II) I810(1): Lowest common panel size for pipe B is 1680 x 1050
(==) I810(1): Secondary head is using Pipe A
(--) I810(1): Using HW Cursor because it's enabled on primary head.
(--) I810(1): Maximum frambuffer space: 12120 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) I810(0): VESA VBE DDC read failed
(II) I810(1): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(1): Maximum space available for video modes: 12120 kByte

-------------------------------------------- Excerpt 2 -----------------------------------------------
Mode: 66 (1680x1050)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc000723f
        BytesPerScanline: 1728
        XResolution: 1680
        YResolution: 1050
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 3
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 1728
        BnkNumberOfImagePages: 3
        LinNumberOfImagePages: 3
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
Mode: 67 (1680x1050)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc000723f
        BytesPerScanline: 3392
        XResolution: 1680
        YResolution: 1050
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 3392
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 230000000
*Mode: 68 (1680x1050)
        ModeAttributes: 0x9b
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc000723f
        BytesPerScanline: 6720
        XResolution: 1680
        YResolution: 1050
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xc0000000
        LinBytesPerScanLine: 6720
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 230000000

------------------------------------------- Excerpt 3 -------------------------------------------------
(II) I810(1): LCD: Using default hsync range of 31.50-37.90 kHz
(II) I810(1): LCD: Using default vrefresh range of 50.00-70.00 Hz
(II) I810(1): Not using mode "1680x1050" (no mode of this name)
(--) I810(1): Virtual size is 640x480 (pitch 640)
(**) I810(1):  Built-in mode "640x480"
(II) I810(1): Attempting to use 60.00Hz refresh for mode "640x480" (850)

---

### Post by veloce on 2007-02-22
The symptoms suggest that you don't have 915resolution installed.  

If you do, try running

sudo 915resolution -l

and see if your desired resolution is listed.

---

### Post by lenorin on 2007-02-22
This is the print out for sudo resolution -l (it was installed). The mode that I need is the last one.

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 400x772, 8 bits/pixel
Mode 61 : 400x772, 16 bits/pixel
Mode 62 : 400x772, 32 bits/pixel
Mode 63 : 512x771, 8 bits/pixel
Mode 64 : 512x771, 16 bits/pixel
Mode 65 : 512x771, 32 bits/pixel
Mode 66 : 1680x1050, 8 bits/pixel
Mode 67 : 1680x1050, 16 bits/pixel
Mode 68 : 1680x1050, 32 bits/pixel

---

### Post by veloce on 2007-02-22
I'm clutching at straws now, but two ideas:

Does your driver have enough memory to display 1680x1050 in 24 bit depth?  If it can't, for some reason, it won't drop back the depth but the resolution.  You could test this by setting the default depth to 16 rather than 24.  The fix might be to specify the memory available for the driver.

The other thing, even more speculative, would be to specify the mode by number (68) rather than by descriptor ("1680x1050") in the screen section.

---

### Post by lenorin on 2007-02-24
Tried the latter, then won't load. Tried the former, and it couldn't find the bus for some reason. However, let's approach this theoretically. Consider this print out from the Xorg.0.log:

 480 (II) I810(0): Lowest common panel size for pipe B is 1680 x 1050
 481 (==) I810(0): Primary head is using Pipe B
 482 (--) I810(0): Maximum frambuffer space: 98136 kByte
 483 (II) I810(0): VESA VBE PanelID read successfully
 484 (II) I810(0): PanelID returned panel resolution : 1680x1050
 485 (II) Loading sub module "ddc"
 486 (II) LoadModule: "ddc"
 487 (II) Reloading /usr/lib/xorg/modules/libddc.so
 488 (II) I810(0): VESA VBE DDC supported
 489 (II) I810(0): VESA VBE DDC Level 2
 490 (II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
 491 (II) I810(0): VESA VBE DDC read failed
 492 (--) I810(0): A non-CRT device is attached to pipe B.
 493         No refresh rate overrides will be attempted.
 494 (--) I810(0): Maximum space available for video modes: 12288 kByte

1680*1050*4 bytes per pixel = 7056000 bytes = 7056KB. Is that the max video mem for modes on both screens or just one? Because if that's total, then I can't do two screens, but if that's per screen then I'm ok. 

--
Lenorin

P.S. Anyone know why setting the depth down to 16 from 24 will cause X server to crash? Says can't find the correct pipe.

---

### Post by lenorin on 2007-02-25
But then again, sorry another thought hit me. I can run the two screens at 1680x1050 on Windows, so there shouldn't be much reason why I can't run it on linux like that. Perhaps the aove max memory number is simply for one pipe. There has to be a way to get it to recognize the mode.

---

### Post by veloce on 2007-02-25
I just noticed that you don't have an  "option monitorlayout" line in your second device section. This could be causing the "correct pipe" error, and may also be why X can't work out what resolution to use.  I would copy this line from your first to second device section and see what happens. 

Other ideas to try if that doesn't work:

You can also specify the memory available to the card as an option line.  This **might** help.

Another thing to try would be to add  the horizontal synch and vertical refresh rates for your monitors.

Lastly, sometimes gnome gets itself confused by remembering stuff about the screen layout.  I had to delete the following directory:  ~/.gconf/desktop/gnome/screen (where ~ is your home directory) and restart X.

---

### Post by tobiasG on 2007-02-27
Hi,
I have the same problem.The option monitorlayout in the second devide section doesn't help unfortunately . Also I tried specifying refresh rates without success. 

I suspect one should interpret the line "Not using mode "1680x1050" (no mode of this name)" as such and work from there on.

In my case I have to set both modes with 915resolution (1280x800 and 1680x1050)  which is a bit puzzling since X11 correctly identifies the first afterwards but not the latter. 

My second monitor displays  1280x1024 but only if it is plugged in when starting the system (otherwise its blank and the first monitor shows a real weird ghostly green when restarting X and X aborts)

System is an FSC amilo Si 1520 laptop with an intel i945GM graphics chip and a samsung BW205b (1680x1050) attached as second screen.

I too would appreciate any help on this issue.

---

### Post by veloce on 2007-02-28
Not sure if any of this will help:

> **tobiasG said:**
> 
In my case I have to set both modes with 915resolution (1280x800 and 1680x1050)  which is a bit puzzling since X11 correctly identifies the first afterwards but not the latter. 


I haven't tried setting two modes with 915resolution, is that working correctly?  (That it, they both show up in the output of 915resolution -l)

> **tobiasG said:**
> 
My second monitor displays  1280x1024 but only if it is plugged in when starting the system (otherwise its blank and the first monitor shows a real weird ghostly green when restarting X and X aborts)


Is 915resolution using the "space" for 1280x1024 when it doesn't detect your second monitor? Again 915resolution -l after starting up without the second monitor connected.

---

### Post by tobiasG on 2007-03-01
Hi,

yes both modes show up in the output of 915resolution -l :
Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel
Mode 60 : 1680x1050, 8 bits/pixel
Mode 61 : 1680x1050, 24 bits/pixel
Mode 62 : 1680x1050, 32 bits/pixel

The 1280x800 is set during boot up with 915 resolution's config file and 1680x1050 manually afterwards.

I don't really understand what you mean with "space for 1280x1024". I set the 1680x1050 resolution to a mode number (mode number == space?) shown as previously unoccupied by xorg.log, i.e. to mode number 61.

According to your signature you seem to have a system running quite similar to mine. How did you do it? Did you need 915resolution ? Are both your monitors running with their native resolution?

Thank you for helping

---

### Post by tobiasG on 2007-03-07
I have found the solution: If I patch the first mode reported as  (0x0) in Xorg.log with 915resolution, in my case Mode: 38 (0x0), it works. First I tried the last one. Curiously X11 still reports this mode as 0x0 but correctly uses 1680x1050 now. 

To make this permanent I added the line 
	    $PROG 38 1680 1050 24
just below the line which takes my 1280x800 from the config
	    $PROG $MODE $XRESO $YRESO $BIT
in /etc/init.d/915resolution
(yes this could be done more elegant but it works :)

For the record: The version of X11 is 7.1.1 on Edgy Eft 6.10

915resolution -l lists now:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1680x1050, 24 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1680x1050, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1680x1050, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

---

### Post by veloce on 2007-03-07
So in your xorg.conf file you refer to mode 38 now?  

This problem and solution appear so bizarre.  What could possibly be the difference between mode 38 and 58?  As far as I know 24 bit and 32 bit are treated exactly the same - perhaps they aren't?

I was very interested to see how you patched the two resolutions.  That may come in handy.

Sorry I couldn't be more help.

---

### Post by tobiasG on 2007-03-08
> **veloce said:**
> So in your xorg.conf file you refer to mode 38 now?  


no, I didn't change the modes in xorg.conf. There they are refered by the resolution e.g.

Section "Screen"
        Identifier      "samsung"
        Device          "Intel Corporation Mobile Integrated Graphics Controller external_screen"
        Monitor         "samsung BW205b"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           32
                Modes           "1680x1050"
        EndSubSection
EndSection

---

### Post by sluggoh on 2008-07-15
Hi, I also have an Amilo 1520 that I want to connect a monitor to. My setup would then be:
[LIST]
[*]Laptop screen - 1280x800
[*]Philips brilliance 200P - 1600x1200
[/LIST]

Is it possible to make this work without using the 915resolution (which I read was obsolete thanks to the new i810 driver from Intel)?

Thanks,
Tomas

---

