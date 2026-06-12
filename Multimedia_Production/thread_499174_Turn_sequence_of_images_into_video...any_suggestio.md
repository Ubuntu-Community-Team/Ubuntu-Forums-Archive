---
title: "Turn sequence of images into video...any suggestions??"
date: 2007-07-12
forum: Multimedia Production
---

### Post by squell on 2007-07-12
Hi everyone,

I've been searching for months and playing around with different programs (ffmpeg, imagemagick etc) but I have not yet found a suitable way to turn images (e.g. *.png) into a video format (e.g. .avi, mpeg etc).  I want the video format to be standard so that it'll work on standard Windows/Mac OS/Linux installations allowing me to use them on other peoples pc's/laptops for presentations.  I'm looking for good quality but nothing that will be too big (NB. there isn't any audio)

Any suggestions would be gratefully received :)

---

### Post by GMU_DodgyHodgy on 2007-07-12
> **squell said:**
> Hi everyone,

I've been searching for months and playing around with different programs (ffmpeg, imagemagick etc) but I have not yet found a suitable way to turn images (e.g. *.png) into a video format (e.g. .avi, mpeg etc).  I want the video format to be standard so that it'll work on standard Windows/Mac OS/Linux installations allowing me to use them on other peoples pc's/laptops for presentations.  I'm looking for good quality but nothing that will be too big (NB. there isn't any audio)

Any suggestions would be gratefully received :)

I started a thread on this a while back.  I wanted to take my photos and turn them into a movie to which I could add effects and music.

Here is what I ended up doing:

1.) I used digikam and created an mpeg video of my photos with titles and transitions.
2.) I imported this mpeg video into KDenlive. This is a great program to edit movies.  I added my musical score and exported into a final video that I was able to play on VLC and Windows Media Player.

Cheers

---

### Post by squell on 2007-07-12
Thanks for your reply, I'll give that a try later.  

I should have said: I want these images to string together to make an animation.  I'd want to set the frames per second and choose the resolution.

---

### Post by jurkki on 2007-07-12
> **squell said:**
> Thanks for your reply, I'll give that a try later.  

I should have said: I want these images to string together to make an animation.  I'd want to set the frames per second and choose the resolution.

```

mencoder mf://*.png -mf type=png:w=800:h=600:fps=1 -ovc lavc -lavcopts vcodec=mpeg4 -oac copy -o foo.avi

```

---

### Post by squell on 2007-07-12
That command seemed to work fine.  However, it won't load up in Windows media player (in XP) or Quicktime (within Mac OS X).  

I don't know if its possible but I am looking for something that will play on the default media players in Windows and Mac (without codecs being downloaded so I can play them on any PC I may come across for giving presentations at conferences etc...)

---

### Post by brettg102 on 2008-02-13
Sorry to bring a thread back from the dead but:
```
mencoder "mf://*.png" -mf type=png:fps=18 -ovc lavc -o output.avi
```

Should give you an uncompressed .avi that works on pretty much any media player, codecs or not. I needed to do this for making animation scripts for ANSYS on SuSe...worked on WMP no problem.

---

### Post by Creative2 on 2008-02-13
install digikam kipi-plugin

then  open digikam----tools----create a mpg from photo

or of course mencoder and ffmpeg 
for ffmpeg 
[http://ffmpeg.mplayerhq.hu/faq.html#SEC12](http://ffmpeg.mplayerhq.hu/faq.html#SEC12)

or more kino can do slideshow :)

---

### Post by bschleusner on 2008-02-13
personally, I use avidemux. It sounds to be exactly what you are looking for. Just open up a folder containing the pictures, select the first image, and it does the rest.

---

