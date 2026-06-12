---
title: "&quot;AC EOB marker is absent&quot; error in Kdenlive/ffmpeg when rendering a video"
date: 2015-07-16
forum: Multimedia Software
---

### Post by tom197 on 2015-07-16
Hello,

I am using Kdenlive 0.9.10 in Ubuntu 12.04 to render a video project from a group of .avi DV video-clips. If I select mp4 H.264/AAC High Profile as output format, Kdenlive crashes after a few seconds with the following error:

```
Rendering of /kdenlive/myvideo.mp4 crashed
[I]medium: [ ref=1, _mlt_properties_load=medium, __mlt_properties_load=medium ]
[mp4 muxer @ 0x7f46f400bae0] [Eval @ 0x7f46f96c7450] Undefined constant or missing '(' in 'faststart' [mp4 muxer @ 0x7f46f400bae0] Unable to parse option value "faststart"
[dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=64 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=64 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=64 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=64 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=65 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=64 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=66 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=70
[dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=66 [dvvideo @ 0x7f44e7ca8720] AC EOB marker is absent pos=64[/I]
```

If I pick Matroska as the output format, Kdenlive still crashes with the following error:

```
Rendering of /kdenlive/myvideo.mkv crashed
[dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=65 [dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=66
[dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=64 [dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=64 [dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=64
[dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=64 [dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=64
[dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=70
[dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=64 [dvvideo @ 0x7f54beeea8c0] AC EOB marker is absent pos=66
```

I browsed the Internet and found out that this error could be due to ffmpeg coming across a sort of index error in the DV source files:
[https://bugs.kdenlive.org/view.php?id=1592](https://bugs.kdenlive.org/view.php?id=1592)

Could this be the real cause of my problem or am I walking down a blind alley?

If that is indeed the cause of my troubles, someone suggested to use mencoder to repair the "broken" source .avi file:
[https://superuser.com/questions/709313/how-can-i-check-the-integrity-of-an-avi-file-and-repair-it-automatically-in-linu](https://superuser.com/questions/709313/how-can-i-check-the-integrity-of-an-avi-file-and-repair-it-automatically-in-linu)
[http://www.kahunaburger.com/2010/01/30/fixing-an-avi-index-with-mencoder/](http://www.kahunaburger.com/2010/01/30/fixing-an-avi-index-with-mencoder/)

Unfortunately, I have tens of short .avi clips in my Kdenlive project and I have no idea which one is causing this crash.

Is there a way to exactly pinpoint the problematic clips? Or can anyone suggest a script or terminal command to parse and fix all .avi files in my project folder?

Thank you very much for your help.

---

