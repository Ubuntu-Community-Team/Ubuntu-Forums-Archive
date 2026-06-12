---
title: "Transmageddon and Hardware Accelerated Video Encoding"
date: 2015-08-21
forum: Multimedia Software
---

### Post by dexter8 on 2015-08-21
Has anyone here managed to get Hardware Accelerated Encoding to work in Ubuntu? I've managed to use the VAAPI test examples with Gstreamer, but it all seems beyond me. I would be willing to throw down some money to fund a quick and dirty GUI for VAAPI Gstreamer Encoding.

I'm using a supported Haswell CPU and Ubuntu 15.04. Transmageddon just seems outdated and uses deprecated gstreamer arguments.

Quicksync encoding is the only thing keeping me tied to windows, its annoying to know that Ubuntu and Linux in general has everything needed for GPU video encoding.

---

### Post by mc4man on 2015-08-21
Transmageddon uses vaapi encoding here on 15.10, would think it would also work in 15.04. While very fast, (a 1 min test clip encoded to .mp4/MPEG4 with h.264 takes around 7-8 sec.) there are no real gui adjustments/options. The quality seems commensurate with speed, ie., very fast but  not that good, non hwaccel in trans is slightly better quality.  Maybe that suits your use case?
Ex. - 
> :~$ transmageddon
.....clipped
 Gst.debug_bin_to_dot_file (self.pipeline, Gst.DebugGraphDetails.ALL, 'transmageddon-debug-graph')
libva info: VA-API version 0.38.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_38
libva info: va_openDriver() returns 0

Maybe see if a dev version of handbrake supports gst-vaapi encoding.. & if so may allow for better encoding options

If not on 15.04 then figure 15.10 which will be using FFmpeg in gst instead of Libav

Edit: tested on 15.04, gst-vaapi also works there in trans..

---

### Post by dexter8 on 2015-08-22
I can not for the life of me, get Transmageddon to touch the GPU? Is this something that you could only get going on 15.10? Like I said, I used the Gstreamer command to generate a test file - which worked. Is there some install method or something?

Cheers

---

### Post by mc4man on 2015-08-22
No, it 'works' in 15.04 also. Only odd thing is trans installs 12 presets but only exposes 9 of then,there is nothing for vaapi
So to beg the obvious - 
Do you have gstreamer1.0-vaapi package installed?
Are you doing an h.264 encoding ?

Edit: as usual gst is hard to understand (here) & of little value (to me)
It would seem it's up to the app to set parameters & trans apparently doesn't, likely uses the minimum default. The element seems to have options available but trans doesn't have a visible means to set.

```
$ gst-inspect-1.0 ELEMENT vaapiencode_h264
Factory Details:
  Rank                     primary (256)
  Long-name                VA-API H.264 encoder
  Klass                    Codec/Encoder/Video
  Description              A VA-API based H.264 video encoder
  Author                   Wind Yuan <feng.yuan@intel.com>

Plugin Details:
  Name                     vaapi
  Description              VA-API based elements
  Filename                 /usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvaapi.so
  Version                  0.6.0
  License                  LGPL
  Source module            gstreamer-vaapi
  Binary package           gstreamer-vaapi
  Origin URL               gwenole.beauchesne@intel.com, sreerenj.balachandran@intel.com

GObject
 +----GInitiallyUnowned
       +----GstObject
             +----GstElement
                   +----GstVideoEncoder
                         +----GstVaapiEncode
                               +----GstVaapiEncodeH264

Implemented Interfaces:
  GstPreset

Pad Templates:
  SINK template: 'sink'
    Availability: Always
    Capabilities:
      video/x-raw(memory:VASurface)
                 format: { ENCODED, NV12, I420, YV12 }
                  width: [ 1, 2147483647 ]
                 height: [ 1, 2147483647 ]
              framerate: [ 0/1, 2147483647/1 ]
         interlace-mode: progressive
      video/x-raw
                 format: { I420, YV12, YUY2, UYVY, AYUV, RGBx, BGRx, xRGB, xBGR, RGBA, BGRA, ARGB, ABGR, RGB, BGR, Y41B, Y42B, YVYU, Y444, v210, v216, NV12, NV21, NV16, NV24, GRAY8, GRAY16_BE, GRAY16_LE, v308, RGB16, BGR16, RGB15, BGR15, UYVP, A420, RGB8P, YUV9, YVU9, IYU1, ARGB64, AYUV64, r210, I420_10LE, I420_10BE, I422_10LE, I422_10BE, Y444_10LE, Y444_10BE, GBR, GBR_10LE, GBR_10BE, NV12_64Z32 }
                  width: [ 1, 2147483647 ]
                 height: [ 1, 2147483647 ]
              framerate: [ 0/1, 2147483647/1 ]
         interlace-mode: progressive

  SRC template: 'src'
    Availability: Always
    Capabilities:
      video/x-h264
          stream-format: { avc, byte-stream }
              alignment: au
                profile: { constrained-baseline, baseline, main, high, multiview-high, stereo-high }


Element Flags:
  no flags set

Element Implementation:
  Has change_state() function: gst_vaapiencode_change_state

Element has no clocking capabilities.
Element has no URI handling capabilities.

Pads:
  SINK: 'sink'
    Pad Template: 'sink'
  SRC: 'src'
    Pad Template: 'src'

Element Properties:
  name                : The name of the object
                        flags: readable, writable
                        String. Default: "vaapiencodeh264-0"
  parent              : The parent of the object
                        flags: readable, writable
                        Object of type "GstObject"
  rate-control        : Rate control mode
                        flags: readable, writable
                        Enum "GstVaapiRateControlH264" Default: 1, "cqp"
                           (1): cqp              - Constant QP
                           (2): cbr              - Constant bitrate
                           (4): vbr              - Variable bitrate
                           (5): vbr_constrained  - Variable bitrate - Constrained
  bitrate             : The desired bitrate expressed in kbps (0: auto-calculate)
                        flags: readable, writable
                        Unsigned Integer. Range: 0 - 102400 Default: 0 
  keyframe-period     : Maximal distance between two keyframes (0: auto-calculate)
                        flags: readable, writable
                        Unsigned Integer. Range: 1 - 300 Default: 30 
  tune                : Encoder tuning option
                        flags: readable, writable
                        Enum "GstVaapiEncoderTuneH264" Default: 0, "none"
                           (0): none             - None
                           (1): high-compression - High compression
  max-bframes         : Number of B-frames between I and P
                        flags: readable, writable
                        Unsigned Integer. Range: 0 - 10 Default: 0 
  init-qp             : Initial quantizer value
                        flags: readable, writable
                        Unsigned Integer. Range: 1 - 51 Default: 26 
  min-qp              : Minimum quantizer value
                        flags: readable, writable
                        Unsigned Integer. Range: 1 - 51 Default: 1 
  num-slices          : Number of slices per frame
                        flags: readable, writable
                        Unsigned Integer. Range: 1 - 200 Default: 1 
  cabac               : Enable CABAC entropy coding mode
                        flags: readable, writable
                        Boolean. Default: false
  dct8x8              : Enable adaptive use of 8x8 transforms in I-frames
                        flags: readable, writable
                        Boolean. Default: false
  cpb-length          : Length of the CPB buffer in milliseconds
                        flags: readable, writable
                        Unsigned Integer. Range: 1 - 10000 Default: 1500 
  num-views           : Number of Views for MVC encoding
                        flags: readable, writable
                        Unsigned Integer. Range: 1 - 10 Default: 1 
  view-ids            : Set of View Ids used for MVC encoding
                        flags: readable, writable
                        Array of GValues of type "guint"
```

---

### Post by Yellow Pasque on 2015-08-22
> **mc4man said:**
> Maybe see if a dev version of handbrake supports gst-vaapi encoding..

I build Handbrake from git and skim through the commit log on a semi-regular basis.  I haven't seen anything in the commit logs about enabling QuickSync or accelerated vaapi support on Linux. Supposedly, it's in their plans to bring it to Linux, and hopefully it will come sooner than later now that Skylake supports HEVC encoding accel.

> there are no real gui adjustments/options

Yeah, transmageddon is a true gnome program aimed at the "don't worry your pretty little head about it" crowd.

> Edit: as usual gst is hard to understand (here) & of little value (to me)
I think it's more valuable to developers than users.

---

### Post by dexter8 on 2015-08-22
[IMG]http://s1.postimg.org/opuuvgm5r/Screenshot_from_2015_08_22_21_34_23.png[/IMG]

A picture says more than 1000 words. Surely my CPU usage shows that VAAPI isn't being utilised?

---

### Post by mc4man on 2015-08-22
> **dexter8 said:**
> 

A picture says more than 1000 words. Surely my CPU usage shows that VAAPI isn't being utilised?
Not always - remove the gstreamer vaapi package, then try that exact same encoding again & see what top says. Likely the cpu use wll be 4x greater give or take.
The bigger issue could be that it's going to use the default parameters & quality setting. Here that produces an 'so-so' encoding with a fair amount of compression artifacts, particular in dark areas 
I'd rather just use ffmpeg with multi-thread cpu encoding..., there are also several gui encoders that do  much better though slower.

(ex. encoding [here]("http://www.datafilehost.com/d/4390aab2"), took 7 sec. but not suitable for me. Maybe trans would be ok for one of those phone presets where image is small??

---

### Post by dexter8 on 2015-08-23
Removing gstreamer vaapi made no difference at all, I'm guessing it wasn't using the GPU.. I'm trying to get quicksync to run under a virtual machine, but to no avail. One guy says it's possible, but doesn't say how.

---

### Post by Yellow Pasque on 2015-08-23
> **dexter8 said:**
> I'm trying to get quicksync to run under a virtual machine, but to no avail. One guy says it's possible, but doesn't say how.

You probably have to have some sort of PCI-e passthrough so that the VM can use your real GPU instead of an emulated one.

---

### Post by dexter8 on 2015-08-25
I stand corrected on most fronts. [https://www.youtube.com/watch?v=Ul7jBKunEyU](https://www.youtube.com/watch?v=Ul7jBKunEyU) top right is a handbrake encode, bottom left is a transmageddon encode and top right is a transmageddon hardware encode. Handbrake seems to have a big where it reports a very wrong status of encode time.

---

