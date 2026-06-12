---
title: "MPV - no usb audio in legacy mode"
date: 2016-09-21
forum: Multimedia Software
---

### Post by lou6 on 2016-09-21
I have a Dell D620 laptop used as a media machine. The video chip is old and too slow to support a new version of OpenGL so when using Smplayer/MPV the video/audio default to Legacy mode as shown here:

lou@lou-Latitude-D620:~$ cd Videos
lou@lou-Latitude-D620:~/Videos$ mpv --ao alsa good.mp4
Playing: good.mp4
 (+) Video --vid=1 (*) (h264)
 (+) Audio --aid=1 --alang=und (*) (aac)

[vo/opengl/x11] X11 error: GLXBadFBConfig
[vo/opengl] Could not create GL3 context. Retrying with legacy context.
[vo/opengl] At least OpenGL 2.1 or OpenGL ES 2.0 required.
Failed to open VDPAU backend libvdpau_i915.so: cannot open shared object file: No such file or directory
[vo/vdpau] Error when calling vdp_device_create_x11: 1

AO: [alsa] 48000Hz stereo 2ch float
VO: [xv] 720x404 yuv420p
AV: 00:02:16 / 00:44:01 (5%) A-V:  0.000

I also use a VGA-to-HDMI converter on this machine to interface with my flatscreen. The converter gets its audio from a usb port.

All is well video-wise but no audio is being forwarded to the flatscreen.

I've looked at available options for MPV but can't see what I can change to get usb sound.  Is there anything I can do to solve this (short of buying a newer laptop to play videos)?

EDIT: should have mentioned that, when using smplayer/mplayer, everything works as it should including usb-driven sound

---

### Post by mc4man on 2016-09-22
see if your device is found in this, if so then you can specify (search the man, --audio-device
```
mpv --audio-device=help
```

---

### Post by lou6 on 2016-09-22
My device may be listed - I'll check it out and see in a bit.  Thanks for replying.

Yes, that did it. My device was listed and adding it to the mpv overrides in the advanced section of smplayer was the answer.  Thanks again, mc4man.

---

