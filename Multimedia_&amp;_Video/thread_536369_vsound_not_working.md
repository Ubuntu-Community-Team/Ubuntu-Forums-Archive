---
title: "vsound not working"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by jackn on 2007-08-27
I need to convert realplay streams to .wav files.

I've tried mplayer, but wasn't able to get it to work.

I thought I'd try vsound, as recording directly from the sound card should be easier, and I don't mind the sound quality so much.

No dice.

I run

```
**vsound -d -t -f test_vsound.wav realplay rtsp://real.npr.org:80/real.npr.na-central/npr/wesat/2005/05/20050507_wesat_18.rm?v1st=A131250D4D988244&mt=1&primaryTopic=1033&assignedTopics=1015,1032,1033,1036**
```

Realplayer gets launched, and I let the cllip play, but then, once i close Realplayer,  I get:

```
Warning: LD_PRELOAD="/usr/lib/vsound/libvsound.so"
Missing file ./vsound27514.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

```

I don't know what the warining means, or hwy it won't create the .au file.

what can be done?

Thanks, 
jackn

---

### Post by Kratos on 2007-10-04
I get the same error.

Any ideas?

---

### Post by Unicast on 2007-10-07
Same here.

Anyone help us?

---

### Post by mdwy62 on 2008-06-01
I'm getting exactly the same errors, whether I run as root or not. Also I get  audio output regardless of whether I specify the -d option.

---

