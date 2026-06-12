---
title: "myth memory usage: does it get released?"
date: 2011-10-07
forum: Mythbuntu
---

### Post by dibuntux on 2011-10-07
Following previous threads and noticing that on heavy usage the system get slow, I monitored it using top. During 3 recs and 1 playback (all SD content), I got this situation:
15784 k free on 2 GB of RAM, 23632 buffers 1483816 k cached 0 k swap used. Soon after, the system started to use swap.

So, I had some DIMMs laying around and put'em in. Now on 4 GB the system was performing better, memory wise, on the same load.
I guessed. Then this morning, after there was just one recording going on, I found the system idle, CPU at 2,4%, with 169364 k free, 156688 k buffers and 3115468 k cached, 0 k swap.

So, no matter what, myth ends up eating all the system RAM?

I have the latest PPA applied and running Transmission torrent client all the time.

Any ideas? Is it normal? TIA



Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen X 2
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by ajgreeny on 2011-10-07
It is much easier to see memory usage with ```
free -m
``` than using top, in my opinion, though I accept it is not as easy to continuously monitor it as top does.

However, don't forget that in general, linux does not release memory until it is needed, so the figure you really need is more easily seen from the **free -m** output in the line ```
-/+ buffers/cache:        ###       ####
``` where the first figure is the memory being actively used by running applications, and the second figure is the memory available, but not necessarily free at the current moment.

Linux works on the idea that empty memory is wasted memory, so why empty it if it is not really needed for something new.  I really don't think you have a problem here, but would prefer the **free -m** output before I make a final judgement.

---

### Post by LowSky on 2011-10-07
Its your processor that is the bottle neck, not MythTV eating your RAM like Candy.

Stop torrenting, it is what is causing high I/O cycles, mixed with MythTV transcoding is causing the system to slow down.

Or go out buy a 4-6 core processor and do everything at once without a slow down.

---

### Post by dibuntux on 2011-10-07
Thanks all for the replies. I will try free -m - but your explanation of memory use is satisfying enough. Still, with only 2 GB the system was paging; hopefully now with 4 GB it will not.

As for the CPU, it is a dual core at 2500 MHz... should be enough. Also top listed 17% use when I had the problem, so I do not think it is the case.

---

### Post by nickrout on 2011-10-07
if you want a low memory/cpu torrent client, use rtorrent.

---

