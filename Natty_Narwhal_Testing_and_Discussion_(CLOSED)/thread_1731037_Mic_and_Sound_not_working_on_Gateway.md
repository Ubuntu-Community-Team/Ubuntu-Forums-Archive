---
title: "Mic and Sound not working on Gateway"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by reddognp on 2011-04-16
I have a Gateway NV52o7u. I love ubuntu! I am a beginner and was not liking Windows, so I switched. I love it! I am having 1 problem with Natty 11.04 beta 2. The mic and sound through headphones aren't working. The sound out of the speaker sounds great, but headphones are not working along with the mic. I do a lot of skyping for work and use headphones a lot. Please help!

---

### Post by screaminj3sus on 2011-04-16
On my gateway m6862 my headphones don't work at all either, until I do this:

> 
You need to edit the alsa-base.conf file, do this by typing this in the terminal:
gksu gedit /etc/modprobe.d/alsa-base.conf 

Then add this line at the very end and save it:
options snd-hda-intel model=eapd probe_mask=1 position_fix=1

After that it works perfectly.

---

### Post by reddognp on 2011-04-16
It is an AMD machine. Does that matter?

UPDATE: I was not really looking.I am sorry. It does work with AMD machines. Thanks.

---

