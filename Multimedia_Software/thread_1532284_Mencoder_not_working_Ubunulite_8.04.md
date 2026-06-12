---
title: "Mencoder not working Ubunulite 8.04"
date: 2010-07-16
forum: Multimedia Software
---

### Post by Mortesins93 on 2010-07-16
Hello,
I have an old computer with Ubuntulite 8.04 installed on it, it works perfectly and brought this old piece of junk back to life. Anyways i managed to install ConverIT but i had problems with some commands so i found out that MEncoder doesn't work. This is what i get:
proprietario@AVM:~$ mencoder
MEncoder 2:1.0~rc2-0ubuntu13.1+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner (Family: 6, Model: 7, Stepping: 3)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
No file given

Exiting... (error parsing command line)


What should i do? I tried reinstalling it but it has the same problem.
Thank you in advance.

---

### Post by andrew.46 on 2010-07-17
Hi Mortesins,

> **Mortesins93 said:**
> 
```
proprietario@AVM:~$ mencoder
MEncoder 2:1.0~rc2-0ubuntu13.1+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel Pentium III Katmai/Pentium III Xeon Tanner (Family: 6, Model: 7, Stepping: 3)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
**[COLOR="Red"]No file given[/COLOR]**

Exiting... (error parsing command line)
```

Hmmm..... you seem to be missing the filename and the actual command, are you trying to use MEncoder by itself? My apologies if I am missing something here...

Andrew

---

### Post by Mortesins93 on 2010-07-18
yes i was trying to convert a flash video in avi using the following command:
mencoder whatever -ovc lavc -oac mp3lame -o whatever2.avi

---

### Post by Mortesins93 on 2010-07-28
Does anyone know what the problem might be?

---

