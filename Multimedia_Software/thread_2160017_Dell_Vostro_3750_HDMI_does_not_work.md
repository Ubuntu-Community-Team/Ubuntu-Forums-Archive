---
title: "Dell Vostro 3750 HDMI does not work"
date: 2013-07-05
forum: Multimedia Software
---

### Post by jendass on 2013-07-05
Good afternoon,

I am running ubuntu 13.04 on my Dell Vostro 3750 notebook with optimus technology (Intell integrated card, Nvidia GeForce GT 525M card). 

Everything is running quite smooth except the HDMI port. When I plug my monitor into the HDMI port, it is not detected at all. VGA works just fine, but the picture is a bit fuzy due to ground loop as I have read. 
I have installed Bumblebee but that did not helped. 
Please does anyone know, how to make it work properly? And by properly, I do not want to run two different session on each monitor, that would not help me... :-(

Thank you for your time. If any further info needed, just write a post and I will provide it.

---

### Post by jendass on 2013-07-10
Just informing, that I have not solved this issue yet and any information concerning this topic is highly welcomed!

---

### Post by DeathByDenim on 2013-07-10
I'm afraid that HDMI with Optimus simply isn't supported in Linux at the moment. The only known workaround is the one with two different sessions that you mentioned...

---

### Post by jendass on 2013-07-10
That is really inconvenient... Why it has to be sooo difficult to get it working? I understand, that Optimus is a bit complicated peace of machinery but still, it works pretty smooth on windows and since the Steam for linux came out and nvidia started to support graphics also on linux, I thought that it would be possible very soon to use my Graph. card properly.

---

### Post by DeathByDenim on 2013-07-10
Yeah, I agree. It's because the main focus for NVidia is Windows development. It wasn't even possible to use the Optimus technology at all, until some people started the Bumblebee project. That was done without the help of NVidia as far as I know. I'm very glad they managed to make 3D acceleration possible at least.

Some more info about the HDMI issue from the Bumblebee wiki ( [https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup](https://github.com/Bumblebee-Project/Bumblebee/wiki/Multi-monitor-setup) ):
> Optimus laptops have two video chips: an integrated Intel and a discrete nVidia one. If the port (DisplayPort / HDMI / VGA) is wired to the Intel chip, you do not need to do anything special to get external monitors to work.

When the port is wired into the nvidia chip, you cannot currently expand the screen over monitors. The monitor may still be used as extra screen (with no desktop running on it) or to run the full desktop on it (with no output on the Intel LVDS output, a.k.a. "the laptop display").

---

