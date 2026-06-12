---
title: "Sound stops working seemingly randomly"
date: 2009-04-11
forum: Multimedia Software
---

### Post by jadkins0123 on 2009-04-11
After a hard drive failed whilst running XP, I recently installed Ubuntu 8.10 on an 8 GB thumb drive and followed the instructions at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) to get everything set up. Afterward, everything worked beautifully. Til today, for whatever reason, without changing anything, my sound decided to stop working and instead make a horrible crackling sound. I refrenced the documentation I mentioned before, thinking I mayve missed something and I found this line

"If you experience crackling sound after rebooting, insert the following line in /etc/modprobe.d/blacklist:

blacklist snd_pcsp"

After checking /etc/modprobe./blacklist, I found out I had done everything properly and inserted that line yet for whatever reason I still got no audio aside from the crackling.

Finally I went to System > Sound and set all the playback options to OSS, which for whatever reason seemed to work for a while before going back to the crackling sound. A reboot fixes it temporarily but after a few minutes the audio will disappear again.

I've tried everything I know how to, and followed all the instructions in documentation correctly, so I'm hoping someone else can figure out a permanent fix to this, as rebooting every 2 - 3 songs/youtube videos/skype calls isnt convienent. Thanks.:KS

---

