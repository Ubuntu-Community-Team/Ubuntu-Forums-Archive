---
title: "Quod Libet won't play anything .flac"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by tgoose on 2007-12-10
I know that Quod Libet played FLAC out of the box on Feisty, but it certainly doesn't work currently on my Gutsy installation - it may or may never have worked; I can't remember.

I have all of quodlibet, quodlibet-ext and quodlibet-plugins installed, and FLAC works fine in totem, firefox, rhythmbox (but I uninstalled it.)

On the console I get

```

Supported formats: mod, mp3, mp4, mpc, spc, trueaudio, wav, wavpack, wma, xiph

```

(if I can get *trueaudio* but not FLAC there must be something wrong :p

If I rename FLAC files from whatever.flac to whatever.mp3 then they play back, so I guess I just need to edit something to let Quod Libet know that .flac is acceptable, but I don't know what!

Thanks in advance.

---

### Post by hugmenot on 2007-12-10
> **tgoose said:**
> 
```

Supported formats: mod, mp3, mp4, mpc, spc, trueaudio, wav, wavpack, wma, xiph

```


You have flac support. It's listed as xiph.

What does mutagen-inspect show, when you run it on a file?

---

### Post by tgoose on 2007-12-11
Ah, my mistake - it was some encoding issue on certain files (container?). mutagen-inspect showed bizarre MPEG attributes, which were certainly incorrect

- MPEG 2 layer 2, 40000 bps, 22050 Hz, 7815.86 seconds (sketchy) (audio/mp3)
COMM=c0='   '=Sweden P3 Analogue Cable FM Broadcast (15 October 2004) > Personal Computer (.wav) > FLAC (Level 8)


So, I decoded and re-encoded it with flac and it's fine now.

Thanks for your help, I wouldn't have figured that out if you hadn't told me about mutagen-inspect!

---

