---
title: "HDA Nvidia Soundcard very quiet in Gutsy"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by clintonthegeek on 2007-09-15
I've just installed Kubuntu Gutsy Gibbon, and everything is working great except my onboard HDA Nvidia sound card.

The mixer only has two channels (Master, PCM), whereas my Feisty install had a whole bunch of them, and maxing out both is barely loud enough to hear over my speakers.

Any suggestions?

According to lspci, I have a
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

---

### Post by choifyken on 2007-10-30
I have the same problem with my ACER AS4520G!

---

### Post by Footer on 2007-11-07
Did you ever figure out your problem?  I have a similar soundcard:

```
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
```

and I can hear MP3s and such fine but when I try to record, I can barely hear the recordings!

---

### Post by urbushey on 2008-04-16
Footer, your problem sounds a bit different and probably related to your microphone. Just guessing based on the information you posted here.

---

### Post by Footer on 2008-04-16
Thanks for the reply urbushey.  However, I was not using a microphone but rather the line-in on the (integrated) sound card.  My problem turned out to be settings on my mixer panel.  All the details are posted here:

[http://audacityteam.org/forum/viewtopic.php?f=14&t=1360](http://audacityteam.org/forum/viewtopic.php?f=14&t=1360)

Thanks again!

---

