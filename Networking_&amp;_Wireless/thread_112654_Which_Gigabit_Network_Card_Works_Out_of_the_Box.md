---
title: "Which Gigabit Network Card Works Out of the Box"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by ptmurphy on 2006-01-04
Can anyone give recomendations based on experience of which Gigabit Ethernet cards work out of th box with Ubuntu Breezy?

I am upgrading my network to gigagbit and have found precious little on Gigabit ethernet on Ubuntu.  What I have found is usually horror stories.  This leads me to believe it is either very painless and most cards work, or very few are upgrading to gigabit yet.

The two that seem the best option to me so far are teh D-Link DGE-530T and the Netgear GA311.

Thanks,

Phillip

---

### Post by MetalMusicAddict on 2006-01-04
I have a [SMC EZ Card 1000]("http://www.buy.com/prod/EZ_Card_1000_SMC9452TX_Network_adapter/q/loc/410/10309930.html") (SMC9452TX V.2)

Ive had no probs on 3 machines. :)

---

### Post by ptmurphy on 2006-01-05
[QUOTE=MetalMusicAddict]I have a [SMC EZ Card 1000]("http://www.buy.com/prod/EZ_Card_1000_SMC9452TX_Network_adapter/q/loc/410/10309930.html") (SMC9452TX V.2)

Ive had no probs on 3 machines. :)[/QUOTE]

Thanks for the feedback. Do you get good Gigabit performance out of the card?

---

### Post by mpvano on 2006-01-05
I haven't used them much yet, but The Linksys EG1032 ver2 seems to work well for me in several machines.

Warning however:

This card and a few other gigabit cards don't seem to work in some older machines and with certain asian motherboards. They don't even show up as being installed in lshw!

I suspect that some of the chipsets only work in machines with 3.3v power on the PCI bus, and there seems to be some confusion in older machines about whether that was a mandatory part of the specification or not.

Cards like this seem to say that they require "PCI 2.2" on the box.

Despite reports to the contrary, the latest kernel builds from Ubuntu SEEM to support most of the common chipsets reasonably well.

Mario

---

### Post by ptmurphy on 2006-01-06
[QUOTE=mpvano]Despite reports to the contrary, the latest kernel builds from Ubuntu SEEM to support most of the common chipsets reasonably well.

Mario[/QUOTE]

Mario,

Thanks for the information.  It is encouraging that most Gigabit cards do work with Ubuntu not-adays.  I guess I need to just try it...  Just $25 for the card!

Anyone else have positive experience with any particular Gigabit card?

Thanks.

---

### Post by MetalMusicAddict on 2006-01-06
[QUOTE=ptmurphy]Thanks for the feedback. Do you get good Gigabit performance out of the card?[/QUOTE]
Im not sure how to test the speed in Ubuntu but it seems pretty fast moving around 7gig .iso images around my network. I also rip/encode mp3s to a network drive no problem.

I also bought a SMC 4-port switch.

---

