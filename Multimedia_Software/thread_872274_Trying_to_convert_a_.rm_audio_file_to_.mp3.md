---
title: "Trying to convert a .rm audio file to .mp3"
date: 2008-07-27
forum: Multimedia Software
---

### Post by jacques83 on 2008-07-27
Hi

I got the following stacktrace...

aj@aa-laptop:~/Desktop$ mencoder Track01.rm -ovc frameno -oac mp3lame -of rawaudio -lameopts cbr:br=128 -o output_file.mp3
MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x8d017
REAL file format detected.
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
[real] Audio stream found, -aid 0
Stream mimetype: logical-fileinfo
Video stream is mandatory!


Any clues on how do I overcome this? My file doesnt have any video component.

Thanks

A

---

### Post by owain123 on 2008-07-29
I think Mencoder might be able to do this. Google it and see what it comes up with. Sorry i haven't had much to do with audio conversion so that about as much as i can help

---

### Post by forger on 2008-07-29
this thread might help:
[http://ubuntuforums.org/showthread.php?t=218246](http://ubuntuforums.org/showthread.php?t=218246)

or this:
[http://anilinux.blogspot.com/2007/11/convert-rm-to-mp3-format.html](http://anilinux.blogspot.com/2007/11/convert-rm-to-mp3-format.html)

---

### Post by Orlsend on 2008-07-29
You can convert them online.... Easy.... just Google "RM to MP3"

---

### Post by ad_267 on 2008-07-29
[http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/85596-how-convert-rm-mp3.html](http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/85596-how-convert-rm-mp3.html)

---

### Post by TenPlus1 on 2008-07-29
Go into Add/Remove and search for a program called SoundConverter...  I use this all the time to convert audio files, especially non-standard ones like real and flv...

---

