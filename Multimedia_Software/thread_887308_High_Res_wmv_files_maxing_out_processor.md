---
title: "High Res wmv files maxing out processor"
date: 2008-08-12
forum: Multimedia Software
---

### Post by gyzer on 2008-08-12
Alright I'm having a problem with high res wmv's playing in totem. It seems that they always max my processor to 100%.

I am running a AMD Athlon XP 2700+ with 1GB of RAM on a Nvidia Geforce 6800GT.

I have very few services going on in the background, and I know awn can eat up a bunch, but even when I turn that off it still eats up 90% of my processor.

Is there something I can do setting wise in ubuntu, or is this just entirly a hardware problem?

I am running on the video drivers Ubuntu 8.04 loaded when I first set the system up. I've messed with the Linux Nvidia drivers in the past on other machines with very funky and inconsistant results, so I'm a bit affraid of trying those drivers on my own machine.

My idle is around 15% to 30%

Any help or sugestions would be welcomed!

---

### Post by gyzer on 2008-08-12
Can anyone help me out?

---

### Post by cor2y on 2008-08-12
Ok heres the bad news.
If its high def/high res its going to be cpu intensive and for you i would recommend a new cpu dual core.
Why doesn't this effect windows?
Because the graphic drivers take the burden off the cpu in windows not in with linux regardless of who the gpu maker is because they haven't been developed that far yet although ati is making more progress than nvidia, in linux with a powerful enough cpu you won't notice the strain, 2.6 ghz dual core will help.
If this is not to your liking you can always transcode to less cpu intensive video codec like say mpeg4 keep the resolution and quality but lower the video bitrate.
To do this try mencoder, ffmpeg, tovid, etc

Thats about the only solutions i can recommend theres nothing you can do other than those to lower the cpu usage that i know of.

---

### Post by gyzer on 2008-08-12
Thanks that helps alot. I had no idea that GPU's in Linux had next to no effect on video performance. Thats good to know.
 
I have transcoded some vids to a half their size and that definatly seems to help alot.
 
Thanks for the info!
 
I'm planing on building an xubuntu media center pc within the next 6 months, and that will be hooked up to a 32" Widescreen 1080i. So with that I'm going to need to go with a pretty sizable dual core, and I shouldn't care too much on the vid card (only get it for the connection types I'm needing)? Just a fast cpu and a good chunk of ram?

---

### Post by cor2y on 2008-08-12
Yeah thats all you need for video playback if the file is encoded with a cpu intensive codec or is hidef.
Although if its going to be of the level of 1080p video then a 2.8 or 3ghz cpu will be needed, dual core or better.
The video card can be your standard nvidia or ati (nothing top of the line aka super expensive) since the drivers for linux don't yet take advantage of the gpu for the latest cards that can ease hidef video playback.

---

### Post by gyzer on 2008-08-12
Thanks for your help.
 
I'm planing on using a Celeron E1400 Allendale 2.0GHz Dual Core with a bsel mod to get its FSB up to 1066 or even up to 1333 if I feel it will help.
 
Thanks again

---

