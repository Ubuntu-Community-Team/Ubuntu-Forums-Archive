---
title: "AC3 Filter &amp; Smplayer problems"
date: 2008-07-19
forum: Multimedia Software
---

### Post by xwhisper on 2008-07-19
Hello!

I have some video clip that uses AC3 filters. When I try to play it it is almost 99% muted (in all sound options set to max I still can't hear it - alsamixer and pulseaudio).

Second - Mplayer plays fine that clip, but Smplayer just can't start it. Where could be the problem?

Third (bonus) - Anyone has a complete codecs list? I think I installed all necessary , but there always should be something missed

```
sudo apt-get install streamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg libxine1-ffmpeg libdvdread3 libdvdcss2 ffmpeg w32codecs x264 dvdauthor quicktime-utils libmikmod2 lame lame-extras flac alsa-base alsa-oss alsa-tools alsa-tools-gui alsa-utils libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter libflashsupport
```

edit: Sound got better when I tried GMplayer, but still too low...

---

### Post by rvm4000 on 2008-07-19
> **xwhisper said:**
> Second - Mplayer plays fine that clip, but Smplayer just can't start it. Where could be the problem?

What does the mplayer log (Options->View logs) says when you try to play a file?

---

