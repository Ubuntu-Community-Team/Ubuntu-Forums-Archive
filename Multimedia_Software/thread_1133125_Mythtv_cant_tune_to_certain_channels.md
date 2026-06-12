---
title: "Mythtv cant tune to certain channels"
date: 2009-04-22
forum: Multimedia Software
---

### Post by theirishfozz on 2009-04-22
Hi everyone

I've been having strange issues with Mythtv (Hauppauge 1800 with Terk OTA TV antenna).

Some channels which are available on Vista Media Center (same computer) are not available on Mythtv. These channels respond just like UNKNOWN channels. When I try to tune to them the screen goes black and I get an "irrecoverable recorder error". They are detected in the channel scan so Im pretty confused as to why I cant view them. Also other channels are detected but I can't get a lock. Im guessing that's just a reception issue but the other channels are available in Vista with the same configuration and antenna position. 

Does anyone have any thoughts as to why this would be happening?

I have attached the mythbackend and mythfrontend shell output from me running, watching tv (working channel) and switching to a channel that works in Vista. Are there other logs I can access?

thanks
Fozz

---

### Post by theirishfozz on 2009-05-06
Well that was successful.

Thinking in broader terms, anyone have any ideas as to why MythTV might not be able to tune to certain channels that WMC can with exactly the same hardware configuration and antenna position?

---

### Post by theirishfozz on 2009-09-10
I've fixed this issue. I removed the Video Source device from MythTv and re-created it. All is well.

---

### Post by rlees42 on 2009-10-29
I had the exact same problem and the same solution.  Wish there was some explanation for this...

---

