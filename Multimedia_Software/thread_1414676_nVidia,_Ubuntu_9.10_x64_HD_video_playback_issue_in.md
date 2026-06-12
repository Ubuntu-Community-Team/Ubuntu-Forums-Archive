---
title: "nVidia, Ubuntu 9.10 x64 HD video playback issue in Totem"
date: 2010-02-23
forum: Multimedia Software
---

### Post by phuc_head on 2010-02-23
I have an issue with HD 720p video, full sized movies (they run about 4.4GB).  Playback in "Movie Player" (totem) is very choppy.  i close down totem and open the same video in VLC and it works great, videos are typically spec'd like so 1280x534 using H.264/AVC video 30 frames per second with MPEG-4 AAC audio stereo (of sometimes 5.1) They play(ed) perfect on this same hardware running WUBI install of Ubuntu 9.04, Vista, and Win7 all OSes are x64.  Just this latest version is when everything stopped working smoothly, Also, I watch some 720p 22min and 42min videos and they all seem to be fine in totem, just seems like it is the full length 1:30+ videos that do it.  

Laptop specs are pretty stellar 6gb (ddr3) memory, intel centrino 2  intel core 2 duo P8600 @ 2.40GHz with nVidia GeForce 9600M GT running at 1680x1050 pixels (17" widescreen display).  

I would just use VLC, but the fact that gnome-screensaver broke the screensaver suspend poke that VLC was using to stop the screensaver, makes it a pain in the posterior.  I might just have to buy a wireless mouse to move every 10-15 mins so the screen does not blank.  

I know this same machine was playing IN LINUX in a WUBI install of 9.04 720p videos, is there something that i should be tweaking? I do have Compiz turned off, but i had it running in the 9.04 instance no issues.  Any help would be good.

Would the Fluendo codecs help with this issue? don't really want to spend the money on something that won't fix the issue, but if i get a solid yes, it should i will concider it.


Thanks for the info.
-phuc

---

### Post by Yellow Pasque on 2010-02-24
> Would the Fluendo codecs help with this issue?
No.

You'll get better results from totem if you can find a PPA containing gstreamer built with libvdpau enabled. This shouldn;t be a problem in Ubuntu 10.04, but it is in Karmic.

---

### Post by phuc_head on 2010-02-28
awesome, i am looking into this now... one other thing that i did notice, kind of a stupid interaction, but IF i put the volume over 100% (by right clicking on the speaker tray icon going to properties and moving the slider to greater then 100% it seems like the skipping and tearing and what not is almost a guaranty. I have got mostly perfect playback on one video at 100% volume, and studdering ever couple of minutes when it was at 150% volume.

sound is a
HDA Intel
Nvidia MCP HDMI
(from alsamixer)

i don't know if that would actually be the cause or if it is more of a coincidence, but wanted to add it.
-phuc

---

### Post by phuc_head on 2010-02-28
wow, ok that seems to have fixed the issue already, the libvdpau gstreamer.  i played a very high quality video i was having some issues with and played it with both the sound at 100% (it was fine) and also at 150% and still was fine.  I thank you Temüjin you have helped me more then words could normally say.
-phuc

---

### Post by Laxman_prodigy on 2010-03-10
From where can I install it? What is the name of this package?

---

