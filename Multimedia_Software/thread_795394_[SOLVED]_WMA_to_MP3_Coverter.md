---
title: "[SOLVED] WMA to MP3 Coverter"
date: 2008-05-15
forum: Multimedia Software
---

### Post by LonelyTraveler on 2008-05-15
Can anyone point me in the direction of a wma to mp3 converter. I had one before, but can't remember what it is called. 

Thanks.

---

### Post by mc4man on 2008-05-15
i know of 2 relativly simple ways
mplayer wma -> wav , then lame -> mp3  ex.
```
mplayer -vc null -vo null -aid 1 -ao pcm:waveheader:file=foo.wav foo.wma
,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,

lame -b 192 -h foo.wav foo.mp3
``` or ffmpeg , ex.
```
ffmpeg -i foo.wma -ab 128k  foo.mp3
```

commands assume file(s) in home directory, change bitrate to suit

---

### Post by Major_Kong on 2008-05-15
[QUOTE=LonelyTraveler]Can anyone point me in the direction of a wma to mp3 converter. I had one before, but can't remember what it is called. 

Thanks.[/QUOTE]

Just install Sound Converter. It should be enough for what you want.

---

### Post by LonelyTraveler on 2008-05-15
Thanks to both of you. Sound Converter was the one I was looking for.

---

