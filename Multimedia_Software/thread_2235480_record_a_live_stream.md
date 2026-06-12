---
title: "record a live stream?"
date: 2014-07-21
forum: Multimedia Software
---

### Post by Tommy_Maersk on 2014-07-21
Hey
I have access to a stream, where I get a m3u file - that basicly holds the url for the stream.

The stream is a video stream with audio.

But does anybody know if it is possible to record this stream, and save it as a video file?

Thanks

---

### Post by tgalati4 on 2014-07-21
Try opening the URL with *vlc* and use the "convert/save" option.  You are not supposed to record video streams as it violates many terms-of-service from providers, but you can "convert/save" them.

---

### Post by Tommy_Maersk on 2014-07-21
I got that to work yes, on my windows machine, thanks.

However, and maybe I wasnt specific enough, I want to do this on a ubuntu server, with no gui - so if there is some commandline util that would do the same trick?

---

### Post by tgalati4 on 2014-07-21
You can install vlc on your server and use the cvlc (command line mode).  Perhaps *mplayer* or *[ffmpeg]("https://help.ubuntu.com/community/FFmpeg")* can do the same.  Sounds like you want to create a digital video recorder, it that case look into [mythtv]("http://www.mythbuntu.org/").  It's designed for a headless-backend.

---

### Post by FakeOutdoorsman on 2014-07-22
```
ffmpeg -i input -codec copy output.mkv
```

Ubuntu doesn't provide ffmpeg, so you'll have to [download](http://ffmpeg.org/download.html) it.

---

