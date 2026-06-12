---
title: "Frontend hangs on &quot;Watch TV&quot; - recorded programs OK"
date: 2011-01-19
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2011-01-19
Returned from 3 weeks away, and discovered (1) Winegard powered antenna (an older version of the GS-2200) was severely degraded, and replaced it; and (2) can no longer watch television using "Watch TV" (Live TV).

I can, however, record shows and watch as they are recorded.

Both frontends (one on the same computer as the backend and one remote) exhibit the same behavior.  They freeze/hang at the "please wait…" interim screen and the frontends become unresponsive and have to be killed with a SIGTERM.

Nothing seems amiss in the frontend or backend logs.

Live TV works fine on Windows Media Center.

Ubuntu 10.10, mythtv fixes/0.24 (v0.24-112-g40df4b6), Hauppage 2250, nvidia GT240.

I could use some suggestions for debugging or fixing this annoyance.   Thanks...

---

### Post by keepitsimpleengr on 2011-05-27
Bad amplifier is Wingard powered antenna.

Replaced antenna, all's well.

---

