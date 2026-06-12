---
title: "Shutdown Frontend 'Gracefully' from script ?"
date: 2008-11-26
forum: Mythbuntu
---

### Post by SiHa on 2008-11-26
I'm starting to play with ACPI and shutdown / wakeup. Essentially I want the machine to only shutdown at night, and wake up again at 07:00. I don't really want to use Mythwelcome, as that's just an added complication to dent the already perilously low WAF.

As I understand it, a BE/FE will not autoshutdown whilst the frontend is running (don't think it cares about remote ones?)

I've noticed once or twice, that when a remote frotend has been stopped via 'killall' and it's watching liveTV, that the backend keeps recording.

So, I'd like to write a little script to put in my crontab to shutdown the FE at a set time (22:55, say), but do it gracefully to ensure the backend knows to stop recording if it's been left in Live TV. My pre-shutdown script will only exit with '0' (and allow shutdown to continue) if the time is 23:00 or later.

Oh, and if someone knows how I can pop-up a little prompt in the Frontend window that says 'I'm going to shutdown - cancel?' that would be really great too.

Any help much appreciated...

---

