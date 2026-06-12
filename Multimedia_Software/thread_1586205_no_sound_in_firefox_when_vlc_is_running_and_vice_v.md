---
title: "no sound in firefox when vlc is running and vice versa"
date: 2010-10-01
forum: Multimedia Software
---

### Post by trc on 2010-10-01
I am wondering if it has to do with the tinkering ive done to finally get my HDMI sound to work on my TV from ubuntu.  

Here is what I put in asound.conf  

pcm.default hdmi:NVidia 
pcm:iec958 hdmi:NVidia  

and this is what I put in modprobe.d/alsa-base.conf  

options snd-hda-intel enable_msi=0 probe_mask=0xffff,0xfff2 

Is there any problems that you can see from this?

Note: When I removed asound.conf I noticed that the sound worked fine in both again, but I won't be able to see if my HDMI still works until I get home.

---

