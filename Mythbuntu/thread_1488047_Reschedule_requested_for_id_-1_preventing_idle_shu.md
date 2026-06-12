---
title: "Reschedule requested for id -1 preventing idle shutdown"
date: 2010-05-19
forum: Mythbuntu
---

### Post by scary_jeff on 2010-05-19
Hi

I had a search around for this and didn't find anyone with a similar issue. I have set up mythshutdown for automatic shutting down of the backend when idle. It has worked a couple of times, but normally the machine stays up even with no clients connected. I had a look at the backend log, and it goes like this:

```
2010-05-19 21:11:27.315 Scheduled 0 items in 0.0 = 0.00 match + 0.03 place
2010-05-19 21:11:28.316 I'm idle now... shutdown will occur in 1200 seconds.
2010-05-19 21:15:28.161 Reschedule requested for id -1.
2010-05-19 21:15:28.193 Scheduled 0 items in 0.0 = 0.00 match + 0.03 place
2010-05-19 21:15:29.194 I'm idle now... shutdown will occur in 1200 seconds.
2010-05-19 21:17:01.779 MainServer::ANN Monitor
2010-05-19 21:17:01.779 adding: scaz as a client (events: 0)
2010-05-19 21:20:34.154 Reschedule requested for id -1.
2010-05-19 21:20:34.189 Scheduled 0 items in 0.0 = 0.00 match + 0.03 place
2010-05-19 21:20:35.190 I'm idle now... shutdown will occur in 1200 seconds.
```

This repeats for hours on end. It seems to say it is adding a client on the local machine (scaz), but no client is running here. I do have mythweb set up, but apache access logs show no accesses in the relevant time periods.

I have deleted all recording schedules and have no upcoming recordings. What is it doing rescheduling 0 items over and over?

Versions are 10.04/0.23. Any ideas or things to try would be greatly appreciated.

Cheers

---

### Post by Neon Dusk on 2010-05-19
If you're using active EIT than 1200 secs for the idle timeout is too long (think it needs to be under 5 mins). 

If your using Freeview in the UK then you can disable active EIT (the epg will get updated when a recording is taking place)

---

### Post by scary_jeff on 2010-05-26
Thanks for the reply and sorry for the delay in getting back. Yes I am a freeview viewer in the UK. I had a look in the backend setup, and there were a couple of options to do with EIT scanning in the 'General' category. From memory, these were something like 'scan timeout before moving to next channel' and 'time to wait after recording finishes before starting EIT scan'. I set both of these options much higher, and the machine has now managed to idle shut-down.

I will come back again if changing this option prevents the EIT from updating.

Cheers

---

