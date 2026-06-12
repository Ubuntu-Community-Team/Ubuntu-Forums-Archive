---
title: "Strange encoder / mysql problems"
date: 2008-07-07
forum: Mythbuntu
---

### Post by jimsiff on 2008-07-07
I've built a mythbuntu 8.04 system with four tuners... two Hauppauge hvr1250, and two Kworld 115s.  I had to update and recompile the kernel w/ 2.6.25.7 to get the 1250s working.  Then I had to write simple UDEV rules to keep the tuners from switching places each reboot.  I currently have three tuners setup in the backend.  During this setup process, I removed and re-added all of the tuners several times in the backend setup.

All three tuners seem to work, but Myth thinks it has six active encoders instead of three.  Why would this be?  Is it because I'm using UDEV rules to dynamically create /dev/dvb symlinks that Myth thinks I have x2 tuners?  is the mythconverg MySQL database filled with junk?  Here's output from mythtv-status:

```
jim@myth:~$ mythtv-status 

MythTV status for localhost
===========================
Status...........: Mon Jul 7 2008, 1:07 AM
Total Disk Space.: Total space is 666,451 MB, with 385,182 MB used (57.8%)
Next Recording In: 3 Hours, 22 Minutes

Encoders:
myth (9) - Idle
myth (10) - Idle
myth (11) - Idle
myth (12) - Idle
myth (13) - Idle
myth (14) - Idle

Scheduled Recordings:
2008-07-07 04:30:00 - It's a Big Big World (KOPB-HD)
2008-07-07 16:00:00 - Oprah Winfrey (KGW-HD)
2008-07-07 18:00:00 - Family Guy (KWBP-Portland's CW Digital)
2008-07-07 18:30:00 - Family Guy (KWBP-Portland's CW Digital)
2008-07-07 21:00:00 - Two and a Half Men (KOIN-DT)
2008-07-08 00:00:00 - RENO 911! (Kpdx-DT)
2008-07-08 00:37:00 - The Late Late Show With Craig Ferguson (KOIN-DT)
2008-07-08 04:30:00 - It's a Big Big World (KOPB-HD)
2008-07-08 11:00:00 - Inside (KOPB-HD)
2008-07-08 16:00:00 - Oprah Winfrey (KGW-HD)
```

---

### Post by jlagrone on 2008-07-07
In the card setup in mythtv-setup, DVB cards have the extra page where you can select some recording options and for some reason on my machine it has the number of recordings at a time set to 2 by default.  Change it to 1 and you should be good.

---

### Post by jimsiff on 2008-07-07
Wow that was quick!  And you are correct, it was the max. number of recordings on the DVB tuner setup.  As soon as I switched it to 1, I have three tuners.  

FWIW, there are a few local broadcasters in my area who multiplex 2-4 programs in their allotted channel space.  I guess if that value is set to 2, I could record two of the multiplexed signals on the same tuner?  Interesting...

---

### Post by ian dobson on 2008-07-07
Hi,

Yep imagine you have to programs back to back on the same channel and have early start/late end for the recordings. With 2 virtual tuners per real tuner it's no problem to record both programs.

Or you can record 2 programs at the same time with one tuner if both are on the same multiplex.

For example I have 2 DVB-C and one PVR-150 in my server and have 5 virtual tuners in my system.

Regards
Ian Dobson

---

