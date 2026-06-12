---
title: "Kdenlive: Very bad/video audio quality after rendering"
date: 2016-12-28
forum: Multimedia Software
---

### Post by tina-9 on 2016-12-28
Hello,

I'm new to Kdenlive and could not find an answer for my question in the old topics. 

I  use Kdenlive 15.12.3 (KDE Frameworks 5.18.0 Qt 5.5.1 (kompiliert gegen  5.5.1) ) with an Ubuntu 16.04 LTS system. I made a video by cutting and  arranging several video clips and photos and adding audio. In Kdenlive,  the finished clip runs smoothly and in good quality in den "Project  Explorer" (Preview). 
However, the result of rendering is awful. The  finished video is very bad quality, edges of pictures are wobbly and the  sound is severely deteriorated.  [IMG]https://forum.kde.org/images/smilies/sad.gif[/IMG]   I tried several codecs, but the results always was really bad. The  "best" results I got using  "Lossless/HQ", MJPEG (mjpeg+pcm_16le),  (video kind of ok, but sound deteriorated). I tried like 10 other  options with results differing in the details, but none was even close  to acceptable. I tried to play the rendered videos in the standard ubuntu Video player and in vlc. This did not make any difference.

How can I get Kdenlive to rendering a clip with  useful audio and video quality? Any help is appreciated, as it would be a  lot of work to redo the clip arrangement in another program... Because  Kdenlive worked so nicely in the preview mode, I never expected the  rendering to be a problem. Before, I had tried OpenShot, that rendered  nicely, but chrashed often during editing the video...

Best regards, Tina

---

### Post by aadamowski on 2017-03-19
Hello Tina,

This might be caused by a bug where proxy clips are used in rendering, regardless of the "Use proxy clips for rendering" render setting.

The workaround is to disable proxies on all the clips in the project before rendering, then re-enabling them afterwards:

[https://forum.kde.org/viewtopic.php?f=265&t=136986#p366468](https://forum.kde.org/viewtopic.php?f=265&t=136986#p366468)

---

