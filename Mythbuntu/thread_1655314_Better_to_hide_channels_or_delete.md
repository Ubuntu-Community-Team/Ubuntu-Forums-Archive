---
title: "Better to hide channels or delete?"
date: 2010-12-29
forum: Mythbuntu
---

### Post by jakev383 on 2010-12-29
I recently moved from cable to DirectTV and built a new backend as part of the process. From SchedulesDirect I get a lot of channels that I do not get as part of my package, and wanted to know if it's better to make the channels non-visible, or remove them from SD's website so they don't appear on my end.

I also had another side question/issue. I have not investigated it much yet, so just throwing it out there.
When watching live TV if I tune to a channel that the Direct box says is not available, the live TV goes away and it puts me back at the frontend menu with a box that says something like recorder error, and the backend logs show this:

```

2010-12-29 09:50:26.255 TVRec(3): HW Tuner: 3->3
2010-12-29 09:50:27.404 ret_pid(0) child(4793) status(0x0)
Excessive channel change retries, commanded 225 got 269
2010-12-29 09:50:27.773 ret_pid(4793) child(4793) status(0xff00)
2010-12-29 09:50:27.829 ChannelBase: external tuning program exited with error 255
2010-12-29 09:50:27.889 TVRec(3) Error: Failed to set channel to 225. Reverting to kState_None
2010-12-29 09:50:27.939 TVRec(3): Changing from WatchingLiveTV to None

```

Obviously I was trying to change to a channel that does not exist, but is this expected behavior? Is there a way to not allow it to tune to channels that do not exist without erroring out like this?

Thanks!

---

### Post by ian dobson on 2010-12-29
Hi,

I would delete the channels in mythtv and from schedules direct. Having less channels to download should speed up the xmltv download.

With your second problem, I'm not sure. I know that trying to watch LiveTV can be abit hit/miss sometimes, but your getting an error that the channel can't be tuned to, so I'd say thats better than crashing,burning/eating your cat or something much worse.


Regards
Ian Dobson

---

### Post by jakev383 on 2011-01-02
Thanks Ian. I went ahead and hid the channels I do not receive and stopped SD from sending data on them. I think I may look at what can be done for tuning to channels that do not exist, versus error'ing out on them.

---

