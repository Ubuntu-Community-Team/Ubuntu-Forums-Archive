---
title: "No DRI with Matrox G450."
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by EvilGrin on 2006-07-08
I have a Matrox 32mb G450 (AGP). I cannot seem to get DRI to work. The configuration is correct in the xorg.conf so I suspected that the kernel modules were not loading. I was correct. I had to manually add 'agpgart' 'drm' and 'mga' into my /etc/modules.conf.

However the agpgart module does not load correctly.

```
[4294696.362000] Linux agpgart interface v0.101 (c) Dave Jones
[4294696.465000] [drm] Initialized drm 1.0.0 20040925
[4294696.518000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294696.518000] [drm:drm_fill_in_dev] *ERROR* Cannot initialize the agpgart module.
[4294696.518000] DRM: Fill_in_dev failed.
```

DRI can work on this box. It was working fine under Gentoo.

---

### Post by EvilGrin on 2006-07-09
I figured this out. I had to load the correct agp support module for my motherboard before loading agpgart. In my case this was intel-agp as I have a 440BX based motherboard.

---

