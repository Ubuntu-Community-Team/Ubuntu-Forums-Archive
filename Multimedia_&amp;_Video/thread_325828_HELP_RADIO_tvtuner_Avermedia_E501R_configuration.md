---
title: "HELP RADIO: tvtuner Avermedia E501R configuration"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by zolly on 2006-12-26
I have an Avermedia AverTV E501R Cardbus (PCMCIA).
It works with [http://ubuntuforums.org/showthread.php?t=220061&highlight=e501r](http://ubuntuforums.org/showthread.php?t=220061&highlight=e501r)
I mean:

sudo rmmod saa7134_alsa
sudo rmmod saa7134
sudo modprobe tda9887 debug=2
sudo modprobe saa7134 card=46 tuner=66

and for sound:

sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp
where dsp1 is device created by saa7134_oss

But the radio doesn't work. I tried with gnomeradio but I hear buzz, no station. I hear something if I put the card=32 or card=79. What should I do ?

---

### Post by Mets on 2007-02-17
Ok so I tried it with sox and it syncs up fine, there's just a noticable quality difference.  Maybe it was in the command that I ran.  I used:

```
tvtime -d /dev/video0 -b /dev/vbi0 | sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp | aplay -
```

Not sure if that is correct, or if there redundant parts in there (i.e. both dsp and vbi and video0) but it syncs.  Again, only works in the terminal.

---

