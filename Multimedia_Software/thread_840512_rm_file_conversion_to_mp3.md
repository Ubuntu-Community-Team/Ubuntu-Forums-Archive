---
title: "rm file conversion to mp3"
date: 2008-06-25
forum: Multimedia Software
---

### Post by roscoetuff on 2008-06-25
I'd like to convert .rm files from real player for a conference I was unable to attend to play on my MP3 Player (Cowon D2). I have tried a number of approaches, but so far come up empty. The files ain't small: one of them runs over 100Mb and covers 2 hours of a presentation. This is too long to sit at the computer, and ability to load up the MP3 and head to the gym is all I wanna do.

Any clue? I'm on 8.04

---

### Post by cariboo on 2008-06-25
If you mencoder and lame installed the snippet should work:

```
mencoder input_file.rm -ovc frameno -oac mp3lame -of rawaudio -lameopts cbr:br=128 -o output_file.mp3 
```

mencoder and lame are available in the repositories, you can use synaptic to install them.

Jim

---

### Post by roscoetuff on 2008-06-25
Jim:

Thanks for the help...

Maybe I'm missing some repositories... but I don't have Mencorder, nor do I find through Synaptic or otherwise. Can you suggest the next step?

THanks,
Skip

---

### Post by roscoetuff on 2008-06-26
Still having problems. Not sure why I get the video message:

pup@ubuntu:~$ mencoder 17thMinsky1.rm -ovc frameno -oac mp3lame -of rawaudio -lameopts cbr:br=128 -o 17thMinsky1.mp3
MEncoder 2:1.0~rc2-0ubuntu13+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz (Family: 6, Model: 15, Stepping: 10)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x6e2ffbd
REAL file format detected.
Stream description: fileinfo
Stream mimetype: logical-fileinfo
Stream description: audio/x-pn-multirate-realaudio logical stream
Stream mimetype: logical-audio/x-pn-multirate-realaudio
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
[real] Audio stream found, -aid 0
Stream description: Audio Stream
Stream mimetype: audio/x-pn-multirate-realaudio
[real] Audio stream found, -aid 1
Video stream is mandatory!

---

