---
title: "No Sound on Realtek ALC888"
date: 2008-01-01
forum: Multimedia &amp; Video
---

### Post by Technogenius on 2008-01-01
I have a K9AGM2-L motherboard with an onboard ALC888 HD sound card. I got the driver for it (realtek-linux-audiopack-4.07a), but every time I install it, no cards are detected. It asks me if I want to probe legacy ISA sound cards/chips, it just pops up with an empty box that has an ok button. Any idea what's going on here? I'd really like to get my sound working in Linux (it works fine in windows).

---

### Post by wasing on 2008-01-03
I'm having the same problem with my Gigabyte GA-MA69VM-S2 it has the same audio set (ALC888) but i cant get any sound either. i was looking through my computer information and it recognizes it as an ALC88**3** and it has the following sound driver  

Type 10: Alsa Emulation.

if you find an answer to your problem please post it here

---

### Post by Technogenius on 2008-03-05
It seems to work fine on my system now. I think it was getting confused with the two other sound cards I had installed also. I just took those out and it worked!

---

