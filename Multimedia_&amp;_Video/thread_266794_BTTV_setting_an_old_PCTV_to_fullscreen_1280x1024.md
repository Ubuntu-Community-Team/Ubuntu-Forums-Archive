---
title: "BTTV: setting an old PCTV to fullscreen 1280x1024"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by MadeR on 2006-09-27
[COLOR=Black]Greetings! I'd like to ask your help.
I'm going to remove Windows from my HD, now that everything works in Ubuntu.
My only regret is the tv card: I have an old Pinnacle PCTV (PCI, mono).
When I use it in windows, I can set this program to show the program fullscreen at a 1280x1024 resolution.
In linux the maximum is 800x600, the rest is a black frame to fill up to the resolution.

How can I set fullscreen to the full screen resolution?

Configuration: dapper, Aiglx (same problem also withouth aiglx), Ati (opensource driver), PCTV, PAL, Italy frequency table.


output of `dmesg | grep bttv`:

[17179593.208000] bttv: driver version 0.9.16 loaded
[17179593.208000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179593.208000] bttv: Bt8xx card found (0).
[17179593.208000] bttv0: Bt878 (rev 17) at 0000:02:04.0, irq: 169, latency: 32, mmio: 0xea100000
[17179593.208000] bttv0: detected: Pinnacle PCTV [bswap] [card=39], PCI subsystem ID is bd11:1200
[17179593.208000] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[17179593.208000] bttv0: gpio: en=00000000, out=00000000 in=00ff67ff [init]
[17179593.216000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179593.220000] bttv0: miro: id=25 tuner=1 radio=no stereo=no
[17179593.220000] bttv0: using tuner=1
[17179593.220000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179593.220000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179593.224000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179593.228000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179593.596000] bttv0: registered device video0
[17179593.600000] bttv0: registered device vbi0
[17179593.600000] bttv0: PLL: 28636363 => 35468950 .<6>parport: PnPBIOS parport detected.


output of `xdpyinfo`:
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    70101000
X.Org version: 7.1.1
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
focus:  window 0x200001e, revert to PointerRoot
number of extensions:    30
    BIG-REQUESTS
    Composite
    DAMAGE
    DOUBLE-BUFFER
    DPMS
    Extended-Visual-Information
    GLX
    MIT-SCREEN-SAVER
    MIT-SHM
    MIT-SUNDRY-NONSTANDARD
    RANDR
    RENDER
    SECURITY
    SGI-GLX
    SHAPE
    SYNC
    TOG-CUP
    X-Resource
    XC-APPGROUP
    XC-MISC
    XFIXES
    XFree86-Bigfont
    XFree86-DGA
    XFree86-DRI
    XFree86-Misc
    XFree86-VidModeExtension
    XInputExtension
    XKEYBOARD
    XTEST
    XVideo
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1280x1024 pixels (342x271 millimeters)
  resolution:    95x96 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x4d
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0x7ba03f
    KeyPressMask             KeyReleaseMask           ButtonPressMask
    ButtonReleaseMask        EnterWindowMask          LeaveWindowMask
    ButtonMotionMask         ExposureMask             VisibilityChangeMask
    StructureNotifyMask      SubstructureNotifyMask   SubstructureRedirectMask
    FocusChangeMask          PropertyChangeMask
  number of visuals:    17
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
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2c
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2d
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2e
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x2f
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x30
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x31
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x32
    class:    DirectColor
    depth:    24 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits
  visual:
    visual id:    0x4b
    class:    TrueColor
    depth:    32 planes
    available colormap entries:    256 per subfield
    red, green, blue masks:    0xff0000, 0xff00, 0xff
    significant bits in color specification:    8 bits[/COLOR]

---

