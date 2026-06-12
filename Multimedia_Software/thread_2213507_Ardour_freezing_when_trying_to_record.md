---
title: "Ardour freezing when trying to record"
date: 2014-03-27
forum: Multimedia Software
---

### Post by kimberly2 on 2014-03-27
hi all!

i have Ardour version 2.8.14, from the repos, and jackd 1.9.10. when i arm recording on my track 1, and then arm recording for ardour, it seems fine (the red record light is blinking at the top), but when i click the play button or hit spacebar, it freezes. my mouse still moves around, but the program doesn't respond at all, and eventually i just have to kill ardour. if i start it with the command line, the only thing i get once it freezes is:

```
no space in Ardour-UI request buffer for thread unknown
```

it seems from a quick google search a couple other people have had this problem:

[https://community.ardour.org/node/3681](https://community.ardour.org/node/3681) (i don't think his solution applies to me)
[https://community.ardour.org/node/2083](https://community.ardour.org/node/2083)

is there anything i can do? i can't even find a verbose option for ardour.

thanks!!

ps: before anyone suggests it, it doesn't work whether pulseaudio is running or not.

---

### Post by silex89 on 2014-03-28
Hi there! :)

I use Linux to run my home studio with Ardour as my DAW and I wasn't completely satisfied with jack, so I switched gears to jack2 (which is a better option if you have a multi-core processor). I don't know what the problem is, but jack2 indeed handles the memory and resources in a more efficient approach when your machine has 2 cores and more. Give it a try and see if changes something (the package is jackd2 in Ubuntu).

Best of luck! :D

---

### Post by kimberly2 on 2014-03-29
well on someone's suggestion, i tried ubuntu studio, with a live CD, to  see if it worked out of the box. it did! so i installed it, and  mysteriously it stopped working. i'll post this here anyway in case  anyone else has the same problem.

however i think i've figured it  out. my frames/period was set to 64 to begin with, and i was seeing  lots of "XRUN callback" in the qjackctl messages. to mess around, i  change it to 2048 and the problem went away, i can now record just fine.  i tried all of the other frames/period and found that they all work  well down to 64, so i'm using 128 now. strangely, even ones lower than  64 didn't make ardour freeze, but the recorded audio sounded very bad.

so in typical ubuntu fashion, i fixed the problem, but i have no idea why.

---

