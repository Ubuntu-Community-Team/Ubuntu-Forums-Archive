---
title: "Audio Sometimes Too Fast"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by Amaroq on 2007-09-11
This isn't really a help topic as much as it is a "oh, this is kinda neat, I'll tell everybody about it" topic.

My sound is perfectly normal most of the time, so this strange issue isn't really a problem for me. It's just that sometimes when I turn on my PC, all audio (and video it seems) goes faster than it should, yielding faster play and sound sounding higher pitched. Even system sounds.

This is easily remedied by a restart. But it's still an interesting anomaly. (If I spelled that wrong, it's the spellchecker's fault.)

A friend of mine recently showed me the lshw command, and how to make it generate an html file. So I did one randomly when he showed me. Then a few days ago, I started my computer and the sound was fast. Curious about what causes this, I ran the lshw command again and generated another html file. I then compared the original and the fast-sound one, and there was only one difference. The IRQ for two things was 17 originally, but they were 16 when the sound was fast. I made lshw do another html file after I restarted and my sound was normal, and the IRQs in question were back to 17 again.

I wonder what significance this has.

---

### Post by ufayzull on 2007-09-14
I got the same problem. I would not call it "a neat feature". I'm not at my PC right now so I can't verify IRQs but I'll do it as soon as it happens again. I literally timed audacious play time with chronometer and one minute song plays in around 50 seconds. 

Does anyone know what I can do to prevent this? This is my HTPC box and I don't want my sound all of a sudden play faster then it is supposed to. TIA

---

