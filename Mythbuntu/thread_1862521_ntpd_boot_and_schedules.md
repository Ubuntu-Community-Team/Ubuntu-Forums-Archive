---
title: "ntpd boot and schedules"
date: 2011-10-16
forum: Mythbuntu
---

### Post by jonnybignote on 2011-10-16
Hey all

I've followed the instructions for ACPI wakeup and it is working.  However, it often takes up to 4 minutes for the machine to make all the incremental clock changes to become current, and as that affects recordings, I have to have it start up unnecessarily early to prevent missing the start of recordings or other timed events.  I'm guessing that there is a one shot sync event maybe handled via NTP but it happens too early to get network access or something??.  As I said, ntpd is working, but I don't want the system clock to be off by 7 hours or so for so long after booting or resuming - anyone have any advice?

thanks

---

### Post by nickrout on 2011-10-16
> **jonnybignote said:**
> Hey all

I've followed the instructions for ACPI wakeup and it is working.  However, it often takes up to 4 minutes for the machine to make all the incremental clock changes to become current, and as that affects recordings, I have to have it start up unnecessarily early to prevent missing the start of recordings or other timed events.  I'm guessing that there is a one shot sync event maybe handled via NTP but it happens too early to get network access or something??.  As I said, ntpd is working, but I don't want the system clock to be off by 7 hours or so for so long after booting or resuming - anyone have any advice?

thanks

It should be right on reboot, certainly not out by 7 hours!

Is your motherboard battery flat?

---

### Post by jonnybignote on 2011-10-16
I think the issue for me is more the type of clock that the motherboard uses

UTC vs RTC - I can't remember which but my motherboard is on a different time than system - it was something I had to configure when sorting the ACPI wakeup stuff.

---

### Post by nickrout on 2011-10-17
That will not put your clock out by 7 hours when you boot up. You have something wrong.

What is yout timezone set as?

---

### Post by jonnybignote on 2011-10-17
I have it set correctly for my location.  PST.  

I suppose then, that the motherboard battery could be to blame - I just don't remember this being an issue on my previous install (9.10) so I was assuming some kind of config problem with 10.04 ..thanks for the help

---

