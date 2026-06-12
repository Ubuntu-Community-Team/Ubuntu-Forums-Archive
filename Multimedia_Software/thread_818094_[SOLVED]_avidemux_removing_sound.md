---
title: "[SOLVED] avidemux removing sound"
date: 2008-06-04
forum: Multimedia Software
---

### Post by paradoxni on 2008-06-04
I am converting some videos using Avidemux, is there a way to remove the audio from the original so that the newly created video has no sound? i see options for encoding the video and audio and also for extracting the audio from the movie, but so far cannot find an option to not include the audio??

---

### Post by chewearn on 2008-06-04
Yes, it's probably not a feature to copy only video.  I can't find how to remove audio too.

But all is not lost.  Give mencoder a try.  It's command line only, but quite powerful.  To copy video only, use -nosound switch, e.g.
```
mencoder inputvideo.avi -nosound -ovc copy -o outputvideo.avi
```

---

### Post by paradoxni on 2008-06-04
I can live with that fairly simple extra step, thanks :)

---

### Post by shirilover on 2008-06-05
Or, in avidemux, with video file opened.
Go to Audio->Main track and select 'None' for the source.

---

### Post by paradoxni on 2008-06-05
must have missed that..cheers.

---

### Post by onus on 2008-09-11
how do i remove the video; keep only the sound. what if i just want to listen to the audio, on a cd playable in all cd players?

---

### Post by shirilover on 2008-09-11
Open the video file and,
select Audio->Save.
This will demux the audio portion, if you want it in audio-cd format you need to use Audio->Encoder and select WAV PCM.

---

