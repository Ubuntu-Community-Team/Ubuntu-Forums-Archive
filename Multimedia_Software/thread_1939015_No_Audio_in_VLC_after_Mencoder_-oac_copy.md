---
title: "No Audio in VLC after Mencoder -oac copy"
date: 2012-03-10
forum: Multimedia Software
---

### Post by Valpskott on 2012-03-10
Normally VLC plays all of my files just fine. But for some reason, if I join two video-files with mencoder, VLC will not play the audio in the new file, while MPlayer plays it just fine.

```
mencoder -oac copy -ovc x264 ../intro.mov movie.mov -o Final-Video.mov
```

Note that VLC plays the audio just fine in the separate files(before they are joined)

Audio: mp3, 44100 Hz, 2 channels, s16, 160 kb/s

If I use "-oac mp3lame" instead of "-oac copy" VLC will play the audio-stream, but the quality is less than admirable because the audio gets dropped to 32 kb/s.

Is there a way to encode mp3 audio with a bitrate of 160 kb/s in mencoder?

Or is it a bug in mencoder... or VLC?

I'd be happy to provide any info, just tell me what to type(in the terminal).

This is all part of a video rendering script I use on a lot of large files on a daily basis, so I'd appreciate any solutions that fixes the problem without adding any more encoding/transcoding steps after the mencoder command.

---

### Post by ron999 on 2012-03-10
> **Valpskott said:**
> 
Is there a way to encode mp3 audio with a bitrate of 160 kb/s in mencoder?

Hi
If you do need to encode the mp3...
your oac command is like this:-
```
-oac mp3lame -lameopts cbr:br=160
```
More mp3 information at **mencoder -lameopts help**

---

### Post by Valpskott on 2012-03-10
Just tried it! Thanks, that fixed the problem! Now the audio in the file gets to be 160 kb/s and it plays fine in VLC :)

---

### Post by ron999 on 2012-03-19
...

---

