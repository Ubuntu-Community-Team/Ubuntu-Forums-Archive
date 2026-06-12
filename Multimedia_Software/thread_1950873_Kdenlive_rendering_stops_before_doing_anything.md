---
title: "Kdenlive rendering stops before doing anything"
date: 2012-04-01
forum: Multimedia Software
---

### Post by J V on 2012-04-01
Kdenlive worked fine until a few days ago when, without any updates (To my knowledge) rendering stopped working.

There are no crashes, and .xsession-errors says rendering completed fine, however the rendering takes 0 seconds and the output file is 0 bytes.

```
//STARTING RENDERING:  true , false , "/usr/bin/melt" , "/home/j/.kde/share/apps/kdenlive/profiles/customprofile0" , "avformat" , "-" , "/tmp/kde-j/kdenliveV13683.mlt" , "/home/j/kdenlive/untitled.mp4" , () , ("f=mp4", "acodec=libmp3lame", "ab=128k", "ar=44100", "vcodec=mpeg4", "minrate=0", "vb=12000k", "aspect=@16/9", "mbd=2", "trellis=1", "mv4=1", "threads=1", "real_time=-1") , -1 , -1 
Started render process:  "/usr/bin/melt"   "/tmp/kde-j/kdenliveV13683.mlt -profile /home/j/.kde/share/apps/kdenlive/profiles/customprofile0 -consumer avformat:/home/j/kdenlive/untitled.mp4 progress=1 f=mp4 acodec=libmp3lame ab=128k ar=44100 vcodec=mpeg4 minrate=0 vb=12000k aspect=@16/9 mbd=2 trellis=1 mv4=1 threads=1 real_time=-1" 
Rendering of  "/home/j/kdenlive/untitled.mp4"  finished
$ ls -l kdenlive/
-rw-rw-r-- 1 j j    0 Apr  1 19:32 untitled.mp4
```With no error messages and no output file, no apparent updates causing it (According to dpkg.log) and no-one else seeming to have this problem, I'm kind of stuck.

---

### Post by Areia on 2012-04-04
> **J V said:**
> Kdenlive worked fine until a few days ago when, without any updates (To my knowledge) rendering stopped working.

There are no crashes, and .xsession-errors says rendering completed fine, however the rendering takes 0 seconds and the output file is 0 bytes.

```
//STARTING RENDERING:  true , false , "/usr/bin/melt" , "/home/j/.kde/share/apps/kdenlive/profiles/customprofile0" , "avformat" , "-" , "/tmp/kde-j/kdenliveV13683.mlt" , "/home/j/kdenlive/untitled.mp4" , () , ("f=mp4", "acodec=libmp3lame", "ab=128k", "ar=44100", "vcodec=mpeg4", "minrate=0", "vb=12000k", "aspect=@16/9", "mbd=2", "trellis=1", "mv4=1", "threads=1", "real_time=-1") , -1 , -1 
Started render process:  "/usr/bin/melt"   "/tmp/kde-j/kdenliveV13683.mlt -profile /home/j/.kde/share/apps/kdenlive/profiles/customprofile0 -consumer avformat:/home/j/kdenlive/untitled.mp4 progress=1 f=mp4 acodec=libmp3lame ab=128k ar=44100 vcodec=mpeg4 minrate=0 vb=12000k aspect=@16/9 mbd=2 trellis=1 mv4=1 threads=1 real_time=-1" 
Rendering of  "/home/j/kdenlive/untitled.mp4"  finished
$ ls -l kdenlive/
-rw-rw-r-- 1 j j    0 Apr  1 19:32 untitled.mp4
```With no error messages and no output file, no apparent updates causing it (According to dpkg.log) and no-one else seeming to have this problem, I'm kind of stuck.

Same probleme here...  two days ago was fine, but now... no render at all, please!

---

