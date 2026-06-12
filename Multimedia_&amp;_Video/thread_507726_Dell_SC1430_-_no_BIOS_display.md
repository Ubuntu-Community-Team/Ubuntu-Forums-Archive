---
title: "Dell SC1430 - no BIOS display"
date: 2007-07-23
forum: Multimedia &amp; Video
---

### Post by The Foz on 2007-07-23
I know that this is not really a Linux issue, but maybe someone knows the answer anyway.

I have a new Dell SC1430. It contains an ATI ES1000 graphics driver chip on the motherboard (not that Dell tells you that when you order!).

I am anyway having issues with the Linux drivers for the ES1000, but I am currently able to get things displayed. I get the Ubuntu splash screen, and the desktop; all the applications work (I just can't display full screen videos at full speed - but that is another issue, covered in another thread).

**What I don't get is any display from the BIOS or from GRUB.** The machine doesn't boot automatically (or maybe I just haven't waited long enough). By trial and error I have found that <F1> <CR> (or maybe that is <ESC><CR>?) will boot Linux in the default mode. Luckily I have so far never had to boot it into any other mode, but one day I know I will need to. It seems that neither the BIOS provided by Dell, nor GRUB, can recognise and drive the ES1000. I would like to be able to boot my machine without guesswork.

Has anyone else experienced this problem?

---

### Post by phr0ze on 2007-10-24
I'm getting this system in the next 2 days and I'll try to post back here. I don't see how dell would ship this with no BIOS display.

---

### Post by The Foz on 2007-10-25
I would appreciate hearing how you get on.

Today I plan to buy another video car (NVIDIA), and set that as my default display. I will also post the results.

---

### Post by phr0ze on 2007-10-27
What are you doing about the slot? Cutting it?  Let me know which card you get. I just booted mine and it's nice. I have the live CD running. One core is at about 5%, and the other 7 are unused. I'll have to do something about that.

---

### Post by phr0ze on 2007-10-27
Ok. I got an old ATI x300 from my brother. He said I can do what I want with it, so I cut the last 33 contacts off the card. According to Tom's Hardware, those are the contacts to remove to go from x16 to x8. 

The card fits in the slot and it works! Now to find a nice nvidia to chop up.

I really want to avoid voiding the dell warranty by cutting the slot.

---

