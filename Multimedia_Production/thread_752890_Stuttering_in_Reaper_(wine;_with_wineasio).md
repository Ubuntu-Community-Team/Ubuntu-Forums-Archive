---
title: "Stuttering in Reaper (wine; with wineasio)"
date: 2008-04-12
forum: Multimedia Production
---

### Post by DevilFish101 on 2008-04-12
I'm getting horrible stuttering in Reaper, which seems to be hardly affected even if I crank up the latency in jack control... The one difference it has made is that on some settings, the transport cursor just doesn't move at all when I press play...

Any thoughts?

---

### Post by DevilFish101 on 2008-04-12
Is the answer simply more RAM? I have 512MB; is that not really enough for all this?

---

### Post by jinnan_tonnix on 2008-05-13
I'm not at my laptop right now, but from memory I did get stuttering as you described.

It was fine when I changed the sound output path from within Reaper itself. 

See if this helps.

If not, PM me to give me a poke to check my laptop settings when I'm at home.

---

### Post by eric71 on 2008-05-13
I have had more problems with Reaper, wineasio and Jack since upgrading to Hardy. I wouldn't call what I'm hearing stuttering.  More like fuzz or distortion. It used to happen occassionally in Gutsy. Closing Reaper, restarting Jackd and re-opening Reaper would usually fix it. Now it only works maybe 1 in 5 times, even with much more forgiving jack settings. 

But your stuttering problem may be something else. I use a laptop with a crappy AC97 onboard sound chip. It runs only at 48K. If your default project settings in Reaper are not also 48K, and the ASIO audio device settings in Reaper are not also 48K, you might get problems (same goes for the Wine audio setup).

This is apparent immediately when trying to play "Making Me Nervous". It plays for a bit and then begins stuttering badly. This is because this demo project is at 44.1K. The default resampling setting (in project settings) in Reaper is too intensive for my laptop under wine. Setting it to the "good" setting allows this project to play fine with my 48K card.

---

