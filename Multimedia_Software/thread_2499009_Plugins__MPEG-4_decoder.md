---
title: "Plugins : MPEG-4 decoder"
date: 2024-07-08
forum: Multimedia Software
---

### Post by angel mike on 2024-07-08
Cannot play mp4 files with VLC. Error message MPEG-4 AAC decoder and H.264 decoder plugins required

---

### Post by TheFu on 2024-07-08
mp4 is a container.  You need both the audio codec decoder and video codec decoder to be installed and working to watch that file.
[https://askubuntu.com/questions/1284815/20-04-ubuntu-video-player-says-h-264-not-supported](https://askubuntu.com/questions/1284815/20-04-ubuntu-video-player-says-h-264-not-supported)  explains how to use the snap pacakge, which I think has been the default for vlc on Ubuntu since 2020.

Other options ... 
Years ago, VLC would compile that support in. I stopped using it for **mpv** nearly a decade ago.  mpv has a few different GUI front-end options. I don't use those, but I think one is **smplayer**.   [https://www.smplayer.info/en/mpv](https://www.smplayer.info/en/mpv)
```
sudo apt install mpv smplayer
```
should install both tools.  You might like them.  If now, they can easily be removed. Neither are snap packages with mandated constraints.  Also, if you have **yt-dlp** installed, **mpv** will play internet streams too.

If you need a fast video editor, LossLessCut is nice and only transcodes when necessary. I use the AppImage for it to avoid conflicting dependencies.

VLC does many more things than just playing videos. If you use those, like the ability to save streams and transcode those streams while saving, perhaps it is useful.  Or maybe use use VLC as a DNLA controller+renderer?  IDK.

If it likely that nothing I've posted is helpful, so hopefully, others will post their answers too.  Of course, watch out for all the "bogus help" you'll find online related to video file playing and transcoding. That part of the industry is full of people stealing code, so stick with vlc and mpv as your players and ffmpeg-based tools like handbrake or ffmpeg directly to handle transcoding. Beware of almost any other webpage with a fancy marketing page.  You know all this already.

---

### Post by angel mike on 2024-07-09
Thanks TheFu for that very detailed reply. I have managed to get the VLC to play so that's good. Will mark as Solved

---

### Post by TheFu on 2024-07-09
> **angel mike said:**
> Thanks TheFu for that very detailed reply. I have managed to get the VLC to play so that's good. Will mark as Solved

But, exactly what did you do?  Help others in the community with the same issue. Please.

---

