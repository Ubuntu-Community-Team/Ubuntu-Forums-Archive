---
title: "No sound from timidity"
date: 2010-04-06
forum: Multimedia Software
---

### Post by mysterian077 on 2010-04-06
I used sudo apt-get install timidity to install the timidity softsynth, but when I run timidity <some midi file>.mid, I get no sound. I know I have my volume up and is working, plus I know the midi file have notes in it, but still, I get nothing. Am I missing anything?

I'm running Lucid Beta 1

---

### Post by RedSingularity on 2010-04-06
Do you have sound in any other applications?

---

### Post by mysterian077 on 2010-04-07
Nope, and I just figured out why. I had the output device set to my HDMI port, currently unattached. Usually works better when you have the correct device enabled. X-P

Thanks for posting, though.

---

