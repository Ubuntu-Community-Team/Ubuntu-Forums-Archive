---
title: "CCTV camera setup problem."
date: 2012-09-20
forum: Multimedia Software
---

### Post by jaisol on 2012-09-20
I'm trying to set up a CCTV camera on a unbuntu 10.04.

Im using a pico 2000 clone card (BT843 or something like that).
I think my system reconises it ok - not 100% sure.

I'm using Xawtv software as it's already installed.

running xawtv -hwscan give the following
> 
oot@james-desktop:/home/james# xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-43-generic)
looking for available devices
port 89-104
    type : Xvideo, image scaler
    name : Intel(R) Teoot@james-desktop:/home/james# xawtv -hwscan
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-43-generic)
looking for available devices
port 89-104
    type : Xvideo, image scaler
    name : Intel(R) Textured Video

port 105-105
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (GrandTec Multi Cap
    flags: overlay capture  
xtured Video

port 105-105
    type : Xvideo, image scaler
    name : Intel(R) Video Overlay

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (GrandTec Multi Cap
    flags: overlay capture  

Running Xawtv from a terminal gives me this - 
> root@james-desktop:/home/james# xawtv -c /dev/video0
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.32-43-generic)
xinerama 0: 1920x1080+0+0
WARNING: No DGA direct video mode for this display.
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=221184;flags=0x1 [MAPPED];field=BOTTOM;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=28;memory=MMAP): Invalid argument
ioctl: VIDIOC_QBUF(index=0;type=VIDEO_CAPTURE;bytesused=221184;flags=0x1 [MAPPED];field=BOTTOM;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=28;memory=MMAP): Invalid argument

I'm not to sure what that lot means.

I did search the web and found I had to add a file to my modprobe.d folder, I did that and I think the system reconises the card ok. 

Any help would be apreciated

---

