---
title: "[SOLVED] Flash Sound Doesn't Work"
date: 2008-11-06
forum: Multimedia Software
---

### Post by Roanoke on 2008-11-06
Whenever I watch a video from say, youtube, the sound does not work. However, everything else (local files, etc) works fine.

---

### Post by Neville Grech on 2008-11-06
Same symptoms here.

I'm using Intrepid 64 bit on a lenovo T500. I tried  to remove obsolete configuration files, and install/remove libflashsupport as in [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965).

I still have no sound in flash.

---

### Post by Neville Grech on 2008-11-07
One thing I noticed when flash plugin initialises:

neville@neville-laptop:~$ firefox
LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]

Anyone can help?

---

### Post by Ferrat on 2008-11-07
are you sure you got NO sound? try turning everything to MAX and see, I get sound but it's so low that with youtube sound, my sound and my soundsystem all turned up to max I just barely hear the sound but I do hear it.. 

everything else works normally

---

### Post by NilsE on 2008-11-07
If you have libflashsupport installed try removing it.  

Since libflashsupport is needed for flash 9 and if you are on flash 10 it may be conflicting.  

If you are on flash 9 and libflashsupport is not installed try installing it.

---

### Post by haud on 2008-11-09
Hi, I had the same problem at first but then I tryd that evrything turned to max and I heard abit sound, so I opened Volume Control and added there front and side and everithing like that, and the sound was there

---

### Post by CLomax on 2008-11-09
Sometimes, for reasons unknown to me, if you have a media player or any program using sound open at the same time, it'll stop other programs using sound. Might be your problem.

---

### Post by Roanoke on 2008-11-09
No. None of these have solved the problem.

---

### Post by Roanoke on 2008-11-21
The problem has still not gone away. Can anyone help?

---

### Post by Elswood on 2008-11-21
Same here.  No sound from flash on Dell m1530, but Amarok has great sound.  No sound from YouTubes and other flash...  Anybody????:(

---

### Post by Roanoke on 2008-11-24
bump.

---

### Post by psyke83 on 2008-11-24
You need to configure PulseAudio correctly.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Roanoke on 2008-11-24
Thank you much, that guide fixed it :D

---

### Post by dharkus on 2008-12-11
same problem here - come on - someone must know how to fix this problen

---

### Post by Roanoke on 2008-12-12
See the guide above, and note the '[SOLVED]' in the title.

---

