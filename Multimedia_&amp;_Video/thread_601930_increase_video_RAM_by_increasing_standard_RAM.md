---
title: "increase video RAM by increasing standard RAM?"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by bluepowder7 on 2007-11-03
on my laptop, the video chipset is the intel 945GML series, and from what i know it doesn't have its own dedicated RAM but rather 'borrows' it from the main system RAM.  is that correct?  being that my laptop currently has 1G of RAM installed (2x512), would i see any video benefits if i were to install 2G of RAM (2x1G)?  basically, i want to improve the video performance of the laptop as much as possible (short of Dremel'ing the mobo and wiring up a dedicated ram board to the video chips), for no specific reason other than to be able to run Compiz Fusion smoothly.  at least for now.  i'm sure i'll find some other way to tax and abuse the system in the near future!!!

laptop is a gateway mx8711, and the ram is DDR2 533MHz.  i assume PC4200?

---

### Post by ddrichardson on 2007-11-03
There's a limit to how much memory is available for graphics chipsets. Moreover in the case of this particular chipset the limitation is the chipset itself rather than the amount of memory. I know there is not much you can do about  this. On most systems, the amount of memory used is allocated from BIOS so have a try and see if it makes a difference.

---

### Post by bluepowder7 on 2007-11-03
BIOS is phoenixBIOS, version 72.14
it looks like the memory is allocated (within BIOS) like this:

Total = 1024MB (dual channel mode)
Slot 1 = 512MB
Slot 2 = 512MB
Video = 8MB

even if i set up a supervisor password and work in supervisor mode in the BIOS, i can't change that portion at all.

whoa!?  only 8 megs is allocated to video?  or is that the default starting point, from which the OS decides to allocate more when needed?

---

### Post by ddrichardson on 2007-11-03
Well, 8Mb Video RAM would make compiz unusable. AFAIK only nVidia Turbocache systems control dynamic memory allocation so I would suggest your first point of contact is your laptop manufacturer to see if there is a BIOS update available.

---

### Post by bluepowder7 on 2007-11-03
checked the site - no bios update available that's more recent than what i have.
i looked at the System -> Admin -> Screen & Graphics, and on the card tab is has a field for video memory, but it's set to automatic and it's grayed out.  hmm...  maybe there IS a way of getting the OS to tweak that???

oh, i found the specs of the laptop - it says up to 224meg shared video memory.  on another spec sheet, it says the default is 64megs.

compiz does work, and it's mostly good, but there's some choppiness on some effects that i'd like to eliminate.

---

### Post by Breathe on 2008-01-26
Have you found something interesting involving this thread in the passed months??
I am looking for some freak that could have been able to do this. Sounds interesting and possible. It's true that you can do hardware configuration soldering some 0 ohms resistances in the chip that governs the GPU but software can do it's own part. And maybe there's some freak out there that has managed to do this. Let's continue looking for a solution to this issue, It would be a great achieve in "hard hack by soft"

---

