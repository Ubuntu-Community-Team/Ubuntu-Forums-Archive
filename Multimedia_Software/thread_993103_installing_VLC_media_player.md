---
title: "installing VLC media player?"
date: 2008-11-25
forum: Multimedia Software
---

### Post by mahela007 on 2008-11-25
Can someone tell me how to install the VLC media player on ubuntu 8.10? the web site says that I should enable multiverse in the repos.  I have it enabled but it VLC doesn't show up. What do to?

---

### Post by Jorge_C on 2008-11-25
If you have multiverse enabled, vlc will show up in synaptic. To intall it, just paste this in a terminal:
```
sudo apt-get install vlc
```

---

### Post by mahela007 on 2008-11-25
no nothing appears in synaptic. I tried searching for more popular programs like blender ut still nothing shows up. I think the search feature is broken because when I look for them manually they are all there

---

### Post by Jorge_C on 2008-11-25
The command I gave you will install vlc, and it will show up under applications->Sound and video
Did you try it? Did it gave any errors?

Regarding searching apps in synaptic, I don't know why it isn't working for you.

---

### Post by Daisuke_Aramaki on 2008-11-25
> **mahela007 said:**
> no nothing appears in synaptic. I tried searching for more popular programs like blender ut still nothing shows up. I think the search feature is broken because when I look for them manually they are all there

then u shud check the sources.list again to see if u added the repositories properly! after u had enabled the repos, did u update ur sources.list? say by 

```
sudo apt-get update
```

---

### Post by zarap on 2008-11-25
You will have to enable the Medibuntu Repository also for some multimedia stuff you will want to have (libdvdcss to play video-dvd's and much more...)
- they have a good tutorial for adding the repo on their website
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

