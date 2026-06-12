---
title: "UPNP Server to stream webcam to TV"
date: 2012-12-31
forum: Multimedia Software
---

### Post by MrQuincle on 2012-12-31
Dear Ubuntu experts,

The last two days I spend trying to figure out how to stream my webcam to my much larger television set which supports UPNP.

To get access to my webcam is easy of course, and sending it out over a normal HTTP socket is no problem. 

```
cvlc v4l2:// :v4l2-vdev=/dev/video0 --sout '#transcode{vcodec=x264{keyint=60,idrint=2},vcodec=h264,vb=400,width=368,heigh=208,acodec=mp4a,ab=32,channels=2,samplerate=22100}:duplicate{dst=std{access=http{mime=video/mpeg},mux=asf,dst=:8082/stream.mpeg}}' --no-sout-audio
```

Pity that I cannot point my TV to an HTTP socket, it understands UPNP however, so let me try to use that. I have been playing around with rygel, with minidlna, plexmediaserver, coherence. I just cannot make it work! The difference between playing a few movie files and online streaming of my webcam shouldn't be so great! What is the easiest way to stream my laptop (not IP) webcam to my television? 

Thanks!

---

### Post by jensgeorg on 2013-01-15
This might be doable with rygel's gst-launch plugin. I'll try to come up with a launchline for it and get back to you

---

### Post by jensgeorg on 2013-01-15
This works for me, though it adds a bit of latency and might need some fps and resolution tweaking:

```
[GstLaunch]
enabled=true
title=Rygel GstLaunch plug-in
launch-items=webcam
webcam-title=Webcam
webcam-mime=video/x-oggm
webcam-launch=v4l2src device=/dev/video1 ! capsfilter caps=video/x-raw-yuv,width=640,height=480,framerate=25/1 ! queue ! theoraenc ! oggmux name=mux

```

---

### Post by MrQuincle on 2013-02-03
Thanks! I will try that as soon as I am home.

---

