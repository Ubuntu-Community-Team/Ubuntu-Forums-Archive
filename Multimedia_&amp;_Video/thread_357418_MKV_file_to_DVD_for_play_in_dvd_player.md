---
title: "MKV file to DVD for play in dvd player"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by paulstaf on 2007-02-09
I have searched and read on and on, but I cannot find any way to convert a video.MKV to a DVD. 

I have tried the video-convert script for Nautilus but it just comes up and says that "you have not selected a valid video type. MimeType= application/octet-stream" error.

I want to take the MKV file and put it on a DVD so that I can watch it on my entertainment system and not the PC.

I am new to Linux and a basic step by step would help.

I have tried:
mencoder /home/testing.mkv -ovc copy -oac copy -o /home/test.avi 

and it runs for a few seconds and then says:  
****************************************************************
Pos: 210.3s   4584f ( 2%) 1130.46fps Trem:   3min 1889mb  A-V:-0.054 [1404:128]
Too many audio packets in the buffer: (4099 in 7345408 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream: 1404.107 kbit/s  (175513 B/s)  size: 36901991 bytes  210.252 secs  4584 frames

Audio stream:  128.000 kbit/s  (16000 B/s)  size: 3379200 bytes  211.200 secs
********************************************************************************

Any help would be greatly appreciated.

Thanks

---

### Post by zerosystem on 2007-02-11
I'm having this problem too, but I'm guessing it's with how the MKV file was encoded, as I have this one MKV that will encode fine with the same command you used, but not with another one.

---

