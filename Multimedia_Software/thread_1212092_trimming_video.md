---
title: "trimming video?"
date: 2009-07-13
forum: Multimedia Software
---

### Post by tommah04 on 2009-07-13
is there anyway I could trim a section of a video?
 
I want to keep the entire length of the video, but just save a certain portion of it
is there any way to do that?
 
I thought maybe cinelerra, but I've found out it doesn't work on my computer (constant crash)
 
so any help with suggested apps would be awesome
 
thanks in advance

---

### Post by catechu on 2009-07-13
Have you tried Kino ([http://www.kinodv.org/)?](http://www.kinodv.org/)?)

It works with DV files, but you should be able to convert with standard formats using something like this: [http://www.singingwizard.org/wiki/index.php?title=Programming](http://www.singingwizard.org/wiki/index.php?title=Programming).

---

### Post by tommah04 on 2009-07-13
I had kino, but it didn't support most file types so I didn't look into it very much and just uninstalled it.
 
if you know for sure It's what I'm looking for I'll get it (or if anyone can confirm it).  but its just a pain to keep converting.  obviously I will if I have to

---

### Post by DaGrimReefah on 2009-07-13
Cinelerra and KdenLive are 2 good Linux editors I've used.

---

### Post by tommah04 on 2009-07-13
yea, I have kdenlive and its awesome, but I'm not sure if its able to actually trim the video.... at least I can't find out how

---

### Post by vinutux on 2009-07-13
Avidemux do that...................100 % sure

```
sudo apt-get install avidemux
```

.

---

### Post by tommah04 on 2009-07-13
I always get a "trouble initializing audio device" error when I open a video.... is that a problem with the format of the video?

---

### Post by tommah04 on 2009-07-13
I can't figuring out how to trim the size of the video in avidemux... only cutting out entire areas of the video.

---

### Post by vinutux on 2009-07-13
> **tommah04 said:**
> I always get a "trouble initializing audio device" error when I open a video.... is that a problem with the format of the video?

Yeh its probably problem related to video format ...i am xperienced with some flvs and mp4

> **tommah04 said:**
> I can't figuring out how to trim the size of the video in avidemux... only cutting out entire areas of the video.

simple in video menu->Filters->Crop (Double click)

..:lolflag:

---

### Post by tommah04 on 2009-07-13
oh, I had to switch to output.... I'd choose crop and crop it and everything, but in the video it wasn't showing cropped......its cause it was playing the "input" file.....

awesome, thanks alot, that was exactly what I needed

---

### Post by xc3RnbFO8P on 2009-07-14
> **tommah04 said:**
> I always get a "trouble initializing audio device" error when I open a video.... is that a problem with the format of the video?

Preferences> Audio> change to Pulse Audio

---

### Post by tommah04 on 2009-07-16
thanks!

---

