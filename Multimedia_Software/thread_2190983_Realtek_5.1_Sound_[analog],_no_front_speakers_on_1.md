---
title: "Realtek 5.1 Sound [analog], no front speakers on 12.04"
date: 2013-11-30
forum: Multimedia Software
---

### Post by g.kafousis on 2013-11-30
I have a problem with my 5.1 sound after updating to ubuntu 12.04 LTS.

I have a Realtek ALC887-VD Analog sound card.

My problem is that front speakers don't work! No sound coming out neither from front- right nor the front-left speaker!!
front-center, lfe and rear speakers work as they should.

When i open alsamixer in the terminal i can see a control named front. I suppose that goes for both front right and left speakers and it's not muted!

I've been searching for days to find a solution without any luck.

I' ve tried to edit my /etc/pulse/daemon.conf file as I saw in several posts.

I changed the number of the channels like this:
default-sample-channels = 6

I also triend to edit my /etc/modprobe.d/alsa-base.conf. I added a line at the end:
options snd-hda-intel model=generic

....but unfortunately no luck at all!

Please if you have any suggestions let me know! Thanks in advance!

---

### Post by g.kafousis on 2013-12-07
Problem still unsovled guys!!! Any suggestions???

---

