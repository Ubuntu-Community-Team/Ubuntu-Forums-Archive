---
title: "setting the default sound device"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by MemoryDump on 2007-10-27
I have 2 sounds cards in my system. 1 is onboard and the other is a PCI Audigy2 card.

I use the Audigy for my 4 speaker setup and the onboard for my headset for online gaming.
My problem is that even though I set my default sound to be the Audigy in the Sound settings, somehow the onboard gets used on occasion.

how can I make it so it's ALWAYS the Audigy card that's the default card. (no matter who is logged even)

thanks
-MD

---

### Post by FNDII on 2007-10-27
I have the same problem. I had it fixed in feisty but now in gutsy its messed up. It is an easy fix, was just so long ago that I cant remember or find the thread.

---

### Post by MemoryDump on 2007-10-29
> **FNDII said:**
> I have the same problem. I had it fixed in feisty but now in gutsy its messed up. It is an easy fix, was just so long ago that I cant remember or find the thread.

same here.. I had found a solution for feisty.. but can't find the info I read to fix it again :(

---

### Post by MemoryDump on 2007-11-09
*bump* please.. 
I need to re-enable my on-board sound device and need to set my Audigy2 as the default for every application!
thxs

---

### Post by jeepee on 2007-11-14
Bump...

I had found how to set it up in Feisty, but in Gutsy, half of my sound applications play with my onboard soundcard, and the other half with my Delta 1010...Weird!

---

### Post by Dave Otter on 2007-11-14
Try the following:-  open terminal  type in
                                                                        asoundconf list

      this will list soundcards
                                            choose one you want
                        in terminal type:- asoundconf set-default-card(card u want to use)

---

