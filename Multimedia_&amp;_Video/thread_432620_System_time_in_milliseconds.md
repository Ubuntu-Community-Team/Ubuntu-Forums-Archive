---
title: "System time in milliseconds"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by sreagvle on 2007-05-04
Hi all,

I'm creating an  program that has graphics (OpenGL) and sound (stk) and will be interactive. The sound and audio are created in two different threads and I want to synchronize them as closely as possible. Can anyone tell me how to get the system time with the highest possible resolution i.e. milliseconds if possible. Any reference time will do i.e. since the program started, the system started, 1970, it doesn't matter.

Many thanks,

Eoin

---

### Post by lloyd_b on 2007-05-04
> **sreagvle said:**
> Hi all,

I'm creating an  program that has graphics (OpenGL) and sound (stk) and will be interactive. The sound and audio are created in two different threads and I want to synchronize them as closely as possible. Can anyone tell me how to get the system time with the highest possible resolution i.e. milliseconds if possible. Any reference time will do i.e. since the program started, the system started, 1970, it doesn't matter.

Many thanks,

Eoin

Take a look at the "gettimeofday()" function ("man gettimeofday").  It will give you the current system date/time, with a 1 microsecond resolution.

Note: questions like this really belong in the "Programming" forum, rather than "Multimedia".  

Lloyd B.

---

