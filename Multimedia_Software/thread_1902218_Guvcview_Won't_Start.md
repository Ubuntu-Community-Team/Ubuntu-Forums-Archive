---
title: "Guvcview Won't Start"
date: 2011-12-30
forum: Multimedia Software
---

### Post by SeQueNceR on 2011-12-30
i've isntalled guvcview on my Ubuntu 10.10 ... my webcam is working fine at all applications but, guvcview never shows up. i've read that for some people they need to start Jack server manually, i've to do but, with no hope....

this is what i'm getting when i start it.. looks like everything is going fine. then it freezes here without showing anything up

in case of just running the application

```
guvcview 1.4.1
unexpected integer value (160000) for acodec_bit_rate
Strings must be quoted
unexpected integer value (0) for vcodec_bit_rate
Strings must be quoted
unexpected integer value (0) for vcodec_fps
Strings must be quoted
unexpected integer value (0) for vcodec_qmax
Strings must be quoted
unexpected integer value (0) for vcodec_qmin
Strings must be quoted
unexpected integer value (0) for vcodec_max_qdiff
Strings must be quoted
unexpected integer value (0) for vcodec_dia
Strings must be quoted
unexpected integer value (0) for vcodec_pre_dia
Strings must be quoted
unexpected integer value (0) for vcodec_pre_me
Strings must be quoted
unexpected integer value (0) for vcodec_me_pre_cmp
Strings must be quoted
unexpected integer value (0) for vcodec_me_cmp
Strings must be quoted
unexpected integer value (0) for vcodec_me_sub_cmp
Strings must be quoted
unexpected integer value (0) for vcodec_last_pred
Strings must be quoted
unexpected integer value (0) for vcodec_gop_size
Strings must be quoted
unexpected float value (0.000000) for vcodec_qcompress
unexpected float value (0.000000) for vcodec_qblur
unexpected integer value (0) for vcodec_subq
Strings must be quoted
unexpected integer value (0) for vcodec_framerefs
Strings must be quoted
unexpected integer value (0) for vcodec_mb_decision
Strings must be quoted
unexpected integer value (0) for vcodec_trellis
Strings must be quoted
unexpected integer value (0) for vcodec_me_method
Strings must be quoted
unexpected integer value (0) for vcodec_mpeg_quant
Strings must be quoted
unexpected integer value (0) for vcodec_max_b_frames
Strings must be quoted
unexpected integer value (0) for vcodec_flags
Strings must be quoted
[B][COLOR=Red]Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started[/COLOR][/B]
video device: /dev/video0 
/dev/video0 - device 1
Init. USB 2.0 HD Camera  (location: usb-0000:00:1a.0-1.4)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/10, 2/15, 1/5, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
vid:064e 
pid:c117 
driver:uvcvideo
checking format: 1196444237
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
fps is set to 1/25
drawing controls

```in case of starting jack server before

```
guvcview 1.4.1
unexpected integer value (160000) for acodec_bit_rate
Strings must be quoted
unexpected integer value (0) for vcodec_bit_rate
Strings must be quoted
unexpected integer value (0) for vcodec_fps
Strings must be quoted
unexpected integer value (0) for vcodec_qmax
Strings must be quoted
unexpected integer value (0) for vcodec_qmin
Strings must be quoted
unexpected integer value (0) for vcodec_max_qdiff
Strings must be quoted
unexpected integer value (0) for vcodec_dia
Strings must be quoted
unexpected integer value (0) for vcodec_pre_dia
Strings must be quoted
unexpected integer value (0) for vcodec_pre_me
Strings must be quoted
unexpected integer value (0) for vcodec_me_pre_cmp
Strings must be quoted
unexpected integer value (0) for vcodec_me_cmp
Strings must be quoted
unexpected integer value (0) for vcodec_me_sub_cmp
Strings must be quoted
unexpected integer value (0) for vcodec_last_pred
Strings must be quoted
unexpected integer value (0) for vcodec_gop_size
Strings must be quoted
unexpected float value (0.000000) for vcodec_qcompress
unexpected float value (0.000000) for vcodec_qblur
unexpected integer value (0) for vcodec_subq
Strings must be quoted
unexpected integer value (0) for vcodec_framerefs
Strings must be quoted
unexpected integer value (0) for vcodec_mb_decision
Strings must be quoted
unexpected integer value (0) for vcodec_trellis
Strings must be quoted
unexpected integer value (0) for vcodec_me_method
Strings must be quoted
unexpected integer value (0) for vcodec_mpeg_quant
Strings must be quoted
unexpected integer value (0) for vcodec_max_b_frames
Strings must be quoted
unexpected integer value (0) for vcodec_flags
Strings must be quoted
Cannot connect to server socket err = Connection refused
Cannot connect to server socket
jack server is not running or cannot be started
video device: /dev/video0 
/dev/video0 - device 1
Init. USB 2.0 HD Camera  (location: usb-0000:00:1a.0-1.4)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/10, 2/15, 1/5, 
{ pixelformat = 'MJPG', description = 'MJPEG' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 400 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 720 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
{ discrete: width = 1280, height = 800 }
    Time interval between frame: 1/30, 1/25, 1/20, 1/15, 1/10, 2/15, 1/5, 
vid:064e 
pid:c117 
driver:uvcvideo
checking format: 1196444237
VIDIOC_G_COMP:: Invalid argument
   compression control not supported
fps is set to 1/25
drawing controls
```i've tired of searching :( any suggestions ??

---

