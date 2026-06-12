---
title: "mythtv cuts off right side of picture"
date: 2009-02-18
forum: Multimedia Software
---

### Post by antitroll on 2009-02-18
I'm having a problem with MythTV. I can watch TV just fine using VLC and ivtv-tune, but if I try to use MythTV, the right screen of the screen is cut off by ~10% (see attached screenshot).

If I exit out of MythTV and then use VLC again, the picture is still cut off on the right side. I have to reboot to fix the problem.

Any help would be appreciated. Let me know if I need to provide more information.

OS: Ubuntu 8.10
MythTV version: MythTV 0.21.0+fixes20005-openglvdpau-0ubuntu0
Capture Card: HVR-1600
Video Card Driver: Nvidia 180.29

MythTV Configuration
Card type: IVTV MPEG-2 encoder card
Video device: /dev/video0
Probed info: Hauppauge HVR-1600 [cx18]
Default input: Tuner 1

xdpyinfo output:
default screen number:    0
number of screens:    1

screen #0:
  dimensions:    1680x1050 pixels (427x267 millimeters)
  resolution:    100x100 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32
  root window id:    0x13b
  depth of root window:    24 planes
  number of colormaps:    minimum 1, maximum 1
  default colormap:    0x20
  default number of colormap cells:    256
  preallocated pixels:    black 0, white 16777215
  options:    backing-store NO, save-unders NO
  largest cursor:    64x64
  current input event mask:    0x7a807f
    KeyPressMask             KeyReleaseMask           ButtonPressMask          
    ButtonReleaseMask        EnterWindowMask          LeaveWindowMask          
    PointerMotionMask        ExposureMask             StructureNotifyMask      
    SubstructureNotifyMask   SubstructureRedirectMask FocusChangeMask          
    PropertyChangeMask       
  number of visuals:    84

---

### Post by punx45 on 2009-02-18
check the overscan settings in MythTV in the general settings.  in my version the path is 

Utilities / Setup > Setup > TV Settings > Playback and hit next until the Overscan section.   mine is set to 2 for vertical, 0 for everything else   if this is the problem your X or Y displacement settings might be off.

---

### Post by antitroll on 2009-02-19
Playing with the [overscan settings]("http://www.mythtv.org/wiki/Overscan") didn't help. I set the x displayment to -50 (max within the GUI) hoping that the picture would move to the left, no dice. It just cut off part of the left side in addition to the right.

I compared the output of "v4l2-ctl --all" while using VLC (see attached v4l2-ctl_good.txt) and while using MythTV (v4l-ctl_bad.txt).

MythTV appears to be setting the Video Capture Width/Height to 480/480 instead of 720/480.

v4l2-ctl_bad.txt:
Format Video Capture:
	Width/Height  : 480/480
	Pixel Format  : MPEG
	Field         : Interlaced
	Bytes per Line: 0
	Size Image    : 131072
	Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)

v4l2-ctl_good.txt:
Format Video Capture:
	Width/Height  : 720/480
	Pixel Format  : MPEG
	Field         : Interlaced
	Bytes per Line: 0
	Size Image    : 131072
	Colorspace    : Broadcast NTSC/PAL (SMPTE170M/ITU601)

This is also the case in the stdout of MythTV, which is somehow expecting 480/480 to have aspect ratio of 1.33

MythTV.txt:
2009-02-19 18:21:26.404 Video Rect    left: 0, top: 0, width: 480, height: 480, aspect: 1.33333

At least I don't have to reboot to fix the problem and get VLC working properly again. The following command sets the width and height back to what they were before using MythTV:
v4l2-ctl --set-fmt-video=width=720,height=480

As always, any help is appreciated.

---

### Post by antitroll on 2009-02-19
The problem was that by default all the recording profiles in MythTV are set to 480x480. I change them all to 720x480 and the problem was solved.

From mythfrontend:
Utilities / Setup > Setup > TV Settings > Recording Profiles

Select MPEG-2 Encoders (PVR-x50, PVR-500). For each profile in the list:
Default
Live TV
High Quality
Low Quality

Set the "image size":
Width:                       Height:

as appropriate for your card.

In my case, I changed them all from 480x480 to 720x480.

---

