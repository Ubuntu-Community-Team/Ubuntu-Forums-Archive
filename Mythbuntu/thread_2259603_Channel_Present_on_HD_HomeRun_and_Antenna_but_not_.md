---
title: "Channel Present on HD HomeRun and Antenna but not in MythBuntu II"
date: 2015-01-05
forum: Mythbuntu
---

### Post by briktoo on 2015-01-05
Similar symptoms as this
[http://ubuntuforums.org/showthread.php?t=2237652](http://ubuntuforums.org/showthread.php?t=2237652)

I was checking out "HDHomerun Live" and noticed three channels that I do not have in MythTV. I would like to add them to MythTV. I can view them on the backend (with vlc via HDHomerun Config GUI) as well as from other PCs with the HDHomerun tools. 

The HDHomerun Config GUI shows Signal Strength at 99%, Signal Quality at 94% and Symbol Quality at 100%. Certainly a decent reception! 

The channels are 2.1 KJWP, 2.2 Grit and 2.3 Escape (Philadelphia market, 19460)

The fix in the post referenced above had no effect. 

I have tried adding channels via the backend setup as well as the instructions here [http://www.mythtv.org/wiki/Updating_Channel_Lineup](http://www.mythtv.org/wiki/Updating_Channel_Lineup) 

I use Scheduled Direct and have confirmed the channels are in the lineup and enabled. 

I would rather not delete all my channels and tuners and re-add everything (unless I was certain that was my only fix). 

My setup.
backend with frontend installed for testing only latest 0.27.X builds running on Mythbuntu 12.04 LTS
two HDHomerun dual tuners with latest firmware. 

Suggestions?

---

### Post by kpatz on 2015-01-05
Have you tried doing a channel scan in the backend setup?

---

### Post by briktoo on 2015-01-05
> **kpatz said:**
> Have you tried doing a channel scan in the backend setup?
I should have mentioned that. Yes, I did a channel scan. I even tried to manually add one of the channels from the backend setup. Thanks for your speedy reply!

---

### Post by briktoo on 2015-01-05
Well - I fixed it. Not sure exactly how unfortunately. I was in the backend setup again. I adjusted some scan options and re-scanned all. Magically they were added.

---

