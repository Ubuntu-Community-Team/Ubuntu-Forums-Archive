---
title: "Recording problem when frontend is shut down"
date: 2009-11-27
forum: Mythbuntu
---

### Post by Senkoboy on 2009-11-27
I am running Unbuntu 8.10 Intrepid, with Myth 0.21, frontend and backend on the same box.  I have a PVR-150 for analog and a ATI HDTV Wonder for OTA digital.  When I program a recording with Manual Schedule I can shut down the frontend and it will still record.  If I program a recording with the Program Guide, it will  show up on upcoming recordings, but it won't record if I shut down the frontend. If I leave the frontend running everything works fine. This is with the ATI card, I don't have Schedules Direct so the only thing in my Program Guide is what I can pick with the ETI. Can't test the PVR-150 with the Program guide, but it works with Manual Schedule.
Why do I have the keep the frontend running to make this work?

Thanks, Mike.

---

### Post by Senkoboy on 2009-11-30
Can I open a database to see is the recording is getting written there?

---

### Post by azmyth on 2009-11-30
You can check the db using something like phpmyadmin would be the easiest. You don't need the FE running. The show could've moved or the time change. Watch some live TV and then bring up the guide and schedule the next show to record, exit the FE and see what happens.

---

### Post by Senkoboy on 2009-11-30
> **azmyth said:**
> You can check the db using something like phpmyadmin would be the easiest. You don't need the FE running. 


I did another test tonight and it worked. I don't know what happened the last time I tried it, as I tried it several times.
I did start and stop the frontend a couple of times, this time,  before I shut it off.  

I will look into the phpmyadmin.

Thanks, Mike....

---

