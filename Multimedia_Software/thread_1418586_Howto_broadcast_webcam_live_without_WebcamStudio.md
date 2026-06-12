---
title: "Howto broadcast webcam live without WebcamStudio"
date: 2010-02-28
forum: Multimedia Software
---

### Post by skipx on 2010-02-28
Hi,

For an (art)installation I want a camera (webcam) to stream it's data to another computer with icecast2 server installed (including theora) in the same space. Problem is I need something without a gui.

The webcam is /dev/video0, and I would like to stream the video with vloopback (is working already with 2 pipes) to /dev/video3. If I'm right then I should be able to stream /dev/video4 to icecast.

**How can I make the webcam video go into pipe /dev/video3?**
From [http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice) I understand I have to do:
```
resize /dev/video0 /dev/video3 320x240 320x240
```
But then I get: 
```
Usage: resize [-u] [-c] [-s [rows cols]]
```

**Would this be the right syntax to make a stream work?**
```
ffmpeg -f /dev/video4 -f mpeg -pix_fmt yuv420p -ad /dev/dsp -ac 1 - | ffmpeg2theora -a 1 -v 5 -x 320 -y 240 -o /dev/stdout - | oggfwd 172.19.3.105 8000 *mypassword* /cam.ogg
```
Now my sweet pc tells me 'pipe does not exists', also if I use /dev/video2 which works, it receives a mjpeg stream from the internet (from another part of the project).

Thanks!,
Bart


(earlier I posted a question how to receive an mjpg stream and send it to /dev/video. [http://ubuntuforums.org/showthread.php?t=1353347](http://ubuntuforums.org/showthread.php?t=1353347), this is working and used in this installation to)

---

### Post by skipx on 2010-03-09
Fixed it by using gstreamer rather then ffmpeg2theora.

```
gst-launch-extra v4l2src ! videorate ! video/x-raw-yuv,width=640,height=480,framerate=15/2 ! ffmpegcolorspace ! theoraenc quality=20 ! oggmux name=mux alsasrc ! audio/x-raw-int ! audioconvert ! queue ! vorbisenc ! mux. mux. ! shout2send ip=*172.19.3.113* port=*8000* password=*password* mount=webcam.ogg
```
*(the italic stuff might need your own variables)*

Only vlc gets stuck after viewing the stream for one hour or so, but for the rest it works. 
Streaming to virtual loopback device was not needed.

---

