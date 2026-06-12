---
title: "PVR-150 ivtv no Pal-m"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by hfsoares on 2006-05-28
Hi guys,

I have installed a WinTv PVR150 and ubuntu, and can't make work MythTv, TvTime or scantv. I have followed the HowTo to Ubuntu Breezy 5.10 to install ivtv. I can tune some channels, but the colors are just wrong. Its just like NTSC and here in Brazil we use PAL-M.

I have seen some log of ivtvctl from other users and appears some PAL-M options on ioctl: VIDIOC_ENUMSTD but in mine doesnt. Any help would be appreciated.

hfsoares@betohomeubu:~/ivtv0.4-0.4.5$ ivtvctl -a
ioctl IVTV_IOC_G_CODEC ok
Codec parameters
aspect      : 2
audio       : 0x00e9
bframes     : 3
bitrate_mode: 0
bitrate     : 8000000
bitrate_peak: 9600000
dnr_mode    : 0
dnr_spatial : 0
dnr_temporal: 8
dnr_type    : 0
framerate   : 0
framespergop: 15
gop_closure : 1
pulldown    : 0
stream_type : 14
ioctl VIDIOC_G_FMT ok
        Type   : Video Capture
        Width  : 720
        Height : 576
ioctl VIDIOC_QUERYCAP ok
        Driver name   : ivtv
        Card type     : WinTV PVR 150
        Bus info      : 0000:00:0b.0
        Driver version: 1029
        Capabilities  : 0x01030011
ioctl: VIDIOC_ENUMINPUT
        Input   : 0
        Name    : Tuner
        Type    : 0x00000001
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x0000000000003000 ( NTSC )
        Status  : 0

        Input   : 1
        Name    : Composite 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 2
        Name    : Composite 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 3
        Name    : S-Video 0
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0

        Input   : 4
        Name    : S-Video 1
        Type    : 0x00000002
        Audioset: 0x00000003
        Tuner   : 0x00000000
        Standard: 0x00000000007F7FFF ( PAL NTSC SECAM )
        Status  : 0
ioctl VIDIOC_G_INPUT ok
Video input = 0
ioctl: VIDIOC_ENUMOUTPUT
ioctl VIDIOC_G_OUTPUT failed: Invalid argument
ioctl: VIDIOC_ENUMAUDIO
        Input   : 0
        Name    : Tuner Audio In

        Input   : 1
        Name    : Audio Line 1

        Input   : 2
        Name    : Audio Line 2

        Input   : 3
        Name    : Audio Line 3

        Input   : 4
        Name    : Audio Line 4
ioctl VIDIOC_G_AUDIO ok
Audio input = 0: Tuner Audio In
ioctl VIDIOC_G_FREQUENCY ok
Frequency = 0
ioctl: VIDIOC_ENUMSTD
        index       : 0
        ID          : 0x0000000000003000
        Name        : NTSC
        Frame period: 1001/30000
        Frame lines : 525

        index       : 1
        ID          : 0x00000000000000FF
        Name        : PAL
        Frame period: 1/25
        Frame lines : 625

        index       : 2
        ID          : 0x00000000007F0000
        Name        : SECAM
        Frame period: 1/25
        Frame lines : 625
ioctl VIDIOC_G_STD ok
Video standard = 0x000000ff
ioctl: VIDIOC_QUERYCTRL
Brightness = 127
Contrast = 63
Saturation = 63
Hue = 0
Volume = 60928
Mute = 0


[]s Humberto

---

### Post by awakatanka on 2006-05-31
I'm using the pvr-500 that is the same as a pvr-150 only it has 2 recievers on it.

I used this links to get it to work and i can select pal-m ,pal and pal-n 

[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)
[http://www.abarbaccia.com/content/view/15/29/](http://www.abarbaccia.com/content/view/15/29/)
[http://www.mythtv.org/wiki/index.php/Ubuntu_Breezy_Installation_Guides](http://www.mythtv.org/wiki/index.php/Ubuntu_Breezy_Installation_Guides)

Ps. i using dapper but used the breezy howto's and slightly adjusted it to dapper.

---

