---
title: "Problems with mencoder and codecs"
date: 2011-06-23
forum: Multimedia Software
---

### Post by lewin on 2011-06-23
I'm posting this here since mencoder is usually used by linux users.
 
I'm trying to create a timelapse video from a large collection of .jpeg files.
 
I'm using mencoder/mplayer, but I'm only using the codec mjpeg, resulting in a large video file. I'm trying to use another codec that will compress the images, but still giving good quality. 
 
The code I'm using is:
 
mencoder -speed 2 mf://*.jpg -mf fps=24:type=jpeg -noskip -of lavf -lavfopts format=mov -ovc lavc -lavcopts vglobal=1:coder=0:vcodec=mjpeg:vbitrate=3000 -vf scale=1028:-2 -o bud-steypustod.mov
 
I'm using the lavc library codecs. I want to use a h.264 codec, but I don´t know what library it's located in and how my code has to change. 
 
Oh, and I'm actually using Windows :)

---

### Post by andrew.46 on 2011-06-23
I guess a starting point is to check if your copy of mencoder has access to H.264 encoding with x264:

```

andrew@skamandros~$ **[COLOR="Red"]mencoder -ovc help[/COLOR]**
MEncoder SVN-r33648-4.5.3 (C) 2000-2011 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
**[COLOR="Red"]   x264     - H.264 encoding[/COLOR]**

```

---

### Post by lewin on 2011-06-24
> **andrew.46 said:**
> I guess a starting point is to check if your copy of mencoder has access to H.264 encoding with x264:
 
```

andrew@skamandros~$ **[COLOR=red]mencoder -ovc help[/COLOR]**
MEncoder SVN-r33648-4.5.3 (C) 2000-2011 MPlayer Team
 
Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
**[COLOR=red]  x264     - H.264 encoding[/COLOR]**

```
 
 
Oh, I have checked it. I forgot to mention it. Now, by the code I posted earlier, it can be seen that I'm using the lavc library.
 
How can I use the x264 library? Can you post an example or change my code?

---

### Post by andrew.46 on 2011-06-24
> **lewin said:**
> How can I use the x264 library? Can you post an example or change my code?

I admit that I usually use FFmpeg these days but perhaps something like the following will get you started:

```

mencoder -speed 2 mf://*.jpg -mf fps=24:type=jpeg -noskip \
  -of lavf -lavfopts format=mov \
**[COLOR="Red"]  -ovc x264 -x264encopts crf=22:b_adapt=2:direct=auto:me=umh:rc_lookahead=50:ref=5:subq=8 \[/COLOR]**
  -vf scale=1028:-2 \
  -o bud-steypustod.mov

```

The red section is the only piece I have altered. The x264 options are drawn from the 'slow' x264 preset and I have used crf instead of bitrate. I would be interested to hear how you go with this?

---

