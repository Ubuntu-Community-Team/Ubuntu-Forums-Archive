---
title: "ati driver issue"
date: 2006-03-16
forum: Multimedia &amp; Video
---

### Post by rachii on 2006-03-16
i have followed various how-to's from the forums, and other video sites, and have had the same problem with the 8.16.20, and 8.23.7 drivers in breezy. 

first i have no errors while installing or compiling any packages or the drivers.  my video card is a radeon 8500 so it should be supported by the drivers, and it worked in hoary.

i continually get errors similiar to this, although it usually says BadValue, and something about XFree86:```
X Error of failed request:  BadColor (invalid Colormap parameter)
  Major opcode of failed request:  1 (X_CreateWindow)
  Resource id in failed request:  0x2c
  Serial number of failed request:  17
  Current serial number in output stream:  20

```

i have also recieved this error:```

...Loading libFL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Error couldn't open the X display
...Warning: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Error couldn't open the X display
...Warning: could not set the given mode (3)

Sys_Error: GLimp_Init() - could not load OpenGL subsystem 
```

when i do fglrxinfo i get:```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 8500 DDR Generic
OpenGL version string: 1.3.1050 (X4.3.0-8.23.7)

```

and dmesg after i run into errors reveals:```
[4386449.388000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4389820.646000] mtrr: no MTRR for d0000000,400000 found
[4389820.646000] mtrr: no MTRR for d0400000,200000 found
[4389820.646000] mtrr: no MTRR for d0600000,100000 found
[4389820.646000] mtrr: no MTRR for d0700000,1000 found
[4389823.164000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4389823.164000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4389823.164000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4389823.165000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4389823.165000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[4389823.165000] agpgart: Putting AGP V2 device at 0000:02:00.0 into 4x mode
[4389823.165000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4389823.222000] [fglrx] free  AGP = 256126976
[4389823.222000] [fglrx] max   AGP = 256126976
[4389823.222000] [fglrx] free  LFB = 116387840
[4389823.222000] [fglrx] max   LFB = 116387840
[4389823.222000] [fglrx] free  Inv = 0
[4389823.222000] [fglrx] max   Inv = 0
[4389823.222000] [fglrx] total Inv = 0
[4389823.222000] [fglrx] total TIM = 0
[4389823.222000] [fglrx] total FB  = 0
[4389823.222000] [fglrx] total AGP = 65536
[4403267.169000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).

```

fglrxinfo seems correct...and glxgears and fgl_glxgears work, im not sure as to what the problem could be?  any thoughts comments or suggestions greatly appreciated
thanks

---

