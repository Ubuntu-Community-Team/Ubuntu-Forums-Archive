---
title: "Skype sounds really really bad."
date: 2006-03-31
forum: Multimedia &amp; Video
---

### Post by jonasmattsson on 2006-03-31
Hi!
I installed Ubuntu for the first time a few days ago on an older machine. 
i downloaded Skype static (qt-compiled in) from Skypes website and unpacked it to ~/.skype, but when i called the echo123 i can hardly hear the woman giving me instructions, there is a large delay and the sound is slowing down and misses half of the frames, i had same problem when i was trying it out with a friend later. 
The machine is a P3-600MHz with 256MB RAM. is it possible that my machine are just too slow (it says: minimum 400MHz & 128MB RAM, on the website)? or are something else that i can do?
It works fine on my laptop wich is running gentoo, with the same kind of installing, but that is a P4 1700MHz with 512MB RAM.

And another thing (quite of-topic but i want to know), what about some threads that i've read about mot being able to play multiple sound sources without a lot of tweaking? I havent tried ye but it seems awful, is this something that the Canonical Ubuntu team is working on?

---

### Post by Jason_25 on 2006-03-31
In your current configuration your pc is probably too slow.  I would like to think though that you could tweak it enough to work with those specs.  Maybe try a different kernel and stop unneeded serviced and kernel modules.

As I understand it, the multiple sound problem is more from programs that use the old OSS sound system instead of alsa, just like skype, and their devs are more responsible for fixing it (i.e. switching to alsa) than anyone.

---

### Post by jonasmattsson on 2006-03-31
Ok, Thanks!
I.ve just read an article that said that switching to an opimized kernel was a good idea, didnt think of this problem then. perhaps it will work. maybe i will get some better perfomance if i switch to fluxbox (or similar).

I'll try it when i get home.

As for the OSS, why dont ubuntu use the OSS-emulation in alsa? i found a package in synaptics called "alsa-oss", i installed it but i dont really know what happend, (nothing happend from what i could see) the OSS kernel modules where still running and no alsa-modules where running (according to lsmod), but alsa is probably compiled into the kernel because i can use it from xmms.
Is the emulation slower? well as long as it doesnt hurt...
Maybe i should recompile the kernel to get it running the way i'm used to in gentoo, or will that just give me a lot of hedace during future upgrades? 

ok, i think i'm getting a litte off topic here. so i'll quit.

---

