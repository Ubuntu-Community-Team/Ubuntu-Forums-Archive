---
title: "Can't watch .mkv/ffmpeg h.264"
date: 2010-12-28
forum: Multimedia Software
---

### Post by DarkovicDK on 2010-12-28
Hey everyone, this is my first post!

My problem seems to be unsolved, from my "research". I simply can't watch 1080p movies that got ffmpeg and x264 coded into them. The sound is clear and good, but the picture is terrible. The colors are making some kind of rails behind them, and after 3-5 sec the picture stops and the sound keeps on going. I can't find a solution for this, but in windows it will run smooth. The same file.
I'm running ubuntu 10.10 and the newest version of VLC.
My specs are pretty low, but windows can so: Hd 5570 1gb, AMD athlon II 1,9 GHz (160i or 190i I mean it's called) and 4 gb ram.
Can someone help me?

---

### Post by endotherm on 2010-12-28
well, I've never liked vlc, so I would try smplayer, but keep in mind your hardware will in part determine whether you will be able to get it going to your satisfaction. the attachment you have provided shows perfectly why i don't like vlc. it will play anything, but not well. 

so for codecs, have you installed the mediubuntu repositories with the w32codecs (or w64 for AMD64 systems) and the ubuntu-restricted-extras package? if so, try totem and smplayer to see if you get better results. there are several PPAs for smplayer that are much more up to date than the repository version.

---

### Post by DarkovicDK on 2010-12-28
I'm using ubuntu-restricted-extras package, but smplayer doesn't do anyhing to the colors and keep them nice, but either it stops or lags. Got anything else that could help?

---

### Post by endotherm on 2010-12-28
I notice your vid card is far superior to your cpu (which i would not expect to support 1080p under any OS), so it will probably have a big impact to offload the vid processing to the card. in smplayer you can select the vid "driver" used. I would select one for ATI cards that supports hardware acceleration (I forget the exact name).

also did you install the w32/64 codecs from mediubuntu? They are not included in the restricted extras (just the gstreamer codecs for totem).

---

### Post by laceration on 2010-12-28
Don't expect that because Windows can do it, that it can be done in Linux.  The Linux drivers are making great strides but are only playing catch up to the Windows drivers.  I haven't been following this too closely lately, but far as I know, Ati is even lagging behind Nvidia.  The whole thrust of this driver development is to take the burden off of the cpu for video processing by utilizing the gpu.  That could be optimized in Windows while in Linux is still working to a greater off your cpu, which is pretty weak to play a 1080p mkv.  [www.phoronix.com](www.phoronix.com) is a good source for info on these developments.

---

### Post by no2498 on 2010-12-29
this helps a lot of people with the color thing
open totem set the hue all the way to the left
if it helped reset to default

---

### Post by no2498 on 2010-12-30
also install smplayer it loads some more codes winff dont
type it in a terminal it tells you how to install it

---

