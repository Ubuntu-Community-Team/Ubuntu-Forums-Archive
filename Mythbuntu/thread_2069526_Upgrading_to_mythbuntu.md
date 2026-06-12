---
title: "Upgrading to mythbuntu"
date: 2012-10-11
forum: Mythbuntu
---

### Post by dheianevans on 2012-10-11
Currently using Mythbuntu 11.04 and .25-fixes.

Want to upgrade to 12.04 and .26. Just wondering what I need to watch out for. I have some custom buttons in my LIRC setup for my Harmony 300. Anything to worry about with LIRC and the upgrade?

Is the upgrade to 12.04 direct or will there be an intermediate upgrade in the middle?

Thanks.

---

### Post by 2F4U on 2012-10-11
My understanding is that you can't do an online upgrade from 11.04 to 12.04 directly. Instead, you would have to upgrade to 11.10 first, and would then be able to upgrade to 12.04. However, it may be possible to download the liveCD and do a direct upgrade:

[http://ubuntuforums.org/showthread.php?t=1951195](http://ubuntuforums.org/showthread.php?t=1951195)

---

### Post by nickrout on 2012-10-11
> **2F4U said:**
> My understanding is that you can't do an online upgrade from 11.04 to 12.04 directly. Instead, you would have to upgrade to 11.10 first, and would then be able to upgrade to 12.04. However, it may be possible to download the liveCD and do a direct upgrade:

[http://ubuntuforums.org/showthread.php?t=1951195](http://ubuntuforums.org/showthread.php?t=1951195)

Back up what you need to keep (primarily your database, and recordings/videos/music etc if they are not on a separate drive) and install 12.04 from scratch. Restore database, upgrade to 0.26, profit.

---

### Post by dheianevans on 2012-10-11
Out of curiosity is there a major reason (except for time savings) to do a clean install vs. command line upgrades to 11.10 then 12.04?

The only reason I ask I that I have a lot of custom crons on my Mythbox for downloading backups from other servers and I'd like to not have to set them and their SSL keys up again.

---

### Post by nickrout on 2012-10-11
> **dheianevans said:**
> Out of curiosity is there a major reason (except for time savings) to do a clean install vs. command line upgrades to 11.10 then 12.04?experience> 

The only reason I ask I that I have a lot of custom crons on my Mythbox for downloading backups from other servers and I'd like to not have to set them and their SSL keys up again.Just back up those bits then.

---

### Post by dheianevans on 2012-10-12
I guess the real question at this point is: if .25 and 11.04 are sailing smoothly right now, is .26 enough of a sea change to make the jump to 12.04? :)

---

