---
title: "Moving backend to a new machine?"
date: 2011-06-11
forum: Mythbuntu
---

### Post by movieman on 2011-06-11
So currently I have a 10.04 backend which is probably running 0.23. I have to get a digital tuner because we're losing analogue soon and the best deal seems to be the HVR-2250 which is PCI-Express, so I need a new machine. And it looks like the new i5 chips aren't properly supported prior to 11.04.

What I'd like to do is copy all the old recordings over to bigger disks in the new machine so I can keep them. But I presume that will, at least, mean going from 0.23 to 0.24. Is there some way to do this in a reasonable manner?

Edit: actually, having read the HVR-2250 thread further down the page, maybe my picking that card is a mistake :) ?

---

### Post by klc5555 on 2011-06-11
Your current analog tuner should get plenty of work, since most cable companies now low-level encrypt everything except the locals. The settop box or DTA (channel-changed via LIRC) decrypts this and sends it to your analog tuner that is permently set on ch. 3 or 4. The locals (only) will be available in SD in clear QAM (digital directly viewable without a box), maybe in HD the same way, and also along with the rest of your former analog lineup in the SD-to-analog signal through the settop box or DTA.

When a cable co. goes from analog to digital, it's usually a two step process. In the first step, most analogs above ch. 20 disappear, and reappear as clear QAM. This nice state of affairs is usually over in a few months, once the cable co. gets frequency assignments and such straightened out, and then overnight >poof< most of the QAM stations get encrypted and become only viewable through the box.

If you replace your current tuner(s) with a hybrid one that also does digital, you'd like to purchase one that uses two physically separate cable inputs, one for digital and one for analog, since a settop box or DTA doesn't do passthrough, and if a box is hooked to a card input, the settop box's signal is all that card input is going to get.

With the database, once your old one is restored into place (take and keep multiple backups of your older mythconverg before starting!) running the backend setup (which you have to do anyway for the new tuning hardware) should take care of upgrading the database. 

Or I suppose you could (after making backups of your current mythconverg, just in case) upgrade your current version of mythtv to 0.24 on your current 10.04 system, since builds are available, which will also upgrade the database. A backup of this newer mythconverg will already be at the correct level when you restore it into your new machine.

---

