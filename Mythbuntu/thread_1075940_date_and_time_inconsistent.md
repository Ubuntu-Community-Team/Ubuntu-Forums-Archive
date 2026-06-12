---
title: "date and time inconsistent"
date: 2009-02-20
forum: Mythbuntu
---

### Post by ctucker10 on 2009-02-20
Over the past several weeks my mythbox has been "forgetting" the correct time. In the past week this has happened at least three times.

Using Synaptic I have reinstalled ntp and ntpdate. I have also made sure the service was running.

During startup I went into the bios and checked the hardware clock. It was not correct. I set it to GMT/UTC, saved the settings, then continued with startup.

In System>Time and Date I switched to manual, set the correct time, then switched back to automatic sync mode. From there I set the correct time zone, America/New York, and everything looked good. Less than 24 hours later, my machine lost track of time...again.

Any suggestions?

---

### Post by Mister.Vash on 2009-02-21
How far off is it getting?  Is it something where everything is changing, for example the time is off by 26 hours and 48 minutes, or is it just that the hours are changing and the minutes are remaining the same?

If everything is changing, you might look at getting a replacement battery for your motherboard

If it's just the hours that are changing, then maybe your o/s is set to utc=no in /etc/default/rcS

---

### Post by ctucker10 on 2009-02-21
I should have mentioned that in my original post...Everything is changing.

My hardware has been in service for about 5 years. I'm going to replace the motherboard battery. I'll post my results. Thanks.

---

### Post by ctucker10 on 2009-02-21
I intalled the new motheboard battery this afternoon. Now only time will tell. (Please forgive the pun, I couldn't help it).

---

