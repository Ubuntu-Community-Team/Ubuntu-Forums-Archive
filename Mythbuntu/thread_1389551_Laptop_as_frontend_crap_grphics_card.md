---
title: "Laptop as frontend crap grphics card"
date: 2010-01-24
forum: Mythbuntu
---

### Post by My Name on 2010-01-24
OK, so i want to use an old lappy as a remote frontend. it's a bit old and the graphics card has only 38MB of memory.
Am i wasting my time or are there settings I can use to get the best from this aging machine
I've tried the presets CPU-- and SLIM but i get jittery playback, unwatchable really
The lappy is an NEC Versa S940
1.7 ghz processor
Intel Extreme Graphics 2 38meg shared memory
512MB ram

thanks

---

### Post by My Name on 2010-01-26
OK, in case anyone is interested...
I have tested the system using the built in wireless and a wired network and the live TV playback is stuttery and not watchable. I have tried using the playback presets with no luck. The machine playes DVDs quite happily.
I thought if a machine could ply a DVD it would be OK for mythtv, but obviously not.

---

### Post by Amorget on 2010-01-26
I would venture to guess it isn't the video card, it's the processor.

---

### Post by marin123 on 2010-01-26
maybe ethernet is 10 Mbps, that why playback is stuttery.. (you said it was an old laptop :D )

---

### Post by SiHa on 2010-01-27
Have you tried CPU+/++?

The CPU-/slim profiles will attempt to offload onto graphics hardware. If there isn't anything that it can work with (as in this case) it generally falls back to something really pants.

It's counter-intuitive, but I've found for older hardware, such as this, the more CPU intensive profiles work better. Certainly, a 1.7GHz should be able to decode SD without making a fuss, as your DVD watching shows.

---

### Post by tgm4883 on 2010-01-27
> **SiHa said:**
> Have you tried CPU+/++?

The CPU-/slim profiles will attempt to offload onto graphics hardware. If there isn't anything that it can work with (as in this case) it generally falls back to something really pants.

It's counter-intuitive, but I've found for older hardware, such as this, the more CPU intensive profiles work better. Certainly, a 1.7GHz should be able to decode SD without making a fuss, as your DVD watching shows.

I second that. Your machine should play back SD content fine. Try some of the other profiles.

---

### Post by My Name on 2010-01-27
Thanks guys, I think I have it now. it's still a little scetchy but it is a LOT better.
FTR I am using the "normal" setting with gl sync disabled.
The DVD still looks a lot better than live TV though.
I'll do a little more digging...

---

### Post by My Name on 2010-01-27
These settings have my CPU at 90+%.
looks like the lappy just hasn't got the juice...

---

