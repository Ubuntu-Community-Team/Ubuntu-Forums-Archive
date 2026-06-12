---
title: "2 cards detected, yet my computer only has one... (need to get rid of it)"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by lechium on 2006-07-14
Hi,

I just installed Kubuntu, and came across something pretty odd: apparently installation process decided that I have 2 sound cards, while my computer only has one.

Here's my /proc/asound/cards
```
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xefffc000 irq 169
1 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xdc80, irq 177
```
The intel one.... well its no real. However my system seemed to have decided to send all audio though the first, bogous card.

I can access volume settings and such on my 2nd card though alsa -s 1, however I cannot find a way to actually remove the card, and re-route sound to the real card.

any suggestions?

wbr,
Victor

---

