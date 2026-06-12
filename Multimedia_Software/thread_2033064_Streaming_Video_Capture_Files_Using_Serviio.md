---
title: "Streaming Video Capture Files Using Serviio"
date: 2012-07-25
forum: Multimedia Software
---

### Post by neutronforrest on 2012-07-25
**Ubuntu and DVR Options**             
                                                                Hi Forum,

Last week I bought a Hauppauge WinTV-HVR-1250 video card.  I installed  the card and went into dmegs and see the OS sees the card.  

[HTML][18.141236] CORE cx23885[0]: subsystem: 0070:7911, board: Hauppauge WinTV-HVR1250 [card=3,autodetected][/HTML]I have installed Kaffeine to record live tv.  Once the tv show is  recorded I am able to play it back on my linux box as a .mpg file.   However, I am unable to stream it to my Samsung TV.  I have many movies  that are .mpg and .avi that stream without any issues.  I have come  across what I believe the issus in that if I take a working .mpg file  that streams over wifi and using ffmpeg I get the following.


[HTML] libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[mpeg @ 0x20f4560] max_analyze_duration reached
Input #0, mpeg, from 'HomeMovie.mpg':
  Duration: 00:29:20.16, start: 1.000000, bitrate: 3681 kb/s
    Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 104857 kb/s, 24 fps, 24 tbr, 90k tbn, 24 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 128 kb/s
At least one output file must be specified[/HTML]However, when I record a program off a clear QAM channel I get the following from ffmegs

[HTML]libavutil    51.  7. 0 / 51.  7. 0
  libavcodec   53.  6. 0 / 53.  6. 0
  libavformat  53.  3. 0 / 53.  3. 0
  libavdevice  53.  0. 0 / 53.  0. 0
  libavfilter   2.  4. 0 /  2.  4. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  52.  0. 0 / 52.  0. 0
[mpeg2video @ 0x1ec6ae0] mpeg_decode_postinit() failure
    Last message repeated 12 times
Input #0, mpegts, from 'TestRecordTV.mpg':
  Duration: 00:09:59.82, start: 84410.203100, bitrate: 13445 kb/s
  Program 8 
    Stream #0.0[0x24]: Video: mpeg2video (Main), yuv420p, 1920x1080 [PAR  1:1 DAR 16:9], 14437 kb/s, 33.23 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x25](eng): Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
At least one output file must be specified[/HTML]have read the forums and I am starting to understand that the recoded  file has extra information.  What can I do to record the file that is  able to stream from Serviio to my Samsung tv.  What does;

[HTML][mpeg2video @ 0x1ec6ae0] mpeg_decode_postinit() failure[/HTML]mean...Please Help...CJ


Thanks...CJ

---

