---
title: "Sound Card Not Working"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by amyfan on 2007-09-04
HDA-intel - HDA ATI SB      
HDA ATI SB 0xc0000000 irq 18    is my sound card i tried evrything i done a full install of ubuntu anyone have any idea how or why i cant get it to work please someone help

---

### Post by EndPerform on 2007-09-04
First of all, tell us a bit about your system.  Is it a laptop?  What brand and model is it?  There are known problems with some laptops and sound.

---

### Post by amyfan on 2007-09-04
sorry lol its a gateway and it is new and had vista on it thn installed xp now installed ubuntu feisty asfor the model i have no idea when i do alsamixer i get alsamixer: function snd_mixer_load failed: Invalid argument    any idea how else to fix it i have installed alsa and alsamixer in synaptic also have installed evrythng under alsa and sound but nothing and all the volume is up on thm

---

### Post by wolfen69 on 2007-09-04
try this: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_work_with_Intel_Integrated_Sound_Cards)

---

### Post by amyfan on 2007-09-04
done it and still not work ive done all theguides no sound what so ever

---

### Post by kellemes on 2007-09-04
Can you give the output of..
alsamixer -h
**and**
find out the version of the alsa-driver your using..

---

### Post by gasolinehabit on 2007-09-04
Dude, I hate to say this, but i couldn't get my HDA INTEL sound to work either.  Soooo I tried two approaches, both of which worked.  Only problem, you will have to spend some ($10-30) money.

1.  I bought a tiny little USB sound adapter, plugged it in, and plugged the speaker wire in.  Flawless! got it from  Amazon.com   $9.99  :)

2.  I broke down and bought a $30 Sound Blaster Audigy SE card at Office Depot.  Prob paid too much.  Then I followed these instructions:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Be sure to read several pages into the thread before starting.............   ROCK ON!

:guitar:

---

### Post by amyfan on 2007-09-04
using alsamixer v1.0.12 usage alsamixer {-h} {-c <card: 0. . .7>} {-D <mixer device>} {-g} {-s} {-v <view>} {-a <abst>} 




and the version i have is Advanced Linux Sound Architecture Driver Version 1.0.14rcl

---

### Post by kellemes on 2007-09-05
I will post some links for you to investigate, there seem to be more people having issues like you have..
[http://y3d1ps.blogspot.com/2007/06/problem-after-feisty-update.html]("http://y3d1ps.blogspot.com/2007/06/problem-after-feisty-update.html")
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570")
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103379]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103379")
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893")

---

