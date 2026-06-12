---
title: "Rocketfish Webcam black screen"
date: 2011-01-18
forum: Multimedia Software
---

### Post by Belgaer on 2011-01-18
Hello, yesterday I got a Rocketfish RF-WEB2C webcam, plugged it into my Dell Inspiron Mini 10, and it worked just fine. Cheese ran it, tinychat ran it, skype ran it, all was good. Today, all I get is a black screen. Tinychat claims that it isn't giving out any signal, though can detect it, and Cheese showed me a black screen, though listed it as the the device it was using. I figure it isn't a lack of drivers, as it worked yesterday, and it really shouldn't have broken yet, as I just opened it yesterday. Any ideas anyone? 
Thanks

---

### Post by no2498 on 2011-01-18
see if it comes on in gstreamer-properties
put that in a terminal click enter
click video
try v4l and v4l2
use the bottom test button for each 1


you may need to set the pic size in cheese smaller

---

### Post by Belgaer on 2011-01-18
So I did that, and nothing popped up. It only acknowledged my webcams existence in v4l2, and when I hit 'Test' a box came up with a bar that claimed it was testing, and nothing else. I tried testing it under every resolution in Cheese, and nothing came up either. Tried using WebcamStudio ([http://www.ws4gl.org/](http://www.ws4gl.org/)) as well, and that froze as soon as I asked for a preview. The microphone in it seems to work fine too for what its worth... Thanks for the suggestions

---

### Post by no2498 on 2011-01-19
try it in vlc player click media, capture, play


cheese uses  gstreamer, good, bad, ugly, and 10

---

### Post by no2498 on 2011-01-19
try it in vlc player click media, capture, play


cheese uses  gstreamer, good, bad, ugly, and 10

---

### Post by no2498 on 2011-01-19
try it in vlc player click media, capture, play


cheese uses  gstreamer, good, bad, ugly, and 10

---

### Post by no2498 on 2011-01-19
cheese uses gstreamer good, bad, ugly, and 10

you can try it in vlc player click media, capture device, play

---

### Post by no2498 on 2011-01-19
cheese uses gstreamer good, bad, ugly, and 10

you can try it in vlc player click media, capture device, play

---

### Post by no2498 on 2011-01-19
cheese uses gstreamer good, bad, ugly, and 10

you can try it in vlc player click media, capture device, play

---

### Post by no2498 on 2011-01-19
cheese uses gstreamer good, bad, ugly, and 10

you can try it in vlc player click media, capture device, play

---

