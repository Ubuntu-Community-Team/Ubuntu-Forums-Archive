---
title: "MthTV Wakealarm &amp; Schedules"
date: 2010-02-05
forum: Mythbuntu
---

### Post by tobiz on 2010-02-05
I'm getting my mythbuntu 8.10 system to work with wakealarm as per [http://www.mythtv.org/wiki/ACPI_Wakeup]("http://www.mythtv.org/wiki/ACPI_Wakeup") and have got as far as testing it wakes up after 5 mins - it does! Question is does ACPI_Wakeup only affect recording schedules or are other mythtv schedule activities such as advert flagging and transcoding also included?

---

### Post by Roebi on 2010-02-05
Hello,


Mythwelcome will check if you have specific MythTV tasks running, and will postpone shutdown until they are finished.
For instance, if you have several transcode jobs launched, one will be running and the other ones will be queued.
MythTV will finish the running job and shutdown, and will start the queud jobs once it is running again.

Whereas I am not sure that comflagging and trascode jobs can be scheduled, I do not believe it is necessary to schedule them. Either they run during of just after the recording, or you run them manually. In both cases MythWelcome will postpone shutdown until a job is completely finished.

I hope this is helpful.

Roebi

---

### Post by tobiz on 2010-02-08
> **Roebi said:**
> Hello,


Mythwelcome will check if you have specific MythTV tasks running, and will postpone shutdown until they are finished.
For instance, if you have several transcode jobs launched, one will be running and the other ones will be queued.
MythTV will finish the running job and shutdown, and will start the queud jobs once it is running again.

Whereas I am not sure that comflagging and trascode jobs can be scheduled, I do not believe it is necessary to schedule them. Either they run during of just after the recording, or you run them manually. In both cases MythWelcome will postpone shutdown until a job is completely finished.

I hope this is helpful.

Roebi

Roebi, thanks for the info. BTW if you look at MythTV Backend Setup you'll see it is possible to set start and end times for Job Queue processing.

---

### Post by tobiz on 2010-03-29
> **tobiz said:**
> Roebi, thanks for the info. BTW if you look at MythTV Backend Setup you'll see it is possible to set start and end times for Job Queue processing.
I now have wakealarm working without any problems, it's almost like magic!  I need to adjust the shutdown time for no user logged in (currently set at 90s) to give slightly more time to log in, I run a backend and front end on the same server.

---

### Post by AKADAP on 2010-03-29
> **tobiz said:**
> I now have wakealarm working without any problems, it's almost like magic!  I need to adjust the shutdown time for no user logged in (currently set at 90s) to give slightly more time to log in, I run a backend and front end on the same server.

That is one of the values you set in the backend setup. Should be on the same page as everything else.

---

