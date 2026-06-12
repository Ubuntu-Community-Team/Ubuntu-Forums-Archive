---
title: "Sound got lost &amp; found"
date: 2007-05-15
forum: Multimedia &amp; Video
---

### Post by rax_m on 2007-05-15
Hi 

I was tinkering today and managed to lose my sound.. but luckily I managed to get it back again. Just thought I write a little about what happenned and how I fixed it in case it helps someone. 


Basically I had a working installation of the Linuxant Soft modem driver (commercial). When I upgraded to the newer kernel it stopped working. I tried uninstalling the old driver and installing the version for my current kernel. Unfortunately this failed, but also managed to remove the drivers and my sound card from being recognised. 

Basically, edgy thought that I didn't have any sound cards. 

To fix this, I re-installed the Alsa drivers I previously had installed (from source). And voila it was all working again. 

I'm still a bit concerned that something as unrelated as my modem driver should mess up the sound.. but at least it wasn't a huge problem. 

Rax

---

