---
title: "Stuck on 480x480 capture"
date: 2008-09-19
forum: Mythbuntu
---

### Post by OmahaVike on 2008-09-19
This is entirely wierd, and I'm hoping someone here knows enough about the mythtv underbelly to help.

Setup:  MythTV installed on top of Hardy.

I verified my capture card (hauppauge pvr-150) is able to record in 720x480.  

```

myuser@mymachine:~$ v4l2-ctl --all
Driver Info:
	Driver name   : ivtv
	Card type     : Hauppauge WinTV PVR-150
	Bus info      : 0000:02:04.0
	Driver version: 65792
	Capabilities  : 0x01070051
		Video Capture
		VBI Capture
		Sliced VBI Capture
		Tuner
		Audio
		Radio
		Read/Write
Format Video Capture:
	Width/Height  : 720/480
	Pixel Format  : MPEG
	Field         : Interlaced
	Bytes per Line: 0
	Size Image    : 131072
	Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
Format Sliced VBI Capture:
	Service Set    : 
	Service Line  0:          /         
	Service Line  1:          /         
	Service Line  2:          /         
	Service Line  3:          /         
	Service Line  4:          /         
	Service Line  5:          /         
	Service Line  6:          /         
	Service Line  7:          /         
	Service Line  8:          /         
	Service Line  9:          /         
	Service Line 10:          /         
	Service Line 11:          /         
	Service Line 12:          /         
	Service Line 13:          /         
	Service Line 14:          /         
	Service Line 15:          /         
	Service Line 16:          /         
	Service Line 17:          /         
	Service Line 18:          /         
	Service Line 19:          /         
	Service Line 20:          /         
	Service Line 21:          /         
	Service Line 22:          /         
	Service Line 23:          /         
	I/O Size       : 0
Format VBI Capture:
	Sampling Rate   : 27000000 Hz
	Offset          : 248 samples (9.18519e-06 secs after leading edge)
	Samples per Line: 1440
	Sample Format   : GREY
	Start 1st Field : 10
	Count 1st Field : 12
	Start 2nd Field : 273
	Count 2nd Field : 12
Crop Capability Video Capture:
	Bounds      : Left 0, Top 0, Width 720, Height 480
	Default     : Left 0, Top 0, Width 720, Height 480
	Pixel Aspect: 10/11
Crop Capability Video Output:
	Bounds      : Left 0, Top 0, Width 720, Height 480
	Default     : Left 0, Top 0, Width 720, Height 480
	Pixel Aspect: 10/11
Video input : 0 (Tuner 1)
Audio input : 0 (Tuner 1)
Frequency: 1236 (77.250000 MHz)
Video Standard = 0x0000b000
	NTSC-M/M-JP/M-KR
Tuner:
	Capabilities         : 62.5 kHz multi-standard stereo lang1 lang2 
	Frequency range      : 44.0 MHz - 958.0 MHz
	Signal strength      : 99%
	Current audio mode   : lang1
	Available subchannels: stereo 

```

I then issued a "cat /dev/video0 > testing.mpg" and verified that the captured video was, indeed, 720x480 (through movieplayer).

I have set all recording profiles in Myth to be 720x480.

YET...  when I schedule a recording through Myth, the captured video is 480x480.  The recording profiles still show 720x480.

AND...  (check this wierdness out) it resets my ivtv settings back to 480x480.
```

myuser@mymachine:~$ v4l2-ctl --all
Driver Info:
        Driver name   : ivtv
        Card type     : Hauppauge WinTV PVR-150
        Bus info      : 0000:02:04.0
        Driver version: 65792
        Capabilities  : 0x01070051
                Video Capture
                VBI Capture
                Sliced VBI Capture
                Tuner
                Audio
                Radio
                Read/Write
Format Video Capture:
        Width/Height  : 480/480
        Pixel Format  : MPEG
        Field         : Interlaced
        Bytes per Line: 0
        Size Image    : 131072
        Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
Format Sliced VBI Capture:
        Service Set    : 
        Service Line  0:          /         
        Service Line  1:          /         
        Service Line  2:          /         
        Service Line  3:          /         
        Service Line  4:          /         
        Service Line  5:          /         
        Service Line  6:          /         
        Service Line  7:          /         
        Service Line  8:          /         
        Service Line  9:          /         
        Service Line 10:          /         
        Service Line 11:          /         
        Service Line 12:          /         
        Service Line 13:          /         
        Service Line 14:          /         
        Service Line 15:          /         
        Service Line 16:          /         
        Service Line 17:          /         
        Service Line 18:          /         
        Service Line 19:          /         
        Service Line 20:          /         
        Service Line 21:          /         
	Service Line 22:          /         
	Service Line 23:          /         
	I/O Size       : 0
Format VBI Capture:
	Sampling Rate   : 27000000 Hz
	Offset          : 248 samples (9.18519e-06 secs after leading edge)
	Samples per Line: 1440
	Sample Format   : GREY
	Start 1st Field : 10
	Count 1st Field : 12
	Start 2nd Field : 273
	Count 2nd Field : 12
Crop Capability Video Capture:
	Bounds      : Left 0, Top 0, Width 720, Height 480
	Default     : Left 0, Top 0, Width 720, Height 480
	Pixel Aspect: 10/11
Crop Capability Video Output:
	Bounds      : Left 0, Top 0, Width 720, Height 480
	Default     : Left 0, Top 0, Width 720, Height 480
	Pixel Aspect: 10/11
Video input : 0 (Tuner 1)
Audio input : 0 (Tuner 1)
Frequency: 4916 (307.250000 MHz)
Video Standard = 0x0000b000
	NTSC-M/M-JP/M-KR
Tuner:
	Capabilities         : 62.5 kHz multi-standard stereo lang1 lang2 
	Frequency range      : 44.0 MHz - 958.0 MHz
	Signal strength      : 99%
	Current audio mode   : lang1
	Available subchannels: mono 

```

Of course, any and all help is GREATLY GREATLY appreciated.  My keyboard is taking a beating from my forehead.  I can't discover where Myth is setting this.

If it helps, I can get into the database to pull from tables, if need be.  Although, at first glance, they appear to be set to 720x480.

TIA

---

### Post by axelsvag on 2008-09-19
I assume that you have been set the resolution in the frontend menu?

---

### Post by OmahaVike on 2008-09-19
Yes.

Under Utilities/Setup -> Setup -> TV Settings -> Recording Profiles -> MPEG2 Encoders 

Then modified the default, livetv, high quality and low quality to all be 720x480.

---

### Post by OmahaVike on 2008-09-23
Hopefully, this data might help spot the problem.  Again, any help is more than appreciated.  I simply cannot see where the problem lies.

Here's the dump of codecparams:
```

mysql> select * from codecparams;
+---------+--------------------------+---------------+
| profile | name                     | value         |
+---------+--------------------------+---------------+
|      54 | autotranscode            | 0             | 
|      54 | width                    | 720           | 
|      54 | height                   | 480           | 
|      54 | rtjpegquality            | 170           | 
|      54 | mpeg4bitrate             | 2200          | 
|      54 | mpeg4maxquality          | 2             | 
|      54 | mpeg4minquality          | 15            | 
|      54 | mpeg4qualdiff            | 3             | 
|      54 | scalebitrate             | 1             | 
|      54 | mpeg4optionvhq           | 0             | 
|      54 | mpeg4option4mv           | 0             | 
|      54 | mpeg4optionidct          | 0             | 
|      54 | mpeg4optionime           | 0             | 
|      54 | encodingthreadcount      | 1             | 
|      54 | mpeg2bitrate             | 8000          | 
|      54 | hardwaremjpegquality     | 100           | 
|      54 | hardwaremjpeghdecimation | 4             | 
|      54 | hardwaremjpegvdecimation | 4             | 
|      54 | mpeg2streamtype          | MPEG-2 PS     | 
|      54 | mpeg2aspectratio         | 4:3           | 
|      54 | mpeg2maxbitrate          | 10000         | 
|      54 | samplerate               | 48000         | 
|      54 | mpeg2audtype             | Layer II      | 
|      54 | mpeg2audbitratel1        | 448           | 
|      54 | mpeg2audbitratel2        | 384           | 
|      54 | mpeg2audbitratel3        | 192           | 
|      54 | mpeg2language            | 0             | 
|      54 | mpeg2audvolume           | 90            | 
|      55 | autotranscode            | 0             | 
|      55 | width                    | 720           | 
|      55 | height                   | 480           | 
|      55 | rtjpegquality            | 170           | 
|      55 | mpeg4bitrate             | 2200          | 
|      55 | mpeg4maxquality          | 2             | 
|      55 | mpeg4minquality          | 15            | 
|      55 | mpeg4qualdiff            | 3             | 
|      55 | scalebitrate             | 1             | 
|      55 | mpeg4optionvhq           | 0             | 
|      55 | mpeg4option4mv           | 0             | 
|      55 | mpeg4optionidct          | 0             | 
|      55 | mpeg4optionime           | 0             | 
|      55 | encodingthreadcount      | 1             | 
|      55 | mpeg2bitrate             | 8000          | 
|      55 | hardwaremjpegquality     | 100           | 
|      55 | hardwaremjpeghdecimation | 4             | 
|      55 | hardwaremjpegvdecimation | 4             | 
|      55 | mpeg2streamtype          | MPEG-2 PS     | 
|      55 | mpeg2aspectratio         | 4:3           | 
|      55 | mpeg2maxbitrate          | 10000         | 
|      55 | samplerate               | 48000         | 
|      55 | mpeg2audtype             | Layer II      | 
|      55 | mpeg2audbitratel1        | 448           | 
|      55 | mpeg2audbitratel2        | 384           | 
|      55 | mpeg2audbitratel3        | 192           | 
|      55 | mpeg2language            | 0             | 
|      55 | mpeg2audvolume           | 90            | 
|      22 | transcodelossless        | 0             | 
|      22 | transcoderesize          | 0             | 
|      22 | width                    | 720           | 
|      22 | height                   | 480           | 
|      22 | rtjpegquality            | 170           | 
|      22 | mpeg4bitrate             | 2200          | 
|      22 | mpeg4maxquality          | 2             | 
|      22 | mpeg4minquality          | 15            | 
|      22 | mpeg4qualdiff            | 3             | 
|      22 | scalebitrate             | 1             | 
|      22 | mpeg4optionvhq           | 0             | 
|      22 | mpeg4option4mv           | 0             | 
|      22 | mpeg4optionidct          | 0             | 
|      22 | mpeg4optionime           | 0             | 
|      22 | encodingthreadcount      | 1             | 
|      22 | mpeg2bitrate             | 4500          | 
|      22 | hardwaremjpegquality     | 100           | 
|      22 | hardwaremjpeghdecimation | 4             | 
|      22 | hardwaremjpegvdecimation | 4             | 
|      22 | mpeg2streamtype          | MPEG-2 PS     | 
|      22 | mpeg2aspectratio         | 4:3           | 
|      22 | mpeg2maxbitrate          | 6000          | 
|      22 | samplerate               | 32000         | 
|      22 | mp3quality               | 7             | 
|      22 | volume                   | 90            | 
|       5 | autotranscode            | 0             | 
|       5 | width                    | 720           | 
|       5 | height                   | 480           | 
|       5 | rtjpegquality            | 170           | 
|       5 | mpeg4bitrate             | 2200          | 
|       5 | mpeg4maxquality          | 2             | 
|       5 | mpeg4minquality          | 15            | 
|       5 | mpeg4qualdiff            | 3             | 
|       5 | scalebitrate             | 1             | 
|       5 | mpeg4optionvhq           | 0             | 
|       5 | mpeg4option4mv           | 0             | 
|       5 | mpeg4optionidct          | 0             | 
|       5 | mpeg4optionime           | 0             | 
|       5 | encodingthreadcount      | 1             | 
|       5 | mpeg2bitrate             | 4500          | 
|       5 | hardwaremjpegquality     | 100           | 
|       5 | hardwaremjpeghdecimation | 4             | 
|       5 | hardwaremjpegvdecimation | 4             | 
|       5 | mpeg2streamtype          | DVD-Special 2 | 
|       5 | mpeg2aspectratio         | 4:3           | 
|       5 | mpeg2maxbitrate          | 6000          | 
|       5 | samplerate               | 48000         | 
|       5 | mpeg2audtype             | Layer II      | 
|       5 | mpeg2audbitratel1        | 448           | 
|       5 | mpeg2audbitratel2        | 384           | 
|       5 | mpeg2audbitratel3        | 192           | 
|       5 | mpeg2language            | 0             | 
|       5 | mpeg2audvolume           | 90            | 
|      57 | autotranscode            | 0             | 
|      57 | width                    | 720           | 
|      57 | height                   | 480           | 
|      57 | rtjpegquality            | 170           | 
|      57 | mpeg4bitrate             | 2200          | 
|      57 | mpeg4maxquality          | 2             | 
|      57 | mpeg4minquality          | 15            | 
|      57 | mpeg4qualdiff            | 3             | 
|      57 | scalebitrate             | 1             | 
|      57 | mpeg4optionvhq           | 0             | 
|      57 | mpeg4option4mv           | 0             | 
|      57 | mpeg4optionidct          | 0             | 
|      57 | mpeg4optionime           | 0             | 
|      57 | encodingthreadcount      | 1             | 
|      57 | mpeg2bitrate             | 8000          | 
|      57 | hardwaremjpegquality     | 100           | 
|      57 | hardwaremjpeghdecimation | 4             | 
|      57 | hardwaremjpegvdecimation | 4             | 
|      57 | mpeg2streamtype          | MPEG-2 PS     | 
|      57 | mpeg2aspectratio         | 4:3           | 
|      57 | mpeg2maxbitrate          | 10000         | 
|      57 | samplerate               | 48000         | 
|      57 | mpeg2audtype             | Layer II      | 
|      57 | mpeg2audbitratel1        | 448           | 
|      57 | mpeg2audbitratel2        | 384           | 
|      57 | mpeg2audbitratel3        | 192           | 
|      57 | mpeg2language            | 0             | 
|      57 | mpeg2audvolume           | 90            | 
|      58 | autotranscode            | 0             | 
|      58 | encodingthreadcount      | 1             | 
|      58 | hardwaremjpeghdecimation | 4             | 
|      58 | hardwaremjpegquality     | 100           | 
|      58 | hardwaremjpegvdecimation | 4             | 
|      58 | height                   | 480           | 
|      58 | mpeg2aspectratio         | 4:3           | 
|      58 | mpeg2audbitratel1        | 448           | 
|      58 | mpeg2audbitratel2        | 384           | 
|      58 | mpeg2audbitratel3        | 192           | 
|      58 | mpeg2audtype             | Layer II      | 
|      58 | mpeg2audvolume           | 90            | 
|      58 | mpeg2bitrate             | 8000          | 
|      58 | mpeg2language            | 0             | 
|      58 | mpeg2maxbitrate          | 10000         | 
|      58 | mpeg2streamtype          | MPEG-2 PS     | 
|      58 | mpeg4bitrate             | 2200          | 
|      58 | mpeg4maxquality          | 2             | 
|      58 | mpeg4minquality          | 15            | 
|      58 | mpeg4option4mv           | 0             | 
|      58 | mpeg4optionidct          | 0             | 
|      58 | mpeg4optionime           | 0             | 
|      58 | mpeg4optionvhq           | 0             | 
|      58 | mpeg4qualdiff            | 3             | 
|      58 | rtjpegquality            | 170           | 
|      58 | samplerate               | 48000         | 
|      58 | scalebitrate             | 1             | 
|      58 | width                    | 720           | 
|      59 | autotranscode            | 0             | 
|      59 | encodingthreadcount      | 1             | 
|      59 | hardwaremjpeghdecimation | 4             | 
|      59 | hardwaremjpegquality     | 100           | 
|      59 | hardwaremjpegvdecimation | 4             | 
|      59 | height                   | 480           | 
|      59 | mpeg2aspectratio         | 4:3           | 
|      59 | mpeg2audbitratel1        | 448           | 
|      59 | mpeg2audbitratel2        | 384           | 
|      59 | mpeg2audbitratel3        | 192           | 
|      59 | mpeg2audtype             | Layer II      | 
|      59 | mpeg2audvolume           | 90            | 
|      59 | mpeg2bitrate             | 8000          | 
|      59 | mpeg2language            | 0             | 
|      59 | mpeg2maxbitrate          | 10000         | 
|      59 | mpeg2streamtype          | MPEG-2 PS     | 
|      59 | mpeg4bitrate             | 2200          | 
|      59 | mpeg4maxquality          | 2             | 
|      59 | mpeg4minquality          | 15            | 
|      59 | mpeg4option4mv           | 0             | 
|      59 | mpeg4optionidct          | 0             | 
|      59 | mpeg4optionime           | 0             | 
|      59 | mpeg4optionvhq           | 0             | 
|      59 | mpeg4qualdiff            | 3             | 
|      59 | rtjpegquality            | 170           | 
|      59 | samplerate               | 48000         | 
|      59 | scalebitrate             | 1             | 
|      59 | width                    | 720           | 
|      60 | autotranscode            | 0             | 
|      60 | encodingthreadcount      | 1             | 
|      60 | hardwaremjpeghdecimation | 4             | 
|      60 | hardwaremjpegquality     | 100           | 
|      60 | hardwaremjpegvdecimation | 4             | 
|      60 | height                   | 480           | 
|      60 | mpeg2aspectratio         | 4:3           | 
|      60 | mpeg2audbitratel1        | 448           | 
|      60 | mpeg2audbitratel2        | 384           | 
|      60 | mpeg2audbitratel3        | 192           | 
|      60 | mpeg2audtype             | Layer II      | 
|      60 | mpeg2audvolume           | 90            | 
|      60 | mpeg2bitrate             | 8000          | 
|      60 | mpeg2language            | 0             | 
|      60 | mpeg2maxbitrate          | 10000         | 
|      60 | mpeg2streamtype          | MPEG-2 PS     | 
|      60 | mpeg4bitrate             | 2200          | 
|      60 | mpeg4maxquality          | 2             | 
|      60 | mpeg4minquality          | 15            | 
|      60 | mpeg4option4mv           | 0             | 
|      60 | mpeg4optionidct          | 0             | 
|      60 | mpeg4optionime           | 0             | 
|      60 | mpeg4optionvhq           | 0             | 
|      60 | mpeg4qualdiff            | 3             | 
|      60 | rtjpegquality            | 170           | 
|      60 | samplerate               | 48000         | 
|      60 | scalebitrate             | 1             | 
|      60 | width                    | 720           | 
|      61 | autotranscode            | 0             | 
|      61 | encodingthreadcount      | 1             | 
|      61 | hardwaremjpeghdecimation | 4             | 
|      61 | hardwaremjpegquality     | 100           | 
|      61 | hardwaremjpegvdecimation | 4             | 
|      61 | height                   | 480           | 
|      61 | mpeg2aspectratio         | 4:3           | 
|      61 | mpeg2audbitratel1        | 448           | 
|      61 | mpeg2audbitratel2        | 384           | 
|      61 | mpeg2audbitratel3        | 192           | 
|      61 | mpeg2audtype             | Layer II      | 
|      61 | mpeg2audvolume           | 90            | 
|      61 | mpeg2bitrate             | 8000          | 
|      61 | mpeg2language            | 0             | 
|      61 | mpeg2maxbitrate          | 10000         | 
|      61 | mpeg2streamtype          | MPEG-2 PS     | 
|      61 | mpeg4bitrate             | 2200          | 
|      61 | mpeg4maxquality          | 2             | 
|      61 | mpeg4minquality          | 15            | 
|      61 | mpeg4option4mv           | 0             | 
|      61 | mpeg4optionidct          | 0             | 
|      61 | mpeg4optionime           | 0             | 
|      61 | mpeg4optionvhq           | 0             | 
|      61 | mpeg4qualdiff            | 3             | 
|      61 | rtjpegquality            | 170           | 
|      61 | samplerate               | 48000         | 
|      61 | scalebitrate             | 1             | 
|      61 | width                    | 720           | 
|      62 | autotranscode            | 0             | 
|      62 | encodingthreadcount      | 1             | 
|      62 | hardwaremjpeghdecimation | 4             | 
|      62 | hardwaremjpegquality     | 100           | 
|      62 | hardwaremjpegvdecimation | 4             | 
|      62 | height                   | 480           | 
|      62 | mpeg2aspectratio         | 4:3           | 
|      62 | mpeg2audbitratel1        | 448           | 
|      62 | mpeg2audbitratel2        | 384           | 
|      62 | mpeg2audbitratel3        | 192           | 
|      62 | mpeg2audtype             | Layer II      | 
|      62 | mpeg2audvolume           | 90            | 
|      62 | mpeg2bitrate             | 8000          | 
|      62 | mpeg2language            | 0             | 
|      62 | mpeg2maxbitrate          | 10000         | 
|      62 | mpeg2streamtype          | MPEG-2 PS     | 
|      62 | mpeg4bitrate             | 2200          | 
|      62 | mpeg4maxquality          | 2             | 
|      62 | mpeg4minquality          | 15            | 
|      62 | mpeg4option4mv           | 0             | 
|      62 | mpeg4optionidct          | 0             | 
|      62 | mpeg4optionime           | 0             | 
|      62 | mpeg4optionvhq           | 0             | 
|      62 | mpeg4qualdiff            | 3             | 
|      62 | rtjpegquality            | 170           | 
|      62 | samplerate               | 48000         | 
|      62 | scalebitrate             | 1             | 
|      62 | width                    | 720           | 
|      63 | autotranscode            | 0             | 
|      63 | encodingthreadcount      | 1             | 
|      63 | hardwaremjpeghdecimation | 4             | 
|      63 | hardwaremjpegquality     | 100           | 
|      63 | hardwaremjpegvdecimation | 4             | 
|      63 | height                   | 480           | 
|      63 | mpeg2aspectratio         | 4:3           | 
|      63 | mpeg2audbitratel1        | 448           | 
|      63 | mpeg2audbitratel2        | 384           | 
|      63 | mpeg2audbitratel3        | 192           | 
|      63 | mpeg2audtype             | Layer II      | 
|      63 | mpeg2audvolume           | 90            | 
|      63 | mpeg2bitrate             | 8000          | 
|      63 | mpeg2language            | 0             | 
|      63 | mpeg2maxbitrate          | 10000         | 
|      63 | mpeg2streamtype          | MPEG-2 PS     | 
|      63 | mpeg4bitrate             | 2200          | 
|      63 | mpeg4maxquality          | 2             | 
|      63 | mpeg4minquality          | 15            | 
|      63 | mpeg4option4mv           | 0             | 
|      63 | mpeg4optionidct          | 0             | 
|      63 | mpeg4optionime           | 0             | 
|      63 | mpeg4optionvhq           | 0             | 
|      63 | mpeg4qualdiff            | 3             | 
|      63 | rtjpegquality            | 170           | 
|      63 | samplerate               | 48000         | 
|      63 | scalebitrate             | 1             | 
|      63 | width                    | 720           | 
|      64 | autotranscode            | 0             | 
|      64 | encodingthreadcount      | 1             | 
|      64 | hardwaremjpeghdecimation | 4             | 
|      64 | hardwaremjpegquality     | 100           | 
|      64 | hardwaremjpegvdecimation | 4             | 
|      64 | height                   | 480           | 
|      64 | mpeg2aspectratio         | 4:3           | 
|      64 | mpeg2audbitratel1        | 448           | 
|      64 | mpeg2audbitratel2        | 384           | 
|      64 | mpeg2audbitratel3        | 192           | 
|      64 | mpeg2audtype             | Layer II      | 
|      64 | mpeg2audvolume           | 90            | 
|      64 | mpeg2bitrate             | 8000          | 
|      64 | mpeg2language            | 0             | 
|      64 | mpeg2maxbitrate          | 10000         | 
|      64 | mpeg2streamtype          | MPEG-2 PS     | 
|      64 | mpeg4bitrate             | 2200          | 
|      64 | mpeg4maxquality          | 2             | 
|      64 | mpeg4minquality          | 15            | 
|      64 | mpeg4option4mv           | 0             | 
|      64 | mpeg4optionidct          | 0             | 
|      64 | mpeg4optionime           | 0             | 
|      64 | mpeg4optionvhq           | 0             | 
|      64 | mpeg4qualdiff            | 3             | 
|      64 | rtjpegquality            | 170           | 
|      64 | samplerate               | 48000         | 
|      64 | scalebitrate             | 1             | 
|      64 | width                    | 720           | 
|      65 | autotranscode            | 0             | 
|      65 | encodingthreadcount      | 1             | 
|      65 | hardwaremjpeghdecimation | 4             | 
|      65 | hardwaremjpegquality     | 100           | 
|      65 | hardwaremjpegvdecimation | 4             | 
|      65 | height                   | 480           | 
|      65 | mpeg2aspectratio         | 4:3           | 
|      65 | mpeg2audbitratel1        | 448           | 
|      65 | mpeg2audbitratel2        | 384           | 
|      65 | mpeg2audbitratel3        | 192           | 
|      65 | mpeg2audtype             | Layer II      | 
|      65 | mpeg2audvolume           | 90            | 
|      65 | mpeg2bitrate             | 8000          | 
|      65 | mpeg2language            | 0             | 
|      65 | mpeg2maxbitrate          | 10000         | 
|      65 | mpeg2streamtype          | MPEG-2 PS     | 
|      65 | mpeg4bitrate             | 2200          | 
|      65 | mpeg4maxquality          | 2             | 
|      65 | mpeg4minquality          | 15            | 
|      65 | mpeg4option4mv           | 0             | 
|      65 | mpeg4optionidct          | 0             | 
|      65 | mpeg4optionime           | 0             | 
|      65 | mpeg4optionvhq           | 0             | 
|      65 | mpeg4qualdiff            | 3             | 
|      65 | rtjpegquality            | 170           | 
|      65 | samplerate               | 48000         | 
|      65 | scalebitrate             | 1             | 
|      65 | width                    | 720           | 
|      66 | autotranscode            | 0             | 
|      66 | encodingthreadcount      | 1             | 
|      66 | hardwaremjpeghdecimation | 4             | 
|      66 | hardwaremjpegquality     | 100           | 
|      66 | hardwaremjpegvdecimation | 4             | 
|      66 | height                   | 480           | 
|      66 | mpeg2aspectratio         | 4:3           | 
|      66 | mpeg2audbitratel1        | 448           | 
|      66 | mpeg2audbitratel2        | 384           | 
|      66 | mpeg2audbitratel3        | 192           | 
|      66 | mpeg2audtype             | Layer II      | 
|      66 | mpeg2audvolume           | 90            | 
|      66 | mpeg2bitrate             | 8000          | 
|      66 | mpeg2language            | 0             | 
|      66 | mpeg2maxbitrate          | 10000         | 
|      66 | mpeg2streamtype          | MPEG-2 PS     | 
|      66 | mpeg4bitrate             | 2200          | 
|      66 | mpeg4maxquality          | 2             | 
|      66 | mpeg4minquality          | 15            | 
|      66 | mpeg4option4mv           | 0             | 
|      66 | mpeg4optionidct          | 0             | 
|      66 | mpeg4optionime           | 0             | 
|      66 | mpeg4optionvhq           | 0             | 
|      66 | mpeg4qualdiff            | 3             | 
|      66 | rtjpegquality            | 170           | 
|      66 | samplerate               | 48000         | 
|      66 | scalebitrate             | 1             | 
|      66 | width                    | 720           | 
|      67 | autotranscode            | 0             | 
|      67 | encodingthreadcount      | 1             | 
|      67 | hardwaremjpeghdecimation | 4             | 
|      67 | hardwaremjpegquality     | 100           | 
|      67 | hardwaremjpegvdecimation | 4             | 
|      67 | height                   | 480           | 
|      67 | mpeg2aspectratio         | 4:3           | 
|      67 | mpeg2audbitratel1        | 448           | 
|      67 | mpeg2audbitratel2        | 384           | 
|      67 | mpeg2audbitratel3        | 192           | 
|      67 | mpeg2audtype             | Layer II      | 
|      67 | mpeg2audvolume           | 90            | 
|      67 | mpeg2bitrate             | 8000          | 
|      67 | mpeg2language            | 0             | 
|      67 | mpeg2maxbitrate          | 10000         | 
|      67 | mpeg2streamtype          | MPEG-2 PS     | 
|      67 | mpeg4bitrate             | 2200          | 
|      67 | mpeg4maxquality          | 2             | 
|      67 | mpeg4minquality          | 15            | 
|      67 | mpeg4option4mv           | 0             | 
|      67 | mpeg4optionidct          | 0             | 
|      67 | mpeg4optionime           | 0             | 
|      67 | mpeg4optionvhq           | 0             | 
|      67 | mpeg4qualdiff            | 3             | 
|      67 | rtjpegquality            | 170           | 
|      67 | samplerate               | 48000         | 
|      67 | scalebitrate             | 1             | 
|      67 | width                    | 720           | 
|      68 | autotranscode            | 0             | 
|      68 | encodingthreadcount      | 1             | 
|      68 | hardwaremjpeghdecimation | 4             | 
|      68 | hardwaremjpegquality     | 100           | 
|      68 | hardwaremjpegvdecimation | 4             | 
|      68 | height                   | 480           | 
|      68 | mpeg2aspectratio         | 4:3           | 
|      68 | mpeg2audbitratel1        | 448           | 
|      68 | mpeg2audbitratel2        | 384           | 
|      68 | mpeg2audbitratel3        | 192           | 
|      68 | mpeg2audtype             | Layer II      | 
|      68 | mpeg2audvolume           | 90            | 
|      68 | mpeg2bitrate             | 8000          | 
|      68 | mpeg2language            | 0             | 
|      68 | mpeg2maxbitrate          | 10000         | 
|      68 | mpeg2streamtype          | MPEG-2 PS     | 
|      68 | mpeg4bitrate             | 2200          | 
|      68 | mpeg4maxquality          | 2             | 
|      68 | mpeg4minquality          | 15            | 
|      68 | mpeg4option4mv           | 0             | 
|      68 | mpeg4optionidct          | 0             | 
|      68 | mpeg4optionime           | 0             | 
|      68 | mpeg4optionvhq           | 0             | 
|      68 | mpeg4qualdiff            | 3             | 
|      68 | rtjpegquality            | 170           | 
|      68 | samplerate               | 48000         | 
|      68 | scalebitrate             | 1             | 
|      68 | width                    | 720           | 
|      69 | autotranscode            | 0             | 
|      69 | encodingthreadcount      | 1             | 
|      69 | hardwaremjpeghdecimation | 4             | 
|      69 | hardwaremjpegquality     | 100           | 
|      69 | hardwaremjpegvdecimation | 4             | 
|      69 | height                   | 480           | 
|      69 | mpeg2aspectratio         | 4:3           | 
|      69 | mpeg2audbitratel1        | 448           | 
|      69 | mpeg2audbitratel2        | 384           | 
|      69 | mpeg2audbitratel3        | 192           | 
|      69 | mpeg2audtype             | Layer II      | 
|      69 | mpeg2audvolume           | 90            | 
|      69 | mpeg2bitrate             | 8000          | 
|      69 | mpeg2language            | 0             | 
|      69 | mpeg2maxbitrate          | 10000         | 
|      69 | mpeg2streamtype          | MPEG-2 PS     | 
|      69 | mpeg4bitrate             | 2200          | 
|      69 | mpeg4maxquality          | 2             | 
|      69 | mpeg4minquality          | 15            | 
|      69 | mpeg4option4mv           | 0             | 
|      69 | mpeg4optionidct          | 0             | 
|      69 | mpeg4optionime           | 0             | 
|      69 | mpeg4optionvhq           | 0             | 
|      69 | mpeg4qualdiff            | 3             | 
|      69 | rtjpegquality            | 170           | 
|      69 | samplerate               | 48000         | 
|      69 | scalebitrate             | 1             | 
|      69 | width                    | 720           | 
|      70 | autotranscode            | 0             | 
|      70 | encodingthreadcount      | 1             | 
|      70 | hardwaremjpeghdecimation | 4             | 
|      70 | hardwaremjpegquality     | 100           | 
|      70 | hardwaremjpegvdecimation | 4             | 
|      70 | height                   | 480           | 
|      70 | mpeg2aspectratio         | 4:3           | 
|      70 | mpeg2audbitratel1        | 448           | 
|      70 | mpeg2audbitratel2        | 384           | 
|      70 | mpeg2audbitratel3        | 192           | 
|      70 | mpeg2audtype             | Layer II      | 
|      70 | mpeg2audvolume           | 90            | 
|      70 | mpeg2bitrate             | 8000          | 
|      70 | mpeg2language            | 0             | 
|      70 | mpeg2maxbitrate          | 10000         | 
|      70 | mpeg2streamtype          | MPEG-2 PS     | 
|      70 | mpeg4bitrate             | 2200          | 
|      70 | mpeg4maxquality          | 2             | 
|      70 | mpeg4minquality          | 15            | 
|      70 | mpeg4option4mv           | 0             | 
|      70 | mpeg4optionidct          | 0             | 
|      70 | mpeg4optionime           | 0             | 
|      70 | mpeg4optionvhq           | 0             | 
|      70 | mpeg4qualdiff            | 3             | 
|      70 | rtjpegquality            | 170           | 
|      70 | samplerate               | 48000         | 
|      70 | scalebitrate             | 1             | 
|      70 | width                    | 720           | 
+---------+--------------------------+---------------+
501 rows in set (0.00 sec)

```

and the dump of recordingprofiles:
```

mysql> select * from recordingprofiles
    -> ;
+----+--------------------+-------------------------+-------------------------+--------------+
| id | name               | videocodec              | audiocodec              | profilegroup |
+----+--------------------+-------------------------+-------------------------+--------------+
|  1 | Default            | NULL                    | NULL                    |            1 | 
|  2 | Live TV            | NULL                    | NULL                    |            1 | 
|  3 | High Quality       | NULL                    | NULL                    |            1 | 
|  4 | Low Quality        | NULL                    | NULL                    |            1 | 
|  5 | Default            | MPEG-2 Hardware Encoder | MPEG-2 Hardware Encoder |            2 | 
|  6 | Live TV            | NULL                    | NULL                    |            2 | 
|  7 | High Quality       | NULL                    | NULL                    |            2 | 
|  8 | Low Quality        | NULL                    | NULL                    |            2 | 
|  9 | Default            | NULL                    | NULL                    |            3 | 
| 10 | Live TV            | NULL                    | NULL                    |            3 | 
| 11 | High Quality       | NULL                    | NULL                    |            3 | 
| 12 | Low Quality        | NULL                    | NULL                    |            3 | 
| 13 | Default            | NULL                    | NULL                    |            4 | 
| 14 | Live TV            | NULL                    | NULL                    |            4 | 
| 15 | High Quality       | NULL                    | NULL                    |            4 | 
| 16 | Low Quality        | NULL                    | NULL                    |            4 | 
| 17 | Default            | NULL                    | NULL                    |            5 | 
| 18 | Live TV            | NULL                    | NULL                    |            5 | 
| 19 | High Quality       | NULL                    | NULL                    |            5 | 
| 20 | Low Quality        | NULL                    | NULL                    |            5 | 
| 21 | RTjpeg/MPEG4       | NULL                    | NULL                    |            6 | 
| 22 | MPEG2              | RTjpeg                  | MP3                     |            6 | 
| 23 | Default            | NULL                    | NULL                    |            8 | 
| 24 | Live TV            | NULL                    | NULL                    |            8 | 
| 25 | High Quality       | NULL                    | NULL                    |            8 | 
| 26 | Low Quality        | NULL                    | NULL                    |            8 | 
| 27 | High Quality       | NULL                    | NULL                    |            6 | 
| 28 | Medium Quality     | NULL                    | NULL                    |            6 | 
| 29 | Low Quality        | NULL                    | NULL                    |            6 | 
| 30 | Default            | NULL                    | NULL                    |           10 | 
| 31 | Live TV            | NULL                    | NULL                    |           10 | 
| 32 | High Quality       | NULL                    | NULL                    |           10 | 
| 33 | Low Quality        | NULL                    | NULL                    |           10 | 
| 34 | Default            | NULL                    | NULL                    |           11 | 
| 35 | Live TV            | NULL                    | NULL                    |           11 | 
| 36 | High Quality       | NULL                    | NULL                    |           11 | 
| 37 | Low Quality        | NULL                    | NULL                    |           11 | 
| 38 | Default            | NULL                    | NULL                    |           12 | 
| 39 | Live TV            | NULL                    | NULL                    |           12 | 
| 40 | High Quality       | NULL                    | NULL                    |           12 | 
| 41 | Low Quality        | NULL                    | NULL                    |           12 | 
| 42 | Default            | NULL                    | NULL                    |            7 | 
| 43 | Live TV            | NULL                    | NULL                    |            7 | 
| 44 | High Quality       | NULL                    | NULL                    |            7 | 
| 45 | Low Quality        | NULL                    | NULL                    |            7 | 
| 46 | Default            | NULL                    | NULL                    |            9 | 
| 47 | Live TV            | NULL                    | NULL                    |            9 | 
| 48 | High Quality       | NULL                    | NULL                    |            9 | 
| 49 | Low Quality        | NULL                    | NULL                    |            9 | 
| 50 | Default            | NULL                    | NULL                    |           13 | 
| 51 | Live TV            | NULL                    | NULL                    |           13 | 
| 52 | High Quality       | NULL                    | NULL                    |           13 | 
| 53 | Low Quality        | NULL                    | NULL                    |           13 | 
| 54 | 720x480 Test       | MPEG-2 Hardware Encoder | MPEG-2 Hardware Encoder |           13 | 
| 55 | 720x480            | MPEG-2 Hardware Encoder | MPEG-2 Hardware Encoder |            2 | 
| 56 | 720x480 Transcoder | MPEG-4                  | MP3                     |            6 | 
| 57 | TestingProfiles    | MPEG-2 Hardware Encoder | MPEG-2 Hardware Encoder |            2 | 
| 58 | testing70          | NULL                    | NULL                    |            1 | 
| 59 | testing2           | NULL                    | NULL                    |            2 | 
| 60 | testing3           | NULL                    | NULL                    |            3 | 
| 61 | testing4           | NULL                    | NULL                    |            4 | 
| 62 | testing5           | NULL                    | NULL                    |            5 | 
| 63 | testing6           | NULL                    | NULL                    |            6 | 
| 64 | testing7           | NULL                    | NULL                    |            7 | 
| 65 | testing8           | NULL                    | NULL                    |            8 | 
| 66 | testing9           | NULL                    | NULL                    |            9 | 
| 67 | testing10          | NULL                    | NULL                    |           10 | 
| 68 | testing11          | NULL                    | NULL                    |           11 | 
| 69 | testing12          | NULL                    | NULL                    |           12 | 
| 70 | testing13          | NULL                    | NULL                    |           13 | 
+----+--------------------+-------------------------+-------------------------+--------------+
70 rows in set (0.06 sec)

```

(and yes, the error existed before i added in all the testing70, testing2, testing3, testing4, testing5...)

and finally...  profilegroups
```

mysql> select * from profilegroups;
+----+----------------------------------------------------------+-----------+------------+-------------+
| id | name                                                     | cardtype  | is_default | hostname    |
+----+----------------------------------------------------------+-----------+------------+-------------+
|  1 | Software Encoders (v4l based)                            | V4L       |          1 | NULL        | 
|  2 | MPEG-2 Encoders (PVR-x50, PVR-500)                       | MPEG      |          1 | NULL        | 
|  3 | Hardware MJPEG Encoders (Matrox G200-TV, Miro DC10, etc) | MJPEG     |          1 | NULL        | 
|  4 | Hardware HDTV                                            | HDTV      |          1 | NULL        | 
|  5 | Hardware DVB Encoders                                    | DVB       |          1 | NULL        | 
|  6 | Transcoders                                              | TRANSCODE |          1 | NULL        | 
|  7 | FireWire Input                                           | FIREWIRE  |          1 | NULL        | 
|  8 | USB Mpeg-4 Encoder (Plextor ConvertX, etc)               | GO7007    |          1 | NULL        | 
|  9 | DBOX2 Input                                              | DBOX2     |          1 | NULL        | 
| 10 | Freebox Input                                            | Freebox   |          1 | NULL        | 
| 11 | HDHomeRun Recorders                                      | HDHOMERUN |          1 | NULL        | 
| 12 | CRC IP Recorders                                         | CRC_IP    |          1 | NULL        | 
| 13 | 720x480 Test                                             | MPEG      |          0 | mainmachine | 
+----+----------------------------------------------------------+-----------+------------+-------------+
13 rows in set (0.00 sec)

```

---

### Post by OmahaVike on 2008-11-11
finally found some time to get this solved.

uninstalled, and purged, and manually wiped the db, of myth.

set v4l2 to 720x480 (again)

installed & configured mythtv.  default was already set for 720x480.

sample recording resulted in 720x480.

good luck to all.

---

