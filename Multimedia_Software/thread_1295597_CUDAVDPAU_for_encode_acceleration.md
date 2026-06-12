---
title: "CUDA?VDPAU for encode acceleration"
date: 2009-10-19
forum: Multimedia Software
---

### Post by ghat on 2009-10-19
hi guys, 
I have a 9500GT card in my jaunty box. 
I cant use VDPAU as I have a dual monitor setup, where I use a wide-screen in landscape mode and a  4:3 screen in portrait mode(rotated) using Xinerma. 

Granted, I am not using much of the nvidia tech... here but I am living with that... 

I however wanted to see if I could still leverage the GPU to accelerate encoding. The box also serves as a media server for me, and also have a tuner and myth-backend on it. 

If I could leverage the GPU to do encodes, then it will get me the real value for money I invested in.... 

I also transcode movies to better format/s resolutions.... and use it with my avchd video cam... GPU encoding will be of great help...

any comments or links to other places which can point me in the right direction ?

---

### Post by Maybelline on 2009-12-27
I'd love to be proven wrong here, but AFAIK there is no Linux app that can leverage the power of the GPU to do any ENcoding.  VDPAU is only for DEcoding.

Please, someone, prove me wrong!

---

### Post by ionic77 on 2009-12-28
> **Maybelline said:**
> I'd love to be proven wrong here, but AFAIK there is no Linux app that can leverage the power of the GPU to do any ENcoding.  VDPAU is only for DEcoding.

Please, someone, prove me wrong!

FFMPEG has vdpau. Say you are transcoding from mpeg-2 to something else. You should see a net gain in performance because vdpau will help at least on the input side.  Google "trancode vdpau" for more info

---

### Post by 11g on 2010-01-08
/deleted/

---

