---
title: "Hardware Decision/Multi-Core Question"
date: 2008-11-11
forum: Mythbuntu
---

### Post by rschapman on 2008-11-11
I'm still a little new to Linux in general but I'm wondering if anyone can answer this for me: When using a multi-core system can you manually dedicate a core to a certain type of process and/or can the system intelligently decide? If I am watching live tv will it use the other core for something like transcoding or commflagging? Thanks in advance.

---

### Post by IceBadger on 2008-11-12
The linux kernel does support multi-core processors.  I do not know if you can manually choose what processes run on what core, but when transcoding movies, I did notice that one core would be near maxed (presumably transcoding), while the other core was free for watching movies/etc.

---

### Post by ian dobson on 2008-11-12
Hi,

Linux supports multiple cores/cpu's without any problems. Although you can force a process to use on cpu/core it's better to let the linux kernel do that for itself.

Have a look here [http://www.linuxjournal.com/article/6799](http://www.linuxjournal.com/article/6799).

Regards
Ian Dobson

---

