---
title: "wow to use my emu10k1 card and not onboard sound?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by gnychis on 2007-06-28
Hey all,

I have a motherboard which has onboard sound support and I have an old (but great) PCI soundblaster card with the emu10k1 chipset.  After installing ubuntu using a minimal server install, its using my onboard sound.  How do I get it to stop using the onboard and use the emu10k1 card?

Thanks!
George

---

### Post by scxtt on 2007-06-28
disable the onboard audio in the BIOS if you never plan to use it ... but ubuntu should be able to use them both, you just choose which is "master" or "default" ... type **lspci** into the terminal to make sure they're both recognized ...

---

