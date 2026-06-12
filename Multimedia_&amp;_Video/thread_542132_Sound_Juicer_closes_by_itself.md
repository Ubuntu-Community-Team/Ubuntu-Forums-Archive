---
title: "Sound Juicer closes by itself"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by martymc on 2007-09-03
Hi All

I'm having some fun with Sound Juicer....

Thanks to the forum's search function, I was able to get it to rip mp3s (not to mention getting the rest of Fiesty up and running). I did a few songs successfully, but now, when I rip, Sound Juicer spontaneously turns itself after ripping for ~10-20 seconds.

No error messages come up and I can start Sound Juicer up again right away. I try again, and it turns itself off again.

.ogg's seem to just lock it up now, but before I got the mp3 "codec" to work, it ripped .ogg's just fine.

What could possibly be happening????

Thanks in advance :)

---

### Post by groeswenphil on 2007-09-08
I've got the same problem............did something a little while back to enable ripping to MP3 format, which worked.
Now, as soon as I try ripping, it simply shuts down BUT if you reset it to rip in OGG format it works.

I'd much prefer MP3 format.

Phil

---

### Post by martymc on 2007-09-09
I was able to solve my problem by running Sound Juicer from the terminal (open the terminal and type in sound-juicer). It kept repeating an error message about the buffer over and over and over again.

According to a search I did on Google, it was a hardware problem causing the shutdown....

I popped open the computer and noticed the processor heatsink and fan caked with dust. I cleaned them up, put some new thermal paste on the heatsink when I reinstalled it and added another case fan. It rips fine now. :)

i ran the performance monitor while I had Sound Juicer on and the CPU runs around 90-99% while ripping.

MP3s may cause a problem that OGGs don't because Sound Juicer uses a LAME plug-in to rip in MP3 format. Maybe OGGs don't require the same amount of "CPU squeezings" to rip??

---

