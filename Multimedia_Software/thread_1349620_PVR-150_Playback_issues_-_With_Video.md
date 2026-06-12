---
title: "PVR-150 Playback issues - With Video"
date: 2009-12-08
forum: Multimedia Software
---

### Post by aflores3 on 2009-12-08
I'm not sure if this belongs here or in the Hardware forum... please move me if I in the wrong place.

I'm relatively new to linux and I've been messing with mythtv for about 6 weeks.

I have a slave backend running mythbuntu 9.10 (kernel 2.6.31) I also have a pvr-150 installed with a TimeWarner STB. I'm running IVTV version 1.4.0. I added the channels by importing from schedulesdirect

When I use cat /dev/video0 > test.mpg or when I try to watch the PVR-150 in mythtv, the results are as follows: [YouTube - MythTV Playback Issues - Example]("http://www.youtube.com/watch?v=-MhFVvh8rr0")

Any idea as to what might be causing this?

---

### Post by aflores3 on 2009-12-09
On another forum, I was asked to post the output from **/usr/bin/v4l2-ctl --all**, so I thought I'd do it here too:
```
Driver Info:
	Driver name   : ivtv
	Card type     : Hauppauge WinTV PVR-150
	Bus info      : PCI:0000:04:09.0
	Driver version: 66561
	Capabilities  : 0x01030051
		Video Capture
		VBI Capture
		Sliced VBI Capture
		Tuner
		Audio
		Read/Write
Format Video Capture:
	Width/Height  : 480/480
	Pixel Format  : 'MPEG'
	Field         : Interlaced
	Bytes per Line: 0
	Size Image    : 131072
	Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)
Format Sliced VBI Capture:
	Service Set    : cc
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
	Service Line 10:       cc / cc      
	Service Line 11:       cc / cc      
	Service Line 12:       cc / cc      
	Service Line 13:       cc / cc      
	Service Line 14:       cc / cc      
	Service Line 15:       cc / cc      
	Service Line 16:       cc / cc      
	Service Line 17:       cc / cc      
	Service Line 18:       cc / cc      
	Service Line 19:       cc / cc      
	Service Line 20:       cc / cc      
	Service Line 21:       cc / cc      
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
Crop Capability Video Output:
	Bounds      : Left 0, Top 0, Width 720, Height 480
	Default     : Left 0, Top 0, Width 720, Height 480
	Pixel Aspect: 10/11
Video input : 0 (Tuner 1)
Audio input : 0 (Tuner 1)
Frequency: 980 (61.250000 MHz)
Video Standard = 0x0000b000
	NTSC-M/M-JP/M-KR
Tuner:
	Name                 : ivtv TV Tuner
	Capabilities         : 62.5 kHz multi-standard stereo lang1 lang2 
	Frequency range      : 44.0 MHz - 958.0 MHz
	Signal strength/AFC  : 99%/0
	Current audio mode   : lang1
	Available subchannels: stereo

```

---

