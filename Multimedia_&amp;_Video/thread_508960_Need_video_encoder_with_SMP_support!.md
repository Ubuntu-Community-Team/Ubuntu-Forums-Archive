---
title: "Need video encoder with SMP support!"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by Donshyoku on 2007-07-24
The only reason (besides a rousing round of CnC3) for me to boot into my Windows partition is that I can't find a good encoder for my Zen Vision. I can encode just fine with mencoder, but it prevents me from using both cores. I do a lot of encoding work for my player daily and it would be much more efficient if I could use both cores and cut down on the times especially with bigger files. Is there a program (preferably with a front-end, if not, that is OK too) that will let me encode MPEG-2 or Xvid/AVIs using both cores of my Pentium D or is that a lost cause?

TIA, all!

---

### Post by sonofusion82 on 2007-07-25
i am not aware of any FOSS multi-threaded video encoder.
for me, if i have 2 or more files to encode. I'll create 2 shell scripts to execute mencoder on two instances of terminal window. that way, it keeps both cores fully occupied 100%.... even better than some multi-threaded encoders in windows as they are sometimes limited by some other factors like thread synchronization if the algorithms are not well designed for multi-threading.

---

### Post by Major_Kong on 2007-07-25
> **Donshyoku said:**
> The only reason (besides a rousing round of CnC3) for me to boot into my Windows partition is that I can't find a good encoder for my Zen Vision. I can encode just fine with mencoder, but it prevents me from using both cores. I do a lot of encoding work for my player daily and it would be much more efficient if I could use both cores and cut down on the times especially with bigger files. Is there a program (preferably with a front-end, if not, that is OK too) that will let me encode MPEG-2 or Xvid/AVIs using both cores of my Pentium D or is that a lost cause?

TIA, all!

The threads=auto option doesn't exist when encoding to MPEG-2 ?

---

### Post by Donshyoku on 2007-07-25
> **Major_Kong said:**
> The threads=auto option doesn't exist when encoding to MPEG-2 ?

I'm off to check now.  I posted on LinuxQuestions too and someone else mentioned setting the threads equal to 2.  I will post back if I have any trouble.

---

### Post by Donshyoku on 2007-07-28
I still haven't gotten the hang of it.  I tried "threads=2" and "--threads 2" as Googling showed me in various places, but it is still only using one core.  Does anyone know the proper line of code for this?  Or better yet, is there a simple graphical frontend to mencoder out there that will let my configure it a little more easily?

---

