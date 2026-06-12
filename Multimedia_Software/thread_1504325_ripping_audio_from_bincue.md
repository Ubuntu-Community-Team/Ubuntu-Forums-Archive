---
title: "ripping audio from bin/cue"
date: 2010-06-07
forum: Multimedia Software
---

### Post by DrDevice on 2010-06-07
Hello!  I've got a bin/cue duo that contains 1 data track and some audio tracks I wish to rip.  However, I can't get to the audio tracks.  I've tried mounting the bin/cue with AcetoneISO, but it just shows me the data part.  I've tried converting the files using ```
bchunk foo.bin foo.cue foo
```, and it converts to 2 files, an iso and a cdr.  The .cdr file, as far as I can see, cannot be opened by anything.  And so I turn to you, dear fellow Ubuntu-ers for assistance.  How can I get to the audio files in the image and rip them?

Thanks for your time!

---

### Post by bulletxt on 2010-06-08
Put the CD-Audio in your drive, open a shell and type:  cdparanoia -B

---

### Post by DrDevice on 2010-06-09
> **bulletxt said:**
> Put the CD-Audio in your drive, open a shell and type:  cdparanoia -B

Sorry Bullet, but not what I needed.  I wanted to be able to get to the audio tracks from either the BIN file directly, or from the CDR file.  I have no CD to use cdparanoia with. :D

But after some more searching, and with the brilliant notion of changing my search terms to include "raw audio data", I have found my solution: Audacity.

All I had to do was install Audacity from Synaptic, then use its Import feature to pull the raw data from the .cdr, then saved it as a lossless .flac.  

Now, I know, a bunch of you are rolling your eyes now thinking "Doi!"; but in my defense; I was looking for CDR help, not raw data.  So thank you all for your time, and hopefully this post will help folks like me who just didn't put two and two together. :oops:

---

### Post by oldmankit on 2010-10-10
I know you've fixed it, but a more elegant solution (not requiring audacity) might be

```
bchunk -w Image.bin Image.cue audio
```which should give you a bunch of files called audioXX.wav

You can then use any mp3 encoder to rip these.  I use oggenc.

---

