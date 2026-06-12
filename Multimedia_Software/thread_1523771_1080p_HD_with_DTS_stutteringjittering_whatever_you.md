---
title: "1080p HD with DTS stuttering/jittering whatever you call it"
date: 2010-07-04
forum: Multimedia Software
---

### Post by niru1978 on 2010-07-04
Hello All,

This forum has been a wonderful treasure of knowledge. thanks to all...

but now I am stuck up with something thats getting onto my nerves....

I have installed lucid and followed the perfect desktop guide.

I have a mkv file (4.6Gigs) 1080p HD with DTS 5.1 audio.

when I play the file either of the video or audio gets stuck (mostly video) I tried every possible configs from this forum but in vain.

Please help me and guide me what would be the best for playing 1080 HD videos.

Im using Dell LAT D830 with 2GB RAM 2.2GHz CPU NVIDIA Graphics.

thanks in advance

---

### Post by mouths on 2010-07-04
You'r lucky to have nvidia.

Go to synaptic and install the latest nvidia drivers (195).

Then install these libraries

_[http://img121.imageshack.us/img121/4597/screenshotymc.png](http://img121.imageshack.us/img121/4597/screenshotymc.png)_.

Install smplayer and go to   options>preferences>video  

and in the "output driver" put "vdpau"

For the latest about video acceleration go to

_[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)_
and
_[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)_

(Hope that your card supports vdpau)

---

### Post by niru1978 on 2010-07-04
hey buddy! thanks! it worked...!!!! I'm so glad I was having trouble with these fullHD movies even I was not able to play in windows...

so now I can wat full HD connected to my TV :D

thanks again for the help....

---

### Post by adowl2001 on 2013-01-15
Thanks a lot. That worked smooth. :)

---

### Post by howefield on 2013-01-15
Old thread closed.

---

