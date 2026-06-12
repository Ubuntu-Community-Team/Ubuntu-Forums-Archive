---
title: "Problems with bluray playback and ffvc1 codec"
date: 2008-10-04
forum: Multimedia Software
---

### Post by aggiemarine07 on 2008-10-04
not quite sure if this belongs in this section of the website or not but I will post it here and move it to where ever it needs to go if that is the case; by anyhow here is my story:

My system specs are: ubuntu 8.04 with a 3.1ghz intel, 512mb nvidia 7900 bfg,  4gb of pc5400 RAM, 750gb seagate-100gb Maxtor-36gb WD 10000rpm, Pioneer Bluray drive

I have been able to successfully dump Spiderman3 from my bluray drive to the HD using dumphd (took an hour or two and 50gbs but hey it did it successfully) but when I try to play them in mplayer the video is great (really smooth) but the sound is choppy. I built the latest SVN mplayer from source and used  the command "mplayer -vc ffvc1 bluraymovie.m2ts"

I then noticed in the terminal that it would give back this output for the ffvc1 codec:

Forced video codec: ffvc1
Cannot find codec matching selected -vo and video format 0x10000005.


When I go back to the terminal and do a mplayer -vc help it spits back this after the command:

ffvc1       ffmpeg    problems  FFmpeg M$ WVC1  [vc1]

I then also tried to play with just "mplayer 00011.m2ts" it had still had the choppy sound (and oddly enough was in japanese :) Dont know how that happened.

Any thoughts or outputs needed I will happily provide, I know I am very close to playing bluray on my linux system and would greatly appreciate any help. Thanks!

gw

---

### Post by Vetal_978 on 2009-11-27
same problem here. is there any solution?

---

### Post by andrew.46 on 2009-11-28
Hi aggiemarine07,

> **aggiemarine07 said:**
>  I built the latest SVN mplayer from source and used  the command 
```

mplayer -vc ffvc1 bluraymovie.m2ts
```

I then noticed in the terminal that it would give back this output for the ffvc1 codec:
```

Forced video codec: ffvc1
Cannot find codec matching selected -vo and video format 0x10000005.
```


Unfortunately I have no experience with BlueRay playback but I believe you are forcing the wrong video codec there and should perhaps be using:

```
mplayer -vc ffh264 bluraymovie.m2ts
```

and better still be using *-vc ffh264vdpau -vo vdpau* if you have an appropriate video card (not sure if this is suitable: nvidia 7900) and a suitably compiled copy of MPlayer. Sounds like you have already read this page:

Playing Blu-Ray and HD DVD Video
[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

As for the choppy sound can you post the full terminal output for MPlayer?

All the best,

Andrew

---

