---
title: "Separate X screens on DVI dual-link?"
date: 2011-05-30
forum: Multimedia Software
---

### Post by Despot on 2011-05-30
Greetings, one and all.

I have an Nvidia Geforce 560 GTX Ti video card with two dual-link DVI outputs on it. Can X be configured to drive two X screens through a single dual-link port? I'm researching the possibility of a quad-head setup with this card.

From what I've read online, it's easy to split the dual-link DVI signal into duplicate single-link DVI signals, which is grand but not useful to me. Each single-link port would need to be mapped to a unique X screen (or a unique part of a very large virtual screen).

I've found that it's possible with the nouveau driver to map outputs to monitors (see [http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors#Permanent_Dual-Monitor](http://en.gentoo-wiki.com/wiki/X.Org/Dual_Monitors#Permanent_Dual-Monitor)), but I haven't found any information on how one might select a particular single-link channel from a dual-link port.

Thanks in advance,
-Despot

---

