---
title: "help needed for ffmpeg conversion WMA to MP3"
date: 2010-05-19
forum: Multimedia Software
---

### Post by slashwannabe94 on 2010-05-19
hey all, 

does anyone know how i convert a WMA file to an MP3 file using ffmpeg. 

i have been using

ffmpeg -i /path/to/file.wma -ab 32 /path/to/output.mp3

what am i doing wrong ?

  Duration: 00:00:00.00, bitrate: 1413 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Output #0, mp3, to '/home/marcom/y.mp3':
    Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, s16, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec for output stream #0.0

---

### Post by mc4man on 2010-05-19
Well you should be using a k as in -ab 32k, ( though I believe ffmpeg would ignore your error and encode to the default of 128k

Your problem is that the wma is lossless which atm ffmpeg doesn't support
> stream #0.0: Audio: pcm_s16le, 44100 Hz, stereo, s16, 1411 kb/s 

Your only solution outside of a win. prog in wine is a 32 bit  mplayer with w32codecs installed.

mplayer -> .wav -> lame -> .mp3 
or 
mplayer -> .wav -> ffmpeg -> .mp3


If you had a bunch to do you could batch convert either thru a command or a script.
or a batch convert using named pipes, mplayer to lame

---

