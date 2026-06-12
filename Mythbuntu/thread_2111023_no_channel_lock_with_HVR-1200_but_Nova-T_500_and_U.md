---
title: "no channel lock with HVR-1200 but Nova-T 500 and USB2 both work."
date: 2013-01-31
forum: Mythbuntu
---

### Post by gpherber on 2013-01-31
For some reason my Haupauge HVR-1200 wont get channel lock in mythtv frontend. The channels were scanned using my first tuner (Nova-T 500) and work great on that and the Nova-T USB2. Any ideas on how to get channel lock on the HVR-1200? Ubuntu 12.04 server, fresh install.

Thanks Gary

---

### Post by Lester_Burnham on 2013-01-31
Hi,

Is the firmware loaded, if required?
Check dmesg for info.
```
dmesg | grep cx
dmesg | grep dvb
```

Lester

---

### Post by gpherber on 2013-02-01
Yes, the firmware is loaded and the card appears in lspci, i can tune the card using mythtv-setup and get about 45 channels which lock, but it cant pick up the BBC channels (both the other cards find them fine and so does my tv so reception isnt an issue).

---

### Post by Lester_Burnham on 2013-02-02
Hi,

Sorry, wrong country for me to go any further :)

Lester

---

### Post by PhilWig on 2013-02-02
I see from 
[http://www.mythtvtalk.com/one-tuner-works-any-one-but-unable-record-multiple-tuners-time-16104/](http://www.mythtvtalk.com/one-tuner-works-any-one-but-unable-record-multiple-tuners-time-16104/) 
that you've fixed your problem.
Did you by any chance power cycle your box before the last rescan?  Hauppauge devices tend to only reload code and settings after a cold boot.
 
Incidentally, why do you need 4 tuners in the uk?  With multirec=3 and 3 tuners my third tuner is never used for recording - just for eit scanning and live tv.
Phil

---

