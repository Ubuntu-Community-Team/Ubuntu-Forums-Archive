---
title: "Default Hz of the generic kernel?"
date: 2010-08-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Motomouse on 2010-08-28
What will be the default Hz for the 10.10 Ubuntu desktop kernels?

I just realized that the low default Hz of the current generic kernels on Ubuntu 10.04 (100Hz) lead to a whole bunch of related problems. (Stuttering sound, sound and video lags, sound recording not working at all in some applications, stuttering applications when running two at once on a quadcore, ...). I could resolve the problems by using custom and realtime kernels. But I think for a desktop kernel 100 Hz is definitly not a vialable default. 

What will be the default kernel Hz?

Regards
Ralph

---

### Post by andrewthomas on 2010-08-29
> **Motomouse said:**
>  I could **resolve the problems by using custom** and realtime kernels. But I think for a desktop kernel 100 Hz is definitely not a viable default. 

What will be the default kernel Hz?

Regards
Ralph
```
CONFIG_HZ_100=y
# CONFIG_HZ_250 is not set
# CONFIG_HZ_300 is not set
# CONFIG_HZ_1000 is not set
CONFIG_HZ=100
```

---

### Post by dino99 on 2010-08-29
see the difference:

[http://lwn.net/Articles/331607/](http://lwn.net/Articles/331607/)

---

### Post by Motomouse on 2010-08-29
Thanks for the infos!

I think I do not like this. During everyday desktop operations I prefer already the real time kernel. When I have to run two compute intense programs with graphical output, I need to use schedtool to fix the CPU affinity. (The graphical output only visualizes the stuttering, I also suffer the consequences when the video output is disabled). 

Perhaps the real time kernel should be the standard kernel for a desktop setup in our time? 

Regards
Ralph

(P.S. The sound and video streaming problems are probably a sign that the scheduling is not optimal also in other contexts less audible and visible.)

(P.P.S. What about automatically starting a reinstallation of the graphics driver after a kernel change. I refrain from suggesting a change to the real time kernel to users because this is not handled automatically yet. I like the already working option to start a one time low resolution session, but an automated reinstallation is the probably the way to go?)

---

### Post by Motomouse on 2010-08-29
Some Info from the mentioned link:

> A high HZ value may affect the performance of the system if its nonidle.
I ran a simple experiment with 2.6.29 kernel running on VMware..
A simple tight loop took about 264s to complete with a HZ value of 1000.
The system serviced a total of 264405 timer interrupts during that time.
The same loop with HZ=100 took only about 255sec to complete.
Total timer interrupts were 25593.
More information here - [http://lkml.org/lkml/2009/4/28/401](http://lkml.org/lkml/2009/4/28/401)


> > We might as
> well keep a logical 1000 for convenience and accuracy.

What is the accuracy factor that you are mentioning here ? i guess you
mean the precision of the timeouts, but that shouldn't matter much
right ? 

When I use schedtool to fix the CPU affinity I accept slower computing performance to achieve a smoother stream of data. This is in many sound and video related use cases (aka on the desktop) preferable in most situations. 

Regards
Ralph

[COLOR="Gray"]
P.S. "What is the accuracy factor that you are mentioning here ? i guess you
mean the precision of the timeouts, but that shouldn't matter much
right ? " 

No! Not right, it matters much on the desktop. ;-)[/COLOR]

---

### Post by dino99 on 2010-08-29
you can set something higher than 100 hz for your needs (streaming, video or audio compositing) , your system will not be so cooler but get lower latency. To do that you have to recompile the kernel with the new settings.

---

### Post by Motomouse on 2010-08-29
Thanks, that is what I do know.

I propose the real time kernel as the standard kernel for future desktop releases and automatic graphics driver reinstallation when a kernel change makes this necessary. 

Not for my convinience. I can help myself :-) 

(If the generic kernel is trimmed for "green" operations it should be called -green not -generic kernel. I build a less energy consuming computer if the goal is to save energy and then a low energy consumption kernel is a good option. If I need the performance i build for, I do not want to be hampered down be a green kernel ;-) 

Regards
Ralph, happy schedtool user

---

### Post by cariboo on 2010-08-29
For the majority of users, this isn't a problem, there is normally an rt kernel available in the repositories, for those that need it. 

I see it hasn't been built yet for the latest version.

---

