---
title: "Sound went dead after update"
date: 2009-07-02
forum: Mythbuntu
---

### Post by cleatus99 on 2009-07-02
Linux mythtv 2.6.27-14-generic #1 SMP Tue Jun 30 19:54:46 UTC 2009 x86_64 GNU/Linux

my audio is 00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

it was running fine, now when I run alsamixer is only has Card: Conexant CX8801

---

### Post by Damanther on 2009-07-03
Does anything show up with either

aplay -l

or

asoundconf -list

??

Have you checked your syslog to see if any other sound devices are detected?

---

### Post by Andrew U.K. on 2009-07-05
Having the same problem as you, I have been running myhbuntu 8.04


With no sound after fresh installation I uninstalled mythbutu9.04 and installed ubuntu 9.04 which had sound. I then went to the repositories to install mythtv and myth control center. After restart I had no sound in either ubuntu 9.04 desktop or mythtv.

I have tried 64bit and 32bit versions of mytbuntu 9.04.

The sound card shows up with aplay -l and it is the correct and only sound card, I have also tried the on board sound card but with no joy either.
 
So I figure it's myth changing a sound setting, rather than a problem with the ubuntu kernel.

A week of frustration so far....

Good luck

p.s.
(loaded 8.04 back on to use while I try to figure out the problem and can't get epg back up)

---

