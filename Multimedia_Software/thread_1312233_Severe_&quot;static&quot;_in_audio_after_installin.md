---
title: "Severe &quot;static&quot; in audio after installing 9.10"
date: 2009-11-03
forum: Multimedia Software
---

### Post by RoyT on 2009-11-03
I have a Dell 8200 (Dimension) that is pretty standard (Soundblaster, etc.) and when I upgraded to 9.10 the audio started having severe (and I do mean SEVERE) static (popping, crackling) noise.

---

### Post by lisiuyiu on 2009-11-03
I have this problem as well. my config is IBM Intellistation M Pro, Pentium 3.0, AC-97 Audio ICH7R, should be quite new and common device, I can still not yet able to find any solution

---

### Post by magnus33 on 2009-11-03
Remove pulse audio and go back to alsa.

---

### Post by RoyT on 2009-11-04
Thanks, "pulseaudio" was the keyword I needed to search for this problem. It still is not fixed, but at least I know where to look.

---

### Post by Bunnybugs on 2009-11-04
Still have the problem with ALSA... pulse is already removed;)

Also looking for the problem... pulse is one hell of a bug... but alsa doesn work that great as well

---

### Post by pmooney78 on 2010-08-04
I had a similar problem, and it turned out to be the most obvious fix imaginable, which I of course overlooked. Try turning down the master output volume in the sound preferences ... it was all the way up for me when I upgraded to 9.10.

---

### Post by Linuxforall on 2010-08-04
I had severe noise with my Yamaha YMF 724 card, I solved that by switching over to KDE Kubuntu which uses arts and it works flawlessly after that, sound quality is too good.

---

