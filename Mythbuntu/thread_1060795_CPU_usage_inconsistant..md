---
title: "CPU usage inconsistant."
date: 2009-02-05
forum: Mythbuntu
---

### Post by Austin_KW on 2009-02-05
As an experiment,I have installed mythbuntu on an old laptop (Celeron 2.8Ghz, 750MB ram) with a nova-t usb dvb card. It runs as back and front ends.

Everything works fine. I can simultaneously record a a couple  of programs from a multiplex and watch another recording with CPU cycles to spare.

Then at other times the CPU usage will spike while just watching a recording or live TV. Both the backend and mysql will start consuming CPU cycles and the playback will stutter.

Any ideas why the CPU usage changes?

---

### Post by ajgreeny on 2009-02-05
Perhaps the system is doing an update of the file database, or something similar, which can take a chunk of cpu activity, if I remember correctly.

---

### Post by newlinux on 2009-02-05
commercial flagging can also eat up CPU - but you can control with commflag jobs run. What type of GPU do you have? Does this happen  consistently with any particular channels or type of programming (like HD)?

---

### Post by Austin_KW on 2009-02-05
Should have mentioned that I disabled the commercial flaging job. The 2.8 Ghz celeron is basically a P4 with a smaller cache.

It seems to happen after I have used pause, ffw and rew. But that may just be coincidence (normal use). All programs are SD (uk terrestial dvb). The decode & playback can use 20-50% of my cpu. The problems are when the backend and mysql start taking the other 50%.

At other times it will happily record and playback another with 70% idle. I dont understand why I suddenly run out of this headroom.

---

### Post by newlinux on 2009-02-05
> **Austin_KW said:**
> Should have mentioned that I disabled the commercial flaging job. The 2.8 Ghz celeron is basically a P4 with a smaller cache.

It seems to happen after I have used pause, ffw and rew. But that may just be coincidence (normal use). All programs are SD (uk terrestial dvb). The decode & playback can use 20-50% of my cpu. The problems are when the backend and mysql start taking the other 50%.

At other times it will happily record and playback another with 70% idle. I dont understand why I suddenly run out of this headroom.

By GPU I mean Graphics processing unit -- your video card. But it doesn't seem to be your playback (although I've seen this problem often with playback and playback profile settings). 

Mysql & mythbackend definitely shouldn't be taking up this much cpu usage, especially without commflagging. Take a look at your backend logs around the times you have the issues. Could be a file I/O issue as well if it happens after ff and rews... Mysql keeps positional information for the video to help keep audio in sync, so I guess this could cause more usage of mysql too...

---

