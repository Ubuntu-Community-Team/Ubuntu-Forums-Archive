---
title: "Kworld DVD Maker PCI"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by Lancerlan on 2007-08-26
Hi 
Several months ago I bought Kworld video capture card and since then I haven't been able to make it run. When capturing with mplayer or tvtime I only get a distroted image wiht no meaning an dno sound. The pci card is called "DVD maker PCI" and has a Conexant CX23883 chip. Now I am running fesity fawn and the dmesg output is the following: (only what I think it's important)

[   39.517816] cx2388x v4l2 driver version 0.0.6 loaded
[   39.518093] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   39.518101] ACPI: PCI Interrupt 0000:01:06.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 21
[   39.518137] CORE cx88[0]: subsystem: 0000:0000, board: KWorld LTV883RF [card=16,insmod option]
[   39.518140] TV tuner 2 at 0x1fe, Radio tuner -1 at 0x1fe
[   39.525981] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[   39.541080] usbcore: registered new interface driver gspca
[   39.541084] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   39.637424] tveeprom 2-0050: Huh, no eeprom present (err=-121)?
[   39.637475] input: cx88 IR (KWorld LTV883RF) as /class/input/input3
[   39.637503] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 21, latency: 32, mmio: 0xfb000000
[   39.670606] cx88[0]/0: registered device video1 [v4l2]
[   39.670640] cx88[0]/0: registered device vbi0
[   39.670658] cx88[0]/0: registered device radio0
[   39.694968] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   39.694972] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   39.694991] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   39.754615] nvidia: module license 'NVIDIA' taints kernel.

Has anybody idea whats wrong here?

Thanks
Lancer
:confused:

---

