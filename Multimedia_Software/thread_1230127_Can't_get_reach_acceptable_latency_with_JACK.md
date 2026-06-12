---
title: "Can't get reach acceptable latency with JACK"
date: 2009-08-03
forum: Multimedia Software
---

### Post by zomgneeks on 2009-08-03
I'm using Qsynth and JACK to play my Axiom 49 controller.
I'm running Jaunty on a thinkpad x200 and have a HDA-Intel sound card.
Here are my JACK settings. The latency is to large but if I lower the frames/period or increase the sample rate I get xruns nearly every second. With these settings I receive 10 xruns in 10 minutes.

Is there another way to lower latency than by just fiddling with JACK's settings? Do I need to purchase a new sound card?

Thanks

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Pulseaudio and Jack recording doesn't work]("http://ubuntuforums.org/showthread.php?t=1217834") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1217834") [2]("http://ubuntuforums.org/showthread.php?t=1217834&page=2"))
[http://ubuntuforums.org/showthread.php?t=1217834](http://ubuntuforums.org/showthread.php?t=1217834)

---

### Post by markbuntu on 2009-08-03
Frames/Period  128 or 256

Periods/Buffer 3

Try that. You will probably not be able to get latency below 10msec with that set up but you can get close. 

Latency is based a lot on the availability of cpu cycles to the sound applications.

Edit /etc/security/limits.conf and add or modify these lines

```

@audio - memlock unlimited
@audio - nice -10
@audio - rtprio 99

```

This will give audio higher cpu priority and better memory access.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

---

