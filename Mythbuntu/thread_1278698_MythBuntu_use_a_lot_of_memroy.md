---
title: "MythBuntu use a lot of memroy"
date: 2009-09-29
forum: Mythbuntu
---

### Post by Ironroot on 2009-09-29
Hi all
I just set up a new mythbuntu box and have noticed that for some reason it use up a lot of ram memory when I am watching movie from my network storage machine.
I have a server on my network that holds a lot of videos and I am sharing that across my whole network using samba( I have some window machines I need to share it with too) and after a couple hours of watching movies my mythbuntu box has gone 1.6 gigs of ram. This seems odd to me and I am wonder what could be causing it.

Thanks

---

### Post by ian dobson on 2009-09-30
Hi,

On linux unused ram is wasted ram. Linux tries to cache as much data as possible rather than reading if from the disk.

Here's what I mean:-

```
root@alpha2:~#  free
             total       used       free     shared    buffers     cached
Mem:       8082976    7911612     171364          0     108512    6555740
-/+ buffers/cache:    1247360    6835616
Swap:            0          0          0
```

If an application needs memory then it can be quickly taken from the cache and given to the app.

Regards
Ian Dobson

---

### Post by sabre2th on 2009-09-30
At any given time, my box shows 2 out of 2 gigs of RAM used, and 10-50 megs of swap used.  Those numbers never really change and performance is great.

> On linux unused ram is wasted ram.
^ that

---

### Post by Ironroot on 2009-09-30
Ok thanks all that makes me feel better.

---

