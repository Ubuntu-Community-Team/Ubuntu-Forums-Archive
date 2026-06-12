---
title: "mplayer on multi-user system woes"
date: 2008-10-26
forum: Multimedia Software
---

### Post by BatteryKing on 2008-10-26
Seeing that Linux is supposed to be a full multi-user system, I have my main computer setup running with two X-server logins.  However my 64-bit Ubuntu 8.04.1 LTS setup with all of the latest patches barfs a lot with this configuration while surprisingly even Windows XP handles multi-user Windows sessions much better.

One of the problems that I have partially compensated for is daily X-server crashes of the first login when there is more than one login.  What I did was go through the guide to setup PulseAudio and get all of the major applications using it and now the initial X-server login crashes sporadically every week or so instead of every day.  (With a single user setup it doesn't crash at all and is perfectly stable.)  An associated problem is the User Switcher doesn't automatically update when new users login nor when the X-server for a user crashes, so I compensate by removing it and re-adding it to the task bar.  (Would be nice if this program had some smarts to it.)

A problem that is really vexing me now is trying to get mplayer to play properly on two simultaneous X-server logins.  Right after following all of the guides and doing all of the 64-bit specific stuff (keeping everything in 64-bit mode on my dual core AMD system), mplayer works fine on the first login, but gets super choppy and out of sync on the second X-server login, even when playing the exact video that worked fine on the first login.  The error I get on the second login that I don't get on the first in mplayer is "[VO_XV] Shared memory not supported" and when I scanned for other video modes, all of the ones that worked at all were still super choppy.  (This computer is using an nVidia GForce 8600 GT with 256 MBs of RAM and has 4GBs of main system memory to better support two X-sessions).

If anybody knows how to make Ubuntu act as a true multi-user system at least as good as Windows is at it (but without all of the aggravating user restrictions of course), it would be greatly appreciated.

---

