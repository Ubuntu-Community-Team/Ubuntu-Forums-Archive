---
title: "SoundJuicer Not Ripping mp3s with ID3 tags"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by happy-and-lost on 2006-12-14
I've managed to get SJ ripping mp3s using this gstreamer...

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=192 ! id3v2mux

And it rips fine... BUT the ID3 tags, whilst showing up in Nautilus file properties, do not show up in EasyTag and, crucially, my mp3 player.

This is the only major annoyance I have with Ubuntu! ](*,)

---

### Post by meng on 2006-12-14
Perhaps try grip instead?

---

### Post by happy-and-lost on 2006-12-14
It's a pathetic excuse, but grip really scares me! Is there a howto out there?

---

### Post by meng on 2006-12-14
[http://nostatic.org/grip/doc/index.html](http://nostatic.org/grip/doc/index.html)
Seems a fairly good starting point.

---

### Post by mb4guns on 2007-06-05
There has to be a solution, i have the same problem, tried with pipes id3v2mux and id3mux, both plugins are installed dubbel checked this. SJ just refuses to add any id3 tags.

---

