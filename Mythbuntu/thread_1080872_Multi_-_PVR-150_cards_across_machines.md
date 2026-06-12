---
title: "Multi - PVR-150 cards across machines"
date: 2009-02-25
forum: Mythbuntu
---

### Post by rodercot on 2009-02-25
Hey All,

 I just want to verify a question before I start. I picked up another PVR-150 today that I want to install in addition to the one already in my master backend and serve it another source. I also have a third PVR-150 in the secondary machine that has it's own rcvr but shares the same source already connected to the one pvr-150 currently in the master. 

So, I have express vu with two rcvrs one on the master and it's pvr150 and one on the secondary hooked to a 2nd pvr150. I am hoping I can add the third card to the master and add a new source (different) to it with it's own channel line up 

 Is this possible and do I have to modify my schedules direct account for tis or creat a new one for the new guide info. 
 How will this new source be accessed from the main menu. will I have two watch TV's or in some other manner. 

 I hope it make a little sense.

 thanks,

 Dave

---

### Post by klc5555 on 2009-02-26
> **rodercot said:**
> Hey All,

 I just want to verify a question before I start. I picked up another PVR-150 today that I want to install in addition to the one already in my master backend and serve it another source. I also have a third PVR-150 in the secondary machine that has it's own rcvr but shares the same source already connected to the one pvr-150 currently in the master. 

So, I have express vu with two rcvrs one on the master and it's pvr150 and one on the secondary hooked to a 2nd pvr150. I am hoping I can add the third card to the master and add a new source (different) to it with it's own channel line up 

 Is this possible and do I have to modify my schedules direct account for tis or creat a new one for the new guide info. 
 How will this new source be accessed from the main menu. will I have two watch TV's or in some other manner. 

 I hope it make a little sense.

 thanks,

 Dave

After the new 150 is installed wherever it's to be installed, if it needs to see and tune a different channel lineup than other tuner cards do, set up a new "Video Source" for it in the backend setup. The SchedulesDirect grabber needs to be indicated in this new Video Source, but the SchedulesDirect account does not to be modified, unless you wish to download schedules for different channels than you currently download.

In "Input Connections", name this new card's tuner anything you want, and connect it to your new Video Source. Have the card scan, to find channels under this new "Video Source". In the "Channel Editor" you may edit/delete channels for each individual "Video Source". Edit/delete until you have the preferred lineup set up for your new Video Source.

After mythfilldatabase runs and the backend(s) is/are restarted, the new Video Source on its new 150 tuner with its own specific lineup will be accessible from the "m" key menu under "change input" as are all the other tuners.

Cheers! :)

---

