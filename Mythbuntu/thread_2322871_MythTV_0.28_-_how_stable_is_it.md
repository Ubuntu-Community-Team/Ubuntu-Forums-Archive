---
title: "MythTV 0.28 - how stable is it?"
date: 2016-05-01
forum: Mythbuntu
---

### Post by nmw01223 on 2016-05-01
I'm currently running 14.04.4 LTS + 0.27.6. It's a pretty reliable system with one drawback - DVB/T2 (I'm on UK Freeview) is not supported for tuners with Si2168 frontend chips (as the PCTV 292e has, and I have two). The consequence is no HD TV from those tuners, since all the UK Freeview HD channels are on multiplexes using the DVB/T2 delivery system. This is reputedly correctly handled in 0.28.

Just saw 2 weeks ago or so that the current stable release of MythTV is 0.28.

Just ran a dist-upgrade and nothing changed from 0.27.6. Went into MythBuntu control centre to change the repository from 0.27 to 0.28, and noted that it still says 0.28 is development only, need to enter a development password etc.

Then I looked at some of the threads here with people trying to upgrade from 0.27 to 0.28 with mixed success, and I'm wondering if a change is a good move at this time.

So my question really is - how robust is 0.28? I do also have an HDHomeRun dual tuner which does handle DVB/T2, so the lack of DVB/T2 and thus HD on the 292e tuners is not disastrous, but I'd like to upgrade if I can as it means all four tuners can handle the same channel set. But, I don't want to KO the system in the process, I use it a lot.

What would be people's advice? Leave it for a bit, or plunge in?

---

### Post by JamesNorris on 2016-05-01
The developer password is actually given there in the MCC screen, so don't worry about that. 
In all honesty, I have very few problems with 0.28. It's been rock solid beyond occasionally locking up when streams/videos end, but I'm not sure if this is my system specifically... 

Can't help with the Si2168 issue, though it might be useful to know that I'm having trouble with HD streams on my PCTV 290, which, apparently, is supported. This isn't necessarily an issue with Myth, however.

---

### Post by nmw01223 on 2016-05-02
Thanks for your reply. The lockups you report are a concern! I see nothing like that with 0.27.

The 290e was always OK for DVB/T2. It is just the newer devices that are a problem because a 'fix' put into the driver was not propagated to Si2168 using devices as the developer felt that apps should have caught up by now, and MythTv were not using the later DVB V5 driver interface which is the real solution. That is what is reputedly done in 0.28. Cannot get 290e tuners now.

However, I think it may be a bit early for me and 0.28. Reliability is paramount.

---

### Post by Bucky Ball on 2016-05-02
If you're up to it you could run 16.04 LTS as a virtual machine using Virtualbox and see if Myth available there comes with that version by default. Or boot 16.04 LTS from live media and 'Try Ubuntu', get to a desktop and check in Software Centre what is available there.

---

