---
title: "How to turn off automatic recording?"
date: 2007-11-24
forum: Mythbuntu
---

### Post by Benthe1st on 2007-11-24
Hi!

I would like to turn off automatic recording (what mytht starts every time to make the program reviewable) in mythtv because i don't have much space on my hard-drive and i don't want to manually delete  the recordings every time. How can i do that?

---

### Post by roseway on 2007-11-24
Automatic recording is necessary to support features like pause and skipback. These temporary recordings are automatically deleted after a period of time, and I think they are automatically deleted if a new recording needs the disk space.

---

### Post by Benthe1st on 2007-11-24
Yes i know, but i don't want to use them either. and i don't want to fill my hard disk with temporary recordings.

---

### Post by ubnewbie2 on 2007-11-24
> **Benthe1st said:**
> Yes i know, but i don't want to use them either. and i don't want to fill my hard disk with temporary recordings.

This is just the way it is written.  I don't see how you could turn it off without rewriting the code.  In older versions, it was written to a ringbuffer or something, and I remember when they changed to the current system and all the discussion about it.

Short answer, there is a setting to reserve any desired amount of space on you hard disk that myth won't use.  Either do this, or put the myth recordings on a separate hard disk or partition.

You definitely don't need to worry about the live TV recordings as far as myth is concerned.  They will be reused when space is required.

---

