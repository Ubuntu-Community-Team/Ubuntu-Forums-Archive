---
title: "Hauppauge PVR-150 with Ubuntu 18.04 64bit"
date: 2019-12-01
forum: Multimedia Software
---

### Post by plainfaceboy on 2019-12-01
My old HVR4000 died so as an interim I've got a couple of cards to get me back up and running.
For analog capture (from VHS Video) I've got an old PVR-150, as  *thought* it would be relatively straightforward to get working - but  not having much luck.
The card seems to be recognised fine - no issues or errors but...
TVTime has an error - inappropriate ioctl device for device.
With Qt V4L2  I can get some stuttering audio and a b/w picture through  S-Video-2 on video32, but can't get anything on any composite input  (video 0, 24 or 32).
No luck with [VLC]("https://www.videohelp.com/software/VLC-media-player") player.
Tried loads of things I've found on various forums eg firmware, hwe kernel tweaks etc), but no change.

Does anyone know how to get it working?
Thanks.

---

### Post by Autodave on 2019-12-01
No help here....sorry.  I had the same card on 16.04 and it took a little work, but I did get it to work finally.  Never managed to get it working on 18.04.

---

### Post by plainfaceboy on 2019-12-01
Thanks,
Only moved to 18.04 recently - if 16.04 is the solution, I might go back! 
Can you remember the steps needed to get it working on that?

---

### Post by Autodave on 2019-12-01
Sorry....no idea.  That was right when 16.04 came out.

---

### Post by plainfaceboy on 2019-12-01
Well, I've got it working through the aerial lead (through the Tuner input). 
The audio's stuttering, but the picture is ok.
Composite would be better of course....but nothing working there still!

---

### Post by viewera on 2019-12-04
You need to select your inputs with v4l2-ctl. If you don't already have it, install v4l-utils.
Examples:

Show list of available video inputs

```
v4l2-ctl --list-input
ioctl: VIDIOC_ENUMINPUT
        Input       : 0
        Name        : Tuner 1
        Type        : 0x00000001 (Tuner)
        Audioset    : 0x00000007
        Tuner       : 0x00000000
        Standard    : 0x0000000000001000 (NTSC-M)
        Status      : 0x00000000 (ok)
        Capabilities: 0x00000004 (SDTV standards)

        Input       : 1
        Name        : S-Video 1
        Type        : 0x00000002 (Camera)
        Audioset    : 0x00000007
        Tuner       : 0x00000000
        Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
        Status      : 0x00000000 (ok)
        Capabilities: 0x00000004 (SDTV standards)

        Input       : 2
        Name        : Composite 1
        Type        : 0x00000002 (Camera)
        Audioset    : 0x00000007
        Tuner       : 0x00000000
        Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
        Status      : 0x00000000 (ok)
        Capabilities: 0x00000004 (SDTV standards)

        Input       : 3
        Name        : S-Video 2
        Type        : 0x00000002 (Camera)
        Audioset    : 0x00000007
        Tuner       : 0x00000000
        Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
        Status      : 0x00000000 (ok)
        Capabilities: 0x00000004 (SDTV standards)

        Input       : 4
        Name        : Composite 2
        Type        : 0x00000002 (Camera)
        Audioset    : 0x00000007
        Tuner       : 0x00000000
        Standard    : 0x0000000000FFFFFF (PAL-B/B1/G/H/I/D/D1/K/M/N/Nc/60 NTSC-M/M-JP/443/M-KR SECAM-B/D/G/H/K/K1/L/Lc)
        Status      : 0x00000000 (ok)
        Capabilities: 0x00000004 (SDTV standards)

```

Show a list of available audio inputs 

```
v4l2-ctl --list-audio-input
ioctl: VIDIOC_ENUMAUDIO
        Input   : 0
        Name    : Tuner 1

        Input   : 1
        Name    : Line In 1

        Input   : 2
        Name    : Line In 2
```

Get current video input 

```
v4l2-ctl ---get-input
Video input : 0 (Tuner 1: ok)
```

Get current audio input 

```
v4l2-ctl --get-audio-input
Audio input : 0 (Tuner 1)
```

Set video input to composite

```
v4l2-ctl --set-input=2
Video input set to 2 (Composite 1: Camera, ok)
```

Set audio input to line-in 

```
v4l2-ctl --set-audio-input=1
Audio input set to 1

```

The v4l2-ctl  command defaults to /dev/video0. If you have more than one capture device, use the device switch

```
v4l2-ctl -d /dev/videoX --list-audio-input
```

As far as I can tell VLC has dropped it's pvr:// support, and I can't get Qt V4L2 to work either.
After setting your inputs you can watch with ffplay

```
ffplay /dev/video0
```

or mpv

```
mpv /dev/video0
```

or even vlc (but it takes a long time to start)

```
vlc  /dev/video0
```

You can record with ffmpeg

```
ffmpeg -i /dev/video0 -c copy "What_ever_name_you_want.mpg"
```

---

