---
title: "Two sound card deactivating: how to?"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by tommasoviola on 2007-06-06
Hi, problems again with sound card. I just got my Ubuntu Studio Distro wich is good but still..

typing

cat /proc/asound/cards

this is what I've got:

tommi@studiotommi:~$ cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with AD1888 at 0x1000, irq 19
 1 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xeea0, irq 20

so if I'm right it seems that there are two soundcards: one external (Audigy) and one integrated in my motherboard.
How can I deactivate the VIA one and make Audigy sound?
thanks
Tommi:D

---

### Post by mainalisuyog on 2007-06-06
You could disable it from the BIOS. Inside the bios, go to "integrated peripherials" and disable the onboard graphics card.

---

