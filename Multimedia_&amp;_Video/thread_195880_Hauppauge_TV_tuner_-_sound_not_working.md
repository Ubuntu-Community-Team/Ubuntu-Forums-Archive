---
title: "Hauppauge TV tuner - sound not working"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by Ariod on 2006-06-13
Hi,

I'm running Ubuntu 6.06 with TVtime installed. I can see video but no sound. This is what I've done so far:

- Connected the TV card and sound card.
- Sound in TVtime is turned up, and everything in Alsa mixer is checked.
- The sound works if I connect my speakers directly to the TV card.
- Sound works in other applications.

Onboard chip is Conexant CX23881.

Do you have any ideas?

---

### Post by tkman on 2006-06-13
What drivers are you using, ivtv?

---

### Post by Ariod on 2006-06-14
Hmm, how to find out? I'm new to Linux.

---

### Post by xargonax on 2006-08-12
I have the exact same problem with my hauppauge card.TvTime shows picture and there is sound output when connected to my speakers directly. However when connected to line-in there is no sound. The line-in is already unmuted. I'm using alsa v1.0.10 (the default with dapper drake) and the hda_intel driver on a Analog Devices AD1986A card. It is on-board sound. help appreciated.

thx.

---

### Post by smsmith050 on 2006-11-28
I recently installed ivtv on my Kubuntu 6.06 box. I am using a PVR-250. I had video but no sound. The How-to's say to remove the msp3400 and saa7115 modules along with some others. The version of ivtv that I have (0.4.7) no longer builds msp3400 and saa7115. So follow the how-to's but don't mv or rm these two modules.

---

