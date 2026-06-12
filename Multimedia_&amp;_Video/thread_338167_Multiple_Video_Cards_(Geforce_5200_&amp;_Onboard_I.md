---
title: "Multiple Video Cards (Geforce 5200 &amp; Onboard Intel i810)"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by Cyhawk on 2007-01-14
Ok, im using Ubuntu Edgy, and I have a Geforce 5200 installed. I also have an onboard Intel i810 I would like to use with Xinerama. Im not very good at this, but is it possible to have both video cards enabled? (I can deal with the xconf later, i just want both to work)

Right now, the 5200 is enabled and working properly. Using the nv driver (Im one of the small population who cant use the new drivers, but thatsanother issue, nv works just fine for now)
The i810 is enabled in the bios and will work when the 5200 is removed with the i810 driver enabled it will run X.

So how can i get both video cards to work at the same time?

---

### Post by pseudonym on 2007-01-14
Check out the last two posts in [this]("http://www.ubuntuforums.org/showthread.php?t=329754&highlight=multi-brand") thread.

HTH

---

### Post by Cyhawk on 2007-01-14
Ive done what the tutorial has said (as well as any possible relavent posts here) xconf has both entries correctly, but the problem is, its an onboard video card. Not to mention my bios only allows two options, AGP/Auto (but the other card/monitor works just fine and X starts up when the agp is unplugged)

Maybe its my motherboard, and it disables the onboard video if an agp slot is installed... I'll have to research it, but ive never thought it would be a problem. Bah!

Anyone have experience getting this type of setup to work with an on-board video card and an agp? It seems no ones really done this, course most people could probably afford a PCI video card ;)

---

