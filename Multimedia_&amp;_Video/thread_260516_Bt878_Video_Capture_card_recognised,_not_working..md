---
title: "Bt878 Video Capture card recognised, not working."
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by corstar on 2006-09-18
Hello, 
I'm hoping to get my bttv card working under dapper.
I've been following these instructions [http://www.burghardt.pl/wiki/articles/pixelview_playtv_pro_pv-bt878p_9x#bttv_driver]("http://www.burghardt.pl/wiki/articles/pixelview_playtv_pro_pv-bt878p_9x#bttv_driver")

The output of my dmesg say's the driver is loaded but I tried to scan channels using scantv command, (in the correct tv zone) and nothing is recieved.

I have a working antenna connection plugged in.

Can anyone help with this?

```
[17179592.808000] Linux video capture interface: v1.00
[17179592.876000] sis900.c: v1.08.09 Sep. 19 2005
[17179592.876000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179592.880000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 9.
[17179592.892000] 0000:00:04.0: Using transceiver found at address 9 as default
[17179592.892000] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 217, 00:11:5b:ef:56:1f.
[17179592.896000] bttv: driver version 0.9.16 loaded
[17179592.896000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179592.896000] bttv: Bt8xx card found (0).
[17179592.896000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179592.896000] bttv0: Bt878 (rev 17) at 0000:00:0b.0, irq: 217, latency: 32, mmio: 0xec005000
[17179592.896000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179592.896000] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[17179592.900000] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[17179592.900000] bttv0: using tuner=-1
[17179592.900000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179592.904000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179592.908000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179592.908000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179592.912000] bttv0: registered device video0
[17179592.912000] bttv0: registered device vbi0
[17179592.932000] bt878: AUDIO driver version 0.0.0 loaded
[17179592.932000] bt878: Bt878 AUDIO function found (0).
[17179592.932000] ACPI: PCI Interrupt 0000:00:0b.1[A] -> GSI 19 (level, low) -> IRQ 217
[17179592.932000] bt878(0): Bt878 (rev 17) at 00:0b.1, irq: 217, latency: 32, memory: 0xec006000
[17179592.948000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 225
[17179593.060000] usbcore: registered new driver hiddev
[17179593.264000] intel8x0_measure_ac97_clock: measured 54856 usecs
[17179593.264000] intel8x0: clocking to 48000
[17179593.748000] Real Time Clock Driver v1.12
[17179593.760000] input: PC Speaker as /class/input/input1
[17179593.796000] Floppy drive(s): fd0 is 1.44M
[17179593.812000] FDC 0 is a post-1991 82077
[17179593.976000] parport: PnPBIOS parport detected.
[17179593.976000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]

```

---

### Post by corstar on 2006-09-25
bump

---

### Post by ttremeth on 2006-11-07
Same issue

---

