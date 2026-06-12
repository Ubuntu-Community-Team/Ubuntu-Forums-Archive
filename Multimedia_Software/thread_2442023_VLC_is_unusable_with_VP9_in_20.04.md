---
title: "VLC is unusable with VP9 in 20.04"
date: 2020-04-28
forum: Multimedia Software
---

### Post by magsnus2 on 2020-04-28
I just installed 20.04 and after installing VLC i tried to view some VP9 encoded content and this is an example of what I mostly got:
[ATTACH=CONFIG]285660[/ATTACH]
(intermingled with frames of the actual video)

1. The same video worked fine with 18.04 and VLC on the same laptop.
2. The same video plays fine in mpv.
3. H264/h265 plays fine in both (although the later seems to have worse performance in VLC than on 18.04 but it might just be me imagining things).
4. The sound plays fine in VLC

This leads me to believe that there is something wrong with the standard video codec settings in VLC. I have looked at them but couldn't spot anything obvious. It is just set to auto which I guess means vaapi for most if not all videos.

vainfo result (again nothing stands out to me):
```
libva info: VA-API version 1.7.0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/iHD_drv_video.so
libva info: Found init function __vaDriverInit_1_7
libva info: va_openDriver() returns 0
vainfo: VA-API version: 1.7 (libva 2.6.0)
vainfo: Driver version: Intel iHD driver for Intel(R) Gen Graphics - 20.1.1 ()
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSliceLP
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSliceLP
      VAProfileJPEGBaseline           :    VAEntrypointVLD
      VAProfileJPEGBaseline           :    VAEntrypointEncPicture
      VAProfileH264ConstrainedBaseline:    VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:    VAEntrypointEncSliceLP
      VAProfileVP8Version0_3          :    VAEntrypointVLD
      VAProfileHEVCMain               :    VAEntrypointVLD
      VAProfileHEVCMain10             :    VAEntrypointVLD
      VAProfileVP9Profile0            :    VAEntrypointVLD
```

CPU: Intel n4200
GPU: Intel® HD Graphics 505 (has vp9 decode support)

I'm at loss here since I don't really like mpv and keeping two video players as standard is a bit clunky. Any suggestions?

FIXED (you can delete this thread if you want to)
Uninstalled the snap version in the app store (3.0.8) and installed the latest stable version (3.0.9) with:
```
sudo add-apt-repository ppa:videolan/stable-daily
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by Yellow Pasque on 2020-05-01
Deleting it would not appropriate, as it may help someone else.
Instead, please mark the thread SOLVED (Thread Tools menu above first post)

---

