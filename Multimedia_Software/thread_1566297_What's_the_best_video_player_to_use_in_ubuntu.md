---
title: "What's the best video player to use in ubuntu?"
date: 2010-09-02
forum: Multimedia Software
---

### Post by UncleMonty on 2010-09-02
I'm having problems with VLC and totem.

---

### Post by cgroza on 2010-09-02
Mplayer and totem!

---

### Post by zeroseven0183 on 2010-09-02
Still depends on your preferences. I use the default, totem, but sometimes Banshee 

> **UncleMonty said:**
> I'm having problems with VLC and totem.

What seems to be the problem?

---

### Post by wojox on 2010-09-02
VLC rocks. You have the medibuntu repo's enabled and the non-free-codecs installed?

---

### Post by dv3500ea on 2010-09-02
VLC is the best video player on any platform IMO. What exactly are the problems you are having with it?

---

### Post by UncleMonty on 2010-09-02
> **dv3500ea said:**
> VLC is the best video player on any platform IMO. What exactly are the problems you are having with it?

It keeps sticking in the middle of movies. Plus if I pause and then press play it jumps back about ten seconds.

---

### Post by shankara on 2010-09-02
hi
Have you updated it fully? It is a must.

If you have easy internet connection and bandwidth, re install it. 

regards

---

### Post by UncleMonty on 2010-09-02
> **shankara said:**
> hi
Have you updated it fully? It is a must.

If you have easy internet connection and bandwidth, re install it. 

regards

A clean reinstallation might be the best solution- yep I have updated it but didn't seem to solve the problems that way :(

---

### Post by wojox on 2010-09-02
You have the medibuntu repo's enabled and the non-free-codecs installed?

---

### Post by UncleMonty on 2010-09-02
> **wojox said:**
> You have the medibuntu repo's enabled and the non-free-codecs installed?

Good question. Not sure if I do (I recently did a clean reinstall and not sure if I got around to that yet). Where can I get them please?

---

### Post by wojox on 2010-09-02
> **UncleMonty said:**
> Good question. Not sure if I do (I recently did a clean reinstall and not sure if I got around to that yet). Where can I get them please?

Open your terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install non-free-codecs
```

```
sudo apt-get install libdvdcss2 gxine libxine1-ffmpeg vlc mplayer mencoder 
```

---

### Post by UncleMonty on 2010-09-02
> **wojox said:**
> Open your terminal

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

```
sudo apt-get install non-free-codecs
```

```
sudo apt-get install libdvdcss2 gxine libxine1-ffmpeg vlc mplayer mencoder 
```

Thanks.

---

