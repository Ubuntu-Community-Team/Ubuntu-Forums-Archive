---
title: "Problem with brightness in webcam stream with vlc"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by skep on 2006-12-18
Hello!

I've got my webcam (Logitech Quickcam Messenger "046d:08da") to work on Ubuntu Edgy, but having some problems adjusting the settings for brightness, contrast ect.. It kinda works if I use Ekiga, OpenWengo, camstream ect., but now I want to stream the webcam-video via Internet. I tried using vlc and it worked without problems, but the video is extremely dark and I can't find a way to adjust the stream-settings (brightness ect.).

This is how I use vlc to stream:
```
vlc -I dummy -v --noaudio --ttl 12 v4l:/dev/video0:size=320x240 --sout '#transcode{vcodec=mp4v,vb=128}:std{access=mmsh,dst=:8080}'
```
& I can watch the stream via:
```
mmsh://xxx.xxx.xxx.xxx:8080
``` but as I said..its darker then dark. Is there any way to tell the streamer (in my case: vlc) to produce a brighter videostream?


EDIT1:
Got the source a bit brighter (included a plugin in vlc to adjust contrast, brightness, saturation ect.)..but now I can't seem to get the stream functional so people can call it via mms://url:8080..hmm.

EDIT2:
Ok..its working now..with
```
vlc -vvv v4l:/dev/video0:size=320x240 --sout '#transcode{vcodec=mp4v,vb=256,scale=1}:duplicate{dst=display, dst=std{access=mmsh,mux=asfh,dst=:8080}}' -v --noaudio
``` + picture-adjust-plugin in vlc (to set brightness ect.) and it's accessable via: mms://xxx.xxx.xxx.xxx:8080
Problem solved..

---

