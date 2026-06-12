---
title: "Capturing a video from a webcam using gstreamer"
date: 2008-06-16
forum: Multimedia Software
---

### Post by Deli on 2008-06-16
Greetings!
I'd like to capture a video from my webcam to a file using this command:
```
gst-launch oggmux name=mux ! filesink location=output.ogg { v4lsrc ! tee name=t ! {queue ! ffmpegcolorspace ! theoraenc ! queue ! mux. } } { alsasrc ! audioconvert ! rawvorbisenc ! queue ! mux. } { t. ! queue ! ffmpegcolorspace ! sdlvideosink }
```

I got several errors i could fix myself but the one i'm stuck on at the moment is freaking me out.

```
WARNING: erroneous pipeline: no element "rawvorbisenc"
```

I was searching for a fix on that all day unsuccessfully. :mad:
I have no idea which package i need to install in order to fix this problem.

gstreamer0.10-plugins-base, libvorbisenc2, libvorbisfile3 and libvorbis0a are all installed with the newest version available.

I'm running Hardy with
```
Linux server 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux
```


I hope someone of you can help me.
Thank you in advance,
-Deli

---

### Post by Deli on 2008-06-18
No idea? :(
Maybe an admin could move this thread to 'Multimedia Production'?!
Perhaps that section is more appropriate to my problem.

Thanks
-Deli

---

### Post by bufsabre666 on 2008-06-18
just a question, why are you trying to capture video with a terminal command? try the program cheese, it has tons of options and is very easy to understand

```
sudo apt-get install cheese
```

it just seems odd to me to not be able to see what im capturing

---

### Post by Deli on 2008-06-18
This is because the machine is a server and doesnt have a graphical interface.
The webcam is for kind of watching who is playing around at my machine ;)

But thanks anyway.
-Deli

---

### Post by loell on 2008-06-21
try camserv.

---

### Post by badmuthahubbard on 2009-10-10
I love it.
"Can someone tell me why this particular command doesn't work?"

"Why are you doing that? Why don't you use another app!"
"Just use this other app."

I have tried all of these apps, unsuccessfully, and any time I ask for help with any of them, people recommend using a different one. lol

---

### Post by rodrigor on 2010-10-31
gstreamer?
this works for me:

## replace host IP for the host who will be receiving the video stream, and the port if that one is unavailable
gst-launch v4l2src ! video/x-raw-yuv, width=320,height=240,framerate=10/1 ! ffmpegcolorspace ! smokeenc keyframe=8 qmax=40 ! udpsink host=192.168.1.105 port=5000

## run this on the pc that will recieve the video stream
gst-launch udpsrc port=5000 ! smokedec ! ffmpegcolorspace ! autovideosink

some routers filter udp, hence this would not work...

good luck!

---

### Post by kamondelious on 2011-01-17
Hey rodrigor,

Awesome!  I'd played with gstreamer before but couldn't seem to get it working.  Your example worked straight up.  Thank you for sharing.

---

