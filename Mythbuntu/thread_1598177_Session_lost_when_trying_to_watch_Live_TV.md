---
title: "Session lost when trying to watch Live TV"
date: 2010-10-16
forum: Mythbuntu
---

### Post by chrismurf2900 on 2010-10-16
When I choose 'watch tv' it looks like it is going to lock and show me a  channel, but before it does I get logged out and have to log back in.

I have just upgraded from Mythbuntu 10.04 64-bit to 10.10 64-bit.  Everything else seems to work fine, except for that.
It has me log back in and then I start with square one again.

Both the front-end and the back-end are on the same machine.  It can still record shows, and I can watch all shows that were already recorded (and new ones recorded), but clicking on the "Watch TV" doesn't work properly.

Any suggestions?

Thanks!

---

### Post by jordoco on 2010-10-19
Same issue here. Systems looks as if it will lock, the frontend crashes and then have to login again.

---

### Post by chrismurf2900 on 2010-10-21
Anyone know what's going on with this?
Why would it log out of my session and not be able to play video?

Please help!

Thanks!

---

### Post by LowSky on 2010-10-22
we need to see the logs to know why its crashing
the file is located here:
```
/var/log/mythtv/mythfrontend.log
```

---

### Post by chrismurf2900 on 2010-10-22
Okay, so here is what fixed my issue.

In the frontend settings, under "TV Settings," "Playback," I just had to  change the playback profile to something different.  In my case it was  "VDPAU High Quality."  Which fixed my problem.

I hope that helps someone else who might also have the same kind of issue.

---

### Post by jordoco on 2010-10-24
THIS IS SO F*'ing COOL That This works!

@Lowsky - Many, many Thanx for the offer of assistance.

@ChrisSmurf - Yep!, same exact setting brought LiveTV up!

---

