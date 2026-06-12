---
title: "Moving Mythtv Setup (setting, channels, channel groups) to another machine?"
date: 2010-06-17
forum: Mythbuntu
---

### Post by DominicF on 2010-06-17
Hi,

I'd like to know if anyone managed to copy/move their current mythtv setup and install on another freshly installed Mythbuntu machine?  What bits would I need to copy? I'm running Mythbuntu
10.04.

I find I'm always trying to fix issues on my system as they arise and at some point usually decide to re-install everything after experimenting and re-apply my fixes.  At the moment I have a two tuner setup one with a DVB-S/S2 card connected to DiSEqC switch feeding 2 sats  and DVB-T card.  I took me a long time to tune and remove unwanted channels and create channel groups and I don't want to loose those settings.  

Thanks.

---

### Post by joshoekstra on 2010-06-17
> **DominicF said:**
> Hi,

I'd like to know if anyone managed to copy/move their current mythtv setup and install on another freshly installed Mythbuntu machine?  What bits would I need to copy? I'm running Mythbuntu
10.04.

I find I'm always trying to fix issues on my system as they arise and at some point usually decide to re-install everything after experimenting and re-apply my fixes.  At the moment I have a two tuner setup one with a DVB-S/S2 card connected to DiSEqC switch feeding 2 sats  and DVB-T card.  I took me a long time to tune and remove unwanted channels and create channel groups and I don't want to loose those settings.  

Thanks.

[Saving or restoring the database]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.5") would help you with the mysql-part. Settings done in files(eg xmltv and remote and so on) would need to be backed up separately...

---

