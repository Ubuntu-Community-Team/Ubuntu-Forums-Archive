---
title: "Remote control / Hauppauge 1900 / 9.10"
date: 2009-10-30
forum: Mythbuntu
---

### Post by pros456 on 2009-10-30
I have a Hauppauge HVR-1900, that worked perfectly in 904. For some reason I decided to do a clean install when I saw 910 (actually tried to upgrade first but that didn't go well).

After install everything is working except for the remote, in 904 I just choose "Hauppauge TV-card" as remote and everything worked out of the box. I did the same thing when setting up 910  and now I get no reaction what so ever when using the remote.

```

In /var/log/daemon.log this can be seen
Oct 30 02:14:22 videostar lircd-0.8.6[3953]: caught signal
Oct 30 02:14:22 videostar lircd-0.8.6[4067]: lircd(default) ready, using /var/run/lirc/lircd
Oct 30 02:14:24 videostar lircd-0.8.6[4067]: accepted new client on /var/run/lirc/lircd
Oct 30 02:14:24 videostar lircd-0.8.6[4067]: could not get file information for /dev/lirc0
Oct 30 02:14:24 videostar lircd-0.8.6[4067]: default_init(): No such file or directory
Oct 30 02:14:24 videostar lircd-0.8.6[4067]: Failed to initialize hardware

```
which doesn't look good :)

Tried running irw in terminal, but got no response at all.

Does anyone have any advice how I would go about solving this, I don't really know where to start?

In 904 I had to extract fw from cd to get card to work, but in 910 everything (livetv, recordings etc) seemed to work without this step. But maybe the remote still requires some fw from the cd?

/p

---

### Post by David Grigor on 2009-10-30
I was messing with that last night as well when I did a fresh install of 9.10. Worked fine under 9.04. I also had Hauppauge but not that exact model. 

Turned out for whatever reason, if I unplug the blaster and plug it back in while the machine was up it started recognizing it with irw.  Just reboot or restarting didn't do it. 

Wasted over an hour.

---

### Post by pros456 on 2009-11-01
> **David Grigor said:**
> Turned out for whatever reason, if I unplug the blaster and plug it back in while the machine was up it started recognizing it with irw.

Ahh, an old remedy, taking things apart and putting it back together until everything works :)

Unfortunately that didn't work for me, after a while I realized my time was better spent elsewhere and went back to 904 and now everything works again.

/p

---

