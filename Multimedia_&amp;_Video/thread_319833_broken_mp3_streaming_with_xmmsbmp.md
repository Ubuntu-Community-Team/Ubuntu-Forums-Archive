---
title: "broken mp3 streaming with xmms/bmp"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by zucca on 2006-12-16
hello everyone!

I managed to break the mp3 playback of xmms and bmp. The error message is the usual 

'Couldn't play audio: 
Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.'

I suspect that everything started when I was messing around with gstreamer plugins to let  Sound juicer rip mp3s. ](*,)
Rythmnbox and vlc work fine. I tried to apt-get remove/reinstall xmms/bmp but i had no luck. As suggested by the help page i also tried to apt-get remove/install all the packages cited in [https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59]("https://help.ubuntu.com/community/RestrictedFormats#head-1340337f2ca1d0c54900935468515ba7630fcc59")
 and I also run 'sudo gst-register-0.8'

any suggestions?

have a nice week-end, zucca :KS

---

