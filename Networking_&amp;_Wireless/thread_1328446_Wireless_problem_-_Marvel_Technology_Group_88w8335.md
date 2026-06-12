---
title: "Wireless problem - Marvel Technology Group 88w8335 card"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by jimcrow on 2009-11-16
Guys,
One week of sleepless nights! Ubuntu 9.10 - I have set everything up and can see the network (even the strength at 54%) but just cant connect. The only possible problem I found is :

@anley-ubuntu:~$ dmesg|grep ndis*

[   25.951863] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   26.409763] ndiswrapper: driver mrv8000c (Marvell,09/17/2004,3.1.0.19) loaded
[   26.410648] ndiswrapper 0000:02:09.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   26.418537] ndiswrapper: using IRQ 18
[   26.686257] ndiswrapper (set_iw_encr_mode:708): setting encryption mode to 6 failed (C00000BB)

Any help would be great or just point me in the right direction. Thanks

---

