---
title: "AverMedia Go 007 sound"
date: 2007-03-05
forum: Multimedia &amp; Video
---

### Post by cazimir on 2007-03-05
Hello..i have an tvtuner AverMedia Go 007 and i follow the instruction [http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM.i](http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM.i) have a problem with this command modprobe saa7134-oss.it gives me the following output FATAL: Error inserting saa7134_oss (/lib/modules/2.6.17-11-generic/kernel/drivers/media/video/saa7134/saa7134-oss.ko): Device or resource busy.On ubuntu 6.06 this works but on 6.10...Please help me to make this work;)

---

### Post by sisco311 on 2007-03-06
i have the same card
```
sudo modprobe saa7134-alsa
```
but in edgy my card was recognized and configured automatically.
so you don't need to modprobe it just try it with tvtime, mplayer, xawtv or anything else.

---

### Post by cazimir on 2007-03-06
Yes you have right..I tried with modprobe saa7134-alsa,and after i write the command sox -c 2 -sw -r 32000 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp and it works with kdetv.Thank you:popcorn:

---

