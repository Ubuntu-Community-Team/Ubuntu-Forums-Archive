---
title: "Kino and audio management"
date: 2008-07-30
forum: Multimedia Software
---

### Post by p221072 on 2008-07-30
Hi,
I'm using Kino (still 1.1.0) to edit short videos and I'm quite happy with it and its semplicity, for my purposes I think it is more than enough.
Although what I find really poor is the audio dubbing/mixing system.
It forces me to use audacity for the mixing/trimming/editing of the audio before dubbing the clip.
Is there another video editor as easy and simple as kino with a better audio manager?
Is Cinelerra a good alternative?
Thanks,
Paolo

---

### Post by pwc on 2008-08-11
p221072, 

Hi, I'm new to Kino also and find it adequate for my simple editing of home videos. I've only edited one home video so far and it went ok, I just cut out the bad stuff. The thing I haven't figured out is why the final edited video is 3.1GB in size when the original unedited video was only 435 MB!
  Anyway I installed Avidemux with Synaptic and did the same video and had a easier time with it, whether it does more or less I don't know, but it seems less complicated. The final cut was a little smaller than original which makes since to me.
  Hope this helps.

---

### Post by timcredible on 2008-08-11
i find cinelarra difficult, avidemux is easier for what i do, but i don't think it supports too many formats.  i've started looking at openmovieeditor, but haven't done much with it yet, but since it uses ffmpeg, it should be able to do just about anything

---

### Post by mateuszbaranski on 2008-09-11
> **p221072 said:**
> Hi,
I'm using Kino (still 1.1.0) to edit short videos and I'm quite happy with it and its semplicity, 
(...)
Is Cinelerra a good alternative?
Thanks,
Paolo

Cinelerra is much more complicated, but has one very important feature (among others):
it could have more than one Video track, and more than one audio track. It's absolutelly essential feature for semi professional NLVE.

Clips do not have to be aligned - you could have gaps between clips. You could also use external effects (thru LADSPA) and much more.

If you don't wanna spend hours on learning cinelerra to do simple tasks - don't use cinelerra.

---

### Post by p221072 on 2008-09-11
Thank you mateuszbaranski,
past week I installed cinelerra and started using it!
It's true is a little complicated at first glance but it doesn't take too long to learn how it works and there are some decent resources online, check here: [http://cinelerra.org/docs.php](http://cinelerra.org/docs.php)
What I am not happy of is the way Cinelerra handles rendering. Cinelerra doesn't export audio and video together in mpeg2 dvd format. You have to do 2 separate exports and then manually render them using ffmpeg from command line.
Also I think that rendering 2 times degrades the quality of the video!

---

