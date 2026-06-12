---
title: "Resolution problem with i915 (Dell 630m)"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by terrax on 2006-09-17
Hello

I got kind of a problem. I cannot choose resolution 800x600 or 640x480, with my intel gma 900 gfx card.

Though everything works ok. I can use aixgl with compiz and everything. 
I used 915resolution to get the 1280x800 resolution.
But I need the lower resolutions also. I get thiese errors in the Xorg.0.log:

This is the first strange part i get:

```

(WW) I810(0): config file hsync range 45.7143-50.5263kHz not within DDC hsync ranges.
(II) I810(0): Dell 630m: Using hsync range of 45.71-50.53 kHz
(II) I810(0): Dell 630m: Using vrefresh value of 60.00 Hz
(II) I810(0): Not using mode "800x600" (no mode of this name)
(II) I810(0): Not using mode "640x480" (no mode of this name)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x800 (pitch 2048)
(**) I810(0): *Built-in mode "1280x800"
(**) I810(0): *Built-in mode "1024x768"

```

Which I think thats why I can't use resolutions other than 1280x800 and 1024x768.

Now to some errors I don't understand:

```

(WW) module minor version (0) is less than the required minor version (1)

(WW) I810(0): Bad V_BIOS checksum

(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
        (Cannot allocate memory)
(II) I810(0): Allocated 32 kB for the logical context at 0xffe2000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1600 pages failed
        (Cannot allocate memory)
(II) I810(0): Allocated 6400 kB for the back buffer at 0xf000000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1600 pages failed
        (Cannot allocate memory)
(II) I810(0): Allocated 6400 kB for the depth buffer at 0xe800000.
(WW) I810(0): xf86AllocateGARTMemory: allocation of 26368 pages failed
        (Cannot allocate memory)
(II) I810(0): Allocated 105472 kB for textures at 0x8100000
(WW) I810(0): xf86AllocateGARTMemory: allocation of 1121 pages failed
        (Cannot allocate memory)

(WW) I810(0): Extended BIOS function 0x5f05 failed.


```

But glxinfo don't come with any errors, and DRI and direct rendering are enabled???

This is my xorg.conf part:

```

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        131072
EndSection

```

If you wonder why I want my resolution down. I can tell I get this error, by running (win) bomberman with wine:

```

err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x18c570) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18bcf0)->(0x10024,00000011)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x18bcf0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

And I think this:

```

err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)

```

Has to do why I can't start the game. I really need to play the win version of bomberman, because we use it on the university in network play :-)

Thx for your help.

---

### Post by terrax on 2006-09-18
Anyone, which can comfirm their i810 driver with a intel gma 900 works proberly?

---

### Post by terrax on 2006-09-18
ok, can anyone tell me, which package the i810 driver contains in?

---

### Post by terrax on 2006-09-19
bump

---

