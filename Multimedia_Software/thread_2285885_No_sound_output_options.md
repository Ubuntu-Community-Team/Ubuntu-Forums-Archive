---
title: "No sound output options"
date: 2015-07-08
forum: Multimedia Software
---

### Post by bjrn4 on 2015-07-08
So, started with ubuntu yesterday, things work fined but for the sound. It did however worked when I switched to send output via hdmi to the projector but the headphones wouldn't work. 

Then today sound settings output doesn't display any output options at all.

I tried 
aplay -l | grep card

which showed that I do have cards
card 0: MID [HDA Intel MID], device 0: VT1828S Analog [VT1828S Analog]
card 0: MID [HDA Intel MID], device 2: VT1828S Alt Analog [VT1828S Alt Analog]
card 0: MID [HDA Intel MID], device 3: VT1828S Digital [VT1828S Digital]
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]

I also tried to run the alsamixer, there it seemed that my headphones was muted, but changing it didn't really change anything.

I don't really have a clue where to look next.

---

