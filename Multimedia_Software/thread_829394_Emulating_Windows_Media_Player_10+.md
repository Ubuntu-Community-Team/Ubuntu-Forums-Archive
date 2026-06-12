---
title: "Emulating Windows Media Player 10+ ?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by Hessesian on 2008-06-14
Hi, I'm running Hardy Heron, and only thing why I'm going to winXP is Warcraft 3 and adding new songs to MP3 player.

Problem is that only way to get song on my MP3 player Sansa c240 is to synchronize them with WMP11. So is there a way to do so in linux ? I don't wanna emulate whole windows XP to get few songs...

Thx for any help on this

---

### Post by unicorn_2003_1 on 2008-06-14
[http://ubuntuforums.org/showthread.php?t=329775](http://ubuntuforums.org/showthread.php?t=329775)
[http://ubuntuforums.org/showthread.php?t=688038](http://ubuntuforums.org/showthread.php?t=688038)

Have you tried these threads. Would change your player mode to USB disk help? 

BTW, Warcraft III ROC & TFT works wonderful on Wine, did you give it a try? faster than on Windows imo

---

### Post by Hessesian on 2008-06-15
Thx, rhytmbox did the job. And yes, I had given a try to war3 through wine, but only thing I got was black screen with no sound.

Maybe I'll do a little research about it :P

---

### Post by soxs on 2008-06-15
I am currently doing a compile plus additional script to make a parallel wine version which should run fine on hardy x86/x86_64 with 0.9.45 source. So, PM in a week or 2 and it might be ready for "release".

---

### Post by unicorn_2003_1 on 2008-06-15
The black screen and no sound problem is mostly due to the movies/opengl.
It's better to delete those .mpg files in your Movies folder, then launch the program (preferably 1.21b). Of course, using OpenGL would speed it up a lot, add the registry entry "Gfx OpenGL" in the warcraft 3 entry and set up the value to "1".

Read the detailed tutorial at this link:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3126)

---

### Post by Hessesian on 2008-06-15
Yeah, renaming Movies folder and registry tweak helped alot. Thank you :)

---

### Post by soxs on 2008-06-15
> **Hessesian said:**
> Yeah, renaming Movies folder and registry tweak helped alot. Thank you :)

Good to year, bad news are, you won'be able to host b.net games without patching source and compiling yourself (sving won't work either in singleplayer/LAN mode)

---

