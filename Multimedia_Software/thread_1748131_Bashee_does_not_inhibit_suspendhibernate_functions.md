---
title: "Bashee does not inhibit suspend/hibernate functions"
date: 2011-05-03
forum: Multimedia Software
---

### Post by exanime on 2011-05-03
It's simple... when I'm listening to music on Banshee it does not prevent suspend/hibernation which means my music gets interrupted all the time.

I could disable power management altogether as a workaround but this would create other functional issues for me.

I reported this in the Banshee forums 2 years ago and they have not even acknowledged it as a functional issue so I am not holding my breath on that front

Can anyone think of a workaround other than uninstalling Banshee and reinstalling good all Rythmbox? I always try hard to give new Ubuntu features/apps an honest try but I am close to the end with Banshee LOL

Thanks in advance guys!

---

### Post by gnuts on 2011-05-03
I have the same concern. natty 64bit. It would be nice to leave the power settings so that if music isn't playing the computer will still sleep. thanks in advance.

---

### Post by Paqman on 2011-05-05
Install [Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ppa") and add Banshee to the list of programs for which it automatically inhibits sleep.

---

### Post by exanime on 2011-05-05
Thanks Paqman! this sounds like a valid workaround... I will give it a try and report my experience.

PS: I'm still disappointed at the Banshee team for not including this or even paying attention to the many comments on the feature request

---

### Post by exanime on 2011-05-05
Ok so I gave Caffeine a try and found the following:

1) yes it solves my problem! I normally either listen to music at home away from my PC or I run Banshee on my netbook while commuting. In both cases I need the music to continue to play. Caffeine does the job

2) the only shortcoming is that Caffeine does not seem to be able to distinguish between a running process and a sleeping one. If I pause my music (new players do not have a stop button anymore) Caffeine still inhibits power management features... this is not a big deal but I usually do not shutdown my music player (ever) which I will have to start doing at night to prevent my PC from staying up needlessly.

Paqman, thanks for your solution

---

