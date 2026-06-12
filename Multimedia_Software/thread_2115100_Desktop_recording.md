---
title: "Desktop recording"
date: 2013-02-11
forum: Multimedia Software
---

### Post by cjwilly7 on 2013-02-11
I'm trying to record my Desktop for gaming and what not, but every program I use, it lags out my computer. what should I do?

---

### Post by evilsoup on 2013-02-12
Get a newer computer :V

More seriously, you could try recording to a less processor-intensive video format (this will give you a massive file, but you can then encode that into something smaller for posting online or whatever). Or you could record only a portion of your screen. Or you could reduce the frame rate you're recording at.

From the command-line, to [record your screen with ffmpeg]("https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20grab%20the%20desktop%20%28screen%29%20with%20FFmpeg") and huffyuv video at a frame rate of 12fps:

```

ffmpeg -f x11grab -r 12 -i :0.0 -c:v huffyuv intermediate.mkv

```If you want audio too:

```

ffmpeg -f x11grab -r 12 -i :0.0 -f alsa -ac 2 -i pulse -c:v huffyuv -c:a pcm_s16le intermediate.mkv

```To encode that second one to an MP4, you can use:

```

ffmpeg -i intermediate.mkv -c:v libx264 -preset veryfast -crf 24 -c:a aac -strict experimental output.mp4

```Some of the GUI applications can probably be configured in a similar way.

---

### Post by cjwilly7 on 2013-02-14
Well, my computer shouldn't be an issue, but I will try your suggestions. thanks.

---

### Post by FakeOutdoorsman on 2013-02-14
Minor typo:
```
-i 0:0
```
should be:
```
-i :0.0
```

---

### Post by evilsoup on 2013-02-15
Thanks for spotting that, corrected.

---

### Post by Gato303co on 2013-02-15
> **evilsoup said:**
> Get a newer computer :V

More seriously, you could try recording to a less processor-intensive video format (this will give you a massive file, but you can then encode that into something smaller for posting online or whatever). Or you could record only a portion of your screen. Or you could reduce the frame rate you're recording at.

From the command-line, to [record your screen with ffmpeg]("https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20grab%20the%20desktop%20%28screen%29%20with%20FFmpeg") and huffyuv video at a frame rate of 12fps:

```

ffmpeg -f x11grab -r 12 -i :0.0 -c:v huffyuv intermediate.mkv

```If you want audio too:

```

ffmpeg -f x11grab -r 12 -i :0.0 -f alsa -ac 2 -i pulse -c:v huffyuv -c:a pcm_s16le intermediate.mkv

```To encode that second one to an MP4, you can use:

```

ffmpeg -i intermediate.mkv -c:v libx264 -preset veryfast -crf 24 -c:a aac -strict experimental output.mp4

```Some of the GUI applications can probably be configured in a similar way.

Hello, is there a way to send the desktop recording to the Livestream server, they told me they accept codecs h.264 and flv, with mp4 as container. 

They also said that i should stream to flash media server and the url should be like (using RTMP streaming):
```

rtmp://publish.livestream.com/mogulus/[channelname]/username=[yourusername]/password=[yourpassword]/isAutoLive=[true/false]/aspectWidth=[16]/aspectHeight=[9]  
```I tried Webcam Studio 4 Gnu/Linux but i only transmit to GISS.tv i can't figure out how it can emit the desktop recordign to livestream/ustream

Thanks for attention :)

---

### Post by GerMulvey on 2013-02-16
I was able to use recordmydesktop to do a small video of me playing counterstrike not sure if it will be what your after but have you tried that?
It was windowed and offline

---

### Post by evilsoup on 2013-02-16
[Here]("https://ffmpeg.org/trac/ffmpeg/wiki/StreamingGuide") is a guide to streaming on the FFmpeg wiki (a very useful resource for using ffmpeg in general).

I would use something along the lines of:
```

ffmpeg -y -f x11grab -r 12 -i :0.0 -f alsa -ac 2 -i pulse \
-c:v libx264 -preset veryfast -tune zerolatency -crf 24 -c:a aac -strict experimental \
-f mp4 rtmp://blahblahblah

```

---

### Post by cjwilly7 on 2013-02-21
thanks for the help guys. ffmpeg worked, but it was still laggy. my computer shouldny be an issue, I've got a Dell Studio XPS 435t / 9000 with an Intel Core i7 920 / 2.66 GHz processor with 6 gigs (24 max) of ram. I don't think my computer would be slow.

---

