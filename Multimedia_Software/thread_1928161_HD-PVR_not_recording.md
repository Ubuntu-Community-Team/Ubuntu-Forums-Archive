---
title: "HD-PVR not recording"
date: 2012-02-19
forum: Multimedia Software
---

### Post by joker35 on 2012-02-19
Hi,

I got problem recording from HD-PVR - the mythbackend.log shows:

Error -1 while setting frequency (v2): Invalid argument

This commands works fine:
cat /dev/video0 >test.ts

I got these cards installed: pvr-150, hvr-1600, hvr-2250.

I'm running Mythbuntu 11.10 with mythtv 0.24 with all fixes loaded.

Anybody got a hint what to look for? 

Thanks

---

### Post by pilesofspam on 2012-02-28
It's because of your channel change script taking too long.

Try substituting it with a shell script that does nothing just to test.  I'm working on a fix- will post it here when it works.

---

