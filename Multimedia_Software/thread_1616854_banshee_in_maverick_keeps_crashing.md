---
title: "banshee in maverick keeps crashing"
date: 2010-11-08
forum: Multimedia Software
---

### Post by giorsat on 2010-11-08
i use maverick 64bit and banshee crashes a few seconds after I start the program
this is what i get 

Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.

any idea ? I deleted the banshee folder in .configure but everytime the library is loaded the problem starts again

---

### Post by Marky-boy on 2010-11-10
I'm on Banshee 1.80 on 32-bit Maverick and having same error. When I refresh the library it crashes after a short time while. And when I play a song it crashes.

I attach the output from terminal running banshee --debug and then playing a song. Hope that it helps both the OP and I.

Any ideas?

---

### Post by NeoZeroG on 2010-11-19
same here, its looking like some kinda mono issue. Everything was fine until I restarted(nearly fresh install), only other thing I remember doing was a little script to substitute another kernel optimization script for when the system starts to hit full load. Any ideas or fixes, all the other alternate sources won't compile for me.

---

### Post by dtach on 2010-12-06
bump-- this just started happening to me today-- :(

---

### Post by Marky-boy on 2010-12-11
...

---

### Post by directhex on 2010-12-12
Using any funny optimization things? Especially things related to /dev/shm?

---

