---
title: "New HD-PVR Firmware 0x18 Audio Lag Problem"
date: 2012-09-07
forum: Mythbuntu
---

### Post by the_crowbar on 2012-09-07
Hi all,

I just got a new HD-PVR and it came with firmware version 0x18. (My old one had firmware 0xf). Recordings from the new HD-PVR come through all washed out. I was able to find a fix for that from the MythTV wiki page for HD-PVR. [http://www.mythtv.org/wiki/Hauppauge_HD-PVR]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR")

My remaining problem is an audio lag of several seconds. It is a known issue and there is a fix in Myth, but it requires an environment variable be set. (FORCE_DTS_TIMESTAMPS=1) Details here [http://code.mythtv.org/trac/ticket/10007]("http://code.mythtv.org/trac/ticket/10007"). My question is, where should I put this environment variable so it gets set every time my system boots.

I have 3 Myth systems total. 
1- Master backend (Mythbuntu 12.04)
2- Slave BE, frontend (Mythbuntu 12.04)
3- Frontend only (Ubuntu 12.04)

I obviously only need the fix on two of the systems. I tried adding the environment variable to /usr/bin/mythfrontend and that worked on one but not the other (although I had only a few minutes to test either system).

I could add it to ~/.bashrc, but because it is a Myth specific setting I would rather it be somewhere that makes it obvious it affects the frontend.

Any ideas?

---

### Post by the_crowbar on 2012-11-10
After testing a few things adding
```

export FORCE_DTS_TIMESTAMPS=1

```
to the end of /etc/mythtv/session-settings seems to be working well.

---

