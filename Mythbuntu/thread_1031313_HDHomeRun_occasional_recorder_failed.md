---
title: "HDHomeRun occasional recorder failed"
date: 2009-01-05
forum: Mythbuntu
---

### Post by uncle hammy on 2009-01-05
I have from time to time where a scheduled recording does not run. If I look at the "Upcoming Recordings" while still in the time block of the show, it shows a status of "Recorder Failed".

The logs for the myth backend always have this entry when this happens...

[B]HDHRChan(<device_id>/<tuner>), Error: Set request failed
eno: Connection reset by peer (104)[/B]

It's not the end of the world, but I would like to eliminate this if possible. Anyone offer any suggestions what is happening?

Thanks,
Scott

---

### Post by uncle hammy on 2009-01-07
bump

---

### Post by crez79 on 2009-01-07
Have you checked the power supply? There is a problem with some power supplies that make the HDHR unstable. Check the Silicon Dust website and if it is that, they will send you out a new power supply right away. This fixed my connection issues I was having.

---

### Post by uncle hammy on 2009-01-07
Thanks for the reply.  

Yes, one of my power supplies had to be replaced a few months ago for that reason.  The other is a version 2, and did not ship with the affected power supply.

---

### Post by Landris on 2009-01-09
I have the same issue as you, once in a while a recording just fails with the same error message as you have in the backend log. I don't have any solutions unfortunately. It's probably once every 10 recordings or so.

I just updated by HDHomerun firmware to the latest (Dec 31 I think) so I'll see if that helps at all. The other thing might be upgrading to a newer libhdhomerun, since SiliconDust has upgraded that too, but I will probably wait for it to filter into newer MythTV builds since I'm not confident about doing a manual upgrade.

---

### Post by uncle hammy on 2009-01-09
That's actually a vry good idea, I think I'll give it a try when I get a chance.  I don't fail once every 10 recordings though, not even close to that.  However, the times it does fail, drops the waf for a few minutes, because it ALWAYS seems to be one of her recordings :lol:

---

### Post by Landris on 2009-02-09
It's been since before my last post here that I haven't had a failed recording, so that's probably 50 recordings and 4 weeks, but I've had another one fail, so the firmware update to the HDHR didn't fix it. Now I plan on waiting till Jaunty is released, I believe it has a newer version of Myth 0.21-fixes available in its repositories than Intrepid which I'm currently running.

---

