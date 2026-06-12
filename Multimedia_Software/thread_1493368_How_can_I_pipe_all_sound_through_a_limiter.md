---
title: "How can I pipe all sound through a limiter?"
date: 2010-05-25
forum: Multimedia Software
---

### Post by _nate on 2010-05-25
I would like to pipe mp3's, streaming audio etc. through a limiter so the volume doesn't spike to a super loud level from one song to the next. Any suggestions?

---

### Post by sgosnell on 2010-05-25
Cable from sound card (jack wherever) to limiter, with speakers plugged into limiter.  It shouldn't be hard, if the limiter has anything close to standard inputs and outputs.  You might need an adapter, but those should be plentiful and cheap.

---

### Post by _nate on 2010-05-25
any idea where I could find a cheap limiter?  do any linux audio programs have a limiter in them?

---

### Post by sgosnell on 2010-05-25
The cheapest might be guitar stomp boxes.  They're mono, though, not stereo.  I have never looked for standalone limiters, so you'll need to use Google or something like that to find them.  Maybe ebay.

Cheaper, but perhaps time-consuming - normalize your music.

---

### Post by xzero1 on 2010-05-26
It should be possible via software. Check out this thread [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) which sets up a system-wide equalizer using a ladspa filter. In the similar way you could use a ladspa limiter filter. How well it works and how easy it will be to set up is another matter.

---

### Post by bth73 on 2011-10-31
guitar center sells limiters for a little over $100. they work a little but it's analog. I can't understand why all these genius programmers can't  write a program to fix the volume of all input sources at a specific volume range. And why are all the volume levels so different?

---

### Post by aeiah on 2011-10-31
might be best to run all your mp3s through a replaygain script. it won't alter the mp3, but will add a replaygain tag to each one. most music players will read the replaygain tags and keep the audio level

---

