---
title: "Mpeg-aac Audio NOT working!"
date: 2008-05-25
forum: Multimedia Software
---

### Post by jastonas on 2008-05-25
I have tried gstreamer, w32codecs, libdvd etc codecs and nothing seems to work!
Is there a solution for this?
Thanx in advance

---

### Post by aeiah on 2008-05-25
what happens when you run the video through, say gmplayer from a terminal?

```
gmplayer path/to/video.ext
```

it should tell you whats needed

---

### Post by jastonas on 2008-05-25
Totem - Mplayer
Forced audio codec: mad
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio) decoder)

By the way.. mplayer and totem wont even play properly this mp4 hdtv videos. They play 1-2 seconds.. then stop. No sound at all though. VLC plays perfectly video but with no sound!

VLC gives me this message 

VLC media player 0.8.6e Janus
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Box: 
main warning: can't store message (Invalid or incomplete multibyte or wide character): read box: "
main warning: can't store message (Invalid or incomplete multibyte or wide character): found Box: 
main warning: can't store message (Invalid or incomplete multibyte or wide character): read box: "

---

### Post by leodido on 2008-05-25
i have the exact same problem, Video plays only if i use VLC and i have no sound in my videos, i can play mp3 tho...

---

### Post by xc3RnbFO8P on 2008-05-25
Try to install **liba52** in Synaptic Package Manager

---

### Post by jastonas on 2008-05-25
Already there! Installed with VLC

---

### Post by leodido on 2008-05-25
Well i made it work but i have no clue how! What i did is restart a few times with the ctrl+alt+backspace combo and at some point i got the sound going ...

---

### Post by ermagana on 2009-08-30
hi, i know this sounds dumb to say but I had the same issue... turns out that all i had to do was go to my preferences for the video player, find the audio section and make sure that it was using the right output routine (in my case ALSA).

---

