---
title: "Problems with Compro Videomate TV PVR/FM - FM radio dosent work"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by Andrey-UA on 2007-04-04
I can not listen radio on TV-tuner Compro Videomate TV PVR/FM. Used Ubuntu 6.10. I was able to look television after such instructions execution:

1. sudo nano /etc/modprobe.d/saa1734

2. added these lines to the file:

alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=40 tuner=37

3. sudo rmmod saa7134_alsa && sudo rmmod saa7134 && sudo modprobe saa7134

File video0 and radio0 it is present. I try to listening radio with kradio and gnomeradio without success. Then I connected the acoustic system straight linear output of TV-tuner and get no results. At this time in Windows television and radio work, so that problem not in a hardware.

---

### Post by scoon on 2007-04-04
Hey there, 

You probably need to unmute those channels for them to be heard.  Open up a terminal and try alsamixer.

-scoon

---

### Post by Andrey-UA on 2007-04-15
Teal me please more detail - what to do?

---

### Post by scoon on 2007-04-15
Hey there, 

man alsamixer will do a much better job of expalining than I could do. :D 

-scoon

---

