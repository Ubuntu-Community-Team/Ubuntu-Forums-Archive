---
title: "No recordings available or screen loading on desktop frontend"
date: 2011-09-24
forum: Mythbuntu
---

### Post by vagster on 2011-09-24
Hi there,

I have a MythBuntu system running on Lucid with mythtv 0.24.1-85-ge16613a. I have a combined backend and frontend and a separate desktop frontend ("bigtv")for my TV. Both machines are up-to-date.

Since updating using the standard MythBuntu updates on Thursday, when I go to the Watch Recordings screen on the bigtv frontend, I get the message "No recordings available, or screen loading...". I have left this for several hours but don't see any changes. 

If I look on the combined frontend/backend, I see all the recordings. Also, using the iPhone App or MythWeb, I can see all the recordings too.

Back to the bigtv frontend, I can watch videos and see listings/upcoming recordings etc which suggests that I can access the database.

The frontend log gives this message:

2011-09-24 20:39:45.000 PlaybackBox Error: SortedList is Empty
2011-09-24 20:39:45.081 PlaybackBox Error: SortedList is Empty

I don't seem to get any errors on the backend at the same time.

Any ideas what to start looking at would be much appreciated.

Thanks very much

Stephen

---

### Post by nickrout on 2011-09-26
On the misbehaving frontend, have you selected a recording group that has nothing in it?

---

### Post by vagster on 2011-09-26
I did check the recording groups and everything looked good. Since then, I noticed a large time lag between the backend and secondary frontend last night. Rebooted the backend today to just the sad noise of a fan whirring. I believe the motherboard has died and this was probably causing problems as it went out.

New box time.

Thanks for the help.

Stephen

---

