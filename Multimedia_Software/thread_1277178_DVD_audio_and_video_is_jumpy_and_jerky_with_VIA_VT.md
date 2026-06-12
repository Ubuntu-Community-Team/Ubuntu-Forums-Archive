---
title: "DVD audio and video is jumpy and jerky with VIA VT6421 SATA card"
date: 2009-09-28
forum: Multimedia Software
---

### Post by feizex on 2009-09-28
Hi Guys,

It took me a while to nut this one out and I thought that I would share. 

Scenario is this:
Athlon XP 2100+ 
KT266A AGP Socket-A mobo
Nvidia Geforce3
512MB DDR-266 RAM
Clean 9.04 Desktop build
Added VIA VT6421 PCI-X sata card and Liteon DVD-ROM

Can play videos from network share perfectly, but DVD playback is jumpy and jerky, especially audio.

I tried std Totem, then Totem (xine) and VLC. All had same issue.

As a red-herring the CPU usage was quite high ~ 90%. I now put this down to waiting on H/W rather than CPU working hard. Now that it is fixed it is down below 70%.

I had also thought that Video card drivers may be to blame, but this was not the case.

Turned out that the SATA card that I had installed, shared the same IRQ as the sound card. 

[B]SOLUTION: move the SATA card to another Slot - one that doesn't share IRQ with video or sound card.
[/B]
This proved a little difficult in my case since I had to also swap out video card because my large aftermarket cooler/fan combo was blocking the only slot that wasn't using the same IRQ. And before you ask, yes I replaced with same type of card, just with std cooling. :P

Hopefully this should help some other poor souls that are battling same issue. It may not be software!

BTW, if you want to know which IRQ is assigned to what, you can look in BIOS, or on bootup screen it normally prints PCI IRQ assignments just before it boots OS. Soundcard may be listed as Multimedia device.

Regards,
Feizex.

:guitar:

---

