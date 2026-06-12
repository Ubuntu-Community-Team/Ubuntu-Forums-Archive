---
title: "Multiple backends - Upcoming Recordings problem"
date: 2011-04-04
forum: Mythbuntu
---

### Post by astrahle on 2011-04-04
Hey guys.
 
I've got an interesting problem that I hope someone brainy enough can help me with. I have a mythbuntu master backend running as a virtual machine (vm). It has no tuners. I also have another physical box which is both a master and a slave which has a tuner card in it. All subsequent slaves connect to the vm. Further, I have used NFS to ensure all data is recorded to the vm and that side all works fine - can playback recordings even when the physical backend is turned off. 
 
The idea for this design was so that the vm can wakeup the physical box only when required to record programs. Now I've configured wakeonlan and that works ok, the issue is that the Upcoming Recording list becomes blank when the physical box is shutdown. Hence, the vm will never wake the physical box because it doesn't know of any up coming recordings.
 
Can anyone advise how I might fix this?
 
Cheers,
 
Ashley Strahle

---

### Post by ian dobson on 2011-04-04
Hi,

I was under the impression that there should only be one master backend in a mythtv network, as the master backend is responsibe for scheduling all recordings/kicking the slave backends when they should start recording.

Regards
Ian Dobson

---

