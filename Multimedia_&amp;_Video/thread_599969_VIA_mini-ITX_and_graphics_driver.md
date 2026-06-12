---
title: "VIA mini-ITX and graphics driver"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by geirergoy on 2007-11-01
Hello folks!
I have a Mini ITX motherboard with 1200 MHz.
The graphics card is called CLE266.

My problem:
I have to use the VESA driver, and all types of video lag.
Not much, just enough to make it really annoying.

I have OK resolution ant everything works well.
My problem is that the videos have a low frames per second or what you'd call it.

And of course: I can't play PPracer...

It is said that this graphics card soes support Linux. But I have never been able to get it to work properly. If I run DPKG-reconfigure xserver-xorg, there is a VIA driver, but it does not work for me.

I can't install an old PCI card, because the PCI slot is already in use for WiFi. No room for the riser card.

---

### Post by Light- on 2007-11-01
This happens because the VESA driver is the generic driver for almost all video cards, and it only gives you the bare minimum required to display things on the screen, fancy things like hardware acceleration dont work.

The best way to fix this would be to buy a card that isnt obscure. A cheap nvidia card would do the trick nicely i believe, unless your card is onboard, and you have no AGP slots

Ae you sure the VIA driver you were trying to use was the correct one for your card?

---

### Post by geirergoy on 2007-11-01
My computer is a Mini-ITX (google it).
The motherboard is 17x17 centimetres, and the main point with these computers is to make things as small as possible.

Yes, it's onboard... I also need the TV out... Do these cheap nVidia cards have video out?

I have PCMCIA on this motherboard. I could buy a PCMCIA wifi card, and free the PCI slot for graphics... But that's the last resort.
I have PCMCIA and PCI. No AGP.

---

