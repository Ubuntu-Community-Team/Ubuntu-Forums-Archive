---
title: "myth 0.26 not calling pre-shutdown"
date: 2012-10-18
forum: Mythbuntu
---

### Post by abecrab on 2012-10-18
Mythtv has stopped calling the pre-shutdown shellscript and shutting down.

I've lengthened the EIT interval beyond the maximum idle time before shutdown  to various much longer values.

I do still see these every few minutes:

Oct 18 22:11:03 abe-desktop mythlogserver: mythbackend[3212]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner

Is this a bug?

Anyone else having the problem.

---

### Post by Lester_Burnham on 2012-10-20
> **abecrab said:**
> Mythtv has stopped calling the pre-shutdown shellscript and shutting down.

I've lengthened the EIT interval beyond the maximum idle time before shutdown  to various much longer values.

I do still see these every few minutes:

Oct 18 22:11:03 abe-desktop mythlogserver: mythbackend[3212]: I Scheduler scheduler.cpp:2126 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner

Is this a bug?

Anyone else having the problem.

Hi,

Have you tried shortening the idle time to less than 300 secs.
This used to work for me.

Lester

---

### Post by abecrab on 2012-10-20
I did yes - I'd set it to 120 seconds.

Yes I'd had that impression in the past and I've always used 120 seconds.

I'm really flummoxed.

---

