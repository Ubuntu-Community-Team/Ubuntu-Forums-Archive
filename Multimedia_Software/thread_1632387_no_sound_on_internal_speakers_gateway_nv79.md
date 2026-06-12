---
title: "no sound on internal speakers gateway nv79"
date: 2010-11-27
forum: Multimedia Software
---

### Post by osmanb on 2010-11-27
I just installed 10.04 on my new gateway laptop. Everything was working ok but the internal speakers. External speakers were ok. I fixed it by looking at the earlier sound problems on the 64 bit forum. The suggestion to add 3 lines to the end of  /etc/modprobe.d/alsa-base.conf file:

options snd-hda-intel model=3stack-dig
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

Worked, I had to experiment with the model=xxxx to find that 3stack-dig worked. Just info for other gateway laptop users. 
Hope that this will be helpful.
-osman

---

### Post by lidex on 2010-11-28
> **osmanb said:**
> I just installed 10.04 on my new gateway laptop. Everything was working ok but the internal speakers. External speakers were ok. I fixed it by looking at the earlier sound problems on the 64 bit forum. The suggestion to add 3 lines to the end of  /etc/modprobe.d/alsa-base.conf file:

options snd-hda-intel model=3stack-dig
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

Worked, I had to experiment with the model=xxxx to find that 3stack-dig worked. Just info for other gateway laptop users. 
Hope that this will be helpful.
-osman

It should work with just the first line. Documentation here:
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

