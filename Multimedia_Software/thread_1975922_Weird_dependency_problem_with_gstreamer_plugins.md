---
title: "Weird dependency problem with gstreamer plugins"
date: 2012-05-08
forum: Multimedia Software
---

### Post by Quaxo76 on 2012-05-08
Hello, I've had this problem since I started using Precise in late beta stage.
I thought it would fix itself after going final but it didn't.
If I try to play video clips, movieplayer says Python must install two plugins. But when it tries to, there are dependency problems. Here's the output:
```
 The following packages have unmet dependencies:

gstreamer0.10-ffmpeg: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                      Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed
                      Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1 is to be installed
                      Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                      Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                      Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                      Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
gstreamer0.10-ffmpeg:i386: Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libavformat-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libavutil-extra-51 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libc6 (>= 2.7) but 2.15-0ubuntu10 is to be installed
                           Depends: libglib2.0-0 (>= 2.31.2) but 2.32.1-0ubuntu2 is to be installed
                           Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.31) but 0.10.36-1 is to be installed
                           Depends: libgstreamer0.10-0 (>= 0.10.31) but 0.10.36-1ubuntu1 is to be installed
                           Depends: liborc-0.4-0 (>= 1:0.4.16) but 1:0.4.16-1ubuntu2 is to be installed
                           Depends: libpostproc-extra-52 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
                           Depends: libswscale-extra-2 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed
```

I find this weird because, for example, it says "Depends: libavcodec-extra-53 (>= 4:0.7.3-1) but 4:0.8.1ubuntu1 is to be installed". As I read it, the condition is satisfied: it needs the lib version higher than 4:0.7.3, and 4:0.8.1 is going to be installed. I think the version that is going to be installed is higher than the version needed, so the condition should be satisfied. So why does it complain?

---

### Post by anspectrum on 2012-05-08
Its good to do some R & D.

BUT

VLC will make your life easier. Give it a go. You can download it through software center.:guitar:

---

