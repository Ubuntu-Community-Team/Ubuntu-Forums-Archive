---
title: "sound problem"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by thec0der on 2006-07-26
Hello. I cannot make my sound to work on 5.1 channels.
My mainboard is Albatron PX 865 Pro Lite v2.0, sound system - Creative Inspire P5800 and Im with lastest distribution of Ubuntu.
lspci:
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

alsamixer tell that audio is working on 6 channels, but this is not true. Rear speakers doest work :(.Central speaker doesnt work. Also low frequences from music a in rear speaker  and this make sound bad.

Im play music with xmms 1.2.10

---

### Post by poekie on 2006-08-25
Same problem, no sound on rear/centre and sub/front are working. Same speakers, different soundcard; soundblaster audigy se. 
lspci gives
0000:00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS

speaker-test -Dplug:surround51 -c6 also works normally, all speakers have sound. Removing D from this line makes only front left/right work.

Anyone any ideas??

---

