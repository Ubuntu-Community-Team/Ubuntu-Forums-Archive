---
title: "strange sound problems when playing movies"
date: 2010-07-21
forum: Multimedia Software
---

### Post by igeorgiev on 2010-07-21
Hello,

I have a very strange problem with Ubuntu when playing movies which I want to share with you in hope someone can give me help or ideas how to resolve it.

I am using Ubuntu 10.04 desktop edition with Gnome. My sound is perfect, I have no problem playing .mp3, .ogg, or any other audio format. I have sound also in the Ubuntu desktop effects.

What bugs me is that when I try to play some movies - e.g. an avi file (SomeName.2002.720p.BRRIP.XviD.AC3-ViSiON.avi), I have no sound when people talk, but have perfectly good sound for the other movie sounds like cars stopping, etc. Only the speech is muted...This occurs both in Totem Movie Player and VLC. And not only in .avi, but sometimes in other video formats, too (the strangest part is that it works for some of them, so the speech is muted on case by case basis). 

I have installed all the required win32 codecs from the medibuntu repository (actually, I have installed all non-free packages from there). Someone having the same problem? Maybe the video encoding uses a special codec which is problematic at my machine?

Thanks in advance.

---

### Post by Fracta on 2010-11-10
I had the same problem. I fixed it by going into sound preferences, hardware tab, selecting audio source (in my case Internal Audio), and then choosing Analog Stereo Output from just below in the Profile drop down box.
I had forgotten that I had set it to 5.1 for my headphones.

---

