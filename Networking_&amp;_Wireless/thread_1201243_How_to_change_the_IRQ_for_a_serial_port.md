---
title: "How to: change the IRQ for a serial port"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by gurt on 2009-06-30
I have a 4-port serial card (SIIG Cyberserial 4S PCIe) installed.

dmesg
```
[    1.104632] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.104714] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.104945] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.105087] serial 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.105195] ttyS1: detected caps 00000700 should be 00000100
[    1.105206] 0000:03:00.0: ttyS1 at I/O 0xbc00 (irq = 17) is a 16C950/954
[    1.105325] ttyS2: detected caps 00000700 should be 00000100
[    1.105336] 0000:03:00.0: ttyS2 at I/O 0xbc08 (irq = 17) is a 16C950/954
[    1.105453] ttyS3: detected caps 00000700 should be 00000100
[    1.105465] 0000:03:00.0: ttyS3 at I/O 0xbc10 (irq = 17) is a 16C950/954
[    1.105478] Couldn't register serial port 0000:03:00.0: -28
```I would like to change ttyS0's IRQ to 17. Is there a way to do it?
Please be gentle, I'm still learning -- Thanks ](*,)

---

### Post by iponeverything on 2009-07-01
Changing the com ports should change the associated irq.

My guess would be that you will have to change com port with a windows utility.

---

### Post by cariboo on 2009-07-01
CHeck your bios, you chould be able to change the hardware address, which should chnage the irq.

---

