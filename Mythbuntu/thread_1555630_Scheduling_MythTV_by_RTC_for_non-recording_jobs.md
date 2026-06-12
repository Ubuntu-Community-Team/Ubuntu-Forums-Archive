---
title: "Scheduling MythTV by RTC for non-recording jobs"
date: 2010-08-18
forum: Mythbuntu
---

### Post by tobiz on 2010-08-18
Is it possible to setup Mythbuntu so that it is 'woken up' by the BIOS RTC for jobs other than recording jobs?  I've set my Mythbuntu system to be woken up by the BIOS RTC to record programmes but I'd also like it to be woken up to do the transcoding/ad removal jobs which would then be run over-night.

---

### Post by LowSky on 2010-08-18
why not transcode while recoding? you can set a computer to wake up whemever you like but why waste electricity if you  can do things all at once. Just enable Myth to run more than one process at a time, and increase the amount of CPU it is allowed to use for jobs.

---

### Post by tobiz on 2010-08-18
> **LowSky said:**
> why not transcode while recoding? you can set a computer to wake up whemever you like but why waste electricity if you  can do things all at once. Just enable Myth to run more than one process at a time, and increase the amount of CPU it is allowed to use for jobs.

Yes I had thought of that one but when it's recording and playing back TV plus perhaps playing back via mythweb the CPU utilisation gets a bit heavy, especially when playing back HDTV. Thanks for the suggestion, I'll try and see how it goes.

---

### Post by AKADAP on 2010-08-18
> **tobiz said:**
> Is it possible to setup Mythbuntu so that it is 'woken up' by the BIOS RTC for jobs other than recording jobs?  I've set my Mythbuntu system to be woken up by the BIOS RTC to record programmes but I'd also like it to be woken up to do the transcoding/ad removal jobs which would then be run over-night.

The short answer is "yes it is possible". But you will have to write your own scripts to do it.

This wiki describes how to do it, but the script was intended for late night system backups, so it needs to be modified for your purposes.
[http://www.mythtv.org/wiki/Using_ACPI_%26_MythTV_to_run_other_applications](http://www.mythtv.org/wiki/Using_ACPI_%26_MythTV_to_run_other_applications)

---

### Post by alien878 on 2010-08-20
A couple of thoughts:

You could set the idle timeout long enough so that the transcodings start.  Mythwelcome won't shutdown the box while it is transcoding.

You could also set a daily wakeup that is long enough to do the transcodings.  However, it will go on even if there are no transcoding jobs scheduled.

---

