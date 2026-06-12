---
title: "Mythbuntu will not set recordings"
date: 2010-06-06
forum: Mythbuntu
---

### Post by meanmrmustard on 2010-06-06
This is a new install of 8.10

I chose a number of programs to record, this time slot weekly and daily, this showing only, etc. doesn't seem to matter.
When I the looked at upcoming recordings and saw there were no recordings listed and a message telling me that I haven't chosen any shows to record.

What could cause this?

---

### Post by klc5555 on 2010-06-07
> **meanmrmustard said:**
> This is a new install of 8.10

I chose a number of programs to record, this time slot weekly and daily, this showing only, etc. doesn't seem to matter.
When I the looked at upcoming recordings and saw there were no recordings listed and a message telling me that I haven't chosen any shows to record.

What could cause this?

8.10? The first recording attempt after a new setup? Could be any of a whole host of reasons, including but not limited to: backend not running; mythtv-setup not completed or not configured correctly; your user name not added to the mythtv group; problems with mysql; a spot of mythconverg database corruption requiring a repair ... etc.

If making sure your mythtv-setup has been configured correctly and your user has been added to the mythtv group (which should happen first time after going into the backend setup from myth control center) and a soft restart doesn't fix it, it's time to check the logs and see what they're telling you.

---

### Post by LowSky on 2010-06-07
8.10? You should really use 9.10 or 10.04.

Anyway the issues can be nearly anything, like klc5555 said.

Is the back-end running?
Are you sure you configured your TV card properly?
Did you do a channel scan?
Can you watch LiveTV?
Do you have a listing of the shows your looking to record?
Is the time set correctly?

---

