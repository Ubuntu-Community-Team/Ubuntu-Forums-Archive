---
title: "Video editor?"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by frogfusious on 2006-12-02
First off: I really like Linux and use it as my main operating system; Windows crashes too much and I don't have the money at the moment to afford a Mac. My only complaint it: no video editing software.
Yes, I do a bit of video editing. All I need is a non linear editor that has a video track and an audio track. I just need to split up clips and put audio over it; no compositing or special effects needed. I'm really convinced there is no way to do this on Linux.
Kino claims to be 'non-linear' but only supports one video track and <i>no</i> audio tracks.
Avidemux is only useful for adding really basic effects and maybe making clips shorter. 
Blender crashes everytime it tries to play audio.
Cinelerra has a buggy/ugly interface, is slow and won't load AVI files for whatever reason.
LIVES takes six minutes to load, opens its ugly/buggy interface and then crashes 10 seconds later.
Diva doesn't work.
Kdenlive runs(after spending an hour fulfilling dependencies and compiling) but crashes every time I try to load a clip.
PiTiVI will work on Ubuntu with the --sync command, but essentially serves no purpose(all it can do is place video files in a timeline; you can't split them up or add another track).

You get the point. I've search around endlessly and can't find a video editor that has even the features of Windows Movie Maker...It is really a let-down. I really don't want to dual-boot Windows just to do simple editing. Surely there has to be something out there that is good?

---

### Post by beameup on 2006-12-02
There is MainConcepts MainActor. I haven't tried it myself and it's a US $199 commercial app; which won't be an issue if it works. You can dowload a fully functional demo version.

[http://www.mainconcept.com/site/index.php?id=395](http://www.mainconcept.com/site/index.php?id=395)

A review here
[http://www.dvformat.com/articles/viewarticle.jsp?id=32719](http://www.dvformat.com/articles/viewarticle.jsp?id=32719)

---

### Post by frogfusious on 2006-12-02
I've tried it and...it crashes a *lot*. Segmentation faults? might be able to fix it except it is proprietary and not free/open source.

---

### Post by beameup on 2006-12-05
Well on the bright side, demand is increasing, and with the up and coming apps that are out there, it can only get better.

---

### Post by ddennedy on 2006-12-07
If you just need something basic, are you sure you need a multitrack timeline UI? In Kino, you can export the audio, bring it into Audacity or similar, do do a mixdown, and then import the audio into Kino using FX->Audio->Dub. Or, for really simple stuff, just stick to Kino FX/Audio Transition/Cross Fade and Mix for music beds.

---

### Post by cdragut on 2006-12-07
> **frogfusious said:**
> First off: I really like Linux and use it as my main operating system; Windows crashes too much and I don't have the money at the moment to afford a Mac. My only complaint it: no video editing software.
Yes, I do a bit of video editing. All I need is a non linear editor that has a video track and an audio track. I just need to split up clips and put audio over it; no compositing or special effects needed. I'm really convinced there is no way to do this on Linux.
Kino claims to be 'non-linear' but only supports one video track and <i>no</i> audio tracks.
Avidemux is only useful for adding really basic effects and maybe making clips shorter. 
Blender crashes everytime it tries to play audio.
Cinelerra has a buggy/ugly interface, is slow and won't load AVI files for whatever reason.
LIVES takes six minutes to load, opens its ugly/buggy interface and then crashes 10 seconds later.
Diva doesn't work.
Kdenlive runs(after spending an hour fulfilling dependencies and compiling) but crashes every time I try to load a clip.
PiTiVI will work on Ubuntu with the --sync command, but essentially serves no purpose(all it can do is place video files in a timeline; you can't split them up or add another track).

You get the point. I've search around endlessly and can't find a video editor that has even the features of Windows Movie Maker...It is really a let-down. I really don't want to dual-boot Windows just to do simple editing. Surely there has to be something out there that is good?
What about cinelerra ?

---

### Post by fsman on 2006-12-08
get cvs version of cinelerra
add this to your repos (works in edgy too)
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./

AVI (mpeg4/xvid/dvix) don't edit very well. Probably best to use avidemux to covert to a better format. 

good site with guides is [http://cvs.cinelerra.org/](http://cvs.cinelerra.org/)

---

### Post by komputes on 2007-10-12
Do you know if Cinerella can process HD video (1080i or 1080p).

---

