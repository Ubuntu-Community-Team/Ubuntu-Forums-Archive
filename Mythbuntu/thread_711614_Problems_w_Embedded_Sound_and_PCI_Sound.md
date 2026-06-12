---
title: "Problems w/ Embedded Sound and PCI Sound"
date: 2008-02-29
forum: Mythbuntu
---

### Post by ebullient on 2008-02-29
So.  I'm setting up a mythbuntu box and the embedded sound on the motherboard appears to be fried.  No problem, I have an Audigy Live! 24 bit and a Diamond 5.1 card.  So I install one (I've tried both) and with some finagling like setting the pci sound to default I get audio when watching TV.  But.  It is delayed.  I think the problem lies in the fact that there is no actual capture line named in the mixer for the card, when I had that problem with motherboard sound I'd just use amixer to set it up on the capture line and I can't seem to do that with the pci boards.

I've tried setting the device in mythbuntu setup, I've tried just about every different way to do that all with no results.  Surely there is some way to use the pci sound but I can't seem to figure out how to get tv audio without lag.  Help?  I'm considering replacing the motherboard with one that has working embedded sound, that's how far this has gone.

---

### Post by ebullient on 2008-02-29
Figured it out.  After determining which was the correct capture line (CD in this case, I have the internal cable), muting and setting it to capture, I switched the pass-through audio device in the General settings to the other, non-default option I had and it worked.

FINALLY.

---

