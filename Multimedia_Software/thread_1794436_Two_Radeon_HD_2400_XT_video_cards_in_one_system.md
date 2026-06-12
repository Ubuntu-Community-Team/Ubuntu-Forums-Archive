---
title: "Two Radeon HD 2400 XT video cards in one system"
date: 2011-07-01
forum: Multimedia Software
---

### Post by daehenoc on 2011-07-01
Hi all,

I have a HP/Compaq 7900 SFF PC and it has a motherboard with two PCIe x16 slots.  I have two HD 2400 XT (each dual head) video cards, so I thought I could drop them in there and have four monitors off my desktop :D

I've popped them in there and done a fresh install of Ubuntu 11.04.  Rebooted, installed restricted drivers, rebooted, and I have both monitors attached to the first video card.  All works as expected, I can configure the monitors how I want.

If I attach a third monitor to the other video card, I can't see anywhere in the control center to configure that video card or that monitor.

Any ideas if this video card is supported in this configuration?  Should I try the driver directly off the ATI site?

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]
20:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]
```

---

### Post by daehenoc on 2011-07-05
OK, all fixored!  I put the video cards in the system one at a time in the different slots, to confirm that both cards worked, as well as confirming that both PCI-e slots worked, and now that I have so confirmed that everything works, I've got all my (four) monitors attached and configured, yay!

Don't know what was going on that first day, all fixed now :)

---

