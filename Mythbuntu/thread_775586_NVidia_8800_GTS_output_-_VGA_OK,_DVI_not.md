---
title: "NVidia 8800 GTS output - VGA OK, DVI not"
date: 2008-04-30
forum: Mythbuntu
---

### Post by dajt on 2008-04-30
Hi,

If I connect my 8800GTS card to my LG 42RT11 SD plasma TV using a DVI-VGA converter, plugging a VGA cable into the TV, things seem to work.

If I use a DVI-DVI cable, I see all the boot up messages and the Mythbuntu loading screen, but as soon as the desktop should appear my TV starts telling me there is no signal.

I'm confused because the signal is coming from the same place in the PC, just going into a different connector on the TV. Obviously the fact a DVI-VGA converter is in use in one instance is a difference, but how would the PC know that and behave differently?

I did not as the NVidia drivers to use the TV-out function of the card.

The straight DVI connection gives me a slightly better picture on the TV so I'd much rather use that.

Has anyone else seen this?

Regards,
David.

---

### Post by majoridiot on 2008-04-30
> **dajt said:**
> Hi,

If I connect my 8800GTS card to my LG 42RT11 SD plasma TV using a DVI-VGA converter, plugging a VGA cable into the TV, things seem to work.

If I use a DVI-DVI cable, I see all the boot up messages and the Mythbuntu loading screen, but as soon as the desktop should appear my TV starts telling me there is no signal.

I'm confused because the signal is coming from the same place in the PC, just going into a different connector on the TV. Obviously the fact a DVI-VGA converter is in use in one instance is a difference, but how would the PC know that and behave differently?

I did not as the NVidia drivers to use the TV-out function of the card.

The straight DVI connection gives me a slightly better picture on the TV so I'd much rather use that.

Has anyone else seen this?

Regards,
David.

your display is ok @ boot because it is running in default vga modes.  once mytbuntu takes over, 
the X server is controlling the display... and is failing, because it is probably not properly configured
to use the DVI output.

you'll get a lot better feedback if  you post a copy of your current /etc/X11/xorg.conf

---

