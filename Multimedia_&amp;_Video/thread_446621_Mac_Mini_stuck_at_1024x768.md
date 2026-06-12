---
title: "Mac Mini stuck at 1024x768"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by vhex on 2007-05-17
Hello.  I've installed Ubuntu 7.04 on an Intel Mac Mini (after installing BootCamp) with BenQ FP71G+ LCD monitor attached to it, and I can only use three resolutions: 1024x768, 800x600 and 640x480. I've been using 1280x1024 on Mac OS X. I've read the forums and tried different tricks with 915resolution (the settings don't survive a reboot), I removed everything but 1280x1024 from xorg.conf, but nothing helps. I'm not very experienced with configuring Xorg, so could somebody please help me figure this out. I've just tried a 19" CRT monitor and nothing changes.

lspci detects my video adapter as:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
```

Related /var/log/Xorg.0.log entries:
```
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
        i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
        915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
...
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
...
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 16064 kB
(II) I810(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 945GM
(--) I810(0): Chipset: "945GM"
(--) I810(0): Linear framebuffer at 0x80000000
(--) I810(0): IO registers at addr 0x90380000
(II) I810(0): 2 display pipes available.
(II) I810(0): detected 16124 kB stolen memory.
(II) I810(0): Kernel reported 232960 total, 1 used
(II) I810(0): I830CheckAvailableMemory: 931836 kB available
(II) I810(0): Will try to reserve 32768 kiB of AGP aperture space
        for the DRM memory manager.
(II) I810(0): Monitoring connected displays enabled
(--) I810(0): Pre-allocated VideoRAM: 16124 kByte
(==) I810(0): VideoRAM: 65536 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 1284
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
              If you encounter this problem please add 
                 Option "DisplayInfo" "FALSE"
              to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: TRUE, present: TRUE, size: (720,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: DFP (digital flat panel): attached: TRUE, present: TRUE, size: (1280,1024)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,1287)
(II) I810(0): Display Info: Second (second CRT): attached: FALSE, present: FALSE, size: (0,1287)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,1287)
(II) I810(0): Display Info: DFP2 (second digital flat panel): attached: FALSE, present: FALSE, size: (0,1287)
(II) I810(0): Display Info: LFP2 (second local flat panel): attached: FALSE, present: FALSE, size: (0,1287)
(II) I810(0): Size of device DFP (digital flat panel) is 1280 x 1024
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0):   CRT
(II) I810(0):   DFP (digital flat panel)
(II) I810(0): Lowest common panel size for pipe A is 1280 x 1024
(II) I810(0): No active displays on Pipe B.
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 65368 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: BNQ  Model: 7688  Serial#: 20058
(II) I810(0): Year: 2006  Week: 28
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate  Composite
(II) I810(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) I810(0): Gamma: 2.20
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
(II) I810(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@67Hz
(II) I810(0): 640x480@72Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@72Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 832x624@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@70Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): 1152x870@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) I810(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) I810(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) I810(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) I810(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) I810(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) I810(0): Monitor name: BenQ FP71G
(II) I810(0): EDID (in hex):
(II) I810(0):   00ffffffffffff0009d188765a4e0000
(II) I810(0):   1c1001036c221b78eac4f6a3574a9c23
(II) I810(0):   114f54bdef80714f81908180818c0101
(II) I810(0):   010101010101302a009851002a403070
(II) I810(0):   1300782d1100001ed50980a0205e6310
(II) I810(0):   10605208782d1100001a000000fd0038
(II) I810(0):   4c1f530e000a202020202020000000fc
(II) I810(0):   0042656e512046503731470a2020002e
(II) I810(0): Using hsync ranges from config file
(II) I810(0): Using vrefresh ranges from config file
(II) I810(0): Printing DDC gathered Modelines:
(II) I810(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) I810(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) I810(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) I810(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) I810(0): Monitor name: BenQ FP71G
(II) I810(0): EDID (in hex):
(II) I810(0):   00ffffffffffff0009d188765a4e0000
(II) I810(0):   1c1001036c221b78eac4f6a3574a9c23
(II) I810(0):   114f54bdef80714f81908180818c0101
(II) I810(0):   010101010101302a009851002a403070
(II) I810(0):   1300782d1100001ed50980a0205e6310
(II) I810(0):   10605208782d1100001a000000fd0038
(II) I810(0):   4c1f530e000a202020202020000000fc
(II) I810(0):   0042656e512046503731470a2020002e
(II) I810(0): Using hsync ranges from config file
(II) I810(0): Using vrefresh ranges from config file
(II) I810(0): Printing DDC gathered Modelines:

```

My xorg.conf contains this:
```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "BenQ FP71G+"
        Option          "DPMS"
        ModeLine "1280x1024" 108 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "BenQ FP71G+"
        Option "UseEdidFreqs" "True"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection
```

---

### Post by vhex on 2007-05-17
Problem solved by:

```
sudo apt-get install xserver-xorg-video-intel
```

I wonder why it used i810 out of the box.

Thank you everybody. ;)

---

