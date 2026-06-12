---
title: "[SOLVED] Easy way to list info for audio (WAV, MP3) files"
date: 2008-05-10
forum: Multimedia Software
---

### Post by xfred on 2008-05-10
Hey

I have my CD collection on a 500G drive in both WAV (backup) and MP3 (actual daily use) format.  Anyhow, due to a misunderstanding with sound-juicer a whole bunch of the more recent WAVs were ripped in mono low bitrate.  And I need to figure out which ones so I can re-rip them properly.  So, to my question...

Q. Is there a way to list the details of a wave file (channels, bitrate) using a simple command-line command?


(otherwise I would have to laboriously go through and manually look at the properties of each file using the gui, which would not be fun for almost 300G worth of files)

Thanks in advance

---

### Post by unutbu on 2008-05-10
```
% file /usr/share/sounds/card_shuffle.wav
/usr/share/sounds/card_shuffle.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 44100 Hz

```

Does that include the info you want?

---

### Post by xfred on 2008-05-11
> **unutbu said:**
> ```
% file /usr/share/sounds/card_shuffle.wav
/usr/share/sounds/card_shuffle.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 44100 Hz

```

Does that include the info you want?


Thanks, that works perfectly (and looks like something I *should* have been able to find on google... except that I was being too specific in my search :oops:).

---

### Post by unutbu on 2008-05-11
Oh, I think you're being too hard on yourself. It's not obvious that `file` would provide much info, and I only get 1.4 billion hits searching for the word 'file'. :)

---

