---
title: "reliable crystalhd suppoort"
date: 2012-11-30
forum: Multimedia Software
---

### Post by markosjal on 2012-11-30
i have tried compiling the current drivers from source as well as those from universe repo . Sometimes crystal hd does not load, and sometimes loads fine.

Does anyone know whats wrong?

# dmesg | grep crystalhd
[   12.951736] Loading crystalhd v3.10.0
[   12.951782] crystalhd 0000:02:00.0: Starting Device:0x1612
[   12.951803] crystalhd 0000:02:00.0: enabling device (0000 -> 0002)
[   12.951820] crystalhd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.955580] crystalhd 0000:02:00.0: irq 42 for MSI/MSI-X
[   13.232164] crystalhd 0000:02:00.0: setting latency timer to 64
[   68.755673] crystalhd 0000:02:00.0: Opening new user[0] handle
[   69.275839]  [<d081c012>] bc_kern_dma_alloc+0xe2/0x100 [crystalhd]
[   69.275861]  [<d081f141>] crystalhd_hw_setup_dma_rings+0xf1/0x200 [crystalhd]
[   69.275874]  [<d081d170>] ? bc_cproc_check_inbuffs+0x110/0x110 [crystalhd]
[   69.275886]  [<d081d236>] bc_cproc_notify_mode+0xc6/0x150 [crystalhd]
[   69.275898]  [<d081b860>] ? chd_dec_alloc_iodata+0x70/0xc0 [crystalhd]
[   69.275909]  [<d081b9b1>] chd_dec_ioctl+0xa1/0x170 [crystalhd]
[   69.275921]  [<d081d170>] ? bc_cproc_check_inbuffs+0x110/0x110 [crystalhd]
[   69.275932]  [<d081b910>] ? chd_dec_free_iodata+0x60/0x60 [crystalhd]
[   69.278514] crystalhd 0000:02:00.0: Insufficient Memory For RX
[   69.300441] crystalhd 0000:02:00.0: Closing user[0] handle via ioctl with mode 417a00
[   69.404044] crystalhd 0000:02:00.0: crystalhd_dioq_fetch: Invalid arg
[   69.404053] crystalhd 0000:02:00.0: ioq not initialized
[   69.404058] crystalhd 0000:02:00.0: crystalhd_dioq_fetch: Invalid arg
[   69.404063] crystalhd 0000:02:00.0: ioq not initialized
[   69.404068] crystalhd 0000:02:00.0: crystalhd_dioq_fetch: Invalid arg
[   69.404073] crystalhd 0000:02:00.0: ioq not initialized

---

