---
title: "Problem: PCM volume has no effect on sound"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by manu_g on 2007-03-14
Hi all,

I've recently installed ubuntu 6.10 on a vmware machine. My problem is that  pcm volume has no effect on sound. 

I tried running xmms, there is no effect if I change volume from within the application or if I change pcm volume using gnome-volume-control or alsamixer. If I change master volume , only then volume changes.

I also tried setting "select device and track to control" to pcm, it also has no effect.

Can anyone please suggest how to fix this problem.

Thanks
manu

---

### Post by ssavelan on 2007-03-16
I suppose that the sounds in question are running in OSS, ESD or another <mechanism?> than PCM.

---

