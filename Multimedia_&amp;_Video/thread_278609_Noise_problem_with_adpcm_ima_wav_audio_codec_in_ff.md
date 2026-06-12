---
title: "Noise problem with adpcm ima wav audio codec in ffmpeg"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by hulet on 2006-10-16
Hello,

I was trying to convert some *.mpg video files where the sound was encoded with mp3  to *.avi files with sound encode adpcm_ima_wav. I can only use this sound codec because that's all my video playing device (gmini 400) handles (well, the manual says it also handles *.avi videos with sound encoded in mp3 but, in actuality, it chokes up while playing this kind of videos). So, the problem is that after converting the files to *.avi when I play them, I noticed a very significant audio noise introduced in the final *.avi file. The noise sounds like the sound a rotor of a helicopter makes. Here is the command I used to change the files:

```
ffmpeg -i blah.mpg -s 320x240 -acodec adpcm_ima_wav  blah.avi
```

I have looked the net for all the info I can get on how to remove this noise but to no avail. Does anyone know how I can use the adpcm_ima_wav codec without introducing this noise? 

Thanks.

---

