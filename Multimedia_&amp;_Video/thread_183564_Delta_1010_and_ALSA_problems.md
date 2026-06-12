---
title: "Delta 1010 and ALSA problems"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by kelcey_s on 2006-05-28
Ok, so I have been scouring the various fora and help docs and cannot fix this problem. I would be really appreciative if anyone has any ideas.

I have a M-Audio 1010 and am running Breezy 5.10, it seems that eveyone else thinks that a 1010 works straight off. However, I can't run Qjackctl without a constant stream of xruns and anytime I go near alsa i just get pop and crackles. I have got the everyday sound working in the Multimedia Systems Selector using OSS (again ALSA doesn't work). I have the .asoundrc file which contains:        

pcm.ice1712 {
           type hw
           card 0
        }

        ctl.ice1712 {
           type hw
           card 0
        }

Any ideas would be amazingly helpful.

---

### Post by kelcey_s on 2006-05-28
Its always the way. After days of fiddling I post this thread and then I immediately get Jack working fine. Sorry to bother you all.

---

### Post by dolson on 2006-05-28
Haha, no problem. Post sooner next time. Then you won't waste days of fiddling, and your problem will instantaneously resolve once you post. ;)

---

