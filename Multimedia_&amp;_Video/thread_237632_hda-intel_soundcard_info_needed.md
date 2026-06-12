---
title: "hda-intel soundcard info needed"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by brk3 on 2006-08-16
Hi, I installed ubuntu dapper on my hp dv8333ea laptop yesterday and the sound volume is very low.
All volume settings are definatly up full (actually all alsa seems to give is master and pcm). 
Kmix reports that it is using the **hda-intel** driver. I have seen some other reports of similar problems with this card except most people seem to get no sound rather than just low sound.

Does anyone have any advice on what I can try, would installing the latest alsa help? Or is there any way I can use a different driver? Any info would be appreciated as music is a big thing for me to get working. Thanks!

---

### Post by egd on 2006-08-23
I'm having exactly the same problem on an intel 975xbx mobo with dapper installed.

---

### Post by KrakensDen on 2006-08-23
I was told that as of now, there is no known fix for this. I also have an hda-intel sound card :/.

---

### Post by egd on 2006-09-05
> **KrakensDen said:**
> I was told that as of now, there is no known fix for this. I also have an hda-intel sound card :/.

I'd have thought Intel would provide some form of driver/code seeing as they're touting Linux.  Guess we'll have to be patient.  I stream my audio to my hifi using a squeezebox anyhow, so it's an inconvenience rather than a big deal.

---

### Post by maleficent on 2007-11-12
I realise this is an old thread (fell over it looking for something else), but for anyone else with this problem on a hp dv8xxx (or any other machine with a 'Conexant CX20551 (Waikiki)' intel-hda codec):

'Just make it work':
```
amixer cset numid=6 30,30
```

'Why':
This codec has both 'PCM Volume' (numid=6) and 'PCM Playback Volume' (numid=14), most mixers seem unaware of 'PCM Volume' and only show you 'PCM Playback Volume', including 'amixer scontols', 'amixer controls' however reveals both.

---

