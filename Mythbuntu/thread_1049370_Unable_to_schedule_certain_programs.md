---
title: "Unable to schedule certain programs"
date: 2009-01-24
forum: Mythbuntu
---

### Post by Torquewrench on 2009-01-24
I'm having difficulty scheduling certain programs. I am able to schedule shows such as 30 Rock, Grey's Anatomy, My Name is Earl, and a few others, but when I try to schedule Masterpiece Classic no matter what options I choose I cannot get it to show any recordings.

I'm running a separate frontend and backend with a single PVR-250 tuner. I am able to watch live tv on the channel where I want to record. Here is the backend log when I try to schedule the recording:

```
2009-01-26 10:33:24.093 Reschedule requested for id 46.
2009-01-26 10:33:24.152 Scheduled 9 items in 0.1 = 0.01 match + 0.05 place
2009-01-26 10:33:26.264 Reschedule requested for id 50.
2009-01-26 10:33:26.307 Scheduled 9 items in 0.0 = 0.01 match + 0.03 place
2009-01-26 10:33:28.455 Reschedule requested for id 49.
2009-01-26 10:33:28.497 Scheduled 9 items in 0.0 = 0.01 match + 0.03 place
2009-01-26 10:33:34.173 Reschedule requested for id 52.
2009-01-26 10:33:34.214 Scheduled 9 items in 0.0 = 0.01 match + 0.03 place
2009-01-26 10:33:37.450 Reschedule requested for id 53.
2009-01-26 10:33:37.490 Scheduled 9 items in 0.0 = 0.01 match + 0.03 place
2009-01-26 10:33:41.492 Reschedule requested for id 51.
2009-01-26 10:33:41.531 Scheduled 9 items in 0.0 = 0.01 match + 0.03 place
2009-01-26 10:34:34.271 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-26 10:35:38.583 Reschedule requested for id 54.
2009-01-26 10:35:38.625 Scheduled 9 items in 0.0 = 0.01 match + 0.03 place
```

The frontend log just shows XML UI parsing, no errors.

I'm not seeing any errors. The recording shows up in the "Set Priorities" area and it colored white, indicating it is not recording, while all others are colored yellow, indicating they will record. I can pump the priority up as high as I want and it doesn't change the recording status.

What gives???

Thanks for the help,

Phil

---

### Post by Torquewrench on 2009-01-29
any help here?

---

### Post by movieman on 2009-01-29
I've had that happen before, but I deleted the schedule in Mythweb and added it again and it worked.

---

