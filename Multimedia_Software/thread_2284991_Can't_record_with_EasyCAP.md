---
title: "Can't record with EasyCAP"
date: 2015-07-02
forum: Multimedia Software
---

### Post by DeNapes on 2015-07-02
Hello, I was reading the getting started guide for the easy cap in linux, and I followed every step (at least I think I did) but it still doesn't record. When I "lsusb" I can see the device ID (so I suppose it's initialized) but when I try: "somagic-capture -n --luminance=2 --lum-aperture=3 | mplayer -vf yadif,screenshot -demuxer rawvideo -rawvideo "ntsc:format=uyvy:fps=30000/1001" -aspect 4:3" It displays this: 

Failed to open USB device: Permission denied
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team

Playing -.
Reading from stdin...
rawvideo file format detected.
Load subtitles in ./
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
Opening video filter: [screenshot]
Opening video filter: [yadif]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x2a604c0] using unscaled uyvy422 -> yuv420p special converter
VO: [xv] 720x480 => 720x540 Planar YV12 
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 


Exiting... (End of file)

Any ideas?

---

