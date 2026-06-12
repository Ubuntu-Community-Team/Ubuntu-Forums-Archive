---
title: "How to separate the audio from a video?"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2007-11-02
I've become the source of free software for my friend lately, which I'm just fine with, but I do need some help. He wants to know if there is a way to separate the audio from a video, and save it as a separate file. I don't know of any way to do this, so I'm hoping someone on this forum does.

Also, does anyone know of a forum or site specifically for finding free software for situations like this?

---

### Post by ZOMGxuan on 2007-11-02
You could perhaps use video editing programs such as Kino and Pitivi Video Edtior.
I don't know much as I have not yet used these programs, they came with Ubuntu Studio.

If worst comes to worst, you could try playing a video and then recording the sound that is being played back using a sound recording program.

Hope this is of some help.

---

### Post by disturbed1 on 2007-11-02
mplayer your.file.avi.-dumpaudio < saves as dump.stream, you'll need to rename it.

or

mplayer your.file.avi -vo null -vc null -ao pcm < real time, meaning a one hour movie will take one hour

or

 mplayer your.file.avi -vo null -vc null -ao pcm:fast < faster, but may have issues with buggy codecs (wma)

or

Use Avidemux, choose copy for audio codec, click on the audio menu up top and chose save audio.

---

### Post by MrFSL on 2007-11-02
I use ffmpeg.

---

### Post by rainwalker on 2007-11-02
Ah...I forgot to mention that he uses Vista.

---

### Post by rsambuca on 2007-11-02
> **rainwalker said:**
> Ah...I forgot to mention that he uses Vista.

More than just a minor detail!!!  Methinks you are asking in the wrong forum!

---

### Post by disturbed1 on 2007-11-02
> **rainwalker said:**
> Ah...I forgot to mention that he uses Vista.

Try this link then [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) :guitar:

---

### Post by MrFSL on 2007-11-02
Windows binaries are available for both ffmpeg and mencorder/mplayer.

---

