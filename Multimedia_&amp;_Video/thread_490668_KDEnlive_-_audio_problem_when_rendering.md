---
title: "KDEnlive - audio problem when rendering"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by Killtown on 2007-07-02
I tried to combine a couple of video clips using KDEnlive, but after I saved it, the audio was delayed starting with where the 2nd clip started.

Anyone else experience this?

I tried saving in all the various formats and they all had the same delayed audio problem at the 2nd clip except with Divx which actually rendered NO audio!



PS - what are the best formats to render/save your final video project in?

---

### Post by Killtown on 2007-07-04
Can someone with KDEnlive try this to replicate my audio problem? 

Import and combine 2 video clips with audio and render it.  See if the audio from where the 2nd clip starts gets delayed.

---

### Post by Killtown on 2007-07-22
Reporting the audio delay problem I was encountering was solved when following these instruction:

[http://doc.ubuntu-fr.org/applications/kdenlive](http://doc.ubuntu-fr.org/applications/kdenlive)

---

### Post by koer on 2007-09-26
erm.... link broken man or page no longer exists .... post the one that works plzz i have the same problem :confused:

---

### Post by Toadmund on 2007-11-03
Well, now I am having this problem as well, the sound of which I extracted from the video file, because I figured I could sync it if I could adjust it in time with the video, but seems the sound file is shorter in duration, so I shortened the video as I could not enlarge the audio, but still, the sound does not match the video.

In short, I separate, (divide and conquer) I match length's, I give one file a head start, and they still un-sync!

What to do, anyone figure this out?

---

### Post by agente100gelo on 2007-11-13
> **Killtown said:**
> Reporting the audio delay problem I was encountering was solved when following these instruction:

[http://doc.ubuntu-fr.org/applications/kdenlive](http://doc.ubuntu-fr.org/applications/kdenlive)

Correct link:
[http://doc.ubuntu-fr.org/kdenlive](http://doc.ubuntu-fr.org/kdenlive)

---

### Post by Toadmund on 2007-11-26
Unfortunately the link is in french, what particular part fixes the a/v sync problem?

---

### Post by Toadmund on 2007-11-26
Never mind, go to (Kdenlive) Settings->configure Kdenlive->default project->DV PAL for video format.

Everything is now in sync for me now!
Do this before you start your project, you may have to restart Kdenlive.

---

### Post by tregeagle on 2007-11-27
Yes it seems to default to ATSC 1080i 60Hz, which I have never heard of.
Changing it to DV PAL fixed up a whole heap of strange Video mixing and Audio errors for me.

---

