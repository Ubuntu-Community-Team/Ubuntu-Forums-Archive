---
title: "Music Sounds bad..."
date: 2010-12-09
forum: Multimedia Software
---

### Post by JimmyVonClaussen on 2010-12-09
Hello Guys,

I'm still new to Ubuntu and I'm trying to get the sound working. I have a Satellite X205-SLi1 and just installed Lucid. Everything is okay, except for the sound. My laptop has 5.1 harman/kardon speakers and I think just some of them are being used and the quality is bad. I'm not sure what to do...

Hope you guys can help me.
Thanks.

---

### Post by tommcd on 2010-12-09
Are these external speakers, or are they part of the laptop?
In any case, for starters, you should open a terminal (applications > accessories > terminal) and run **alsamixer**.
If anything is muted, you can unmute the levels by toggling the "M" (lowercase) key. 
You can raise and lower the levels with the arrow keys. Hit the Esc key to quit alsamixer when you are done.

Note: To say the sound quality is "bad" is rather subjective. Try to provide more info if you can. Have you verified that some of the speakers are not working?
For now, see if using alsamixer helps.

Also, try going to: system > preferences > sound, and try setting everything to alsa if you can.

And welcome to the Ubuntu forums!

---

### Post by plecebo.mc on 2011-01-25
i have the same issue but its most likely because the subwoofer isnt working. i have tried using the mixer before but subs its not in there. Having taken apart this notebook before i will say that the 5.1 speaker setup is wired like this: 2 wires run 2 sets of mids and highs and one wire runs the subwoofer. the mixer says the chip is a realtek alc268 and the card is HDA intel. I have seen other people with these same types of problems with 5.1 audio laptops. Im running ubuntu 10.04 LTS.

---

