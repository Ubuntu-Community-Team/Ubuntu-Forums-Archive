---
title: "saa7134 Sound Issue Resolved."
date: 2009-04-07
forum: Multimedia Software
---

### Post by wbee on 2009-04-07
Hello,

Fair warning,I'm going to vent. I won't rant,because you gotta draw a line someplace.:-)

--I finally got sound from an saa7134 sound card by attaching the audio out from the TV tuner card to a line in on my Soundblaster card and selecting the line in from the sound table. But the sound was so bad,so distorted,that it was not usable.

--Thanks to Google.TVTimes's bug page, and this forum,I got the information I needed to get sound by directing the alsa feed to an Oss driver,using this code:

```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp2 -t ossdsp -w -r 32000 /dev/dsp
&
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80% unmute
```

The terminal prompted me to add some more stuff,but it worked,kinda.n

But alas,the video and the audio were a little over a second out of synch.

So,if you are considering an saa7134 TV tuner card, for analogue TV, for Linux/Debian,avoid the ones with the TDA 8275 chip. They work fine with XP,but get a better one for L/D.

-----------

Thank you

PS Thank you mark and Cariboo and Loving Linux for the help along the way.

---

### Post by Prospero2006 on 2009-04-07
I have the same model saa7134, and the line in to the sound card works well.
Tvtime works well.

What kind of motherboard are you running?

---

### Post by wbee on 2009-04-07
Prospero 2006.

It is an MSI TV Anywhere Plus card. In addition to the saa7134 chip,it has a TDA8290 +75 chip. Mine is the TDA8275 chip. It is card=82 tuner=54.

The Motherboard is an MSI with the sound disabled,and the external card is a Soundblaster Audigy SE,the low end one for about twenty dollars,US.

The best descriptive word I can come up with for the line in sound is "garbled".

------------

W

---

### Post by wbee on 2009-04-16
Prospero,

I should have looked through your books more carefully.:-)

I did not account for the impedance difference between,"mike in" and "line in".

When I directed it correctly,it sounded OK.

------------

W

---

