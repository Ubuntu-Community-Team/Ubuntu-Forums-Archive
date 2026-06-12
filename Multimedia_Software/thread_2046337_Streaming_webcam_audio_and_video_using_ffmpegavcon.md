---
title: "Streaming webcam audio and video using ffmpeg/avconv"
date: 2012-08-22
forum: Multimedia Software
---

### Post by schmidtbag on 2012-08-22
I'm trying to stream the video and audio a USB webcam using avconv (or ffmpeg) using just port 8080 over a network.

I can successfully stream audio using the following command:
```
avconv -f oss -ar 8000 -ac 1 -i /dev/dsp1 -acodec mp2 -f rtp rtp://172.17.2.2:9090
```
and VLC will read it just fine, with maybe a 1 second delay.


I can successfully stream video using:
```
avconv -f video4linux2 -i /dev/video0 -vcodec mpeg2video -r 25 -pix_fmt yuv420p -me_method epzs -b 2600k -bt 256k -f rtp rtp://172.17.2.2:8080
```
which will also work just fine in VLC, but with a slightly greater delay.



However, I can't combine them both with rtp.  So far the best I can do is:
```
avconv -f video4linux2 -i /dev/video0 -f oss -i /dev/dsp2 -vcodec mpeg2video -pix_fmt yuv420p -me_method epzs -r 25 -b 2600K -bt 256k -acodec mp2 -ar 8000 -ac 1 -ab 128k -async 1 udp://172.17.2.2:8080/stream.mpg
```
which does NOT work in VLC, but will work using:
```
ffplay -i udp://172.17.2.2:8080/stream.mpg
```
However, this turns out to have a 6-second delay.


So, does anyone know how I can get rtp to work, or at least an alternative that would get VLC to work with it?


EDIT:
I would like to point out that this is running on an ARM platform and I'm trying to stick with the "main" repository only.

---

### Post by schmidtbag on 2012-08-24
bump?

---

### Post by kaan52 on 2012-10-08
did you find a solution for this?

i also can't receive the stream via vlc.

---

### Post by schmidtbag on 2012-10-08
unfortunately, no, I haven't.  I just sent the streams separately.  I wish there was more up-to-date documentation on this kind of stuff because when streaming RTP, I get all sorts of issues because i'm missing some file, I forget what it is, something like SDP?  It lists the codec info and I can't seem to get it working.  There are guides on how to send this file but they're all out of date and don't work anymore.

---

### Post by kaan52 on 2012-10-08
i think there is a solution with vlc. i know it uses also ffmeg and avconv but maybe we're not using the right parameters or there are missing parameters for streaming.

let me guess, you want to use the Raspberry pi?

---

### Post by schmidtbag on 2012-10-08
I thought about doing VLC but I personally find it more of a pain in the *** to configure, and it seems to have a slower delay.

I'm actually not using RPi, but Beagleboard XM.  Considering RPi is armel, I didn't think it was quite good enough.  BB is armhf, which is a LOT better in terms of performance per clock.

---

### Post by kaan52 on 2012-10-08
i see...

i tried to stream with a tut.
[http://sirlagz.net/2012/08/04/how-to-stream-a-webcam-from-the-raspberry-pi/](http://sirlagz.net/2012/08/04/how-to-stream-a-webcam-from-the-raspberry-pi/)
it worked fine for me, but it's only mjpeg. i've also tried to rewrite the parameters so that i will work for mpeg4 or with flv .. no chance..
i also get sometimes errors like 

```
[tcp @ 0xc8e920] TCP connection to localhost:80 failed: Connection refused
http://localhost:80: Input/output error
```or 

```
/dev/video0: Operation not permitted
```

when this won't take an end i'll also feel the same pain..

---

### Post by schmidtbag on 2012-10-08
> **kaan52 said:**
> i see...

i tried to stream with a tut.
[http://sirlagz.net/2012/08/04/how-to-stream-a-webcam-from-the-raspberry-pi/](http://sirlagz.net/2012/08/04/how-to-stream-a-webcam-from-the-raspberry-pi/)
it worked fine for me, but it's only mjpeg. i've also tried to rewrite the parameters so that i will work for mpeg4 or with flv .. no chance..
i also get sometimes errors like 

```
[tcp @ 0xc8e920] TCP connection to localhost:80 failed: Connection refused
http://localhost:80: Input/output error
```or 

```
/dev/video0: Operation not permitted
```

when this won't take an end i'll also feel the same pain..

Yeah, I've had enough issues trying to get VLC to stream video in a GUI, I figure it'd probably be more difficult by a CLI but I could be wrong.  I'll experiment a little later and let you know what I come up with.  Personally I don't mind mjpeg, as it's very compatible and overall easy on bandwidth.

---

### Post by kaan52 on 2012-10-08
k
the same for me.. will also let you know, if i'll find a solution or even a clue..

thanks in meantime

---

