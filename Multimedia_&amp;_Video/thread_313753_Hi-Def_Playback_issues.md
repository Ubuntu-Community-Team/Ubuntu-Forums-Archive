---
title: "Hi-Def Playback issues"
date: 2006-12-06
forum: Multimedia &amp; Video
---

### Post by Fatec on 2006-12-06
Hi,
   i was just wondering if anyone has problems playing back hi-def videos in ubuntu?

as they all play very jerky/slow for me, even worse with beryl on.

Also CPU usage jumps  from 2% to anywhere from 50-90% during playback, which of course is a major problem as it slows EVERYTHING down. 

Dont matter what media player i use.

Is this a codec problem? as the files play fine in windows.

My specs are :

AMD64 3200+ (2.01ghz)
2GB PC3700 DDR400
Geforce 7600GT (256mb PCI-Express)
120Gig Sata Drive (main)

etc.

Can someone please help?

have everything else working great, just not video playback.

P.S Sorry if this is in the wrong place.

---

### Post by Fatec on 2006-12-06
anyone?

i know replying to my own thread may seem a little impatient but im desperate to get this problem sorted otherwise im gonna have to go back to XP :(

---

### Post by drphilngood on 2006-12-06
Enter the following in a terminal and post the results:
```
glxinfo | grep render
```

---

### Post by Fatec on 2006-12-06
> **drphilngood said:**
> Enter the following in a terminal and post the results:
```
glxinfo | grep render
```

> direct rendering: Yes
OpenGL renderer string: GeForce 7600 GT/PCI/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 

Thats it..

---

### Post by MetalMusicAddict on 2006-12-06
I playback the hi-def version of "Elephants Dream" just fine on my 7900GT.

---

### Post by Fatec on 2006-12-06
> **MetalMusicAddict said:**
> I playback the hi-def version of "Elephants Dream" just fine on my 7900GT.

that's nice...but that dont help me, does it?

as i said...playback in fine in windows...and even when its not usin the cards gpu for playback cpu usage is only around 30-40%

---

