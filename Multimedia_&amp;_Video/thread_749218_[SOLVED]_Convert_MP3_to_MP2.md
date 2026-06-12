---
title: "[SOLVED] Convert MP3 to MP2"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by zombie-si on 2008-04-08
This is my first post - so please be gentle with me!
I need to convert an MP3 file to MP2 to use in a DVD menu.
Can anyone suggest a quick way?

---

### Post by zombie-si on 2008-04-09
Yes MP2 - MPEG-1 Audio Layer II (MP2, sometimes incorrectly called Musicam)

I've sorted it myself now.
 Convert MP3 to wav:-

mpg321 -w wavfile.wav mp3file.mp3

Convert wav to MP2:-

mp2enc -r 48000 -o mp2file.mp2 < wavfile.wav

:guitar:

---

