---
title: "OS hangs while using Mythtv"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by pulpinator on 2007-03-29
I'm pretty new at this. I'm not looking for a silver bullet, but more of pointers of where I can go look.

I installed Mythtv on Edgy, and everything is working (after figuring out some problems with lirc). Twice in the last 4 days I've had a disturbing issue: mythtv will be recording a program in the background while I'm watching LiveTV on the second tuner. Then I hit a few remote buttons (the second time was actually some keyboard buttons), and kaplam! The whole system hangs.

No Alt-F4, no Alt-Tab, no hard drive activity LED anymore. Reboot button is the only thing that "fixes" it.

So, where do I start to look (log files, etc)? :confused:

---

### Post by majoridiot on 2007-03-30
first, see if anything is obvious in the mythbackend log: /var/log/mythtv/mythbackend.log

then, check the rest of the system logs in /var/log  -- the most recent have no suffix, older logs
are tagged .0 .1 .2, etc.

---

### Post by PhilJess on 2007-04-01
The symptoms sound like some sort of mysql problem. Look through your mythbackend logs for messages about corrupt tables.

---

