---
title: "MythTV doesn't scan channels"
date: 2009-07-12
forum: Mythbuntu
---

### Post by daehenoc on 2009-07-12
Hi all,

I can scan TV channels using tzap and watch the tuned channel using mplayer on my MythTV box.  When I go to set up the channels in mythtv-setup, MythTV can't scan any of my channels, just coming up with Timeout messages.  I've even tried to import the channels.conf file that works for tzap and do the 'scan', but MythTV then shows much fewer Timeout messages.

I'm using the same user for doing all of the above, so permissions aren't a problem, at least I don't think they are.

What the heck is going on here??? Why can't MythTV scan my local channels (Brisbane, Australia), when I can tune them manually?!?!

Thanks,
G

---

### Post by daehenoc on 2009-07-13
HAH, fixed!  The timeout for the Compro DVB-T300 tuner card I have was too low (500ms), I increased this to 6000ms and used the channels.conf file and MythTV tuned the channels successfully!

---

