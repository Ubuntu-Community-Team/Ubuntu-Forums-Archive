---
title: "nVidia old with New?"
date: 2010-11-19
forum: Multimedia Software
---

### Post by 67comet on 2010-11-19
Hello; I'm having some issues getting my old(er) nVidia card to play nice with my other old(er) nVidia card.

I've got an AGP GeForce 7600 GS running 2 HP 2009m monitors (just fine) and a PCI GeForce2 MX/MX 400 I want to run a separate X screen (TwinView for the 2 LCD HPs/Separate X for the MAG 17" LCD).

Back last summer I tried to get them to work together by using the older 76.xxx nVidia driver but it never worked quite right.

Since the older card is not really supported by nVidia any longer; may I use the nv driver to run it (no 3D) as my extra screen for chat windows, movies, Banshee, slide shows .. what ever? And my currently installed "current" driver for the other two? I used to hand write my xorg.conf files (I ran 5 monitors at one time a few years ago; but all the vid cards were legacy) so I could probably figure out how to re-write xorg.conf if I had a little kick start.

Thank you,

---

### Post by P4man on 2010-11-19
IM not sure, I tried getting an ATI and nVidia card to work together (just for the heck of it), and I found it impossible to get working unless I used the nouveau driver for the nvidia card and the open radeon drivers for the ATI card. Installing restricted drivers for either would ruin it (display corruption, black screen or not even starting X) no matter how much I fiddled with xorg.conf.
Even with the open drivers, I still couldnt enable desktop effects

Anyway, Id try nouveau drivers.

---

