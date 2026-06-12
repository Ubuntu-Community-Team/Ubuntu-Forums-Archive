---
title: "VLC is not playing video files"
date: 2012-05-16
forum: Multimedia Software
---

### Post by arka.sharma on 2012-05-16
Hi,

   I have installed 11.04 and installed vlc media player from Update Manager.It is smoothly playing mp3 audio files but while playing avi video files it is displaying following error message

```
 [COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "mp4v". Unfortunately there is no way for you to fix this.[/COLOR]

```however background audio is being played and 
in terminal from where I am running vlc getting the following message
```
main decoder error: no suitable decoder module for fourcc `mp4v'. VLC probably does not support this sound or video format.
```.


I have already installed libavcodec52 from Synaptic but still not working.Please help unable to watch movies and videos.

Regards,
Arka

---

### Post by arka.sharma on 2012-05-21
I upgraded to 11.10 and now vlc is smoothly playing avi files. However can anybody please explain me why this happened ? Expecting an answer...

Regards,
Arka

---

### Post by carl4926 on 2012-05-21
> **arka.sharma said:**
> However can anybody please explain me why this happened ? Expecting an answer...

Regards,
Arka

Not really, as we didn't really dig in to the original problem

---

### Post by mc4man on 2012-05-21
this error is typically seen when having a mis-matched vlc & libavcodecXX version.
Can happen easily thru the use of some ppa's & possibly in Ubuntu release upgrades

You could have probably resolved by removing all the ffmpeg(libav) shared libraires, vlc, ect., then re-installing them from the ubuntu repos

---

