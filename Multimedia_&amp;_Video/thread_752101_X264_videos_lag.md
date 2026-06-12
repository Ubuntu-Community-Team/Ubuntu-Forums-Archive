---
title: "X264 videos lag"
date: 2008-04-11
forum: Multimedia &amp; Video
---

### Post by ashrack on 2008-04-11
Using Hardy and when playing 720p movies the sound lags in Totem although the CPU is only at 50%.

I've also tried with Kaffeine-xine but it just terminates.

---

### Post by aeiah on 2008-04-11
i get the best results with mplayer. xine also works quite well but i get the occasional audio lag on HD content. what does the terminal say when you launch Kaffeine-xine from it?

```
kaffeine-xine /path/to/720p.mkv
```

---

### Post by stefangr1 on 2008-04-11
> **ashrack said:**
> Using Hardy and when playing 720p movies the sound lags in Totem although the CPU is only at 50%.

I've also tried with Kaffeine-xine but it just terminates.


Do you mean that the cpu is at 50% like one core on 100% and the other idle? In Linux, only one core can be used for x264 decoding unless some very specific encoding requirements have been met (which is very rare).

I personally get the best results with mplayer without gui or terminal.

---

### Post by aeiah on 2008-04-11
mplayer can multithread though. whilst this isnt true dualcore decoding, it can off the audio onto the 2nd core, which makes things go nicer. my dualcore always has both cores working when im watching HD

but anyway, i didnt think an athlon 5000 was dualcore?

---

### Post by ashrack on 2008-04-18
Sorry for not answering sooner was working on my Laptop with gentoo install.
Anyway now Kaffeine works and the video doesn't lag anymore.
Could be that I have installed FGLRX before I was using RADEONHD and update Hardy but I am not sure.

> **stefangr1 said:**
> Do you mean that the cpu is at 50% like one core on 100% and the other idle? In Linux, only one core can be used for x264 decoding unless some very specific encoding requirements have been met (which is very rare).

I personally get the best results with mplayer without gui or terminal.
The cores are both around 25% so that accumulates to ~50%

> **aeiah said:**
> mplayer can multithread though. whilst this isnt true dualcore decoding, it can off the audio onto the 2nd core, which makes things go nicer. my dualcore always has both cores working when im watching HD

but anyway, i didnt think an athlon 5000 was dualcore?
athlon 5000 X2 black edition are dual core.

---

### Post by geoken on 2008-04-18
Switching to Totem-xine will also fox your issues. Frankly, I don't know why Totem-gstreamer is the default.

---

### Post by ashrack on 2008-04-18
I am also at a loss why totem-gstreamer is the default since it clearly sucks since the get go.

---

