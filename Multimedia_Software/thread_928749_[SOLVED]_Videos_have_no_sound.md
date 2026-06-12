---
title: "[SOLVED] Videos have no sound"
date: 2008-09-24
forum: Multimedia Software
---

### Post by GeorgeMurango on 2008-09-24
For some reason my videos have stopped playing sound. Video is laggy in mplayer, while in vlc it works just fine, but neither makes any sound. However, my mp3s all play, as do flash videos online. Can anyone help me figure this out?

---

### Post by kshmya on 2008-09-24
Hello there

Need help to watch online streaming under ubuntu
HI I am new to Ubuntu and I must say its owesome I love this so much I cant express. I need one help from you guys i am trying to watch online TV show but I am keep getting errors like media player dont support needs plugin . I tried lot but no luck . Can any one pls. help me what kind universal player i need and how to install the same under ubuntu

---

### Post by GeorgeMurango on 2008-09-25
> **kshmya said:**
> Hello there

Need help to watch online streaming under ubuntu
HI I am new to Ubuntu and I must say its owesome I love this so much I cant express. I need one help from you guys i am trying to watch online TV show but I am keep getting errors like media player dont support needs plugin . I tried lot but no luck . Can any one pls. help me what kind universal player i need and how to install the same under ubuntu

You need to install the mplayer plugin and the nonfree flash plugin. They are in the repos. Just go to synaptic and search flashplugin-nonfree and mplayer plugin. You should find them.

As for my problem, Reinstalling the gstreamer engines and a quick restart fixed it.

---

