---
title: "video capture card almost disappeared in intrepid"
date: 2008-11-30
forum: Multimedia Software
---

### Post by cyrulution on 2008-11-30
After upgrading to Intrepid i cant find any bttv in dmesg any more. that's all about my video capture card:
```
[    0.697858] PCI: 0000:01:00.0 reg 10 32bit mmio: [de000000, deffffff]
[    0.697868] PCI: 0000:01:00.0 reg 14 32bit mmio: [d0000000, d7ffffff]
[    0.697895] PCI: 0000:01:00.0 reg 30 32bit mmio: [dfdf0000, dfdfffff]
```
```
[    2.041795] pci 0000:01:00.0: Boot video device
[    2.041819] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
```
and lspci says:
```
02:0d.0 Multimedia video controller: Brooktree Corporation Bt879(??) Video Capture (rev 11)
02:0d.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```
It's such a cheap Ebay 4-port video capture card. It used to work in Gutsy as bttv card=77
How can I get it working again? Take out an reinstall?

---

### Post by cariboo on 2008-11-30
Have you checked to see it the bttv modules is loaded? In a Applications-->Accessories-->Terminal type:

```
lsmod | grep bt
```

Jim

---

