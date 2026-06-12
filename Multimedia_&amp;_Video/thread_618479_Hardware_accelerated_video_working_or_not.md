---
title: "Hardware accelerated video working or not?"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by snek on 2007-11-20
I am currently running a:

- amd sempron64 3400+
- kernel 2.6.22 amd64
- 1.5gb ram
- nvidia 7600gs passive
- envy installed nvidia drivers

Now, what's confusing me is that Xorg is taking up 50% CPU when playing a normal 350mb tv episode encoded in xvid using VLC as a player. I don't notice much difference switching to other players..

Mind you 720p video will not play smooth at all..

Is this normal? Under Windows I am used to the videoplayer just taking about 10% CPU.. Thus, what really confuses me is that it's not the mediaplayer using up the cpu, but Xorg..

Can someone explain this to me, and maybe tell me if hardware acceleration is enabled or not (and possibly how to enable it if it isn't).

---

### Post by stunner on 2007-11-20
Are you using Xv?  What is the output of xvinfo?

---

### Post by snek on 2007-11-22
Hi, thanks for willing to help!

Yes I am using XV as output and here is the output of xvinfo:

```

X-Video Extension version 2.2
screen #0
  Adaptor #0: "NV17 Video Texture"
    number of ports: 32
    port base: 355
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
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
      depth 24, visualID 0x22
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
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
    number of attributes: 3
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_ITURBT_709" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SYNC_TO_VBLANK" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
    maximum XvImage size: 2046 x 2046
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
  Adaptor #1: "NV05 Video Blitter"
    number of ports: 32
    port base: 387
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x21
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
      depth 24, visualID 0x22
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
      depth 24, visualID 0x63
      depth 24, visualID 0x64
      depth 24, visualID 0x65
      depth 24, visualID 0x66
      depth 24, visualID 0x67
      depth 24, visualID 0x68
      depth 24, visualID 0x69
      depth 24, visualID 0x6a
      depth 24, visualID 0x6b
      depth 24, visualID 0x6c
      depth 24, visualID 0x6d
      depth 24, visualID 0x6e
      depth 24, visualID 0x6f
      depth 24, visualID 0x70
      depth 24, visualID 0x71
    number of attributes: 2
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_SYNC_TO_VBLANK" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2046 x 2046
    Number of image formats: 5
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x3
        guid: 03000000-0000-0010-8000-00aa00389b71
        bits per pixel: 32
        number of planes: 1
        type: RGB (packed)
        depth: 24
        red, green, blue masks: 0xff0000, 0xff00, 0xff

```

---

### Post by stunner on 2007-11-22
To force vlc to use xv, hit ctrl+s -> output modules (check 'advanced options') change video output module to XVideo.

I've had a similar experience with my ATI card on XGL, and from what I understand it occurs because for some reason the xv overlay gets cpu-accelerated rather than video card accelerated, and I can't even full-screen properly.  In stock xorg, xv results in xorg using ~10% cpu.

But since you're using binary nvidia drivers (3D works, right?), I'm kind of stumped. What exactly is your X setup? AIGLX? Stock xorg? Are you running compiz?



Also, re 720p - I can play some 720p files beautifully with no stuttering, artifacts, etc, and then others just get totally mangled...no rhyme or reason that I've been able to discover.

---

### Post by snek on 2007-11-22
Thank you, thank you, thank you :D  
Switching VLC to XVideo as standard output seems to have done the trick! 
At first, like I posted above, Xorg was using up to 60 - 80% cpu on normal res tv rips, but now it's down to a measly 1-2%!   

This is **exactly** what I wanted..   

From what I can tell 720p should play beautifully now, my cpu usage is down to about 5% now, whereas before it was nearing 85 - 100% (depends what was running in the background..) 

Time to download a 720p source and try this out!

---

### Post by stunner on 2007-11-22
Glad it worked out for you :)

---

