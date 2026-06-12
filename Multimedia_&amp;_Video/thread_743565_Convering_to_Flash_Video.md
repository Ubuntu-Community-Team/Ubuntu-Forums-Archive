---
title: "Convering to Flash Video"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by teamkiller87 on 2008-04-02
Hey there,

So I've been fiddling around with ffmpeg trying to convert from an mpg file to an flv file. The video turns out great but I seem to have problems with the audio in the sense that I DON'T HAVE ANY. I've been trying helplessly to find a solution arount the web... but none showed up. Anybody with a fix out there?

---

### Post by warp99 on 2008-04-02
Try using the '-acodec copy' switch to just copy over the audio. You can always recode the audio in another format.

Edit:

FLV uses mp3 encoding so you would use the following string:

ffmpeg -i input.avi -acodec mp3 -ar 44100 -ab 32 -vcodec flv output.flv

---

