---
title: "Speakers and Headphone problems (and internal microphone!)"
date: 2011-05-20
forum: Multimedia Software
---

### Post by soylentcola on 2011-05-20
I'm running Ubuntu 11.04 on an ASUS K60IJ and am having an issue with my speakers on my laptop. I thought I'd fixed this problem earlier but it seems to have reappeared... The speakers play fine but when I plug my headphones in, the speakers mute, but there's no sound coming out the headphones, when I plug the headphones out, the speakers work fine again.

Can someone instruct me on how to fix this?

Also, my internal microphone is not showing up at all in Ubuntu...

I've run alsa-info-script in case it provides any help and it's hosted [here](http://www.alsa-project.org/db/?f=228c33f853b1995cf8f4cbd997725cd8aa948e07), hoping I can get this fixed soon. D:

---

### Post by papibe on 2011-05-20
Have you tried [alsamixer]("http://alsa.opensrc.org/Alsamixer")? Chech [this]("http://www.patheticcockroach.com/mpam4/index.php?p=62").

Regards.

---

### Post by soylentcola on 2011-05-20
I have tried the alsamixer, and the headphone option (even when plugged in) is greyed out, and I cannot change the value (which is permanently at 00, not muted) here's a screenshot of what I have...

[[IMG]http://i.imgur.com/kkUUSl.jpg[/IMG]](http://imgur.com/kkUUS)

---

### Post by soylentcola on 2011-05-20
Ah, I changed the "front" value to 100 (after unmuting it) and now it seems that the music is playing out my headphones AND speakers...at least we're making progress!

---

### Post by papibe on 2011-05-20
Sometimes the changes you make on alsamixer are not saved next time you boot. If that's the case try this right after adjusting the levels on alsamixer:
```
$ alsactl store
```
I hope it helps.

---

### Post by soylentcola on 2011-05-20
All right, I had to change the output connector from "analog output" to "analog headphones" and that fixed it. :D Now I just need to figure out why my internal mic isn't working...

---

### Post by soylentcola on 2011-05-20
Okay, so my internal microphone seems to be working, but it's recording from my speakers, and not my voice. :( I'm not entirely sure what is causing this, I'm going to fiddle around a bit more with ALSA mixer more to see what is causing it, and see if I can't fix it.

---

