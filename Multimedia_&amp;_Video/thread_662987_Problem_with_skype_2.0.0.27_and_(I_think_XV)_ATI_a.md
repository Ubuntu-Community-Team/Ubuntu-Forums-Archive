---
title: "Problem with skype 2.0.0.27 and (I think XV) ATI and Creative Optia"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by MadeR on 2008-01-09
I have the following problems:
1) colors show by the webcam are really wrong: I am shown in turquoise and my partner is green/violet;
2) when I start "my video", I see me only in the small box; but as soon as someone shows me his/her video, I see him/her both in the small picture and the big one
2.b) or if i start my video after the partner started his/hers, I see Myself both in the small and in the big box.
3) sometimes I can see (for a fraction of a second) the picture of the person not currently shown - the partner if I am in both boxes, me if my partner is shown in both boxes - in both boxes, of course!

Any ideas?

I am using kubuntu gutsy gibbon.

[img]http://www.massimilianodellarovere.eu/bildoj/ceterajxoj/skype_problem.png[/img]


**fglrxinfo**
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6473 (8.37.6)

```


**xvinfo**
```

X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon AVIVO Video"
    number of ports: 4
    port base: 115
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
      depth 24, visualID 0x33
      depth 24, visualID 0x34
      depth 24, visualID 0x35
      depth 24, visualID 0x36
      depth 24, visualID 0x37
      depth 24, visualID 0x38
      depth 24, visualID 0x39
      depth 24, visualID 0x3a
      depth 24, visualID 0x3b
      depth 24, visualID 0x3c
      depth 24, visualID 0x3d
      depth 24, visualID 0x3e
      depth 24, visualID 0x3f
      depth 24, visualID 0x40
      depth 24, visualID 0x41
      depth 24, visualID 0x42
      depth 24, visualID 0x43
      depth 24, visualID 0x44
      depth 24, visualID 0x45
      depth 24, visualID 0x46
      depth 24, visualID 0x47
      depth 24, visualID 0x48
      depth 24, visualID 0x49
      depth 24, visualID 0x4a
      depth 24, visualID 0x4b
      depth 24, visualID 0x4c
      depth 24, visualID 0x4d
      depth 24, visualID 0x4e
      depth 24, visualID 0x4f
      depth 24, visualID 0x50
      depth 24, visualID 0x51
      depth 24, visualID 0x52
      depth 24, visualID 0x53
      depth 24, visualID 0x54
      depth 24, visualID 0x55
      depth 24, visualID 0x56
      depth 24, visualID 0x57
      depth 24, visualID 0x58
      depth 24, visualID 0x59
      depth 24, visualID 0x5a
      depth 24, visualID 0x5b
      depth 24, visualID 0x5c
      depth 24, visualID 0x5d
      depth 24, visualID 0x5e
      depth 24, visualID 0x5f
      depth 24, visualID 0x60
      depth 24, visualID 0x61
      depth 24, visualID 0x62
    number of attributes: 13
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLENDING_MODE" (range 0 to 1)
              client settable attribute
              client gettable attribute
      "XV_CLEAR_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute
      "XV_OFFSCREEN_RENDER" (range 0 to 1)
              client settable attribute
              client gettable attribute
    maximum XvImage size: 4096 x 4096
    Number of image formats: 2
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)

```

**xdpyinfo**
```
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10300000
X.Org version: 1.3.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
supported pixmap formats:
    depth 1, bits_per_pixel 1, scanline_pad 32
    depth 4, bits_per_pixel 8, scanline_pad 32
    depth 8, bits_per_pixel 8, scanline_pad 32
    depth 15, bits_per_pixel 16, scanline_pad 32
    depth 16, bits_per_pixel 16, scanline_pad 32
    depth 24, bits_per_pixel 32, scanline_pad 32
    depth 32, bits_per_pixel 32, scanline_pad 32
keycode range:    minimum 8, maximum 255
focus:  window 0x5400007, revert to PointerRoot
number of extensions:    36
    ATIFGLEXTENSION
    ATIFGLRXDRI
    ATITVOUT
    BIG-REQUESTS
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RECORD
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XAccessControlExtension
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XINERAMA
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
    glesx
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1280x1024 pixels (340x270 millimeters)
  resolution:    96x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x79
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0xfa4031
    KeyPressMask             EnterWindowMask          LeaveWindowMask
    KeymapStateMask          StructureNotifyMask      SubstructureNotifyMask
    SubstructureRedirectMask FocusChangeMask          PropertyChangeMask
    ColormapChangeMask
  number of visuals:    64
  default visual id:  0x23
  visual:
    visual id:    0x23
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x24
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x25
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x26
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x27
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x28
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x29
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x30
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x31
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x32
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x33
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x34
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x35
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x36
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x37
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x38
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x39
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3a
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3b
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3c
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3d
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3e
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x3f
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x40
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x41
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x42
    class:    TrueColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x43
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x44
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x45
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x46
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x47
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x48
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x49
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x50
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x51
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x52
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x53
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x54
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x55
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x56
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x57
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x58
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x59
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5a
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5b
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x5f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x60
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x61
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x62
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits

```

**uname -a**
```
Linux silmarillion 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux
```

**dmesg**
```


[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007fff0000 (usable)
[    0.000000]  BIOS-e820: 000000007fff0000 - 000000007fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff3000 - 0000000080000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f59e0
[    0.000000] Entering add_active_range(0, 0, 524272) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524272
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524272
[    0.000000] On node 0 totalpages: 524272
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292593 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F74C0 checksum 0
[    0.000000] ACPI: RSDP 000F74C0, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 7FFF3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FFF30C0, 3DB6 (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FFF0000, 0040
[    0.000000] ACPI: APIC 7FFF6E80, 0068 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 520177
[    0.000000] Kernel command line: root=UUID=ebeaf16e-17f9-4ff1-bdfa-002cec4d4557 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3007.134 MHz processor.
[   25.627094] Console: colour VGA+ 80x25
[   25.627384] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.627708] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.721697] Memory: 2067584k/2097088k available (2015k kernel code, 28184k reserved, 916k data, 364k init, 1179584k highmem)
[   25.721706] virtual kernel memory layout:
[   25.721708]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.721709]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.721710]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.721711]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.721712]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.721713]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
[   25.721714]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
[   25.721717] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.721756] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   25.801651] Calibrating delay using timer specific routine.. 6018.28 BogoMIPS (lpj=12036572)
[   25.801676] Security Framework v1.0.0 initialized
[   25.801681] SELinux:  Disabled at boot.
[   25.801694] Mount-cache hash table entries: 512
[   25.801815] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[   25.801824] monitor/mwait feature present.
[   25.801826] using mwait in idle threads.
[   25.801831] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   25.801834] CPU: L2 cache: 1024K
[   25.801836] CPU: Physical Processor ID: 0
[   25.801838] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000
[   25.801848] Compat vDSO mapped to ffffe000.
[   25.801863] Checking 'hlt' instruction... OK.
[   25.817722] SMP alternatives: switching to UP code
[   25.818154] Early unpacking initramfs... done
[   26.097766] ACPI: Core revision 20070126
[   26.097811] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.101294] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   26.101311] SMP alternatives: switching to SMP code
[   26.101400] Booting processor 1/1 eip 3000
[   26.111491] Initializing CPU#1
[   26.189035] Calibrating delay using timer specific routine.. 6014.08 BogoMIPS (lpj=12028169)
[   26.189044] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[   26.189051] monitor/mwait feature present.
[   26.189057] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   26.189059] CPU: L2 cache: 1024K
[   26.189062] CPU: Physical Processor ID: 0
[   26.189064] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000
[   26.189334] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   26.189375] Total of 2 processors activated (12032.37 BogoMIPS).
[   26.189501] ENABLING IO-APIC IRQs
[   26.189677] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   26.336904] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   26.356888] Brought up 2 CPUs
[   26.451796] migration_cost=81
[   26.451954] Booting paravirtualized kernel on bare hardware
[   26.452021] Time: 15:48:51  Date: 00/09/108
[   26.452044] NET: Registered protocol family 16
[   26.452131] EISA bus registered
[   26.452136] ACPI: bus type pci registered
[   26.475918] PCI: PCI BIOS revision 2.10 entry at 0xfbb10, last bus=2
[   26.475921] PCI: Using configuration type 1
[   26.475923] Setting up standard PCI resources
[   26.486176] ACPI: EC: Look up EC in DSDT
[   26.489808] ACPI: Interpreter enabled
[   26.489811] ACPI: (supports S0 S1 S4 S5)
[   26.489831] ACPI: Using IOAPIC for interrupt routing
[   26.494958] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.494964] PCI: Probing PCI hardware (bus 00)
[   26.495414] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   26.495418] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   26.496005] PCI: Transparent bridge - 0000:00:1e.0
[   26.496033] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.496151] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   26.502707] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   26.502815] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   26.502918] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   26.503020] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   26.503123] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   26.503226] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   26.503328] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[   26.503430] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 9 10 11 *12 14 15)
[   26.503537] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.503548] pnp: PnP ACPI init
[   26.503558] ACPI: bus type pnp registered
[   26.506367] pnp: PnP ACPI: found 13 devices
[   26.506370] ACPI: ACPI bus type pnp unregistered
[   26.506374] PnPBIOS: Disabled by ACPI PNP
[   26.506434] PCI: Using ACPI for IRQ routing
[   26.506437] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.523227] NET: Registered protocol family 8
[   26.523230] NET: Registered protocol family 20
[   26.523308] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
[   26.523315] pnp: 00:0c: iomem range 0xcf400-0xcffff has been reserved
[   26.523318] pnp: 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   26.523321] pnp: 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   26.523324] pnp: 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   26.524521] Time: tsc clocksource has been installed.
[   26.553644] PCI: Bridge: 0000:00:01.0
[   26.553648]   IO window: 9000-9fff
[   26.553653]   MEM window: d0000000-efffffff
[   26.553657]   PREFETCH window: 88000000-880fffff
[   26.553663] PCI: Bridge: 0000:00:1e.0
[   26.553666]   IO window: a000-afff
[   26.553671]   MEM window: f0000000-f1ffffff
[   26.553675]   PREFETCH window: 88100000-881fffff
[   26.553692] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   26.553703] NET: Registered protocol family 2
[   26.592591] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.592662] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   26.593503] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.593751] TCP: Hash tables configured (established 131072 bind 65536)
[   26.593754] TCP reno registered
[   26.604750] checking if image is initramfs... it is
[   27.051984] Switched to high resolution mode on CPU 1
[   27.055866] Switched to high resolution mode on CPU 0
[   27.156304] Freeing initrd memory: 7063k freed
[   27.156637] audit: initializing netlink socket (disabled)
[   27.156651] audit(1199893731.184:1): initialized
[   27.156763] highmem bounce pool size: 64 pages
[   27.159093] VFS: Disk quotas dquot_6.5.1
[   27.159153] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.159250] io scheduler noop registered
[   27.159253] io scheduler anticipatory registered
[   27.159255] io scheduler deadline registered
[   27.159270] io scheduler cfq registered (default)
[   27.159356] Boot video device is 0000:01:00.0
[   27.159532] isapnp: Scanning for PnP cards...
[   27.510639] isapnp: No Plug & Play device found
[   27.537226] Real Time Clock Driver v1.12ac
[   27.537326] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.537408] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.537544] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.538120] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.538357] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   27.539172] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.539397] input: Macintosh mouse button emulation as /class/input/input0
[   27.539484] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   27.539487] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   27.790827] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.790975] mice: PS/2 mouse device common for all mice
[   27.791103] EISA: Probing bus 0 at eisa.0
[   27.791142] EISA: Detected 0 cards.
[   27.791214] TCP cubic registered
[   27.791225] NET: Registered protocol family 1
[   27.791246] Using IPI No-Shortcut mode
[   27.791390]   Magic number: 8:23:841
[   27.791491]   hash matches device ptyu7
[   27.791503]   hash matches device ptyra
[   27.791719] Freeing unused kernel memory: 364k freed
[   27.834150] input: AT Translated Set 2 keyboard as /class/input/input1
[   29.002882] AppArmor: AppArmor initialized<5>audit(1199893732.684:2):  type=1505 info="AppArmor initialized" pid=1198
[   29.011509] fuse init (API version 7.8)
[   29.016668] Failure registering capabilities with primary security module.
[   29.024690] ACPI: Fan [FAN] (on)
[   29.030925] ACPI: Unable to turn cooling device [df802180] 'on'
[   29.030931] ACPI: Thermal Zone [THRM] (70 C)
[   29.547333] usbcore: registered new interface driver usbfs
[   29.547366] usbcore: registered new interface driver hub
[   29.547400] usbcore: registered new device driver usb
[   29.548701] USB Universal Host Controller Interface driver v3.0
[   29.548782] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   29.548798] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   29.548805] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   29.548956] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   29.548991] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bc00
[   29.549167] usb usb1: configuration #1 chosen from 1 choice
[   29.549208] hub 1-0:1.0: USB hub found
[   29.549219] hub 1-0:1.0: 2 ports detected
[   29.651704] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   29.651719] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   29.651724] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   29.651758] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   29.651786] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000b000
[   29.651914] usb usb2: configuration #1 chosen from 1 choice
[   29.651961] hub 2-0:1.0: USB hub found
[   29.651969] hub 2-0:1.0: 2 ports detected
[   29.672991] SCSI subsystem initialized
[   29.681537] libata version 2.21 loaded.
[   29.718776] Floppy drive(s): fd0 is 1.44M
[   29.755489] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   29.755505] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   29.755511] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   29.755544] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   29.755577] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b400
[   29.755721] usb usb3: configuration #1 chosen from 1 choice
[   29.755763] hub 3-0:1.0: USB hub found
[   29.755772] hub 3-0:1.0: 2 ports detected
[   29.770525] FDC 0 is a post-1991 82077
[   29.859337] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   29.859353] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   29.859359] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   29.859392] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   29.859417] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000b800
[   29.859555] usb usb4: configuration #1 chosen from 1 choice
[   29.859602] hub 4-0:1.0: USB hub found
[   29.859611] hub 4-0:1.0: 2 ports detected
[   29.891148] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   29.963304] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 19
[   29.963345] skge 1.11 addr 0xf1020000 irq 19 chip Yukon-Lite rev 9
[   29.963491] skge eth0: addr 00:0a:48:18:57:b1
[   29.964537] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   29.964555] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   29.964561] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   29.964613] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   29.964659] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   29.964674] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf2000000
[   30.006992] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.007160] usb usb5: configuration #1 chosen from 1 choice
[   30.007205] hub 5-0:1.0: USB hub found
[   30.007216] hub 5-0:1.0: 8 ports detected
[   30.113717] ata_piix 0000:00:1f.1: version 2.11
[   30.113734] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   30.113771] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   30.113863] scsi0 : ata_piix
[   30.113932] scsi1 : ata_piix
[   30.114113] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   30.114119] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   30.282878] ata1.00: Host Protected Area detected:
[   30.282880]  current size: 120101087 sectors
[   30.282881]  native size: 120103200 sectors
[   30.302582] ata1.00: native size increased to 120103200 sectors
[   30.302586] ata1.00: ATA-7: Maxtor 6Y060L0, YAR41VW0, max UDMA/133
[   30.302589] ata1.00: 120103200 sectors, multi 16: LBA
[   30.302760] ata1.01: Host Protected Area detected:
[   30.302762]  current size: 240115519 sectors
[   30.302763]  native size: 240121728 sectors
[   30.335472] ata1.01: native size increased to 240121728 sectors
[   30.335475] ata1.01: ATA-7: Maxtor 6Y120P0, YAR41BW0, max UDMA/133
[   30.335478] ata1.01: 240121728 sectors, multi 16: LBA
[   30.350772] ata1.00: configured for UDMA/133
[   30.366741] ata1.01: configured for UDMA/133
[   30.414332] usb 1-1: device not accepting address 2, error -71
[   30.686065] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A106, max UDMA/33
[   30.861786] ata2.00: configured for UDMA/33
[   30.861907] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y060L0   YAR4 PQ: 0 ANSI: 5
[   30.862060] scsi 0:0:1:0: Direct-Access     ATA      Maxtor 6Y120P0   YAR4 PQ: 0 ANSI: 5
[   30.866305] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A106 PQ: 0 ANSI: 5
[   30.866376] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
[   30.866396] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   30.866437] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   30.866489] scsi2 : ata_piix
[   30.866545] scsi3 : ata_piix
[   30.866672] ata3: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001c402 bmdma 0x0001d000 irq 18
[   30.866677] ata4: SATA max UDMA/133 cmd 0x0001c800 ctl 0x0001cc02 bmdma 0x0001d008 irq 18
[   31.030541] ata3.00: ATA-7: Maxtor 7V300F0, VA111900, max UDMA/133
[   31.030545] ata3.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   31.046499] ata3.00: configured for UDMA/133
[   31.211284] scsi 2:0:0:0: Direct-Access     ATA      Maxtor 7V300F0   VA11 PQ: 0 ANSI: 5
[   31.227936] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[   31.227956] sd 0:0:0:0: [sda] Write Protect is off
[   31.227959] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.227980] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.228041] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors (61493 MB)
[   31.228053] sd 0:0:0:0: [sda] Write Protect is off
[   31.228056] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   31.228075] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.228079]  sda: sda1 sda2 < sda5 sda6<6>usb 5-2: new high speed USB device using ehci_hcd and address 3
[   31.288195]  sda7 sda8 >
[   31.299479] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.299557] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   31.299575] sd 0:0:1:0: [sdb] Write Protect is off
[   31.299580] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   31.299609] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.299676] sd 0:0:1:0: [sdb] 240121728 512-byte hardware sectors (122942 MB)
[   31.299694] sd 0:0:1:0: [sdb] Write Protect is off
[   31.299698] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   31.299727] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.299734]  sdb: sdb1 sdb2 sdb3
[   31.321520] sd 0:0:1:0: [sdb] Attached SCSI disk
[   31.321592] sd 2:0:0:0: [sdc] 586114704 512-byte hardware sectors (300091 MB)
[   31.321609] sd 2:0:0:0: [sdc] Write Protect is off
[   31.321614] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   31.321642] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.321702] sd 2:0:0:0: [sdc] 586114704 512-byte hardware sectors (300091 MB)
[   31.321718] sd 2:0:0:0: [sdc] Write Protect is off
[   31.321722] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   31.321754] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   31.321759]  sdc:sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.325755] Uniform CD-ROM driver Revision: 3.20
[   31.325798] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   31.340651]  sdc1 < sdc5 sdc6 sdc7 sdc8 >
[   31.381431] sd 2:0:0:0: [sdc] Attached SCSI disk
[   31.387967] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.388000] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   31.388029] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   31.388057] sd 2:0:0:0: Attached scsi generic sg3 type 0
[   31.702314] usb 5-2: configuration #1 chosen from 1 choice
[   31.888874] Attempting manual resume
[   31.888879] swsusp: Resume From Partition 8:8
[   31.888882] PM: Checking swsusp image.
[   31.899007] PM: Resume from disk failed.
[   31.932941] kjournald starting.  Commit interval 5 seconds
[   31.932954] EXT3-fs: mounted filesystem with ordered data mode.
[   32.395226] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   32.574638] usb 1-1: configuration #1 chosen from 1 choice
[   32.834453] usb 2-1: new low speed USB device using uhci_hcd and address 2
[   33.012056] usb 2-1: configuration #1 chosen from 1 choice
[   33.309712] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   33.498422] usb 3-2: configuration #1 chosen from 1 choice
[   35.019150] ACPI: Unable to turn cooling device [df802180] 'on'
[   38.647920] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   38.674474] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.030870] Linux agpgart interface v0.102 (c) Dave Jones
[   39.087777] agpgart: Detected an Intel 865 Chipset.
[   39.098292] agpgart: AGP aperture is 256M @ 0xc0000000
[   39.106389] intel_rng: FWH not detected
[   39.216218] iTCO_vendor_support: vendor-support=0
[   39.308323] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   39.308409] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   39.308449] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   39.699460] input: PC Speaker as /class/input/input2
[   39.728124] Linux video capture interface: v2.00
[   39.772504] parport_pc 00:09: reported by Plug and Play ACPI
[   39.772597] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   40.231502] usbcore: registered new interface driver hiddev
[   40.244008] input: Cypress Sem PS2/USB Browser Combo Mouse as /class/input/input3
[   40.244102] input: USB HID v1.00 Mouse [Cypress Sem PS2/USB Browser Combo Mouse] on usb-0000:00:1d.0-1
[   40.259218] input: Microsoft Comfort Optical Mouse 1000 as /class/input/input4
[   40.259314] input: USB HID v1.11 Mouse [Microsoft Comfort Optical Mouse 1000] on usb-0000:00:1d.1-1
[   40.259336] usbcore: registered new interface driver usbhid
[   40.259341] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.263175] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7004
[   40.263197] usbcore: registered new interface driver usblp
[   40.263205] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[   40.346149] uvcvideo: Adding mapping Brightness to control 00000000-0000-0000-0000-000000000101/2.
[   40.346157] uvcvideo: Adding mapping Contrast to control 00000000-0000-0000-0000-000000000101/3.
[   40.346163] uvcvideo: Adding mapping Hue to control 00000000-0000-0000-0000-000000000101/6.
[   40.346169] uvcvideo: Adding mapping Saturation to control 00000000-0000-0000-0000-000000000101/7.
[   40.346176] uvcvideo: Adding mapping Sharpness to control 00000000-0000-0000-0000-000000000101/8.
[   40.346183] uvcvideo: Adding mapping Gamma to control 00000000-0000-0000-0000-000000000101/9.
[   40.346189] uvcvideo: Adding mapping Backlight Compensation to control 00000000-0000-0000-0000-000000000101/1.
[   40.346196] uvcvideo: Adding mapping Gain to control 00000000-0000-0000-0000-000000000101/4.
[   40.346204] uvcvideo: Adding mapping Power Line Frequency to control 00000000-0000-0000-0000-000000000101/5.
[   40.346211] uvcvideo: Adding mapping Hue, Auto to control 00000000-0000-0000-0000-000000000101/16.
[   40.346218] uvcvideo: Adding mapping Pan (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[   40.346225] uvcvideo: Adding mapping Tilt (relative) to control 63610682-5070-49ab-b8cc-b3855e8d2256/1.
[   40.346232] uvcvideo: Adding mapping Pan/Tilt (reset) to control 63610682-5070-49ab-b8cc-b3855e8d2256/2.
[   40.346239] uvcvideo: Adding mapping Exposure, Auto to control 00000000-0000-0000-0000-000000000001/2.
[   40.346246] uvcvideo: Adding mapping Exposure (Absolute) to control 00000000-0000-0000-0000-000000000001/4.
[   40.346254] uvcvideo: Adding mapping White Balance Temperature, Auto to control 00000000-0000-0000-0000-000000000101/11.
[   40.346261] uvcvideo: Adding mapping White Balance Temperature to control 00000000-0000-0000-0000-000000000101/10.
[   40.346314] uvcvideo: Probing known UVC device 2 (041e:4057)
[   40.346325] uvcvideo: Found format MJPEG.
[   40.346329] uvcvideo: - 640x480 (30.0 fps)
[   40.346333] uvcvideo: - 320x240 (30.0 fps)
[   40.346336] uvcvideo: - 160x120 (30.0 fps)
[   40.346339] uvcvideo: - 352x288 (30.0 fps)
[   40.346342] uvcvideo: - 176x144 (30.0 fps)
[   40.346346] uvcvideo: Found format YUV 4:2:2 (YUYV).
[   40.346349] uvcvideo: - 640x480 (30.0 fps)
[   40.346352] uvcvideo: - 320x240 (30.0 fps)
[   40.346355] uvcvideo: - 160x120 (30.0 fps)
[   40.346358] uvcvideo: - 352x288 (30.0 fps)
[   40.346361] uvcvideo: - 176x144 (30.0 fps)
[   40.346369] uvcvideo: Found a Status endpoint (addr 82).
[   40.346373] uvcvideo: Found UVC 1.00 device Live! Cam Optia (041e:4057)
[   40.346381] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/2 to device 2 entity 5
[   40.346387] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/3 to device 2 entity 5
[   40.346393] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/6 to device 2 entity 5
[   40.346399] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/7 to device 2 entity 5
[   40.346406] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/8 to device 2 entity 5
[   40.346412] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/9 to device 2 entity 5
[   40.346418] uvcvideo: Added control 00000000-0000-0000-0000-000000000101/5 to device 2 entity 5
[   40.346425] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/2 to device 2 entity 1
[   40.346440] uvcvideo: Added control 00000000-0000-0000-0000-000000000001/4 to device 2 entity 1
[   40.346446] uvcvideo: Scanning UVC chain: OT 3 <- XU 6 <- PU 5 <- SU 4 <- IT 1
[   40.346455] uvcvideo: Found a valid video chain (1 -> 3).
[   40.392491] saa7130/34: v4l2 driver version 0.2.14 loaded
[   40.392559] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
[   40.392571] saa7133[0]: found at 0000:02:0a.0, rev: 209, irq: 21, latency: 32, mmio: 0xf1026000
[   40.392579] saa7133[0]: subsystem: 11bd:002f, board: Pinnacle PCTV 310i [card=101,autodetected]
[   40.392588] saa7133[0]: board init: gpio is 600e000
[   40.426856] uvcvideo: UVC device initialized.
[   40.426881] usbcore: registered new interface driver uvcvideo
[   40.426886] USB Video Class driver (v0.1.0)
[   40.502328] input: Pinnacle PCTV as /class/input/input5
[   40.502379] ir-kbd-i2c: Pinnacle PCTV detected at i2c-0/0-0047/ir0 [saa7133[0]]
[   40.542126] saa7133[0]: i2c eeprom 00: bd 11 2f 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   40.542144] saa7133[0]: i2c eeprom 10: ff e0 60 06 ff 20 ff ff 00 30 8d 2e 39 35 ff ff
[   40.542161] saa7133[0]: i2c eeprom 20: 01 2c 01 23 23 01 04 30 98 ff 00 e7 ff 21 00 c2
[   40.542179] saa7133[0]: i2c eeprom 30: 96 10 03 32 15 20 ff 15 0e 6c a3 eb 03 c7 81 35
[   40.542197] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.542214] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.542232] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.542248] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   40.733836] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   40.781748] tuner 0-004b: setting tuner address to 61
[   40.821685] tuner 0-004b: type set to tda8290+75a
[   41.009577] ACPI: Unable to turn cooling device [df802180] 'on'
[   42.195491] tuner 0-004b: setting tuner address to 61
[   42.235433] tuner 0-004b: type set to tda8290+75a
[   43.568827] saa7133[0]: registered device video1 [v4l2]
[   43.568858] saa7133[0]: registered device vbi0
[   43.568884] saa7133[0]: registered device radio0
[   43.641233] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   43.641262] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   43.657207] saa7134 ALSA driver for DMA sound loaded
[   43.657247] saa7133[0]/alsa: saa7133[0] at 0xf1026000 irq 21 registered as card -2
[   43.887028] DVB: registering new adapter (saa7133[0]).
[   43.887037] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   43.956685] tda1004x: setting up plls for 48MHz sampling clock
[   43.964665] intel8x0_measure_ac97_clock: measured 54611 usecs
[   43.964670] intel8x0: clocking to 48000
[   44.300416] lp0: using parport0 (interrupt-driven).
[   44.339637] ndiswrapper version 1.45 loaded (smp=yes)
[   44.418222] ndiswrapper: driver gplus (D-Link,04/09/2004,6.0.0.18) loaded
[   44.418415] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 22 (level, low) -> IRQ 23
[   45.001228] ndiswrapper: using IRQ 23
[   45.236289] wlan0: ethernet device 00:11:95:47:07:6b using NDIS driver: gplus, version: 0x5000200, NDIS version: 0x501, vendor: 'TNET1130', 104C:9066.5.conf
[   45.236447] wlan0: encryption modes supported: WEP; TKIP with WPA
[   45.238658] usbcore: registered new interface driver ndiswrapper
[   45.290458] Adding 1477940k swap on /dev/sda8.  Priority:-1 extents:1 across:1477940k
[   45.714593] EXT3 FS on sda5, internal journal
[   46.205102] tda1004x: timeout waiting for DSP ready
[   46.245023] tda1004x: found firmware revision 0 -- invalid
[   46.245028] tda1004x: trying to boot from eeprom
[   47.000050] ACPI: Unable to turn cooling device [df802180] 'on'
[   48.573311] tda1004x: timeout waiting for DSP ready
[   48.613279] tda1004x: found firmware revision 0 -- invalid
[   48.613282] tda1004x: waiting for firmware upload...
[   52.990492] ACPI: Unable to turn cooling device [df802180] 'on'
[   58.980902] ACPI: Unable to turn cooling device [df802180] 'on'
[   61.217123] tda1004x: found firmware revision 20 -- ok
[   64.971302] ACPI: Unable to turn cooling device [df802180] 'on'
[   70.962956] ACPI: Unable to turn cooling device [df802180] 'on'
[   76.952161] ACPI: Unable to turn cooling device [df802180] 'on'
[   82.942674] ACPI: Unable to turn cooling device [df802180] 'on'
[   88.933051] ACPI: Unable to turn cooling device [df802180] 'on'
[   92.599933] kjournald starting.  Commit interval 5 seconds
[   92.600117] EXT3 FS on sda7, internal journal
[   92.600122] EXT3-fs: mounted filesystem with ordered data mode.
[   92.630637] kjournald starting.  Commit interval 5 seconds
[   92.630803] EXT3 FS on sdc6, internal journal
[   92.630807] EXT3-fs: mounted filesystem with ordered data mode.
[   92.653422] kjournald starting.  Commit interval 5 seconds
[   92.653722] EXT3 FS on sdb3, internal journal
[   92.653727] EXT3-fs: mounted filesystem with ordered data mode.
[   92.676291] kjournald starting.  Commit interval 5 seconds
[   92.676462] EXT3 FS on sdc7, internal journal
[   92.676467] EXT3-fs: mounted filesystem with ordered data mode.
[   92.695327] kjournald starting.  Commit interval 5 seconds
[   92.695510] EXT3 FS on sda6, internal journal
[   92.695514] EXT3-fs: mounted filesystem with ordered data mode.
[   92.716831] kjournald starting.  Commit interval 5 seconds
[   92.717020] EXT3 FS on sdc5, internal journal
[   92.717025] EXT3-fs: mounted filesystem with ordered data mode.
[   92.768976] kjournald starting.  Commit interval 5 seconds
[   92.769170] EXT3 FS on sdc8, internal journal
[   92.769174] EXT3-fs: mounted filesystem with ordered data mode.
[   92.810499] kjournald starting.  Commit interval 5 seconds
[   92.810742] EXT3 FS on sdb1, internal journal
[   92.810746] EXT3-fs: mounted filesystem with ordered data mode.
[   93.812506] No dock devices found.
[   93.932194] input: Power Button (FF) as /class/input/input6
[   93.932225] ACPI: Power Button (FF) [PWRF]
[   93.932284] input: Power Button (CM) as /class/input/input7
[   93.932307] ACPI: Power Button (CM) [PWRB]
[   94.923558] ACPI: Unable to turn cooling device [df802180] 'on'
[   95.598656] ppdev: user-space parallel port driver
[   95.647875] skge eth0: enabling interface
[   96.114924] audit(1199890200.839:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5124 profile="/usr/sbin/cupsd"
[   96.254503] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   96.254509] apm: disabled - APM is not SMP safe.
[   97.442051] skge eth0: Link is up at 100 Mbps, full duplex, flow control both
[   98.073777] Failure registering capabilities with primary security module.
[   98.127460] [fglrx] Maximum main memory to use for locked dma buffers: 1899 MBytes.
[   98.127563] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   98.148416] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   98.440026] Bluetooth: Core ver 2.11
[   98.440547] NET: Registered protocol family 31
[   98.440553] Bluetooth: HCI device and connection manager initialized
[   98.440558] Bluetooth: HCI socket layer initialized
[   98.456233] Bluetooth: L2CAP ver 2.8
[   98.456239] Bluetooth: L2CAP socket layer initialized
[   98.508629] Bluetooth: RFCOMM socket layer initialized
[   98.508978] Bluetooth: RFCOMM TTY layer initialized
[   98.508984] Bluetooth: RFCOMM ver 1.8
[  100.489734] [fglrx] total      GART = 134217728
[  100.489742] [fglrx] free       GART = 118226944
[  100.489747] [fglrx] max single GART = 118226944
[  100.489751] [fglrx] total      LFB  = 268304384
[  100.489754] [fglrx] free       LFB  = 250474496
[  100.489757] [fglrx] max single LFB  = 250474496
[  100.489761] [fglrx] total      Inv  = 268435456
[  100.489764] [fglrx] free       Inv  = 268435456
[  100.489768] [fglrx] max single Inv  = 268435456
[  100.489773] [fglrx] total      TIM  = 0
[  100.913941] ACPI: Unable to turn cooling device [df802180] 'on'
[  102.673013] NET: Registered protocol family 17
[  105.561489] NET: Registered protocol family 10
[  105.562012] lo: Disabled Privacy Extensions
[  105.562555] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  106.904394] ACPI: Unable to turn cooling device [df802180] 'on'
[  112.894778] ACPI: Unable to turn cooling device [df802180] 'on'
[  115.757993] eth0: no IPv6 routers present
[  118.885436] ACPI: Unable to turn cooling device [df802180] 'on'
[  124.875702] ACPI: Unable to turn cooling device [df802180] 'on'
[  130.866121] ACPI: Unable to turn cooling device [df802180] 'on'
[  136.856535] ACPI: Unable to turn cooling device [df802180] 'on'
[  142.846991] ACPI: Unable to turn cooling device [df802180] 'on'
[  148.837423] ACPI: Unable to turn cooling device [df802180] 'on'
[  154.827771] ACPI: Unable to turn cooling device [df802180] 'on'
[  160.818298] ACPI: Unable to turn cooling device [df802180] 'on'
[  163.857230] uvcvideo: Trying format 0x56595559 (YUYV): 32767x32767.
[  163.857237] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[  164.092145] uvcvideo: Trying format 0x56595559 (YUYV): 1x1.
[  164.092152] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[  164.335815] uvcvideo: Control 0x00980904 not found.
[  164.335823] uvcvideo: Control 0x00980905 not found.
[  164.335828] uvcvideo: Control 0x00980906 not found.
[  164.335832] uvcvideo: Control 0x00980907 not found.
[  164.335888] uvcvideo: Control 0x00980908 not found.
[  164.335957] uvcvideo: Control 0x00980909 not found.
[  164.336008] uvcvideo: Control 0x0098090a not found.
[  164.336076] uvcvideo: Control 0x0098090b not found.
[  164.336110] uvcvideo: Control 0x0098090c not found.
[  164.336149] uvcvideo: Control 0x0098090d not found.
[  164.336216] uvcvideo: Control 0x0098090e not found.
[  164.336270] uvcvideo: Control 0x0098090f not found.
[  164.338765] uvcvideo: Control 0x00980911 not found.
[  164.338772] uvcvideo: Control 0x00980912 not found.
[  164.338778] uvcvideo: Control 0x00980913 not found.
[  164.338796] uvcvideo: Control 0x00980914 not found.
[  164.338815] uvcvideo: Control 0x00980915 not found.
[  164.338834] uvcvideo: Control 0x00980916 not found.
[  164.338852] uvcvideo: Control 0x00980917 not found.
[  164.338872] uvcvideo: Control 0x08000000 not found.
[  164.343052] uvcvideo: Control 0x08000003 not found.
[  164.343058] uvcvideo: Control 0x08000004 not found.
[  164.343148] uvcvideo: Control 0x08000005 not found.
[  164.343189] uvcvideo: Control 0x08000006 not found.
[  164.343231] uvcvideo: Control 0x08000007 not found.
[  164.343296] uvcvideo: Control 0x08000008 not found.
[  164.343405] uvcvideo: Control 0x08000009 not found.
[  164.346425] uvcvideo: Control 0x0800000c not found.
[  164.346432] uvcvideo: Control 0x0800000d not found.
[  164.346438] uvcvideo: Control 0x0800000e not found.
[  164.347327] uvcvideo: Trying format 0x59455247 (GREY): 160x120.
[  164.347331] uvcvideo: Unsupported format 0x59455247.
[  164.347354] uvcvideo: Trying format 0x31424752 (RGB1): 160x120.
[  164.347360] uvcvideo: Unsupported format 0x31424752.
[  164.347500] uvcvideo: Trying format 0x4f424752 (RGBO): 160x120.
[  164.347507] uvcvideo: Unsupported format 0x4f424752.
[  164.347647] uvcvideo: Trying format 0x51424752 (RGBQ): 160x120.
[  164.347652] uvcvideo: Unsupported format 0x51424752.
[  164.347665] uvcvideo: Trying format 0x50424752 (RGBP): 160x120.
[  164.347671] uvcvideo: Unsupported format 0x50424752.
[  164.347804] uvcvideo: Trying format 0x52424752 (RGBR): 160x120.
[  164.347810] uvcvideo: Unsupported format 0x52424752.
[  164.348052] uvcvideo: Trying format 0x33424752 (RGB3): 160x120.
[  164.348059] uvcvideo: Unsupported format 0x33424752.
[  164.348276] uvcvideo: Trying format 0x33524742 (BGR3): 160x120.
[  164.348282] uvcvideo: Unsupported format 0x33524742.
[  164.349573] uvcvideo: Trying format 0x34424752 (RGB4): 160x120.
[  164.349577] uvcvideo: Unsupported format 0x34424752.
[  164.350730] uvcvideo: Trying format 0x34524742 (BGR4): 160x120.
[  164.350735] uvcvideo: Unsupported format 0x34524742.
[  164.351115] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[  164.351121] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[  164.586161] uvcvideo: Trying format 0x59565955 (UYVY): 160x120.
[  164.586167] uvcvideo: Unsupported format 0x59565955.
[  164.586174] uvcvideo: Trying format 0x50323234 (422P): 160x120.
[  164.586177] uvcvideo: Unsupported format 0x50323234.
[  164.586252] uvcvideo: Trying format 0x32315559 (YU12): 160x120.
[  164.586259] uvcvideo: Unsupported format 0x32315559.
[  166.808725] ACPI: Unable to turn cooling device [df802180] 'on'
[  172.799087] ACPI: Unable to turn cooling device [df802180] 'on'
[  178.789587] ACPI: Unable to turn cooling device [df802180] 'on'
[  184.779956] ACPI: Unable to turn cooling device [df802180] 'on'
[  190.770406] ACPI: Unable to turn cooling device [df802180] 'on'
[  196.760873] ACPI: Unable to turn cooling device [df802180] 'on'
[  202.751236] ACPI: Unable to turn cooling device [df802180] 'on'
[  208.741663] ACPI: Unable to turn cooling device [df802180] 'on'
[  214.732088] ACPI: Unable to turn cooling device [df802180] 'on'
[  220.722528] ACPI: Unable to turn cooling device [df802180] 'on'
[  226.712949] ACPI: Unable to turn cooling device [df802180] 'on'
[  232.703421] ACPI: Unable to turn cooling device [df802180] 'on'
[  238.693813] ACPI: Unable to turn cooling device [df802180] 'on'
[  244.684323] ACPI: Unable to turn cooling device [df802180] 'on'
[  250.674765] ACPI: Unable to turn cooling device [df802180] 'on'
[  256.665109] ACPI: Unable to turn cooling device [df802180] 'on'
[  262.655541] ACPI: Unable to turn cooling device [df802180] 'on'
[  268.645971] ACPI: Unable to turn cooling device [df802180] 'on'
[  274.636402] ACPI: Unable to turn cooling device [df802180] 'on'
[  280.626838] ACPI: Unable to turn cooling device [df802180] 'on'
[  286.617276] ACPI: Unable to turn cooling device [df802180] 'on'
[  292.607699] ACPI: Unable to turn cooling device [df802180] 'on'
[  298.598127] ACPI: Unable to turn cooling device [df802180] 'on'
[  304.592623] ACPI: Unable to turn cooling device [df802180] 'on'
[  310.583058] ACPI: Unable to turn cooling device [df802180] 'on'
[  316.573418] ACPI: Unable to turn cooling device [df802180] 'on'
[  322.563915] ACPI: Unable to turn cooling device [df802180] 'on'
[  328.554325] ACPI: Unable to turn cooling device [df802180] 'on'
[  334.544779] ACPI: Unable to turn cooling device [df802180] 'on'
[  340.539151] ACPI: Unable to turn cooling device [df802180] 'on'
[  346.529601] ACPI: Unable to turn cooling device [df802180] 'on'
[  352.520019] ACPI: Unable to turn cooling device [df802180] 'on'
[  358.510432] ACPI: Unable to turn cooling device [df802180] 'on'
[  364.500880] ACPI: Unable to turn cooling device [df802180] 'on'
[  370.491333] ACPI: Unable to turn cooling device [df802180] 'on'
[  376.481749] ACPI: Unable to turn cooling device [df802180] 'on'
[  542.013191] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[  542.121004] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[ 1345.104960] audit(1199891454.155:4):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=7661 profile="/usr/sbin/cupsd"
[ 3613.124641] [fglrx] PCIe has already been initialized. Reinitializing ...
[ 3613.147378] [fglrx] total      GART = 134217728
[ 3613.147385] [fglrx] free       GART = 118226944
[ 3613.147390] [fglrx] max single GART = 118226944
[ 3613.147393] [fglrx] total      LFB  = 268304384
[ 3613.147397] [fglrx] free       LFB  = 250474496
[ 3613.147400] [fglrx] max single LFB  = 250474496
[ 3613.147404] [fglrx] total      Inv  = 268435456
[ 3613.147409] [fglrx] free       Inv  = 268435456
[ 3613.147413] [fglrx] max single Inv  = 268435456
[ 3613.147418] [fglrx] total      TIM  = 0
[ 5142.308987] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[ 5142.416826] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[ 5911.284546] uvcvideo: Trying format 0x56595559 (YUYV): 32767x32767.
[ 5911.284555] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 5911.519684] uvcvideo: Trying format 0x56595559 (YUYV): 1x1.
[ 5911.519693] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 5911.762539] uvcvideo: Control 0x00980904 not found.
[ 5911.762547] uvcvideo: Control 0x00980905 not found.
[ 5911.762554] uvcvideo: Control 0x00980906 not found.
[ 5911.762558] uvcvideo: Control 0x00980907 not found.
[ 5911.762562] uvcvideo: Control 0x00980908 not found.
[ 5911.762618] uvcvideo: Control 0x00980909 not found.
[ 5911.762642] uvcvideo: Control 0x0098090a not found.
[ 5911.762683] uvcvideo: Control 0x0098090b not found.
[ 5911.762781] uvcvideo: Control 0x0098090c not found.
[ 5911.762828] uvcvideo: Control 0x0098090d not found.
[ 5911.762858] uvcvideo: Control 0x0098090e not found.
[ 5911.762888] uvcvideo: Control 0x0098090f not found.
[ 5911.765660] uvcvideo: Control 0x00980911 not found.
[ 5911.765666] uvcvideo: Control 0x00980912 not found.
[ 5911.765729] uvcvideo: Control 0x00980913 not found.
[ 5911.765790] uvcvideo: Control 0x00980914 not found.
[ 5911.765883] uvcvideo: Control 0x00980915 not found.
[ 5911.765920] uvcvideo: Control 0x00980916 not found.
[ 5911.765954] uvcvideo: Control 0x00980917 not found.
[ 5911.766023] uvcvideo: Control 0x08000000 not found.
[ 5911.770149] uvcvideo: Control 0x08000003 not found.
[ 5911.770155] uvcvideo: Control 0x08000004 not found.
[ 5911.770169] uvcvideo: Control 0x08000005 not found.
[ 5911.770232] uvcvideo: Control 0x08000006 not found.
[ 5911.770343] uvcvideo: Control 0x08000007 not found.
[ 5911.770465] uvcvideo: Control 0x08000008 not found.
[ 5911.770499] uvcvideo: Control 0x08000009 not found.
[ 5911.774272] uvcvideo: Control 0x0800000c not found.
[ 5911.774280] uvcvideo: Control 0x0800000d not found.
[ 5911.774287] uvcvideo: Control 0x0800000e not found.
[ 5911.774637] uvcvideo: Trying format 0x59455247 (GREY): 160x120.
[ 5911.774644] uvcvideo: Unsupported format 0x59455247.
[ 5911.774717] uvcvideo: Trying format 0x31424752 (RGB1): 160x120.
[ 5911.774724] uvcvideo: Unsupported format 0x31424752.
[ 5911.774768] uvcvideo: Trying format 0x4f424752 (RGBO): 160x120.
[ 5911.774774] uvcvideo: Unsupported format 0x4f424752.
[ 5911.774819] uvcvideo: Trying format 0x51424752 (RGBQ): 160x120.
[ 5911.774825] uvcvideo: Unsupported format 0x51424752.
[ 5911.774833] uvcvideo: Trying format 0x50424752 (RGBP): 160x120.
[ 5911.774839] uvcvideo: Unsupported format 0x50424752.
[ 5911.774847] uvcvideo: Trying format 0x52424752 (RGBR): 160x120.
[ 5911.774877] uvcvideo: Unsupported format 0x52424752.
[ 5911.774885] uvcvideo: Trying format 0x33424752 (RGB3): 160x120.
[ 5911.774890] uvcvideo: Unsupported format 0x33424752.
[ 5911.774898] uvcvideo: Trying format 0x33524742 (BGR3): 160x120.
[ 5911.774903] uvcvideo: Unsupported format 0x33524742.
[ 5911.774911] uvcvideo: Trying format 0x34424752 (RGB4): 160x120.
[ 5911.774916] uvcvideo: Unsupported format 0x34424752.
[ 5911.774923] uvcvideo: Trying format 0x34524742 (BGR4): 160x120.
[ 5911.774929] uvcvideo: Unsupported format 0x34524742.
[ 5911.774936] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[ 5911.774943] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 5912.130177] uvcvideo: Trying format 0x59565955 (UYVY): 160x120.
[ 5912.130182] uvcvideo: Unsupported format 0x59565955.
[ 5912.130190] uvcvideo: Trying format 0x50323234 (422P): 160x120.
[ 5912.130193] uvcvideo: Unsupported format 0x50323234.
[ 5912.130199] uvcvideo: Trying format 0x32315559 (YU12): 160x120.
[ 5912.130204] uvcvideo: Unsupported format 0x32315559.
[ 5991.360377] uvcvideo: Trying format 0x56595559 (YUYV): 32767x32767.
[ 5991.360385] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 5991.595226] uvcvideo: Trying format 0x56595559 (YUYV): 1x1.
[ 5991.595234] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 5991.838776] uvcvideo: Control 0x00980904 not found.
[ 5991.838784] uvcvideo: Control 0x00980905 not found.
[ 5991.838789] uvcvideo: Control 0x00980906 not found.
[ 5991.838793] uvcvideo: Control 0x00980907 not found.
[ 5991.838797] uvcvideo: Control 0x00980908 not found.
[ 5991.838891] uvcvideo: Control 0x00980909 not found.
[ 5991.838927] uvcvideo: Control 0x0098090a not found.
[ 5991.839028] uvcvideo: Control 0x0098090b not found.
[ 5991.839093] uvcvideo: Control 0x0098090c not found.
[ 5991.839156] uvcvideo: Control 0x0098090d not found.
[ 5991.839243] uvcvideo: Control 0x0098090e not found.
[ 5991.839247] uvcvideo: Control 0x0098090f not found.
[ 5991.841299] uvcvideo: Control 0x00980911 not found.
[ 5991.841351] uvcvideo: Control 0x00980912 not found.
[ 5991.841357] uvcvideo: Control 0x00980913 not found.
[ 5991.841361] uvcvideo: Control 0x00980914 not found.
[ 5991.841366] uvcvideo: Control 0x00980915 not found.
[ 5991.841370] uvcvideo: Control 0x00980916 not found.
[ 5991.841375] uvcvideo: Control 0x00980917 not found.
[ 5991.841379] uvcvideo: Control 0x08000000 not found.
[ 5991.847013] uvcvideo: Control 0x08000003 not found.
[ 5991.847019] uvcvideo: Control 0x08000004 not found.
[ 5991.847025] uvcvideo: Control 0x08000005 not found.
[ 5991.847039] uvcvideo: Control 0x08000006 not found.
[ 5991.847097] uvcvideo: Control 0x08000007 not found.
[ 5991.847162] uvcvideo: Control 0x08000008 not found.
[ 5991.847309] uvcvideo: Control 0x08000009 not found.
[ 5991.850629] uvcvideo: Control 0x0800000c not found.
[ 5991.850635] uvcvideo: Control 0x0800000d not found.
[ 5991.850641] uvcvideo: Control 0x0800000e not found.
[ 5991.851053] uvcvideo: Trying format 0x59455247 (GREY): 160x120.
[ 5991.851057] uvcvideo: Unsupported format 0x59455247.
[ 5991.851064] uvcvideo: Trying format 0x31424752 (RGB1): 160x120.
[ 5991.851067] uvcvideo: Unsupported format 0x31424752.
[ 5991.851073] uvcvideo: Trying format 0x4f424752 (RGBO): 160x120.
[ 5991.851077] uvcvideo: Unsupported format 0x4f424752.
[ 5991.851083] uvcvideo: Trying format 0x51424752 (RGBQ): 160x120.
[ 5991.851086] uvcvideo: Unsupported format 0x51424752.
[ 5991.851092] uvcvideo: Trying format 0x50424752 (RGBP): 160x120.
[ 5991.851095] uvcvideo: Unsupported format 0x50424752.
[ 5991.851102] uvcvideo: Trying format 0x52424752 (RGBR): 160x120.
[ 5991.851105] uvcvideo: Unsupported format 0x52424752.
[ 5991.851111] uvcvideo: Trying format 0x33424752 (RGB3): 160x120.
[ 5991.851114] uvcvideo: Unsupported format 0x33424752.
[ 5991.851120] uvcvideo: Trying format 0x33524742 (BGR3): 160x120.
[ 5991.851123] uvcvideo: Unsupported format 0x33524742.
[ 5991.851130] uvcvideo: Trying format 0x34424752 (RGB4): 160x120.
[ 5991.851134] uvcvideo: Unsupported format 0x34424752.
[ 5991.851298] uvcvideo: Trying format 0x34524742 (BGR4): 160x120.
[ 5991.851304] uvcvideo: Unsupported format 0x34524742.
[ 5991.851454] uvcvideo: Trying format 0x56595559 (YUYV): 160x120.
[ 5991.851462] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[ 5992.086503] uvcvideo: Trying format 0x59565955 (UYVY): 160x120.
[ 5992.086509] uvcvideo: Unsupported format 0x59565955.
[ 5992.086516] uvcvideo: Trying format 0x50323234 (422P): 160x120.
[ 5992.086519] uvcvideo: Unsupported format 0x50323234.
[ 5992.086583] uvcvideo: Trying format 0x32315559 (YU12): 160x120.
[ 5992.086590] uvcvideo: Unsupported format 0x32315559.
[ 7077.230303] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[ 7077.338139] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[ 7668.158412] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[ 7668.266231] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[ 8912.438898] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[ 8912.550730] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[13298.113581] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[13298.221413] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[17178.754972] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[17178.862784] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[20001.360982] uvcvideo: Trying format 0x32315559 (YU12): 320x240.
[20001.360989] uvcvideo: Unsupported format 0x32315559.
[20001.360995] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[20001.361000] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[20001.595750] uvcvideo: Setting frame interval to 1/15 (666666).
[20001.987812] uvcvideo: Trying format 0x32315559 (YU12): 320x240.
[20001.987818] uvcvideo: Unsupported format 0x32315559.
[20001.987827] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[20001.987832] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[20002.337403] uvcvideo: Setting frame interval to 1/15 (666666).
[20002.728742] uvcvideo: Trying format 0x32315559 (YU12): 320x240.
[20002.728748] uvcvideo: Unsupported format 0x32315559.
[20002.728756] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[20002.728761] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[20003.078560] uvcvideo: Setting frame interval to 1/15 (666666).
[20003.749327] uvcvideo: Button event (0).
[21078.150398] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[21078.262212] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[21958.813284] uvcvideo: Trying format 0x32315559 (YU12): 320x240.
[21958.813292] uvcvideo: Unsupported format 0x32315559.
[21958.813299] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[21958.813303] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[21959.048384] uvcvideo: Setting frame interval to 1/15 (666666).
[21959.286468] uvcvideo: Trying format 0x32315559 (YU12): 320x240.
[21959.286474] uvcvideo: Unsupported format 0x32315559.
[21959.286482] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[21959.286486] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[21959.521402] uvcvideo: Setting frame interval to 1/15 (666666).
[21959.760707] uvcvideo: Trying format 0x32315559 (YU12): 320x240.
[21959.760714] uvcvideo: Unsupported format 0x32315559.
[21959.766651] uvcvideo: Trying format 0x56595559 (YUYV): 320x240.
[21959.766661] uvcvideo: Using default frame interval 33333.3 us (30.0 fps).
[21960.002023] uvcvideo: Setting frame interval to 1/15 (666666).
[21970.954630] uvcvideo: Setting frame interval to 1/25 (400000).
[23279.565326] uvcvideo: Control 0x00980904 not found.
[23279.565334] uvcvideo: Control 0x00980905 not found.
[23279.565339] uvcvideo: Control 0x00980906 not found.
[23279.565343] uvcvideo: Control 0x00980907 not found.
[23279.565347] uvcvideo: Control 0x00980908 not found.
[23279.565352] uvcvideo: Control 0x00980909 not found.
[23279.565357] uvcvideo: Control 0x0098090a not found.
[23279.565363] uvcvideo: Control 0x0098090b not found.
[23279.565369] uvcvideo: Control 0x0098090c not found.
[23279.565375] uvcvideo: Control 0x0098090d not found.
[23279.565381] uvcvideo: Control 0x0098090e not found.
[23279.565387] uvcvideo: Control 0x0098090f not found.
[23279.567450] uvcvideo: Control 0x00980911 not found.
[23279.567456] uvcvideo: Control 0x00980912 not found.
[23279.567461] uvcvideo: Control 0x00980913 not found.
[23279.567513] uvcvideo: Control 0x00980914 not found.
[23279.567579] uvcvideo: Control 0x00980915 not found.
[23279.567637] uvcvideo: Control 0x00980916 not found.
[23279.567741] uvcvideo: Control 0x00980917 not found.
[23279.567894] uvcvideo: Control 0x08000000 not found.
[23279.571939] uvcvideo: Control 0x08000003 not found.
[23279.571946] uvcvideo: Control 0x08000004 not found.
[23279.571952] uvcvideo: Control 0x08000005 not found.
[23279.571983] uvcvideo: Control 0x08000006 not found.
[23279.572069] uvcvideo: Control 0x08000007 not found.
[23279.572208] uvcvideo: Control 0x08000008 not found.
[23279.572301] uvcvideo: Control 0x08000009 not found.
[23279.575188] uvcvideo: Control 0x0800000c not found.
[23279.575194] uvcvideo: Control 0x0800000d not found.
[23279.575201] uvcvideo: Control 0x0800000e not found.
[23490.992317] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[23491.104123] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0
[24312.655857] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=1
[24312.763688] Pinnacle PCTV: unknown key: key=0x39 raw=0x39 down=0

```

---

### Post by CarpKing on 2008-01-09
The colors issue might be improved by adding options to /etc/modprobe.d/options (for instance "options gspca force_rgb=1" or "options gspca OffRed=-16 OffBlue=16 OffGreen=0 gamma=4").  This assumes your webcam uses the gspca driver.  If it doesn't there's probably a way to do something similar with whatever you use.

---

### Post by MadeR on 2008-01-09
No webcam Creative Optia uses the uvc drivers (it is really plug and play).

---

### Post by CarpKing on 2008-01-09
There is probably still a way to alter its colors.  It may even read options from that same file (you have to specify the module the options go to).  You should look into configuring that module.  How do other webcam apps perform?

---

### Post by MadeR on 2008-01-09
I only have kopete and in the msn protocol it looks fine with proper colors, light and all the stuff.

I can use the v4lctl command to set some of the parameters: can't enter "negative" values for *hue*, and use either Exposition. (see below)
 
That's because the camera is officially supported by the uvc module: [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

**modinfo uvcvideo**
```
filename:       /lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko
license:        GPL
description:    USB Video Class driver
author:         Laurent Pinchart <laurent.pinchart@skynet.be>
srcversion:     31D48A107BD2FAF50C734FD
alias:          usb:v*p*d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0200d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v5986p0100d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v18CDpCAFEd*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v041Ep4057d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v19ABp1000d*dc*dsc*dp*ic0Eisc01ip00*
alias:          usb:v046Dp08C7d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C6d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C5d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C3d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C2d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v046Dp08C1d*dc*dsc*dp*icFFisc01ip00*
alias:          usb:v045Ep00F8d*dc*dsc*dp*ic0Eisc01ip00*
depends:        usbcore,videodev,v4l2-common,v4l1-compat,compat_ioctl32
vermagic:       2.6.22-14-generic SMP mod_unload 586
parm:           trace:uint

```

**v4lctl -c /dev/video0 list**
```
ioctl: VIDIOC_G_STD(std=0x804eaf7bffb3e78 [PAL_H,PAL_I,PAL_D,PAL_D1,PAL_N,PAL_Nc,PAL_60,NTSC_M,NTSC_M_JP,SECAM_B,SECAM_D,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
config: invalid value for input: Television
valid choices for "input": "Camera 1"
config: invalid value for norm: PAL
valid choices for "norm":
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | (null)  | (null)  |
input      | choice | Camera  | Camera  | Camera 1
bright     | int    |      84 |      30 | range is 0 => 100
contrast   | int    |       2 |       2 | range is 0 => 6
color      | int    |       3 |       3 | range is 0 => 8
hue        | int    |       0 |       0 | range is -4 => 4
Gamma      | int    |       2 |       3 | range is 0 => 7
Power Line | choice | 50 Hz   | Disable | Disabled 50 Hz 60 Hz
Sharpness  | int    |      96 |      40 | range is 0 => 96
Exposure,  | int    |       2 |       2 | range is 0 => 0
Exposure ( | int    |     626 |      79 | range is 20 => 5000

```


**v4l-info /dev/video0**
```

### v4l2 device info [/dev/video0] ###
general info
    VIDIOC_QUERYCAP
        driver                  : "uvcvideo"
        card                    : "Live! Cam Optia"
        bus_info                : "0000:00:1d.7"
        version                 : 0.1.0
        capabilities            : 0x4000001 [VIDEO_CAPTURE,STREAMING]

standards

inputs
    VIDIOC_ENUMINPUT(0)
        index                   : 0
        name                    : "Camera 1"
        type                    : CAMERA
        audioset                : 0
        tuner                   : 0
        std                     : 0x0 []
        status                  : 0x0 []

video capture
    VIDIOC_ENUM_FMT(0,VIDEO_CAPTURE)
        index                   : 0
        type                    : VIDEO_CAPTURE
        flags                   : 1
        description             : "MJPEG"
        pixelformat             : 0x47504a4d [MJPG]
    VIDIOC_ENUM_FMT(1,VIDEO_CAPTURE)
        index                   : 1
        type                    : VIDEO_CAPTURE
        flags                   : 0
        description             : "YUV 4:2:2 (YUYV)"
        pixelformat             : 0x56595559 [YUYV]
    VIDIOC_G_FMT(VIDEO_CAPTURE)
        type                    : VIDEO_CAPTURE
        fmt.pix.width           : 320
        fmt.pix.height          : 240
        fmt.pix.pixelformat     : 0x56595559 [YUYV]
        fmt.pix.field           : NONE
        fmt.pix.bytesperline    : 640
        fmt.pix.sizeimage       : 2621440
        fmt.pix.colorspace      : unknown
        fmt.pix.priv            : 0

controls
    VIDIOC_QUERYCTRL(BASE+0)
        id                      : 9963776
        type                    : INTEGER
        name                    : "Brightness"
        minimum                 : 0
        maximum                 : 100
        step                    : 1
        default_value           : 30
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+1)
        id                      : 9963777
        type                    : INTEGER
        name                    : "Contrast"
        minimum                 : 0
        maximum                 : 6
        step                    : 1
        default_value           : 2
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+2)
        id                      : 9963778
        type                    : INTEGER
        name                    : "Saturation"
        minimum                 : 0
        maximum                 : 8
        step                    : 1
        default_value           : 3
        flags                   : 0
    VIDIOC_QUERYCTRL(BASE+3)
        id                      : 9963779
        type                    : INTEGER
        name                    : "Hue"
        minimum                 : -4
        maximum                 : 4
        step                    : 1
        default_value           : 0
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+1)
        id                      : 134217729
        type                    : MENU
        name                    : "Power Line Frequency"
        minimum                 : 0
        maximum                 : 2
        step                    : 1
        default_value           : 0
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+2)
        id                      : 134217730
        type                    : INTEGER
        name                    : "Sharpness"
        minimum                 : 0
        maximum                 : 96
        step                    : 1
        default_value           : 40
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+10)
        id                      : 134217738
        type                    : INTEGER
        name                    : "Exposure, Auto"
        minimum                 : 0
        maximum                 : 0
        step                    : 1
        default_value           : 2
        flags                   : 0
    VIDIOC_QUERYCTRL(PRIVATE_BASE+11)
        id                      : 134217739
        type                    : INTEGER
        name                    : "Exposure (Absolute)"
        minimum                 : 20
        maximum                 : 5000
        step                    : 1
        default_value           : 79
        flags                   : 0

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "Live! Cam Optia"
        type                    : 0x1 [CAPTURE]
        channels                : 1
        audios                  : 0
        maxwidth                : 640
        maxheight               : 480
        minwidth                : 48
        minheight               : 32

channels
ioctl VIDIOCGCHAN: Invalid argument

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
        brightness              : 55049
        hue                     : 32768
        colour                  : 24576
        contrast                : 21845
        whiteness               : 18724
        depth                   : 16
        palette                 : YUYV

buffer
ioctl VIDIOCGFBUF: Invalid argument

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 320
        height                  : 240
        chromakey               : 0
        flags                   : 0

```

---

