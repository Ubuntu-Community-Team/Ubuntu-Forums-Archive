---
title: "SoundBlaster 16 (ISA) error"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by GooOS on 2006-07-07
The problem is that the soundcard is detected by the alsaconf, and at the end it says that it was successfully configured, but when I hit alsamixer i get this messege:
```
alsamixer: function snd_ctl_open failed for default: No such device

```

and when i try to modprobe it manualy i get:
```
# modprobe snd-sb16
FATAL: Error inserting snd_sb16 (/lib/modules/2.6.15-25-386/kernel/sound/isa/sb/snd-sb16.ko): No such device

```

help needed!

thnx

---

### Post by GooOS on 2006-07-08
OK, here a detailed what-i-did:

```
alsaconf
((opens the welcome screen))
(searching for soundcards)
No supported PnP or PCI card found.
Would you like to probe legacy ISA sound cards/chips? 
(yes)
(i choose sb16)
(probing sb16)
(a window with only OK opens in console i hit OK)
(back to console... no sound, no soundcard configured!)

```

please help me.

---

### Post by Jack Jebedee on 2006-08-01
I have exactly the same problem.  Can't get it to work to save my life.  I switched an older ISA SB16 with one that is two years newer (but still ancient).  It didn't make a difference.  "No such device" was returned for both cards.  I can't wait to learn what's gone wrong!

... JJ

---

### Post by GooOS on 2006-08-06
Fixed it, the solution was to configure the BIOS that the IRQ5 is assigned to LEGACY ISA.
then modprobe snd-sb16
worked like a charm



at last!

---

### Post by corax on 2007-02-21
Hey GooOS ! You are the man !

THANKS VERY MUCH !!! really :) It worked for me too !! But I think I would have not come up with this ever ! :) Good work !

---

### Post by Mark Lobjoit on 2007-05-03
Thanks very much for this info! I have booted from the feisty desktop CD and was perturbed to find no sound. I was thinking to go ahead with the install and see if I could work it out later but this fixed it like a dream.

For the benefit of Ubuntu newcomers like myself, I would just add that the full command, in a terminal window, would be:

[FONT="Courier New"]sudo modprobe snd-sb16[/FONT]

Also, so long as you have **some** IRQ configured in BIOS for legacy ISA cards, it probably doesn't have to be IRQ5.

---

