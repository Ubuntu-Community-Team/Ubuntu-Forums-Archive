---
title: "Internal subwoofer on an Acer laptop doesn't work on 9.10"
date: 2010-02-28
forum: Multimedia Software
---

### Post by aneganov on 2010-02-28
Hi all,

After upgrading from 9.04 to 9.10 internal subwoofer on my Acer Aspire 5930G laptop stopped working. 

Any ideas?

UPDATE and FIX: Problem was fixed after upgrading to ALSA 1.0.22 using instructions from this topic: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
NOTE: be sure that ALSA driver was really updated using this commmand:
**cat /proc/asound/version**, if not, see these posts:
problem: [http://ubuntuforums.org/showpost.php?p=8915593&postcount=670](http://ubuntuforums.org/showpost.php?p=8915593&postcount=670)
solution: [http://ubuntuforums.org/showpost.php?p=8925366&postcount=678](http://ubuntuforums.org/showpost.php?p=8925366&postcount=678)

---

### Post by aneganov on 2010-02-28
I read somewhere, that internal subwoofer is not like real one, so could not be adjusted. But. On 9.04 I had "Side" channel which actually regulated subwoofer's power. 

Just want to understand - is this because of bugs in ALSA or in Ubuntu?

---

### Post by optimusmedia on 2010-03-24
Bump - because I'd like to know this too. I have an Acer Aspire 7736Z-4088

---

### Post by aneganov on 2010-03-25
> **optimusmedia said:**
> Bump - because I'd like to know this too. I have an Acer Aspire 7736Z-4088

Upgrade ALSA up to 1.0.22 using this instructions:
[http://ubuntuforums.org/showthread.php?p=9020750](http://ubuntuforums.org/showthread.php?p=9020750)

Also see these posts if you will stick with old version of ALSA:
problem: [http://ubuntuforums.org/showpost.php?p=8915593&postcount=670](http://ubuntuforums.org/showpost.php?p=8915593&postcount=670)
solution: [http://ubuntuforums.org/showpost.php?p=8925366&postcount=678](http://ubuntuforums.org/showpost.php?p=8925366&postcount=678)

---

