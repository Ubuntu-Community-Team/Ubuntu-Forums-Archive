---
title: "mencoder motion compensation deinterlacing"
date: 2010-05-24
forum: Multimedia Software
---

### Post by ptrxyz on 2010-05-24
Is it just me, or is the motion compensation deinterlacer missing in Ubuntu's Version of Mencoder?

mencoder -vf help doesn't show it (I guess this means it's not installed...), although mencoder's man pages do have an mcdeint entry.

I have those versions installed:
```
ii  mencoder                               2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1      MPlayer's Movie Encoder
ii  gnome-mplayer                          0.9.9.2-1                                       A GTK+ interface for MPlayer
ii  mplayer                                2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1      movie player for Unix-like systems
ii  mplayer-doc                            2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1      documentation for MPlayer
ii  mplayer-fonts                          3.5-2                                           Fonts for mplayer
ii  mplayer-nogui                          2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1      movie player for Unix-like systems (transitional package)
ii  ffmpeg                                 4:0.5.1-1ubuntu1                                multimedia player, server and encoder
ii  gstreamer0.10-ffmpeg                   0.10.10-1                                       FFmpeg plugin for GStreamer
ii  libavcodec-extra-52                    4:0.5.1-1ubuntu1+medibuntu1                     ffmpeg codec library
ii  libavcodec-unstripped-52               4:0.5.1-1ubuntu1+medibuntu1                     ffmpeg utility library - transitional package
rc  libavcodec52                           4:0.5.1-1ubuntu1                                ffmpeg codec library
rc  libavdevice-extra-52                   4:0.5.1-1ubuntu1                                ffmpeg device handling library
ii  libavdevice52                          4:0.5.1-1ubuntu1                                ffmpeg device handling library
ii  libavfilter0                           4:0.5.1-1ubuntu1                                ffmpeg video filtering library
rc  libavformat-extra-52                   4:0.5.1-1ubuntu1                                ffmpeg file format library
ii  libavformat52                          4:0.5.1-1ubuntu1                                ffmpeg file format library
ii  libavutil-extra-49                     4:0.5.1-1ubuntu1+medibuntu1                     ffmpeg utility library
ii  libavutil-unstripped-49                4:0.5.1-1ubuntu1+medibuntu1                     ffmpeg utility library - transitional package
rc  libavutil49                            4:0.5+svn20090706-2ubuntu2                      ffmpeg utility library
rc  libpostproc-extra-51                   4:0.5+svn20090706-2ubuntu3                      ffmpeg video postprocessing library
ii  libpostproc51                          4:0.5.1-1ubuntu1                                ffmpeg video postprocessing library
rc  libswscale-extra-0                     4:0.5+svn20090706-2ubuntu3                      ffmpeg video scaling library
ii  libswscale0                            4:0.5.1-1ubuntu1                                ffmpeg video scaling library
```
(I first tried the Versions shipped with Ubuntu Lucid Lynx, then I installed them from the Medibuntu repositories. Both without any success.)
Does anyone know, how to enable mcdeint support? Is there a repository or something I could add to my sources?

---

### Post by ptrxyz on 2010-05-24
bump

---

### Post by andrew.46 on 2010-05-25
Hi ptrxyz,

Perhaps build you own from svn? In my own copy this filter is available:

```
andrew@skamandros~$ **[COLOR="Red"]mplayer -vf help | grep -m 1 'mcdeint'[/COLOR]**
  mcdeint        : motion compensating deinterlacer
```

There are a few guides on these forums that could be easily modified to include MEncoder and this filter.

All the best,

Andrew

---

