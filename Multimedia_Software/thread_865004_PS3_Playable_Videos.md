---
title: "PS3 Playable Videos"
date: 2008-07-20
forum: Multimedia Software
---

### Post by grapnell on 2008-07-20
I have tried everything possible. I have searched thousands of threads, but I cannot, for the life of me, create a playable video file for my PS3. My PS3 will play almost any .mpg video that I download from the net, but if its not mpg format, it won't play. Also, If I try to transcode it to mpg, my ps3 just says data corrupted, or unsupported data. Even though these transcoded files will play just fine on my computer. I have tried transcoding these videos a million different ways, using mencoder, ffmpeg, avidemux, the list goes on and on. I have tried transcoding them to both MP4 and MPG formats, yet the PS3 will not read them. I have tried various GUIs such as kino, vlc, vive, winff etc etc. All I want to do is transcode some of my Southpark videos, some are in avi and some are in mp4 format when I download them. BTW, I though PS3 was supposed to be able to play MP4, why won't it play the ones I download? Can some give me a command that will convert xxx.mp4 to PS3 readable format. and the same for xxx.avi 2 ps3 format. I would greatly appreciate it.

Thanks,
Grap

---

### Post by fenian on 2008-07-20
You probably need to use the H.264 codec which is not included with ubuntu's default version of ffmpeg , you need to get it from the Medibuntu repo's.You can check out this post to see how to remove ffmpeg and reinstall it with the Medibuntu version.You could also continue along with the how to and install HandBrake GUI which has presets for the PS3.

---

