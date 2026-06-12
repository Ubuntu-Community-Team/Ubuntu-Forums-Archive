---
title: "Add alsaconf to init"
date: 2007-01-05
forum: Multimedia &amp; Video
---

### Post by prototype_angel on 2007-01-05
I run ubuntu edgy with kde, the i386 platform on an amd chip.
I have a Creative Audigy sound card that works just fine with amarok, etc, and another onboard sound card.
but sound didn't work, so I installed the alsa, lsb and alsautils package. But configuration was difficult and all sound used to go to my onboard sound card when I'd get better quality through my creative audigy.

So I ran alsaconf and it detected my other soundcard and raised volumes to optimum levels. And everything works fine. The problem is that when I restart I have to do this over again.
Is there any way I can do this by adding it to init so that things work fine. I need this to wake up in the morning(who needs alarm clocks when you can wake up to slayer) but I'm afraid a power outage etc might cause a restart like it did sometime back and disable the alarm.

Is there anyway I can make my sound work fine on a restart.

---

### Post by Pjotr123 on 2007-01-05
I have a similar problem. But it is not alsaconf that should run at init, but Linux simply has to remember it's bloody sound driver that was configured with alsaconf. 

How is it possible that a driver is forgotten? Seems like a bug to me. And how can this bug be circumvented?

I hope somebody will come with a solution.

Greeting across the continents from the Netherlands, 
Pjotr.

---

### Post by stanthecaddy22 on 2007-01-06
I seem to remember saving the default volume by using the following at a terminal:

'sudo alsactl store'

I'm not sure if this will solve your problems but you could try it out or at least investigate the possibility.

Good luck!

---

### Post by prototype_angel on 2007-01-06
Thanks @stanthecandy22 and@pjotr23
That seems to have worked. I saved it to a file (/var/lib/als/asound.state) copied it to my home directory and added alsactl (path to saved file) into my init shell. Now it seems to have worked.

---

