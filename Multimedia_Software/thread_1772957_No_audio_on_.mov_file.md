---
title: "No audio on .mov file"
date: 2011-06-01
forum: Multimedia Software
---

### Post by YeeP on 2011-06-01
I have tried this file on multiple different video players, none of them will play the audio(mplayer, vlc and xine). Seems like a codec issue to me. I do have the medibuntu, and the w32codecs. Here is a screenshot I got from xine.

[IMG]http://i440.photobucket.com/albums/qq123/YeeP79/Selection_009.png[/IMG]

Anyone know where I can get this lpcm codec?

Thank you.

---

### Post by andrew.46 on 2011-06-01
A recent copy of MPLayer seems to have that codec:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ac help | grep -i 'lpcm'[/COLOR]**

dvdpcm      dvdpcm    working   Uncompressed DVD/VOB LPCM
fflpcm      ffmpeg    working   Blu-ray LPCM  [pcm_bluray]

```

Can you post a link to the file?

---

