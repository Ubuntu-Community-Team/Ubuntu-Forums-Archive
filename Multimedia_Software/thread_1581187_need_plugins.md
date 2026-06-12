---
title: "need plugins"
date: 2010-09-24
forum: Multimedia Software
---

### Post by bill23 on 2010-09-24
[SIZE=3][COLOR=Navy]When I try and play a DVD, I am told I need some plugins for Totem in order for the movie player to play the DVD's. I hope there is someone who can tell me where I can get these plugins. I also seem to have some kind of conflict with totem. I tried installing some extra totem plugins for totem and there was a conflict so the installation could not go forward. Right now I am concentrating on where can I get the proper plugins so I can watch some DVD's.
bill23
[/COLOR][/SIZE]

---

### Post by lkjoel on 2010-09-24
> **bill23 said:**
> [SIZE=3][COLOR=Navy]When I try and play a DVD, I am told I need some plugins for Totem in order for the movie player to play the DVD's. I hope there is someone who can tell me where I can get these plugins. I also seem to have some kind of conflict with totem. I tried installing some extra totem plugins for totem and there was a conflict so the installation could not go forward. Right now I am concentrating on where can I get the proper plugins so I can watch some DVD's.
bill23
[/COLOR][/SIZE]
Try:
```
sudo apt-get install gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```

---

### Post by Rasa1111 on 2010-09-24
See here~ [http://ubuntuforums.org/showthread.php?t=1573805](http://ubuntuforums.org/showthread.php?t=1573805)

It seems we got them going, 
Should be able to get you going... 

> Sandy (member here) said that one needs medibuntu repos, and also you need 
libdvdcss2. (she knows what shes talkin'bout) lol

Quote:
libdvdcss2 is in mediubuntu. just adding medibuntu will not install libdvdcss2.and nor will it install win32codecs (or is w32codecs?
Quote:
youll need it if your playing encrypted dvds.

 So, I think you need to add medibuntu to your repositories, 
then install **libdvdcss2** from synaptic package manager.

---

### Post by Rasa1111 on 2010-09-24
double post.
Sorry. 
gahhh

---

