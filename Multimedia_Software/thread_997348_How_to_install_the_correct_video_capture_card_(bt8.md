---
title: "How to install the correct video capture card (bt878)"
date: 2008-11-29
forum: Multimedia Software
---

### Post by cyrulution on 2008-11-29
I have a strange problem configuring my video capture card for Zoneminder in Hardy. In dmesg i´m getting
```
 37.041163] bttv: driver version 0.9.17 loaded
[   37.041171] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   37.063591] usb 1-2: new low speed USB device using ohci_hcd and address 14
[   37.131638] bt878: AUDIO driver version 0.0.0 loaded
[   37.131732] bt878: Bt878 AUDIO function found (0).
[   37.131765] ACPI: PCI Interrupt 0000:02:0d.1[A] -> GSI 21 (level, low) -> IRQ 18
[   37.131777] bt878_probe: card id=[0x0], Unknown card.
[   37.131779] Exiting..

```
How can I teach dmesg to find the following options (from ZM forum):
```
options bttv card=77 tuner=4 radio=0 triton1=0 vsfx=0 autoload=0
```

---

