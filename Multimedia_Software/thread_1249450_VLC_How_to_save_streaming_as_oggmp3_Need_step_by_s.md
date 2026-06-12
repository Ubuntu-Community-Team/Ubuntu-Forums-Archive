---
title: "VLC: How to save streaming as ogg/mp3? Need step by step instruction"
date: 2009-08-25
forum: Multimedia Software
---

### Post by guhpraset on 2009-08-25
I tried to save [http://radio.vstreamer.net:8000/dradio.m3u](http://radio.vstreamer.net:8000/dradio.m3u) as ogg, but the file size keep on zero.

Is there any clear step by step instruction on how to stream and save it? As OGG, or MP3 (i wonder which is better?).

I use VLC 0.99a Grishenko on ubuntu 9.04

Thank You

---

### Post by andrew.46 on 2009-08-26
Hi guhpraset,

> **guhpraset said:**
> I tried to save [http://radio.vstreamer.net:8000/dradio.m3u](http://radio.vstreamer.net:8000/dradio.m3u) as ogg, but the file size keep on zero.

Unfortunately I was not able to open this stream at all. Is the address correct, and can you play it?

Andrew

---

### Post by guhpraset on 2009-08-26
Yes, it is correct. 
I can not play it in firefox (by click), but if i copy the link and paste into VLC then it play ok. 

The problem is i cant save it as ogg.

---

### Post by del_diablo on 2009-08-26
I can play this in the browser(Opera) with Xine's plugin.

---

### Post by CAT-III on 2009-08-28
It just drives me crazy. VLC simply can't save to file, the file is always 0 bytes. Not from the GUI, nor (following the few posts available) from the CLI. 

It's a syntax issue. It's cross-platform. Tried Linux and Windows, same thing--0 bytes.
Even the automagically-generated stream output string you find in the GUI is wrong.

The VLC folks must finalize their CLI syntax once and for all and stick to it.

Anyway, I found this clue (luckly, it pertains to the current version of VLC, but wait! It's going to be obsolete just as soon as the new syntax is upgraded/improved](*,)](*,)](*,) )
[http://forum.videolan.org/viewtopic.php?f=4&t=63879](http://forum.videolan.org/viewtopic.php?f=4&t=63879)

So, here it is:

```
vlc [http://URL-of-your-radio-feed](http://URL-of-your-radio-feed) --sout="#transcode{acodec=mpga,ab=128,channels=2,samplerate=44100}:duplicate{dst=std{access=file,mux=raw,dst=/home/user/audiotest.mp3}}"

```
Or, if you want to listen at the same time, add this at the end:  .../user/audiotest.mp3},**dst=display**}
So the complete command is:
```
vlc [http://URL-of-your-radio-feed](http://URL-of-your-radio-feed) --sout="#transcode{acodec=mpga,ab=128,channels=2,samplerate=44100}:duplicate{dst=std{access=file,mux=raw,dst=/home/user/audiotest.mp3},dst=display}"

```

Of course, change /home/user/audiotest.mp3 to the appropriate path/filename.


It's the position of the double quotes that did the trick for me. Other posts suggest something like
  '--sout=#transcode.......}'
The single quotes don't work. No single quotes don't work either. 


Oh, BTW: this won't fix your .ogg problem. But at least you won't get a 0-byte file...

Good luck.

---

