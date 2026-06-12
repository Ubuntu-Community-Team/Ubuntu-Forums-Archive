---
title: "Problem running HD videos"
date: 2010-09-02
forum: Multimedia Software
---

### Post by dragao-azul on 2010-09-02
Hey,

I have an Acer Revo R3600 (dual core atom, ion graphics and 4gb ram) and I can't play HD videos on ubuntu...

In windows I can play 720p movies absolutely fine (1080p ones have breaks) but I can't get any of them to play decently on ubuntu.

I have the nvidia drivers from their site installed and I'm opening the movies with vlc.

Is it possible to have the same performance in ubuntu as in windows? How?

Thz

---

### Post by cchhrriiss121212 on 2010-09-02
Install smplayer and choose vdpau output in video preferences.

---

### Post by tripmix on 2010-09-02
What he said. XBMC also has vdpau support, vdpau is really the key to playing HD in linux with nvidia. If you can almost play 1080p in windows with vlc I'm pretty sure 1080p will run smooth in linux with a fast vdpau compliant player, vlc is notorious for being very slow. I find vlc is more of a last resort option, if thats what your using in windows as well you should check out media player classic.

---

### Post by dragao-azul on 2010-09-02
In windows I have WMP (with codecs) and media player classic, both work with 720p and not with 1080p.

In linux I just tried mplayer (with gui) and although it is better that vlc it is still a little bit jumpy, I get something like half the frames per second :S

---

### Post by tripmix on 2010-09-02
Are you sure your using vdpau? Not sure how to use it in mplayer as I usually just use XBMC at the moment. There it's pretty straight forward just "settings > video > use vdpau for playback". If you'd like to try it these are the repos for ubuntu and the package is xbmc ```
deb http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main universe multiverse
deb-src http://ppa.launchpad.net/team-xbmc/ppa/ubuntu lucid main universe multiverse
```

---

### Post by dragao-azul on 2010-09-02
XBMC is perfect! It even runs 1080p movies! :D

I'm just having a little problem: I get some vertical lines in the middle of the screen when the scenes change rapidly, can I correct this?

And one more (unrelated) thing: I think the linux kernel was updated because grub has 2 ubuntu options now, is it safe to remove the old one?
(I just have to remove the linux-image-... packages that are older than my version, right?)

Thz

---

### Post by dragao-azul on 2010-09-02
I meant horizontal lines, sorry. They only seam to appear on the lower half of the screen

---

