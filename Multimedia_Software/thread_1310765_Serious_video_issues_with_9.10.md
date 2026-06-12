---
title: "Serious video issues with 9.10"
date: 2009-11-02
forum: Multimedia Software
---

### Post by the hoplite on 2009-11-02
Hi guys, so this is my 4th install of the Koala, the first two were RC so I thought that was the problem..
It can't play Divx, with the vlc and the extra repositories enabled (via Ubuntu Tweak). 

This is the output:
lu@lu-laptop:~/Desktop$ vlc Video.avi
VLC media player 1.0.2 Goldeneye
+[0x914f128] main interface error: no interface module matched "globalhotkeys,none"
[0x914f128] main interface error: no suitable interface module
[0x90a5140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x90a5140] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xb7313ef8] avcodec decoder error: cannot open codec (MPEG-4 Video)
[0xb7313ef8] main decoder error: no suitable decoder module for fourcc `XVID'.
VLC probably does not support this sound or video format.
[0x935c448] pulse audio output: No. of Audio Channels: 2

And so if I try to install ffmpeg:
ffmpeg:
 Depends: libavcodec52 but it is not going to be installed or
 	libavcodec-extra-52 (<4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
 Depends: libavdevice52 but it is not going to be installed or
 	libavdevice-extra-52 (<4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
 Depends: libavfilter0 but it is not going to be installed or
 	libavfilter-extra-0 (<4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
 Depends: libavformat52 but it is not going to be installed or
 	libavformat-extra-52 (<4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed
 Depends: libswscale0 but it is not going to be installed or
 	libswscale-extra-0 (<4:0.5+svn20090706-99) but 4:0.5+svn20090926-0ubuntu3~tj~ppa1k is to be installed

This is my first Ubuntu distribution not working out of the box (I have repositories issues too). I'm really confused, please help. Roger and out.

---

