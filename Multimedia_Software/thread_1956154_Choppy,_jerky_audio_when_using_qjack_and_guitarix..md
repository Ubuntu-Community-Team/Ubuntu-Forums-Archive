---
title: "Choppy, jerky audio when using qjack and guitarix."
date: 2012-04-10
forum: Multimedia Software
---

### Post by geekofubunt on 2012-04-10
I just started using guitarix with my guitar, and I'm getting a nice tone out of it. However, its only nice between the jerks, crackles and pops that guitarix seems to produce. All of my wires have been checked and they are definitely not the cause (the crackling continues while unplugged), and I think that it is purely the fault of guitarix or my sound card, although my card is the built in Dell one and seems to be fine with everything else (microphone, speakers, etc.). :confused:

I've been looking around Google, but I couldn't find an answer to my  problems. If anybody could help or refer me to someone who could, that  would be great!

:guitar:

If it helps, these are my PC specs;

Dell Precision 390
Intel Core 2 Duo
2gb ECC DDR2 RAM
Ubuntu 11.10 (fully updated)

---

### Post by adegert on 2012-04-12
you probably get xruns because jackd misses the deadline for the next audio buffer. This is often a problem with internal soundcards.

Another ubuntu forum thread is
[http://ubuntuforums.org/showthread.php?t=1834547](http://ubuntuforums.org/showthread.php?t=1834547),

or someone who was successful with his dell laptop
:-)
[http://old.nabble.com/How-I-got-JACK-working-on-the-internal-sound-card-of-a-Dell-Latitude-D430-td19237669.html](http://old.nabble.com/How-I-got-JACK-working-on-the-internal-sound-card-of-a-Dell-Latitude-D430-td19237669.html)

---

### Post by geekofubunt on 2012-05-04
Thanks for your help, and sorry that I took so long to reply, as my eMail sent my notification to junk!

After experimenting, I found out that there was just an error with the sample rate in the settings.

---

