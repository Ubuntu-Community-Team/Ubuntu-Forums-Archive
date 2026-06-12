---
title: "XRANDR Question for ATI Radeon 8500DV"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by StriperTS on 2007-11-13
I'm running Kubuntu 7.10 on an older machine with an ATI Radeon 8500DV graphics card, trying to get TV-Out to work.  My research over the last couple of days shows that there may be hope with the latest drivers incorporated into Gutsy.

I'm under the impression that xrandr 1.2 might be the way to the promised land this time around.

I've been messing around for a while trying various things, but to keep things simple, if I delete my xorg.conf file and reboot, the system comes up fine and everything appears ok - resolution/framerates are good, glxgears reports decent FPS, etc..  I get similar results if I perform "dpkg-reconfigure xserver-org" and use a plain xorg.conf.

However, when I run xrandr, it only shows one output device (DVI-0) with no mention of the S-video / TV Out interfaces.

```
xrandr --verbose
Screen 0: minimum 320 x 200, current 1152 x 864, maximum 1280 x 1200
DVI-0 connected 1152x864+0+0 (0x50) normal (normal left inverted right) 300mm x 225mm
        Identifier: 0x4c
        Timestamp:  983443426
        Subpixel:   no subpixels
        Clones:
        CRTC:       0
        CRTCs:      0 1
        EDID_DATA:
                00ffffffffffff003e295a46b0010000
                160901021d2018a0ea9d19a255479827
                10484cfffe0031594559714f81408180
                010101010101ea240060410028303060
                13002ce11000001e000000ff005a4639
                323230303433320a2020000000fd0032
                781e460b000a202020202020000000fc
                005137312d330a202020202020200006
                dvi_monitor_type: auto
                scaler: off
                tmds_pll: bios
        load_detection: 1 (0x00000001) range:  (0,1)

```

Shouldn't I be seeing the other outputs?  I read somewhere about the output devices only being detected at bootup, so I have run a S-Video cable to one of the inputs on my TV.  The TV shows the standard boot screens right up until X starts and then goes blank.

Anyone with an 8500DV able to see the other outputs with xrandr?

Thanks,

-- Tom

---

### Post by StriperTS on 2007-11-15
Found out from the folks working on the open source ATI driver that there is no support for cards that use the rage theater hardware for TV-out.. only "integrated TVOut" is supported.

-- Tom

---

### Post by CarpKing on 2007-11-15
What happens if you enter (with the TV hooked up through S-Video):

```
xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
```

I don't know about what sort of theatre chip my card has, but it's a slightly old ATI as well (9600).  On my machine the above command clones the upper right 800x600 area of my monitor on the TV.

---

### Post by StriperTS on 2007-11-15
Thats the point I was trying to get to, but the 8500DV doesn't support this function.

-- Tom

---

