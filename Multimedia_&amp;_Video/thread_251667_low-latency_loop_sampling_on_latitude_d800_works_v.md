---
title: "low-latency loop sampling on latitude d800 works very well"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by capsid on 2006-09-05
Hi there.  I just wanted to report on my sooperlooper experience with dapper 6.06 on a dell latitude d800.  I'm not very knowledgeable about the sound card it uses, it's listed as sigmatel on windows, but comes up as intel ac97 on linux.   if anyone can clear this up for me, I'd appreciate it.  

In any case, IT WORKS GREAT!  Let me elaborate...

Under Windows, I was never able to get latency lower than 50ms for realtime synthesis or live recording.  I switched to the latest 686 kernel and installed the nvidia drivers (which seemed to make gnome a whole lot snappier and responsive), and configured Jack manually since it complained that the default setting was using a less efficient hotplug layer.  I tested sooperlooper with electroplankton, a nintendo ds game/instrument, and was shocked at how quickly the audio tracked into the pc and out to the speakers.  
Here's electroplankton layered a few times:
[http://applecoremedia.org/capsid/electroplankton01.ogg]("http://applecoremedia.org/capsid/electroplankton01.ogg")

Audacity couldn't initialize the host (or something annoying like that) while I was running Jack and my other apps, so I just ran the audio out to a second Ubuntu machine that was only running audacity.  

Anyway, thanks to linux/ubuntu/jackd/everybody else for making my stock soundcard work well enough that I don't have to buy a fancy one:)  I guess I haven't tried any computationally expensive realtime-synthesis yet, but I thought the low-latency loop sampling was impressive, especially considering I was running a heavyweight like Gnome instead of Blackbox AND I wasn't using a completely preemptible kernel.

---

