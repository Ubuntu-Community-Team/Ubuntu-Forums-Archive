---
title: "TriHead w/ 2 GFX Cards?"
date: 2008-05-17
forum: Multimedia Software
---

### Post by rapha on 2008-05-17
Hi all,

if this is not possible at all, please excuse the question. I'm trying to run three screens here, which are connected to an older desktop PC containing one Matrox G450 (AGP) and one NVidia GeForce 2 MX400 (PCI).

- When PCI is the primary graphics adaptor in the BIOS, the screen on the NVidia card works perfectly fine. When xorg.conf is configured with Xinerama to include they two screens on the Matrox card, it will work correctly (one of the screens left of the NVidia-connected screen, the other one to its right), but the image will be enormously distorted. Like a TV screen where the station is is off by half a Megahertz...

- When AGP is the primary graphics adaptor in the BIOS, it is not possible at all to configure xorg.conf in such a way that all three screens do something. As soon as you add the NVidia card to the configuration, the MGA driver will complain that there was "no section for PCI device 1:0:0" (which is the Matrox card alright). Most curiously, when the NVidia card is _removed_ from the configuration, both screens on the Matrox card will work _just_fine_ at their maximum resolution - with no distortion or otherwise diminished quality _at_all_.

I did try moving the NVidia card to different PCI slots, but I did not try all combinations possible of juggling the PCI cards around since it didn't seem to help really.

Any hints or ideas on how to get this to work would be greatly appreciated :-)

Regards,
Raphael

P.S.: all three screens are CRTs, if that's significant. The middle one hooked up to the NVidia card can do 2048x1536, the other two can do 1600x1200.

---

### Post by wererabbit on 2008-05-17
I'm not sure on how it works on the Linux side of things, but on the Windows side of things, you'd have to have two drivers loaded, and running at the same time, in order to use two different brands of video cards together.

If you have a dual-head Nvidia agp card lying around, you might want to try that in place of the Matrox and see whether the system is happier.

---

