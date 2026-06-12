---
title: "&quot;Trouble Initializing Audio Device&quot; on AVIDEMUX"
date: 2008-12-11
forum: Multimedia Software
---

### Post by SteveDee on 2008-12-11
The AVIDEMUX application survived the upgrade from Hardy to Intrepid, but sometime during the last 10 days, a routine Ubuntu update has broken the sound. So when I load a video, select the main audio track, and then press play, I get the message "Trouble Initializing Audio Device". I'm sure its nothing I've done because computer #2 has exactly the same issue.

Anyone had the same experience, or understand the reason why?

It looks like an ALSA update has caused this problem as I can fix it by going to Edit > Preferences > Audio and changing Audio Output from ALSA to just about anything else.

But I'm beginning to regret switching from 8.04 as I now have 3 applications that worked great on Hardy, but seem to have been broken by Intrepid. The other 2 apps being Kompozer (now scared of mice) and MPlayer (A/V sync + crash).

---

### Post by SteveDee on 2008-12-14
I found the solution to this one, its a minor bug with avidemux as described here: [https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/215560](https://bugs.launchpad.net/ubuntu/+source/avidemux/+bug/215560)

Selecting Pulse Audio for Audio Output fixes this.

---

