---
title: "daily-live ubi-migrationassistant failed - code 141"
date: 2010-11-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-11-21
This "ubi-migrationassistant failed with exit code 141" error has been around for several  testing releases.

I checked previous ones (Lucid) and used the recommended  ```
ubiquity --no-migration-assistant
``` from a command line.

That worked. The problem was getting to a gtk for ubiquity to work.

What I needed to do was open a VT terminal and restart gdm just to get a desktop. I was missing window decorations and compiz crashed.

I know that some have success with using the live installed
(debian). I was wondering if anyone has experienced the exit code141 error using daily-live.

I couldn't find a bug report on natty, as it may pertain just to my setup. I have a nvidia Geforce 6150SE nForce 430 video chip.

---

### Post by muchmusic on 2010-11-21
This occurred in a vmware vm with today's live cd for me. I think that logging a bug would be good since it isn't unique to your setup.

---

### Post by rtalcott on 2010-11-21
Have the same problem with virtual Box.
rt

---

### Post by VMC on 2010-11-21
Thanks for the confirmation. I think I will wait until alpha1, then file a bug report. Maybe by then ubiquity will be updated. Its way early in the testing cycle.

---

### Post by kansasnoob on 2010-11-21
> **VMC said:**
> Thanks for the confirmation. I think I will wait until alpha1, then file a bug report. Maybe by then ubiquity will be updated. Its way early in the testing cycle.

Yeah, this early "stuff" is bound to happen.

I'm battling problems with desktop changes that don't like my custom desktop prefs.

This is going to be a really interesting change :D

Many challenges no doubt.

I've been paying more attention to USC and I'm honestly having trouble finding fault. Once they drop Synaptic I do wonder how we'll easily view changelogs, but I'm guessing it'll be figured out.

I actually like the "BIG" changes. It makes life fun.

---

