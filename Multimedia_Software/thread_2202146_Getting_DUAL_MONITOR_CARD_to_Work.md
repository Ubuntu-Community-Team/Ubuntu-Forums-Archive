---
title: "Getting DUAL MONITOR CARD to Work"
date: 2014-01-27
forum: Multimedia Software
---

### Post by Rick St. George on 2014-01-27
Hello again,

Problem - I'm trying to get my dual monitor card to work in Xubuntu v13.10. Have two VGA Flat Screen monitors, and the main one works. The second one is in Power Save Mode and doesn't want to respond. 

System - custom build with 1Gb Ram, about a 2Ghz chip, plenty HD space.

Video Card - ATI Radeon 7000 64MB AGP with DVI & TV out

#2 monitor is hooked up to TV out via S-Video cable to a VGA adapter cable/plug into the monitor.

Going to Settings Manager / Display, it sees both monitors. #1 at 1280 X 1024 and to the Right #2 at 800 X 600. Use this Output is checked in both. But nothing will show on the monitor.

Any ideas?

Thanks
Rick

---

### Post by Rick St. George on 2014-01-27
Forgot to add, Printout of lshw -C video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: RV100 [Radeon 7000 / Radeon VE]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:16 memory:d8000000-dfffffff ioport:9000(size=256) memory:e1000000-e100ffff memory:e0000000-e001ffff
--------------------------------------


Would this work?
From: [http://ubuntuforums.org/showthread.php?t=2194601&highlight=dual+monitor](http://ubuntuforums.org/showthread.php?t=2194601&highlight=dual+monitor)
```

sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update 
sudo apt-get install fglrx
sudo amdcccle

```

???

---

### Post by Rick St. George on 2014-01-27
H E L P ! ! !

I tried the above and now my screen has blue lines and can not login!

Any Suggestions? How do I get my computer back???

Thanks!
Rick

---

### Post by magicman1223 on 2014-01-31
Alright so I take no responsibility for anything that happens to your box. However, this is what I would do. At your login screen with blue lines take a picture with you phone and upload it to the forums, I am curious what it looks like. Then at the login screen you are currently at hit ctrl+alt+f2 , this will put you at the console (black backround white text). Login with your username and password. You must know your username for this to work btw. Then run the following post the results, I will try to respond back as soon as i can should be less then 8 hours.


```
lspci | grep VGA
lshw -C video
```

Notice the caps !

---

### Post by Rick St. George on 2014-02-11
OK ... I re-installed with v12.04, upgraded online to v12.10, then v13.10 Xubuntu.
Back to where I was before. Sorry magicman - hitting combo of keys did nothing, wherefore I had to re-install the OS.

See my first post above - thats where I am at. When I click to activate the second monitor, it overlays the background pic over my no.1 monitor!
No.2 monitor never shows anything. That was in v12.10, now in v13.10 it no longer does that. However, No. 2 monitor still doesn't respond even
though it is checked. I am stumped with this Radeo ATI 7000 64MB card with TV out via Svideo ! ! !
I have the Svideo cable going to a 3-way plug going into the monitor.

Any suggestions?
Rick

---

### Post by Rick St. George on 2014-02-13
Does this help.... Printout;

```


stephen@linus4us:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      75.0*    60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        59.9*+
stephen@linus4us:~$ xrandr --output S-video --set "tv standard" ntsc
stephen@linus4us:~$ dmesg | egrep 'drm|radeon'
[   15.760086] [drm] Initialized drm 1.1.0 20060810
[   16.785883] [drm] radeon kernel modesetting enabled.
[   16.847682] [drm] initializing kernel modesetting (RV100 0x1002:0x5159 0x1002:0x053A).
[   16.847718] [drm] register mmio base: 0xE1000000
[   16.847721] [drm] register mmio size: 65536
[   16.850633] radeon 0000:01:00.0: putting AGP V2 device into 4x mode
[   16.850643] radeon 0000:01:00.0: GTT: 128M 0xD0000000 - 0xD7FFFFFF
[   16.850653] radeon 0000:01:00.0: VRAM: 128M 0x00000000D8000000 - 0x00000000DFFFFFFF (64M used)
[   16.850951] [drm] Detected VRAM RAM=128M, BAR=128M
[   16.850956] [drm] RAM width 64bits DDR
[   16.874090] [drm] radeon: 64M of VRAM memory ready
[   16.874094] [drm] radeon: 128M of GTT memory ready.
[   17.018530] radeon 0000:01:00.0: WB disabled
[   17.018545] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x00000000d0000000 and cpu addr 0xf840e000
[   17.018551] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   17.018554] [drm] Driver supports precise vblank timestamp query.
[   17.022731] [drm] radeon: irq initialized.
[   17.022763] [drm] Loading R100 Microcode
[   17.090483] [drm] radeon: ring at 0x00000000D0001000
[   17.090513] [drm] ring test succeeded in 1 usecs
[   17.090782] [drm] ib test succeeded in 0 usecs
[   17.139515] [drm] No TV DAC info found in BIOS
[   17.139642] [drm] Radeon Display Connectors
[   17.139647] [drm] Connector 0:
[   17.139650] [drm]   VGA-1
[   17.139653] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   17.139655] [drm]   Encoders:
[   17.139657] [drm]     CRT1: INTERNAL_DAC1
[   17.139659] [drm] Connector 1:
[   17.139661] [drm]   DVI-D-1
[   17.139663] [drm]   HPD1
[   17.139666] [drm]   DDC: 0x64 0x64 0x64 0x64 0x64 0x64 0x64 0x64
[   17.139668] [drm]   Encoders:
[   17.139669] [drm]     DFP1: INTERNAL_TMDS1
[   17.139671] [drm] Connector 2:
[   17.139673] [drm]   SVIDEO-1
[   17.139675] [drm]   Encoders:
[   17.139677] [drm]     TV1: INTERNAL_DAC2
[   17.305969] [drm] fb mappable at 0xD8040000
[   17.305976] [drm] vram apper at 0xD8000000
[   17.305978] [drm] size 5242880
[   17.305981] [drm] fb depth is 24
[   17.305983] [drm]    pitch is 5120
[   17.308939] fbcon: radeondrmfb (fb0) is primary device
[   17.469867] [drm] crtc 1 is connected to a TV
[   18.152337] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   18.152339] radeon 0000:01:00.0: registered panic notifier
[   18.422794] [drm] Initialized radeon 2.34.0 20080528 for 0000:01:00.0 on minor 0
[   23.987269] [drm] crtc 1 is connected to a TV
[ 1561.428680] [drm] crtc 1 is connected to a TV
[ 1669.482797] [drm] crtc 1 is connected to a TV

```

Seems it is showing a connection, but still nothing on the VGA no.2 monitor?!?!?

---

### Post by Rick St. George on 2014-04-11
Guess Not ! ! !

---

### Post by Rick St. George on 2014-10-28
Bought another Dual Monitor card and started another thread. 
This issue is still unsolved, but closing this thread.

Thanks for everyones help!
Rick

---

