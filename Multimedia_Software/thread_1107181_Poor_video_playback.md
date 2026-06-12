---
title: "Poor video playback"
date: 2009-03-26
forum: Multimedia Software
---

### Post by c-m on 2009-03-26
I have Ubuntu UMPC 8.10 installed on my netbook.

I installed all of the necessary files to play restricted formats, through medibuntu. 

The problem i am having though is that when playing back dvds or divx, or flash videos, I am getting tears, jerky panning and generally poor playback or pausing.

Obviously the netbook is more than powerful enough to play back these items, hell some people even playback 720p content.

I just want to play normal video files.

Can anyone help?

The problem is the same in VLC and Mplayer

---

### Post by c-m on 2009-03-30
anyone with any suggestions at all?

Format and try again? Diffrernt distribution

---

### Post by aeiah on 2009-03-30
which netbook? is this with compiz on? how much ram is being used by the onboard graphics card? have you tried changing the video output to something else? (the -vo flag in mplayer does this i believe)

---

### Post by c-m on 2009-04-03
Its an Acer Aspire One 512Mb (tried 1.5gb), all desktop effects are turned off.

It is much worse when outputted to an external monitor too.

I have tired XV and X11 output modes

---

### Post by hermanhobnob on 2009-04-11
I've also just ran into this problem. It seems to skip when doing disk reads. I just tried OpenGL output from VLC. This seemed smoother but pixelated.

That's about as far as I got in 5 minutes but it might be good enough for the moment. Hope this helps.

---

### Post by yipidee on 2009-07-07
I realise this is a very old thread, but this problem was driving me insane. I tried every fix and work around I came across to no avail. In the end though it was a very simple thing in my case. I simply downloaded the proprietary video drivers, restarted and it was all fine.

The opensource drivers I was using worked fine for everything bar video playback in VLC. Had I not finally got that sorted I might have given up on Ubuntu.

Hopes this works for others too. There's very little useful info on this topic.

---

### Post by yipidee on 2009-07-07
Guess some technical info would be useful:

Running Intrepid on a HP Pavilion Notebook, ATI Radeon Xpress 200M video card.
VLC video playback by X11 in preferences.
Video playback is disabled in Compiz, though I haven't tried turning it back on since driver install

---

