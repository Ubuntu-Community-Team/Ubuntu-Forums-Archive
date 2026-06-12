---
title: "How to rip sound from a DVD ?!"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by artvds2708 on 2007-11-14
How can I rip the sound of a DVD ?
I got a great concert DVD but I want this also on CD.
Is there a program I can use to do this with ?
I use Ubuntu Gutsy at the moment.
:guitar:

---

### Post by ajopaul on 2007-11-14
One way to do it is using ffmpeg by accessing the .vob. replace the appropriate /media mountpoint. 

```
ffmpeg -i /media/dvd/video_ts/vts_01_1.vob -vn -acodec pcm_s16le -ar 44100 -ac 2 soundout.wav

```

---

### Post by artvds2708 on 2007-11-15
So I just insert my DVD and enter that line in my terminal ?!
That's it ?
If not please explain this in a way that a newbie understands.
Thanks.:wink:

---

