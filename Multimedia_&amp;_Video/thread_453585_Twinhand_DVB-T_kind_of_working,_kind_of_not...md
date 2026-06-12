---
title: "Twinhand DVB-T kind of working, kind of not.."
date: 2007-05-24
forum: Multimedia &amp; Video
---

### Post by Burbruee on 2007-05-24
Hello, 

Trying to get my Twinhan DTV (DVB-T) card working with Feisty Fawn 7.04 and to some point it does.
I did modprobe for dvb_bt8xx, dvbcore and dst as suggested by this page: 
[http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Mini_Ter](http://www.linuxtv.org/wiki/index.php/TwinhanDTV_Mini_Ter)

And actually, after that it all worked fine, I later used scan to generate my channels.conf and after that I created a symbolic link to .mplayer/channels.conf.

After that, executing the command 'mplayer dvb://TV6' worked just fine, and the picture show up. However, the picture is really glitchy and bad, it's like the signal is really really low and the sound is horrible and all that stuff, you probably know what I mean..

So, first thing I could think of is that I need to adjust my antenna, which I tried for about 5 minutes without any improvements whatsoever.
And then I thought of the idea to reboot into windows ( I still DualBoot. ), and surprise surprise, the signal is at 98% and picture is perfect..

So then I start to think that it's a problem with the linux driver for the card, and that the windows driver is much better, what do you think?
Transponder is set to se-Horby in linux, and set to Hörby in Windows too, so frequency and all that stuff is the same in both cases.

Any ideas?

---

