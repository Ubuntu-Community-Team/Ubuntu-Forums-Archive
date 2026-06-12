---
title: "mupen64plus crashes (intel chipset)"
date: 2009-09-10
forum: Multimedia Software
---

### Post by ViMMeD on 2009-09-10
Hey, I'm using the mupen64plus emulator for the n64 and am trying to get Zelda OoT to work.  The only issue I'm having is when I push the Start key, no matter what key I set it to, the application crashes.  Apart from that, the framerate and textures are all as they should be.  The following is the terminal output.

```
evan@evan-laptop:~$ mupen64plus
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Version 1.5

Config Dir:  /home/evan/.mupen64plus/
Install Dir: /usr/local/share/mupen64plus/
Plugin Dir:  /usr/local/share/mupen64plus/plugins/

Rescanning rom cache.
Scanning... /home/evan/Desktop/n64 roms/
Rom cache up to date. 3 ROMs.
Compression: Uncompressed
Imagetype: .v64 (byteswapped)
Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
MD5: 5BD1FE107BF8106B2AB6650ABECD54D6
80 37 12 40
ClockRate = f
Version: 1449
CRC: ec7011b7 7616d72b
Name: THE LEGEND OF ZELDA
Manufacturer: 43000000
Cartridge_ID: 4c5a
Country: USA
PC = 80000400
EEPROM type: 0
init timer!
[blight's SDL input plugin]: version 0.0.10 initialized.
memory initialized
fb_clear 1 fb_smart 1
extensions 'CHROMARANGE TEXCHROMA TEXMIRROR PALETTE6666 FOGCOORD EVOODOO TEXTUREBUFFER TEXFMT'
fb_hires
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
get fences failed: -1
param: 6, val: 0
packed pixels extension used
NPOT extension used
use_fbo 0
f 1 z 7.7486e-06
f 2 z 7.62939e-06
f 4 z 7.39098e-06
f 8 z 6.91414e-06
f 16 z 5.96046e-06
f 32 z 4.05312e-06
f 64 z 2.38419e-07
f 128 z 7.39098e-06
f 256 z 2.26498e-05
f 512 z 5.31673e-05
f 1024 z 0.000114202
f 2048 z 0.000236273
f 4096 z 0.000480413
f 8192 z 0.000968695
f 16384 z 0.00194526
f 32768 z 0.00389838
f 65536 z 0.00780463
 --> bias factor 64
num_tmu 2
bebefore
bebefore2
before
after
tbuf_size 2Mb
[JttL's SDL Audio plugin] version 1.5 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
copyteximage 1024x1024 fmt 8049 old 0x0 oldfmt 1
mupen64plus: intel_tex_image.c:355: intelTexImage: Assertion `texImage->RowStride == postConvWidth' failed.
Aborted
```

The lines: "mupen64plus: intel_tex_image.c:355: intelTexImage: Assertion `texImage->RowStride == postConvWidth' failed.
Aborted" only appear after a push the start key, then it crashes.

```
Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
2.6.28-15-generic
```

I have read over the intel fix for Jaunty which only aids in decreasing the framerate substantially, and still doesn't fix the issue.  Any help would be appreciated.

---

