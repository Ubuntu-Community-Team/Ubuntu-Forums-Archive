---
title: "Switching to full duplex with an Intel 82567LM-3 card causes packet loss to manifest"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by ph8 on 2011-12-23
Hi all,

I have a new build machine that is having problems switching to full duplex in Natty (i've not gone to Oneiric because of the new desktop/gnome causing issues with NX which is how users login to these remote desktop machines).

The machine boots and goes to half duplex. When I manually switch to full duplex @ 100Mbit with ethtool every 10th ping or so gets dropped (packet loss) and it's very puzzling.

The machine had Windows installed and at that time worked fine, so I don't think it's a machine hardware problem.

It is connected to a 100mbit switch which is confirmed working (from several other machines connected to it), i have tried three different ports on the device just to be sure.

I have also tried switching out the network cable for a replacement.

So my only conclusion is that it must be something with how the kernel (2.6.38-13-generic-pae) supports this particular brand of network card. Has anyone got any ideas on how I might fix this/things i can check next?

As I say it works 'fine' in half duplex, if you count half duplex as fine!

All ideas gratefully received.

Best Regards,

ph8

---

### Post by dandnsmith on 2011-12-23
Just what do you want to do with full duplex? I don't believe that is the standard way of operating.
Have you checked that the card/chipset is capable of 'mastering' - this may be the cause of the non-full duplex setting.

---

### Post by ph8 on 2011-12-23
Sorry what? Full duplex is absolutely the norm!

---

