---
title: "Scheduling overruns and recording conflicts"
date: 2009-10-13
forum: Mythbuntu
---

### Post by Crusty Juggler on 2009-10-13
For once I post in the Mythbuntu section without a problem.  This time it's a question/suggestion.

I'm sure everyone experiences TV stations messing with DVR users by starting shows late and running past the scheduled time.  One of my more common stations to record from starts prime time out about 5 mins late and ends up a good 15 or so.

Not a huge deal, but it is really irritating when something I want to record doesn't record due to conflict with the previous show running long.  Sure, it's my fault for scheduling things overlapping, but is there any way to configure Mythbuntu to start recording say, 2 minutes late if there is a 2 minute overlap rather than just not recording at all.

If there isn't, there should be!

---

### Post by gwagchunks on 2009-10-13
I thought that for DVB cards EIT data would update programme times if the program was running late or changed, maybe not, I'm not sure? [http://www.mythtv.org/wiki/EIT](http://www.mythtv.org/wiki/EIT)

---

### Post by SiHa on 2009-10-13
In my experience, Myth (or any other PVR I've used) isn't clever enough to know that a program has overrun. The schedules data tells Myth when a program is due to broadcast and when to record.  Generally if the first overruns, I just miss the end, and it's at the beginning of the next recording. BBC1 does this to me most Saturdays evenings.

With Freeview in the UK, there is something called "Accurate Recording" that allows the receiver to adjust times according to stop & start signals broadcast, but I don't think Myth Supports this.

Do you find that this happens with **all** recordings due to record back to back? How many tuners do you have? Are you sure it's not your setup adding a default couple of minutes to the end of the recording that screws up the next one?

@gwagchunks: EIT may show schedule changes, but it doesn't update frequently enough to cater for a 2-minute overrun.

---

