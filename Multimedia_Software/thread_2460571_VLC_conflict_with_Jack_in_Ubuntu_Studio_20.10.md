---
title: "VLC conflict with Jack in Ubuntu Studio 20.10"
date: 2021-04-13
forum: Multimedia Software
---

### Post by eloctogono on 2021-04-13
Hi!

I'm using Ubuntu Studio 20.10 since its release. I'm quite happy with it. However I'm experiencing issues with VLC as default video player. Whenever I have Jack working, if I play a video for the first time, VLC works fine but, if I try to open another video it stays blank. It only happens when Jack is on. If I'm with ALSA only it works as expected. I searched online if someone had the same issue but found nothing. I'm currently using Celluloid as an alternative. Any clues?

Thanks!

---

### Post by Xian on 2021-04-13
In VLC go to Tools[COLOR=#242729][FONT=Arial] &#8594; [/FONT][/COLOR]Preferences[COLOR=#242729][FONT=Arial] &#8594; [/FONT][/COLOR]Video[COLOR=#242729][FONT=Arial] and set the output to OpenGL or X11 --- or something else other than automatic. 


[/FONT][/COLOR]

---

### Post by eloctogono on 2021-04-14
THanks @xian that did the trick!  I somehow related the issue with Jack but probably was just because I record audio and video with OBS while using Jack...

---

