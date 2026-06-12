---
title: "vlc+webcam = &gt;:("
date: 2010-11-17
forum: Multimedia Software
---

### Post by scottch.eezem on 2010-11-17
Hi all, been knocking my head on my desk trying to fix a new problem with vlc and my logitech quick cam.

Basically I had a really nice setup where I could remotely turn on streaming from my logitech quick cam connected to my ubuntu machine via script.  But after I updated to lucid, I was tempted by the possibility of being able to stream to an iphone/android in the latest vlc nightly I attempted to add the software source and get working.  This was a total fail, could not run it at all.  So I attempted to revert back to 1.06 ( the latest stable that I know of) by doing a complete remove and reinstall of vlc through synaptic. After getting it back to the point where I could launch vlc without errors, I tried to access my webcam in the usual way (open capture device...) but now, I am not able to get any output what so ever!  I can still access the output via Cheese, guvcview, and I can even do something like

cat /dev/video1 > temp 

then open temp and see a picture.  but with vlc when I try to open I get a variety of errors.  when I run my script (which is just a call to vlc with some appropriate arguments that have always worked in the past) I get

[0x96d4f38] main decoder warning: can't get output picture

 for every time it tried to read a new frame from the cam



output of lsusb

Bus 002 Device 002: ID 046d:08da Logitech, Inc. QuickCam Messanger


dmesg shows 

[63577.615211] zc3xx: probe 2wr ov vga 0x0000

and fwiw

lsmod | grep gspca
gspca_zc3xx            45189  0 
gspca_main             21199  1 gspca_zc3xx
videodev               34361  5 tuner,cx8800,cx88xx,v4l2_common,gspca_main

which brings up another point. I also have an old tv tunner card which still works fine in vlc tvtime and other programs

---

