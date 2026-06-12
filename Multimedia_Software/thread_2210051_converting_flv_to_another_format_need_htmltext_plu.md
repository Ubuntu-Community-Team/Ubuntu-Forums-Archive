---
title: "converting flv to another format need html/text plugin"
date: 2014-03-08
forum: Multimedia Software
---

### Post by blukami on 2014-03-08
got an flv that wont play in vlc. I think because the sound channel is off not sure. Any how every program I have tried said something about html/text is this some kind of security for flv's? 
this is the output i get from ffmpeg:
  
libavutil      52. 66.101 / 52. 66.101
  libavcodec     55. 52.102 / 55. 52.102
  libavformat    55. 33.101 / 55. 33.101
  libavdevice    55. 11.100 / 55. 11.100
  libavfilter     4.  3.100 /  4.  3.100
  libswscale      2.  5.101 /  2.  5.101
  libswresample   0. 18.100 /  0. 18.100
  libpostproc    52.  3.100 / 52.  3.100
[flv @ 0x9fd8340] Format flv detected only with low score of 1, misdetection possible!
[flv @ 0x9fd8340] Could not find codec parameters for stream 0 (Audio: none, 0 channels): unspecified sample format
Consider increasing the value for the 'analyzeduration' and 'probesize' options
/home/eechat.flv: could not find codec parameters

here is the command I used:
ffmpeg -i ~/eechat.flv -an -b 2048k ~/eechat.avi

any ideas or suggestions?

---

### Post by andrew.46 on 2014-03-08
Is the sample small enough that you can post it online somewhere?

---

### Post by blukami on 2014-03-08
close to 10 mb so nope.

---

### Post by andrew.46 on 2014-03-08
> **blukami said:**
> close to 10 mb so nope.

[http://www.datafilehost.com/](http://www.datafilehost.com/)

---

### Post by ssam on 2014-03-09
can you run
```
file ~/eechat.flv
```

Maybe it is actually an HTML file. Did you download it from somewhere?

---

### Post by monkeybrain20122 on 2014-03-09
If you install vlc from the repo it won't play because it is compiled against libav (avconv). But if you compile against ffmpeg then it would (same goes with mplayer)  I have came across a few .flvs like that. I keep one just for testing my players.

---

