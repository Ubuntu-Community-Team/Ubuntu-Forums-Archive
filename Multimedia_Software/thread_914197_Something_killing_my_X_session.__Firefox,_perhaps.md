---
title: "Something killing my X session.  Firefox, perhaps?"
date: 2008-09-08
forum: Multimedia Software
---

### Post by walkeraj on 2008-09-08
I've been having a problem on my work desktop for awhile now.  Periodically, I will be running firefox and it suddenly disappears along with window decorations.  Other windows remain.  Often, the x-server will re-initialize window decorations, then crash, kicking me back to GDM.  When I log in again, it invariably pops up a dialog that says:

```
Internal Error
failed to initialize HAL!
```

 The system has the following relevant specs:

Model: Dell Precision 490
CPU: 4x Intel Xeon5110 @ 1.60GHz
Graphics: nVidia Corporation NV44 [Quadro NVS 285] (rev a1)
Monitors:
- Dell 2007FP 1600x1200
- Dell 2005FWP 1680x1050

This system has the latest nonfree nVidia driver, and is running these two monitors in "TwinView" configuration.

Attached is a bzip tarball of some (hopefully) relevant information from /var/log/messages.  The raw text exceeds upload limits for the forum, but some highlights are as follows (note: I have replaced the timestamp and hostname with "..." to save horizontal space):

```
... kernel: [430837.193448] Xorg invoked oom-killer: gfp_mask=0x2d0, order=0, oomkilladj=0
... kernel: [430837.193458] Pid: 6186, comm: Xorg Tainted: P        2.6.24-19-generic #1
... kernel: [430837.193484]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
... kernel: [430837.193514]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
... kernel: [430837.193538]  [agpgart:__alloc_pages+0x36c/0x3a0] __alloc_pages+0x36c/0x3a0
... kernel: [430837.193547]  [apic_timer_interrupt+0x28/0x30] apic_timer_interrupt+0x28/0x30
... kernel: [430837.193556]  [nvidia:kunmap_atomic+0x3d/0x2f30] kunmap_atomic+0x3d/0xb0
... kernel: [430837.193581]  [ext3:__get_free_pages+0x37/0x820] __get_free_pages+0x37/0x50
... kernel: [430837.193619]  [<f97102f9>] nv_vm_malloc_pages+0x109/0x310 [nvidia]
... kernel: [430837.193840]  [<f9711e73>] nv_alloc_pages+0x243/0x400 [nvidia]
... kernel: [430837.194041]  [<f9673070>] _nv003885rm+0x3b/0x3f [nvidia]
... kernel: [430837.194262]  [<f96022c0>] _nv005711rm+0x31/0x170 [nvidia]
... kernel: [430837.194474]  [<f95d6730>] _nv004246rm+0x8a9/0xa84 [nvidia]
... kernel: [430837.194708]  [<f961a4a4>] _nv002789rm+0x993/0x2298 [nvidia]
... kernel: [430837.194954]  [<f9614938>] _nv005015rm+0x65/0xee [nvidia]
... kernel: [430837.195175]  [<f94dc73c>] _nv002878rm+0x1cc/0x5fd [nvidia]
... kernel: [430837.195378]  [<f9679b47>] rm_ioctl+0x3e/0x6d [nvidia]
... kernel: [430837.195597]  [<f9712b47>] nv_kern_ioctl+0x117/0x3b0 [nvidia]
... kernel: [430837.195797]  [remove_vma+0x41/0x50] remove_vma+0x41/0x50
... kernel: [430837.195819]  [<f9712e18>] nv_kern_unlocked_ioctl+0x18/0x20 [nvidia]
... kernel: [430837.195999]  [<f9712e00>] nv_kern_unlocked_ioctl+0x0/0x20 [nvidia]
... kernel: [430837.196165]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
... kernel: [430837.196190]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
... kernel: [430837.196207]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
... kernel: [430837.196222]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
... kernel: [430837.196256]  =======================
... kernel: [430837.196260] Mem-info:
... kernel: [430837.196263] DMA per-cpu:
... kernel: [430837.196268] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
... kernel: [430837.196274] CPU    1: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
... kernel: [430837.196279] CPU    2: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
... kernel: [430837.196284] CPU    3: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
... kernel: [430837.196288] Normal per-cpu:
... kernel: [430837.196293] CPU    0: Hot: hi:  186, btch:  31 usd: 162   Cold: hi:   62, btch:  15 usd:  55
... kernel: [430837.196298] CPU    1: Hot: hi:  186, btch:  31 usd: 135   Cold: hi:   62, btch:  15 usd:  60
... kernel: [430837.196304] CPU    2: Hot: hi:  186, btch:  31 usd:  86   Cold: hi:   62, btch:  15 usd:  48
... kernel: [430837.196309] CPU    3: Hot: hi:  186, btch:  31 usd: 146   Cold: hi:   62, btch:  15 usd:  55
... kernel: [430837.196313] HighMem per-cpu:
... kernel: [430837.196315] CPU    0: Hot: hi:  186, btch:  31 usd: 170   Cold: hi:   62, btch:  15 usd:  11
... kernel: [430837.196318] CPU    1: Hot: hi:  186, btch:  31 usd:  49   Cold: hi:   62, btch:  15 usd:   9
... kernel: [430837.196321] CPU    2: Hot: hi:  186, btch:  31 usd:  60   Cold: hi:   62, btch:  15 usd:   5
... kernel: [430837.196325] CPU    3: Hot: hi:  186, btch:  31 usd: 173   Cold: hi:   62, btch:  15 usd:   9
... kernel: [430837.196329] Active:375022 inactive:201127 dirty:26 writeback:55 unstable:0
... kernel: [430837.196330]  free:30100 slab:11726 mapped:326538 pagetables:1265 bounce:0
... kernel: [430837.196335] DMA free:3536kB min:68kB low:84kB high:100kB active:0kB inactive:0kB present:16256kB pages_scanned:0 all_unreclaimable? yes
... kernel: [430837.196340] lowmem_reserve[]: 0 873 4048 4048
... kernel: [430837.196353] Normal free:3732kB min:3744kB low:4680kB high:5616kB active:0kB inactive:152kB present:894080kB pages_scanned:287 all_unreclaimable? yes
... kernel: [430837.196357] lowmem_reserve[]: 0 0 25400 25400
... kernel: [430837.196369] HighMem free:113132kB min:512kB low:3916kB high:7324kB active:1500112kB inactive:804356kB present:3251200kB pages_scanned:0 all_unreclaimable? no
... kernel: [430837.196374] lowmem_reserve[]: 0 0 0 0
... kernel: [430837.196382] DMA: 0*4kB 0*8kB 1*16kB 0*32kB 1*64kB 1*128kB 1*256kB 0*512kB 1*1024kB 1*2048kB 0*4096kB = 3536kB
... kernel: [430837.196405] Normal: 256*4kB 20*8kB 2*16kB 2*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 3776kB
... kernel: [430837.196426] HighMem: 207*4kB 169*8kB 42*16kB 6*32kB 62*64kB 384*128kB 114*256kB 28*512kB 9*1024kB 2*2048kB 0*4096kB = 112996kB
... kernel: [430837.196450] Swap cache: add 5168, delete 2910, find 1782/2064, race 0+0
... kernel: [430837.196453] Free swap  = 9844180kB
... kernel: [430837.196456] Total swap = 9855836kB
... kernel: [430837.196460] Free swap:       9844180kB
... kernel: [430837.209763] 1048576 pages of RAM
... kernel: [430837.209770] 819200 pages of HIGHMEM
... kernel: [430837.209772] 409238 reserved pages
... kernel: [430837.209777] 497798 pages shared
... kernel: [430837.209778] 2258 pages swap cached
... kernel: [430837.209780] 26 pages dirty
... kernel: [430837.209782] 55 pages writeback
... kernel: [430837.209786] 326538 pages mapped
... kernel: [430837.209788] 11726 pages slab
... kernel: [430837.209791] 1265 pages pagetables

```

This repeats a few times, and is followed by:

```

... kernel: [430852.027551] NVRM: VM: nv_vm_malloc_pages: failed to allocate a page
... pulseaudio[31697]: pid.c: Stale PID file, overwriting.
... kernel: [430877.708262] end_request: I/O error, dev fd0, sector 0
... kernel: [430877.730750] end_request: I/O error, dev fd0, sector 0
... kernel: [430878.484331] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430878.484364] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430911.676349] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430911.676485] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430911.677739] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430911.677849] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430931.654630] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430931.654663] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430931.656178] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [430931.656205] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431016.683613] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431016.683765] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431016.685142] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431016.685257] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431183.781814] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431183.781849] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431183.783208] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431183.783234] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431256.594151] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431256.594308] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431256.595775] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431256.595894] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431285.827330] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431285.827360] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431285.828907] VMBlock warning: DentryOpRevalidate: invalid args from kernel
... kernel: [431285.828933] VMBlock warning: DentryOpRevalidate: invalid args from kernel

```

So, it definitely appears to be a problem with the video card.  Any ideas?  Any help resolving this would be *greatly* appreciated, as it is causing me to lose valuable work each time it occurs.

---

### Post by walkeraj on 2008-09-09
Okay, since no one had any ideas, I set out on my own.  Tried the official nvidia drivers, which I ran as root.

```
NVIDIA-Linux-x86-173.14.12-pkg1.run
```

was nice enough to me, but nothing worked after that.  The Nvidia logo would appear and disappear a few times during bootup at which point GDM would tell me that my displays couldn't be detected.

So, I tried out Envy.  Now my x server starts up and twinview works fine, but compiz doesn't work.  Attempts to enable desktop effects tell me the composite extension isn't available, only it IS enabled in my xorg.conf:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 1400 0
    Screen      1  "Screen1" LeftOf "Screen0"
EndSection

Section "Module"
    Load           "glx"
    Load           "GLcore"
    Load           "v4l"
EndSection

Section "ServerFlags"

# Removed Option "Xinerama" "true"
    Option         "Xinerama" "1"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Dell"
    ModelName      "Dell 2007FP (Digital)"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Unknown"
    ModelName      "DELL 2005FPW"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 2007FP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:8:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:8:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
    BusID          "PCI:8:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 285"
    BusID          "PCI:8:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "800x600@72" "800x600@75" "800x600@56" "800x600@60" "640x480@75" "832x624@75" "640x480@72" "1024x768@75" "640x480@60" "1024x768@70" "1024x768@60" "1152x864@75" "1280x1024@75" "1280x960@60" "1280x1024@60" "1280x960@75" "1400x1050@60" "1400x1050@75" "1600x1200@65" "1600x1200@60" "1792x1344@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: 1400x1050@60 +0+0; DFP-1: 1280x960@75 +0+0; DFP-1: 1280x1024@60 +0+0; DFP-1: 1280x960@60 +0+0; DFP-1: 1280x1024@75 +0+0; DFP-1: 1152x864@75 +0+0; DFP-1: 1024x768@60 +0+0; DFP-1: 1024x768@70 +0+0; DFP-1: 1024x768@75 +0+0; DFP-1: 832x624@75 +0+0; DFP-1: 800x600@60 +0+0; DFP-1: 800x600@75 +0+0; DFP-1: 800x600@72 +0+0; DFP-1: 800x600@56 +0+0; DFP-1: 640x480@75 +0+0; DFP-1: 640x480@72 +0+0; DFP-1: 640x480@60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1600x1200 +0+0; DFP-0: 800x600@72 +0+0; DFP-0: 800x600@75 +0+0; DFP-0: 800x600@56 +0+0; DFP-0: 800x600@60 +0+0; DFP-0: 640x480@75 +0+0; DFP-0: 832x624@75 +0+0; DFP-0: 640x480@72 +0+0; DFP-0: 1024x768@75 +0+0; DFP-0: 640x480@60 +0+0; DFP-0: 1024x768@70 +0+0; DFP-0: 1024x768@60 +0+0; DFP-0: 1152x864@75 +0+0; DFP-0: 1280x1024@75 +0+0; DFP-0: 1280x960@60 +0+0; DFP-0: 1280x1024@60 +0+0; DFP-0: 1280x960@75 +0+0; DFP-0: 1400x1050@60 +0+0; DFP-0: 800x600 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

So I tried installing xserver-xgl.  This enabled compositing, but I could no longer run nvidia-settings.

So.  What can I do to get this working again?

---

### Post by walkeraj on 2008-09-09
UPDATE: So, I was looking at the configuration file there, and I noticed something was a little squirrely.  Twinview had seemed to be working, but I guess it had gotten turned off somehow.  So, I told nvidia-settings to re-enable it, and now suddenly compiz works.  I can't entirely explain that, does anyone know what happened?  Was it because it was running them as two separate x sessions?

---

