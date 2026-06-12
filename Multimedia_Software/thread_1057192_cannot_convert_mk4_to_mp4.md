---
title: "cannot convert mk4 to mp4"
date: 2009-02-01
forum: Multimedia Software
---

### Post by kwilliams0 on 2009-02-01
For some reason I could not reply in this thread: [http://ubuntuforums.org/showthread.php?t=548547&page=6](http://ubuntuforums.org/showthread.php?t=548547&page=6) so I am creating a new one.

First off, thanks for the pointers on converting mkv to mp4 on that thread.  I have the video and audio parsed out, however, when I run this command:

> neroAacEnc -ignorelength -q 0.20 -if audiodump.wav -of audio.m4a & mplayer  audio.ac3 -vc null -vo null -ao pcm:fast -channels 6 -novideo

I get the following error:

> *************************************************************
*                                                           *
*  Nero AAC Encoder                                         *
*  Copyright 2008 Nero AG                                   *
*  All Rights Reserved Worldwide                            *
*                                                           *
*  Package build date: Sep 17 2008                          *
*  Package version:    1.3.3.0                              *
*                                                           *
*  See -help for a complete list of available parameters.   *
*                                                           *
*************************************************************

MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ (Family: 15, Model: 75, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Option msglevel: Unknown suboption 5
Warning unknown option msglevel at line 5
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/kevin/Videos/300/audio.ac3.
libavformat file format detected.
[mp3 @ 0xbe8990]Could not find codec parameters (Audio: mp1, 224 kb/s)
LAVF_header: av_find_stream_info() failed
libavformat file format detected.
[mp3 @ 0xbe8990]Could not find codec parameters (Audio: mp1, 224 kb/s)
LAVF_header: av_find_stream_info() failed


Exiting... (End of file)


I've beaten my head on this now for 8 hours, so am finally posting :)  I'm running Ubuntu Intrepid 64 bit if that matters at all?

Any help, or pointers on what I can try next to resolve would help a lot!

---

### Post by kwilliams0 on 2009-02-01
Still troubleshooting.  Turned up debug logging on mplayer, and go the following right before the failure:

> Checking for Nullsoft Streaming Video
Checking for MOV
Checking for VIVO
Checking for PVA
Checking for MPEG-TS...
TRIED UP TO POSITION 69855, FOUND 47, packet_size= 0, SEEMS A TS? 0
Checking for LMLM4 Stream Format
Invalid packet in LMLM4 stream: ch=32766 size=-63144518
LMLM4 Stream Format not found
sync_mpeg_ps: seems to be MP3 stream...
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 8  p101: 1 p1B6: 0 p12x: 0 sli: 2 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 105, synced: 0
sync_mpeg_ps: seems to be MP3 stream...
MPEG Stream reached EOF
ds_fill_buffer: EOF reached (stream: video)  
MPEG packet stats: p100: 8  p101: 1 p1B6: 0 p12x: 0 sli: 2 a: 0 b: 0 c: 0 idr: 0 sps: 0 pps: 0 PES: 0  MP3: 105, synced: 0
==> Found video stream: 0
==> Found audio stream: 0
ds_fill_buffer: EOF reached (stream: video)  
LAVF_check: MPEG audio
libavformat file format detected.
[mp3 @ 0xbe8990]Could not find codec parameters (Audio: mp1, 224 kb/s)
LAVF_header: av_find_stream_info() failed
Checking for DV
demux_aac_probe, failed to detect an AAC stream

vo: x11 uninit called but X11 not inited..

Exiting... (End of file)



I checked my config and I am using xv not xll, besides, I have the video set to null, so not sure why that would show up at all?

Any help would be great!

---

