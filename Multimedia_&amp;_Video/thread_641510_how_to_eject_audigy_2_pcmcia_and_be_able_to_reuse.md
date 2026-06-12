---
title: "how to eject audigy 2 pcmcia and be able to reuse"
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by lbharti on 2007-12-15
When I use this card in windows, I am able to remove the card and reinsert and be able to use without a problem. In Linux when I eject, the dmesg command shows :

snd-emu10k1: Suspected sound card removal
[39351.624000] pccard: card ejected from slot 0
[39355.076000] CCMP: received packet without ExtIV flag from 00:0f:66:95:2a:70

But when I reinsert the card, I receive these messages in dmesg:
[39471.820000] snd-emu10k1: Suspected sound card removal
[39471.924000] snd-emu10k1: Suspected sound card removal

which is opposite of what I should be seeing. How do I fix it?

---

