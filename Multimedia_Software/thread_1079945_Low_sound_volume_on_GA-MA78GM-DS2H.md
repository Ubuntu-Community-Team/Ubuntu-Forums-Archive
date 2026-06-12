---
title: "Low sound volume on GA-MA78GM-DS2H"
date: 2009-02-24
forum: Multimedia Software
---

### Post by pongtawat on 2009-02-24
Hello,

I am using Ubuntu Intrepid AMD64 on Gigabyte GA-MA78GM-DS2H motherboard (AMD 780G chipset, Realtek ALC889A audio chip). The sound volume I get on Ubuntu is quite low compared with the volume on Windows. 

I have make sure that I set all volume sliders to max and read many posts in this forums. I have also try to add "options snd-hda-intel model=XXX" to alsa-base file but it doesn't help: no different in sound volume at all :cry:. FYI, I try the following models: 3stack-dig, 6stack-dig, 3stack-6ch, 3stack-6ch-dig (other models look like notebooks).

Does anybody know how to solve this?
What model should I set for this board?

FYI: I use the green jack on the rear of motherboard to connect to my headphone. I notice that if I use the front case jack, the sound is somewhat louder (still less than Windows). However, the front case jack is quite inconvenient for me.

Thank you,
Pongtawat

---

### Post by cariboo on 2009-02-24
Do your headphones have an internal amplifier, as all the you get from the speaker output is line level, You need to amplify the signal to make it usable.

Jim

---

### Post by pongtawat on 2009-02-25
My headphone is just a small headphone without amp.

Do I really need an amp if I wish to use the rear speaker out jack?

The volume level is loud enough on Windows. So, may be there is something wrong with my Ubuntu setting?

Thank you.

---

### Post by cariboo on 2009-02-25
Have you double clicked the speaker icon in the upper panel and  turned up all the sliders including the one for headphones?

Jim

---

### Post by pongtawat on 2009-02-25
Yes.

I'm sure all my volume sliders--master, pcm, front-- are max or almost max (I sometimes get distorted sound if everything is 100%.). FYI, surround, center, LFE and other sliders don't affect my headphone sound volume.

I have also check with alsamixer and all volume sliders are ok.

---

