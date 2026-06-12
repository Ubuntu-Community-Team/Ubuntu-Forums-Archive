---
title: "avconv, trouble extracting clip"
date: 2017-03-10
forum: Multimedia Software
---

### Post by bill-lancaster on 2017-03-10
I wish to extract a clip from a dv file.
This should work but doesn't.
```
avconv -i /home/bill/1.dv -ss 100 -t 100  acodec /home/bill/aa1.dv
```
this is the output:-
avconv version 9.20-6:9.20-0ubuntu0.14.04.2+fdkaac, Copyright (c) 2000-2014 the Libav developers
  built on Feb 13 2017 12:16:45 with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
[dv @ 0x100e720] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from '/home/bill/1.dv':
  Duration: 00:04:51.24, start: 0.000000, bitrate: 28800 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, PAR 16:15 DAR 4:3, 25 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.2: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
Unable to find a suitable output format for 'acodec'

Have read a lot of posts on this but am still stuck.

Any ideas would be welcome

---

### Post by alien878 on 2017-03-10
I suggest you remove "acodec" from the command.  If you want to change the audio codec, it should be "-acodec <new codec>".  If you want to leave it the same, then just omit it.

---

### Post by bill-lancaster on 2017-03-10
Thanks for the response, tried,
```
avconv -i /home/bill/1.dv -ss 100 -t 100 /home/bill/aa1.dv
```
Got:
avconv version 9.20-6:9.20-0ubuntu0.14.04.2+fdkaac, Copyright (c) 2000-2014 the Libav developers
  built on Feb 13 2017 12:16:45 with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
[dv @ 0x16ef020] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from '/home/bill/1.dv':
  Duration: 00:04:51.24, start: 0.000000, bitrate: 28800 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, PAR 16:15 DAR 4:3, 25 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.2: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
File '/home/bill/aa1.dv' already exists. Overwrite ? [y/N] y
[dv @ 0x16f6f80] Can't initialize DV format!
Make sure that you supply exactly two streams:
     video: 25fps or 29.97fps, audio: 2ch/48kHz/PCM
     (50Mbps allows an optional second audio stream)
Output #0, dv, to '/home/bill/aa1.dv':
  Metadata:
    encoder         : Lavf54.20.4
    Stream #0.0: Video: dvvideo, yuv420p, 720x576 [PAR 16:15 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (dvvideo -> dvvideo)
  Stream #0:1 -> #0:1 (pcm_s16le -> pcm_s16le)
Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted

---

### Post by alien878 on 2017-03-10
It looks like the input file is not a standard dv format (audio is 32khz instead of 48khz).

You might try adding -c:a copy after the -t 100.  avconv might still complain though.  If so, you will have to convert the audio.  I think that would be -c:a pcm.

---

### Post by bill-lancaster on 2017-03-10
Thanks again!
Converted the .dv file to .mp4 and could split it easily.
The dv files are from Sony video camera tapes.
I'll start looking at the best format to convert to (perhaps mp4 isn't best).
Also, perhaps there's a way to correct whatever is wrong with the original dv files

---

### Post by bill-lancaster on 2017-03-10
Should have posted this:-
```
avconv -i /home/bill/1.dv -ss 100 -t 100 -c:a copy /home/bill/x1.dv
```

gives:-
avconv version 9.20-6:9.20-0ubuntu0.14.04.2+fdkaac, Copyright (c) 2000-2014 the Libav developers
  built on Feb 13 2017 12:16:45 with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
[dv @ 0xa58fe0] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from '/home/bill/1.dv':
  Duration: 00:04:51.24, start: 0.000000, bitrate: 28800 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, PAR 16:15 DAR 4:3, 25 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.2: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
[dv @ 0xa61020] Can't initialize DV format!
Make sure that you supply exactly two streams:
     video: 25fps or 29.97fps, audio: 2ch/48kHz/PCM
     (50Mbps allows an optional second audio stream)
Output #0, dv, to '/home/bill/x1.dv':
  Metadata:
    encoder         : Lavf54.20.4
    Stream #0.0: Video: dvvideo, yuv420p, 720x576 [PAR 16:15 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, 1024 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (dvvideo -> dvvideo)
  Stream #0:1 -> #0:1 (copy)
Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted

And,
```
avconv -i /home/bill/1.dv -ss 100 -t 100 -c:a -c:a pcm copy /home/bill/x1.dv
```

gives

avconv version 9.20-6:9.20-0ubuntu0.14.04.2+fdkaac, Copyright (c) 2000-2014 the Libav developers
  built on Feb 13 2017 12:16:45 with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
[dv @ 0x1024e20] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from '/home/bill/1.dv':
  Duration: 00:04:51.24, start: 0.000000, bitrate: 28800 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, PAR 16:15 DAR 4:3, 25 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.2: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
Unable to find a suitable output format for 'pcm'

---

### Post by alien878 on 2017-03-10
> **bill-lancaster said:**
> 
Make sure that you supply exactly two streams:
     video: 25fps or 29.97fps, audio: 2ch/48kHz/PCM
     (50Mbps allows an optional second audio stream)

According to the error message, dv expect audio to be 48khz pcm

You could try:

avconv -i /home/bill/1.dv -ss 100 -t 100 -c:a pcm_s16le -r:a 48000 /home/bill/x1.dv

If that doesn't work, I'm at a bit of a loss as I'm not much of an expert of dv format.  You could check avconv -codecs to list available codecs.

---

### Post by bill-lancaster on 2017-03-10
Oh well!  Thanks so much for trying.
```
avconv -i /home/bill/1.dv -ss 100 -t 100 -c:a pcm_s16le -r:a 48000 /home/bill/x1.dv
```

Gives:-

  built on Feb 13 2017 12:16:45 with gcc 4.8 (Ubuntu 4.8.4-2ubuntu1~14.04.3)
[dv @ 0x1003000] Estimating duration from bitrate, this may be inaccurate
Input #0, dv, from '/home/bill/1.dv':
  Duration: 00:04:51.24, start: 0.000000, bitrate: 28800 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, PAR 16:15 DAR 4:3, 25 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
    Stream #0.2: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
[dv @ 0x100b120] Can't initialize DV format!
Make sure that you supply exactly two streams:
     video: 25fps or 29.97fps, audio: 2ch/48kHz/PCM
     (50Mbps allows an optional second audio stream)
Output #0, dv, to '/home/bill/xx1.dv':
  Metadata:
    encoder         : Lavf54.20.4
    Stream #0.0: Video: dvvideo, yuv420p, 720x576 [PAR 16:15 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 32000 Hz, stereo, s16, 1024 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (dvvideo -> dvvideo)
  Stream #0:1 -> #0:1 (pcm_s16le -> pcm_s16le)
Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted

---

### Post by SeijiSensei on 2017-03-10
> **bill-lancaster said:**
> I'll start looking at the best format to convert to (perhaps mp4 isn't best).

I usually choose Matroska as the output container if the devices I'm using support it.  The mkvtoolnix package has a nice array of applications to extract, merge, etc., tracks to or from an .mkv file, too.

---

### Post by mc4man on 2017-03-11
Most of the commands you tried were poorly/improperly written and orig. not copying (i.e. "extracting).
couple of ex.
red wrong, encodes a & v
```
avconv -i /home/bill/1.dv -ss 100 -t 100 [COLOR="#FF0000"] acodec[/COLOR] /home/bill/aa1.dv
```
red encode & copy?, blue does nothing
```
avconv -i /home/bill/1.dv -ss 100 -t 100 [COLOR="#0000CD"]-c:a [/COLOR][COLOR="#FF0000"]-c:a pcm copy[/COLOR] /home/bill/x1.dv
```
Not sure what red was going to do
```
avconv -i /home/bill/1.dv -ss 100 -t 100 -c:a pcm_s16le [COLOR="#FF0000"]-r:a 48000[/COLOR] /home/bill/x1.dv
```

In any event that version of avconv wouldn't deal with 32kHz pcm so didn't matter commands were wrong.

FFmpeg would handle that audio (which is apparently allowed), if you had that version of avconv from ppa you could just install ppa's ffmpeg for use of the binaries.
For 'extracting' you'd could use a stream  copy parameter, period
-c copy
avconv -i /home/bill/1.dv -ss 100 -t 100 -c  copy /home/bill/x1.dv

For ffmpeg you could of copied the video, re-encoded audio, ex.
```
ffmpeg  -i /home/bill/1.dv -ss 100 -t 100 -c:v copy -c:a pcm_s16le -ar 48000 /home/bill/x1.dv
```
or 
```
ffmpeg -ss 100  -i /home/bill/1.dv  -t 100 -c:v copy -c:a pcm_s16le -ar 48000 /home/bill/x1.dv
```
You should read here about placement of -ss & some possible codec copy issues
[https://trac.ffmpeg.org/wiki/Seeking](https://trac.ffmpeg.org/wiki/Seeking)

---

### Post by bill-lancaster on 2017-03-14
Thank you very much mc4man.
I've learned a lot and my project is progressing!

---

