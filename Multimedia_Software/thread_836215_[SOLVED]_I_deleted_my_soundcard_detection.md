---
title: "[SOLVED] I deleted my soundcard detection"
date: 2008-06-21
forum: Multimedia Software
---

### Post by billesboelle on 2008-06-21
Hi.

I used the guide stickied with sound problems.

aplay -l listed my card, i used alsamixer, didnt read properly enough and store setting from my motherboard sound settings as the card number my pci sound card has.
Then i did the routine to get my cpu to choose my pci card first (index=0 in alsa-base), and somehow in all thise i get my machine to stop loading drivers or something for my pci sound card (cmi8738 i think)

aplay -l doesnt list my pci card, only the inherent from my motherboard :-(

Any help would be very welcome.

Regards, Alex.

---

### Post by billesboelle on 2008-06-21
problem solved by not acting stupid.

E-g "use the dammed sticky guide again and dont be silly"

---

