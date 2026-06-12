---
title: "Lubuntu 14.04 multiple video cards?"
date: 2014-05-01
forum: Multimedia Software
---

### Post by Don_Tai on 2014-05-01
I have a fresh install of Lubuntu 14.04 on a Asus P4B533 desktop, Intel P4 1.8Ghz processor. I am trying to have dual monitors using two separate video cards: an Nvidia Riva tnt2 and an ATI/AMD 3D Rage 2 Mach64. The nouveau driver (automatically installed) works well for the NVidia card. The xserver-xorg-video-mach64 driver (automatically installed) also works well for the ATI card. Installed in the computer separately both cards work well by themselves. Installed together the computer displays the NVidia card for the lxde desktop. The ATI card displays the default lxde background and nothing else.

I can see lubuntu detects both cards. Both cards are detected and display correctly in the System Tools > System Profiler as valid VGA compatible controllers. An lshw says the Nvidia card has detected correctly but the ATI card shows "display UNCLAIMED". An xrandr  also shows the Nvidia card but not the ATI card.

I believe that ubuntu cannot have 2 video cards in one computer, but want confirmation.

[http://ubuntuforums.org/showthread.php?t=2192417](http://ubuntuforums.org/showthread.php?t=2192417) says "Ubuntu is limited to 1 desktop per GPU". Two video cards would be 2 GPUs?
[https://wiki.debian.org/XStrikeForce/HowToRandR12](https://wiki.debian.org/XStrikeForce/HowToRandR12) says multi-board support is broken

Is there anything else I can do to get my two video cards to work? I realize I can go buy a dual head video card that uses 1 GPU, but as this is an old computer I'd rather not.

Thanks for any help. I am enjoying the numerous hours of research needed to tweak Lubuntu 14.04!

$ sudo lshw -C video

```
  *-display               
       description: VGA compatible controller
       product: NV5 [Vanta / Vanta LT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 15
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:16 memory:f4000000-f4ffffff memory:f6000000-f7ffffff memory:f5ff0000-f5ffffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Mach64 GTB [3D Rage II+ DVD]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 9a
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master
       configuration: latency=32 mingnt=8
       resources: memory:f2000000-f2ffffff ioport:b400(size=256) memory:f1800000-f1800fff memory:f5ee0000-f5efffff

```

$ xrandr
```

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2048 x 2048
VGA-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1 

```

---

