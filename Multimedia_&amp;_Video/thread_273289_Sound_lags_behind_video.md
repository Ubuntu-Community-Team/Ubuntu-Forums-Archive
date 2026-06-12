---
title: "Sound lags behind video"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by SC2Sick on 2006-10-07
On the install of ubuntu on my new box i have an issue where the sound will lag about a second consistently behind the video.

I've tried both totem and mplayer


it's an AMD Athlon 64 3000+ using 6.06LTS 32bit version

i'm using the k-7 kernel and i recompiled the sound stuff after upgrading kernels.

my laptop is a Sempron (64bit also) 3000+ same kernel, same apps and has absolutely no problems whatsoever.

please assist or let me know what other information you need.

---

### Post by JayTee on 2006-10-08
I'm having the same problem with sound delay on my system. I'm running 6.06 Dapper with the i686 kernel. My system is a Pentium D 940. When I watch a video in Movie Player the delay doesn't seem as long as when I watch a DVD I've burned using DeVeDe. Hope someone out there has some ideas as to what might cause this.

Edit: I've noticed that Totem movie player plays the movie without audio delay but when I play it in mplayer it has the delay. DeVeDe uses mplayer for previewing and uses mencoder as well. Someone suggested in another thread choosing OSS or ESD as sound output but discs I've burned that way have no audio when played on my DVD player. I've tried tweaking the audio delay but it's a royal pain in the @$$ as it's never dead on. I think I'll probably go back to using my Windoze box with Nero to burn DVDs from AVI files and stop ](*,) with multimedia authoring on Ubuntu until someone fixes some of these bugs or I can find a program that will do what DeVeDe or Qdvdauthor does without bugs, audio delay etc. If Totem-xine can play the movies fine I'm wondering if there is an authoring tool that uses those libs instead of the gstreamer ones with ALSA which is where the bug seems to be.

---

### Post by turbotuba on 2006-10-22
bump...](*,) me too.

---

### Post by Se7h on 2007-11-17
I'm unhappy to see that I'm not the only one with this issue.
I've notice the gap between video and sound sync since I updated to gutsy.

Any help from an expert fr this problem would be greatly appreciated in the community :KS

If no expert's around, a hint to how to solve this would be just great... Point your fingers ubuntuers...

Pleaaaseeee ?! [-o<

---

### Post by wladyx on 2008-01-27
I'm also experiencing this in smplayer&mplayer...

---

### Post by rvm4000 on 2008-01-28
Have you tried another audio driver? (**-ao alsa** or **-ao oss**)

If the problem happens only with one video... maybe that video is wrong?

---

### Post by tanas on 2008-03-10
Same thing here.. even in youtube (which makes me wonder if it really is a Linux thing... but as someone said, I can't remember of this happening before Hardy)

---

