---
title: "sound juicer help"
date: 2008-09-14
forum: Multimedia Software
---

### Post by dogsipod on 2008-09-14
i am planning on using sound juicer to rip some higher quality mp3's.  using the default mp3 pipline i was getting rips of 128kbps.  i wanted 256kbps quality.  i used ```
gst-inspect-0.10 lame
``` to see how i needed to write the pipline.
this is what i used ```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=2 vbr-mean-bitrate=256
```
I ripped the first track of of weezer's green album, a 3:24 song.  What i got was a 3.9mb file. Even though sound juicer knows what album and the titles of all the tracks all where listed unknown in the file.  the bitrate is listed as 32kbs and duration is over 16 minutes.  Any help about how to get a file with the correct information and of 256kbps quality would be great.

---

### Post by markbuntu on 2008-09-15
CDs are 2 channel 44.1kbs. Recording them at a higher bitrate is a useless exercise that cannot improve the quality of the sound and will actually reduce it due to resampling errrors.

---

### Post by dogsipod on 2008-09-15
nvm fixed the pipeline. used```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 vbr=4 quality=1 preset=1001 vbr-max-bitrate=320 ! xingmux ! id3v2mux
```

---

### Post by Vryko Lakas on 2008-09-15
> **markbuntu said:**
> CDs are 2 channel 44.1kbs.
I think you are confused. The sample rate is 44.1 kHz, which measures a different aspect altogether. 
The *bitrate* of CD audio is 1,411.2 kbit/s.

I don't think I could even listen to music encoded at a bitrate of 44.1 kb/s. It would sound awful.

---

