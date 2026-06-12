---
title: "How to find out what's wrong with MP3 and possibly encode it?"
date: 2010-10-24
forum: Multimedia Software
---

### Post by keenPenguin on 2010-10-24
Hi, 

a friend gave me an MP3 audiobook. While the MP3s can be perfectly well played on Ubuntu, my portable MP3 player has a problem. It plays the files  but they sound completely blurred and distorted. Although the voice is recognizeable, it is impossible to make out the words. 

The information which mplayer gives me on the audio files is:

Codec: MP3
Channels: Stereo
Sample rate: 22050 Hz
Bitrate: 64kbps

What can I do about the distorted sound? 
Maybe re-encode the files? (What program would I use for that?)

---

### Post by ron999 on 2010-10-24
Try resampling one of the tracks with LAME and see if it plays OK in your mp3 player.
The tracks are 22050 Hz.
Maybe 44100 Hz is better.

Like this:-

> lame --resample 44.1 track.mp3 track_new.mp3

---

### Post by keenPenguin on 2010-10-27
Worked like a charm and the MP3 is now read flawlessly both on mplayer and the portable MP3 player! Thanks very much ron!

---

