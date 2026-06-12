---
title: "XVideo playback won't go over 384 x 2048 on ATI Mach64"
date: 2006-03-18
forum: Multimedia &amp; Video
---

### Post by clintonthegeek on 2006-03-18
Hi Everyone!

I'm having problems with my older ATI Video card playing back video with XVideo. lspci says that it's specifically an *ATI Technologies Inc 264VT [Mach64 VT] (rev 48)*. Every time that I try to play a moderatly sized video, all I get is the key-color (green) regardless of which video player I use. I've determined that the problem is that maximum size a video can be for playback is 384 x 2048, according to xvinfo. Here's it's complete output.


```
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Mach64 Back-end Overlay Scaler"
    number of ports: 1
    port base: 61
    operations supported: PutImage
    supported visuals:
      depth 16, visualID 0x23
      depth 16, visualID 0x24
      depth 16, visualID 0x25
      depth 16, visualID 0x26
      depth 16, visualID 0x27
      depth 16, visualID 0x28
      depth 16, visualID 0x29
      depth 16, visualID 0x2a
    number of attributes: 8
      "XV_AUTOPAINT_COLOURKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLOURKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 3137)
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 3137)
      "XV_COLOURKEY_MASK" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 65535)
      "XV_COLORKEY_MASK" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 65535)
      "XV_SET_DEFAULTS" (range 0 to 0)
              client settable attribute
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 384 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
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

I've already had to set the colour-depth of my monitor to 16-bit from 24-bit in order to get resolutions over 640x480, I'm now running at 1024x768. But I can't view videos in full screen on this computer however, because XVideo won't scale to fit my screen, and trying to stretch X11 output (such as mplayer with the options "-zoom -fs -vo x11") lags horribly and drops over half the frames.

Any help on how to change my "maximum XvImage size" in XVideo to something a little better would be much appreciated. I've looked around have found very little reference to my problem. I've tried compiling the CVS versions of Mesa and DRM for X11, as I saw in a different thread regarding the Mach64, but it hasn't helped any.

Thanks!

-Clinton

---

