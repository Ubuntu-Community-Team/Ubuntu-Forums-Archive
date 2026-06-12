---
title: "gtk-recordMyDesktop record video sound?"
date: 2009-12-01
forum: Multimedia Software
---

### Post by cd-r80 on 2009-12-01
Hi! I cannot figure out how to configure gtk-recordMyDesktop to capture desktop & flash video with sound. All slow boring youtube tutorials show how to capture using mic. I don't want to use mic. I have tried: default , hw:0,0 , pulse , jackd. All of them give me errors or no sound is captured.

hw:0,0 No sound
pulse  Exited with status 768
default No sound
jackd :

creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa

16:00:03.657 Post-shutdown script terminated with exit status=256.
16:00:05.280 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

---

### Post by cd-r80 on 2009-12-01
I got jackd running but now gtk-recordMy... gives error 3584 cannot load jack library?

---

### Post by cd-r80 on 2009-12-01
R.I.P. jackd, recordmydesktop, & pulseaudio. Sound system in Ubuntu is too clumsy & complicated.

---

