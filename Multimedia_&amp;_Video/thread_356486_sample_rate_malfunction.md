---
title: "sample rate malfunction"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by psylocat on 2007-02-08
Howdy. I've been using Ardour for some time to produce an album, and have suddenly come across a huge problem. Whenever I open an old sessions in ardour, ardour tells me although the record/playback sample rate is 44100 Hz, all my previously recorded sound files have a sample rate of 48000...which is strange because they were all recorded using a sample rate of 44100. In any case, this is a huge blow, because all the previous files sound rediculous. Any suggestions??

Thanks!

---

### Post by bgryderclock on 2007-03-06
> **psylocat said:**
> Howdy. I've been using Ardour for some time to produce an album, and have suddenly come across a huge problem. Whenever I open an old sessions in ardour, ardour tells me although the record/playback sample rate is 44100 Hz, all my previously recorded sound files have a sample rate of 48000...which is strange because they were all recorded using a sample rate of 44100. In any case, this is a huge blow, because all the previous files sound rediculous. Any suggestions??

Thanks!

I had the same problem with WAV files  being created in Hydrogen at a sample rate of 44.1K and them imported and played too fast in Ardour at a sample rate of 48k. 

**Answer**

i found a work around. i used a terminal command call sox, like this:

```
sox OrigSoundFile.wav -r 48000 correctedNewfile.wav rate
```

Are there any simple gui interfaces for sox?:mrgreen:

---

