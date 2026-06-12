---
title: "Could not connect to JACK server as client."
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by danielfretto on 2006-09-24
Forgive my double posting.  I was hoping to get a bit more attention with a more direct subject line.

Audiophile USB works great with Quod and other media players as well as with system sounds and has since the moment i installed Dapper.

After following all the steps on Ubuntu Studio site I'm not getting signal to or from Audiophile. PCs keyboard input triggers software synths as the meter lights show.

Seems as though Audiophile is seen by Jack in device dropdowns.

Can only start Jack with Dummy driver...no other works. Here's the errors:

21:42:09.417 Startup script...
21:42:09.419 artsshell -q terminate
can't create mcop directory
Creating link /home/d/.kde/socket-shedd.
21:42:09.737 Startup script terminated with exit status=256.
21:42:09.739 JACK is starting...
21:42:09.741 /usr/bin/jackd -R -dalsa -r44100 -p64 -n2 -D -Chw:1 -Phw:1 -S
21:42:09.755 JACK was started with PID=9993 (0x2709).
jackd 0.100.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
apparent rate = 44100
creating alsa driver ... hw:1|hw:1|64|2|44100|0|0|nomon|swmeter|-|16bit
control device hw:1
configuring for 44100Hz, period = 64 frames, buffer = 2 periods
Note: audio device hw:1 doesn't support a 16bit sample format so JACK will try a 24bit format instead
Note: audio device hw:1 doesn't support a 24bit sample format so JACK will try a 32bit format instead
Sorry. The audio interface "hw:1" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa
21:42:09.872 Could not connect to JACK server as client. Please check the messages window for more info.
could not attach as JACK client (server has exited)
21:42:10.020 JACK was stopped successfully.

I've scoured the forums all night with no luck.

Any ideas?

---

### Post by chameleon_789 on 2006-09-27
Not exactly sure what the problem, is, but instead of using a custom script try searching for **qjackctl** in synaptic, it's makes jack easier to set up. Once it's installed there's a shortcut to it in applications/sound and video.

---

### Post by dolson on 2006-09-27
I'm pretty sure that he is using JACK Control already, since he said that he picked his device in the dropdowns. Scripts don't usually have dropdown menus like that..

Anyhow, the log shows the problem:

*Sorry. The audio interface "hw:1" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.*

Try setting your sampling rate to 48KHz, and try using a higher Period/Frames, and any combination of the two.

---

### Post by chameleon_789 on 2006-09-27
[quote=dolson]I'm pretty sure that he is using JACK Control already, since he said that he picked his device in the dropdowns.[/quote]
Oops, my bad, didn't read the post fully :|

---

### Post by danielfretto on 2006-09-27
dolson,

thanks.  i will apply your suggestion later today...round 5p pacific.  i was shooting for lowest latency.

---

### Post by dolson on 2006-09-27
Just to clarify my reasoning:

If your sound card supports it, you will want 48KHz probably. It increases latency slightly, but not enough to worry about it. But some cards have issues with one or the other sampling rate, so that could be the only issue here.

And some cards have issues with certain buffer sizes, too. Basically keep trying settings and you should hit one that works. If not, hopefully someone else here knows a solution, or maybe the LAU mailing list.

---

### Post by CadetD on 2006-10-12
> **danielfretto said:**
> 
Note: audio device hw:1 doesn't support a 16bit sample format so JACK will try a 24bit format instead
Note: audio device hw:1 doesn't support a 24bit sample format so JACK will try a 32bit format instead
Sorry. The audio interface "hw:1" doesn't support any of the hardware sample formats that JACK's alsa-driver can use.
ALSA: cannot configure capture channel
cannot load driver module alsa


Do you have multiple sound cards? Maybe a USB controller?
It coulbe picking up the wrong card. 

cat /proc/asound/cards

If the wrong card is hw:1 then start jackd from the command line as such:

jack -d alsa -d hw:x & 

#where x is the correct card from above

Dudley C.

---

