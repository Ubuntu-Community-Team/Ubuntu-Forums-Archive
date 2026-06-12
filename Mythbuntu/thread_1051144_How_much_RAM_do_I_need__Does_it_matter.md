---
title: "How much RAM do I need?  Does it matter?"
date: 2009-01-26
forum: Mythbuntu
---

### Post by Caps18 on 2009-01-26
I checked my system stats this weekend because I was bored, and found that it was using 890 MB out of the 1GB that is in the system.  And it wasn't recording or playing any video at the time.  I will need to check it again since I rebooted it since then to see if that made any difference.  But my linux laptop only uses 250MB out of 1.25GB until I start up Firefox.

Will I see any video performance improvements if I get 2GB of RAM?  Are other people using a similar amount, or is it only after running for a few weeks straight that it gets up that high?

---

### Post by movieman on 2009-01-26
Linux uses free RAM to cache disk files; what you need to look at is how much RAM the software is using rather than the cache. So long as you're not seeing much in the swap file you probably don't need more RAM.

Disk cache will provide some benefits to video, but not too much; for example, if you have 1GB of RAM and play a 2GB video file and then play it again, the beginning of the file will no longer be in the cache so it will have to be read from the disk.

---

### Post by ian dobson on 2009-01-26
Hi,

Linux uses all free memory as a disk cache which it'll give back to applications as soon as they need it.

My frontend only box seems to use about 350-450Mb ram max. The more ram you have, the more that can be used for cache (which would help for recording/commflagging/transcoding) but it wouldn't make a huge difference.

My big fully loaded backend (Quad Core,4 Tuners, 4Tb raid array) uses about 700-800Mb ram.

Regards
Ian Dobson

---

### Post by Caps18 on 2009-01-28
I looked into this again last night, and it looks like it is only using 460MB out of the 1GB max now.  So, something must have been happening in the background, or it needs to be restarted every two weeks or so to clear out the memory.

---

### Post by tgm4883 on 2009-01-28
> **Caps18 said:**
> I looked into this again last night, and it looks like it is only using 460MB out of the 1GB max now.  So, something must have been happening in the background, or it needs to be restarted every two weeks or so to clear out the memory.

I don't think you are understanding.  You don't want to "clear out the memory", you will get worse performance that way.

---

### Post by ian dobson on 2009-01-28
Hi,
 
What are you using to "see" how much memory is being used?
 
In the terminal if you use free, you'll see something like:-
[FONT="Fixedsys"] 
      total  used   free    shared buffers cached
Mem: 4055096 3925220 129876     0    92564 2791044
-/+ buffers/cache: 1041612 3013484
Swap: 0 0 0
[/FONT]
 
Only 12987Kb free,no. Almost 3Gb is being used as cache. Cache memory is memory not required by other processes and if another process needs more memory then part of the cache can be cleared and goven to the process.
 
Regards
Ian Dobson

---

### Post by Caps18 on 2009-01-29
You can look at they system stats right in the MythTV front end.

I'm not in front of it right now, but it is the option below MythWeather or MythWeb in the information menu option.

---

### Post by brian_hayward on 2009-01-29
> **movieman said:**
> Linux uses free RAM to cache disk files; what you need to look at is how much RAM the software is using rather than the cache. So long as you're not seeing much in the swap file you probably don't need more RAM.

Disk cache will provide some benefits to video, but not too much; for example, if you have 1GB of RAM and play a 2GB video file and then play it again, the beginning of the file will no longer be in the cache so it will have to be read from the disk.

I just built me a Mythbuntu box from an old Gateway Pentium III tower that i found.  I used the memory that came with it (about 384 MB if i remember correctly), and when i watch live tv the sound doesn't match the action on the screen.  Is this a product of the video capture card or is it a product of too little RAM?

---

### Post by tgm4883 on 2009-01-29
> **brian_hayward said:**
> I just built me a Mythbuntu box from an old Gateway Pentium III tower that i found.  I used the memory that came with it (about 384 MB if i remember correctly), and when i watch live tv the sound doesn't match the action on the screen.  Is this a product of the video capture card or is it a product of too little RAM?

What tuner do you have?

---

### Post by brian_hayward on 2009-01-29
> **tgm4883 said:**
> What tuner do you have?

Hauppauge WinTv

---

