---
title: "Config sound properties"
date: 2007-01-16
forum: Multimedia &amp; Video
---

### Post by LeDieu on 2007-01-16
Hello,

I have a question about alsa.
I have a audigy sound card and it works under ubuntu edgy eft. The only problem is that i cant get all my sound boxes working.
I use xmms for mp3 music. In the configuration of xmms you can choose if you use:
-hw:0,0
-hw:0,1
-hw:0,2
-hw:0,3

Or default.
when i choose hw:0,0 i get sound over the front two speakers. when i choose hw:0,1 i get the rear two speakers. And when i choose hw:0,3 i get my sub woofer and the front center speaker. But i want to config alsa that he always takes my sub woofer/LFE and my front 2 speakers. 

Is this possible? So yes how.

I hope you can help me,

Greetz,
LeDieu

---

### Post by Lucardo Mamones on 2007-01-16
have you tried with the "alsamixer" command from a command line?

---

### Post by LeDieu on 2007-01-16
Well if you mean if i tried to look if the sound is up than yes. The problem is not that the boxes doused working but that i cant select to use the sub woofer and the front 2 boxes. If i remember correctly you can config something like this in /etc/asound.conf. But i dont know how.

---

### Post by Lucardo Mamones on 2007-01-17
does this also happen if you watch a DVD with surround sound? I am not too familiar with XMMS so I dont think that I will of too much help.

I can tell you that in xine for example there is a setting that you have to change to have 5.1 sound and unless you set that you get standard stereo sound.

---

