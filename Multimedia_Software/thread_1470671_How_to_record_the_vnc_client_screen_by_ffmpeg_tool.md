---
title: "How to record the vnc client screen by ffmpeg tool."
date: 2010-05-03
forum: Multimedia Software
---

### Post by alex188 on 2010-05-03
Hi everyone,

  I have a special application. That is I need to use VNC Client to login server and control the server to do something. Then I need to record my VNC screen. So, I used the command "sudo ffmpeg -f x11grab -r 30 -s 800x600 -i :0.0 -vcodec libx264 -vpre hq -threads 0 out1.avi" to record screen, but the video content is server screen not my VNC screen. 

  I check my export variable and get the DISPLAY variable is ":2.0". So I change my command to record ":2.0" and there is error occur. The following is error message.

[alex@taipei:~$] export | grep DISPLAY
declare -x DISPLAY=":2.0"
[alex@taipei:~$] sudo ffmpeg -f x11grab -r 30 -s 800x600 -i :2.0 -vcodec libx264 -vpre lossless_ultrafast -threads 0 out1.avi

FFmpeg version SVN-r23008, Copyright (c) 2000-2010 the FFmpeg developers
  built on May  3 2010 11:42:42 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.15. 0 / 50.15. 0
  libavcodec    52.66. 0 / 52.66. 0
  libavformat   52.62. 0 / 52.62. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0.10. 0 /  0.10. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[x11grab @ 0xaa38420]device: :2.0 -> display: :2.0 x: 0 y: 0 width: 800 height: 600
Xlib:  extension "Generic Event Extension" missing on display ":2.0".
[x11grab @ 0xaa38420]shared memory extension  found
Segmentation fault
[alex@taipei:~$]  

Could anyone give some suggestions for this problem. Thanks a lot!!

---

### Post by alex188 on 2010-05-03
Could anyone give some suggestions, I will appreciate for it. Thanks!!

---

