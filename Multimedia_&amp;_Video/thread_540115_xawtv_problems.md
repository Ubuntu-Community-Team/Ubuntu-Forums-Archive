---
title: "xawtv problems"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by kudos1uk on 2007-09-01
I'm having a few problems with xawtv, I just get an blank screen with 1024x480 at the top of the window which changes to ???.

I have a Sony C1VN with motioneye camera built in, the camera works fine in other software "motioneye" and "effectv".

I'm a bit lost now, any advice welcome or a suggestion for alternative software.

Thanks Tony

This is the output:

> tony@tony-laptop:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-386)
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0xb7e58990b7ff3e52 [PAL_B1,PAL_I,PAL_D1,PAL_N,PAL_Nc,PAL_60,NTSC_M,NTSC_M_JP,SECAM_B,SECAM_D,SECAM_G,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Invalid argument


---

