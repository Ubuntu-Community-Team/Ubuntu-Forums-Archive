---
title: "Nvidia Graphic Card and ATI TV tuner problem working together"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Blackie_Chan on 2010-01-11
Hi All, 

I recently updated my computer. I got a new Nvidia Graphic Card and using my old ATI TV Wonder pro. 

After my upgrade, when I start tvtime I am unable to adjust the volume, it's stuck at 0. 

After some investigating, I think the problem is because both the graphic card and the tv card are using the same irq number because of 

```
blackie@ubuntu:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7
  0:        133          0          0          0          0          0          0          0   IO-APIC-edge      timer
  1:          0          0          0        684          0          0          0          0   IO-APIC-edge      i8042
  4:          0          0          0          7          0          0          0          0   IO-APIC-edge
  8:          0          0          0          1          0          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          0          0          0      56495          0          0          0          0   IO-APIC-edge      i8042
 16:          0          0          0          0          0          0          0     809519   IO-APIC-fasteoi   ehci_hcd:usb1, cx88[0], nvidia
 18:          0          0          0          0          0          0          0          0   IO-APIC-fasteoi   ahci
 19:          0     206566          0          0          0          0          0          0   IO-APIC-fasteoi   pata_jmicron
 21:          0          0      63413          0          0          0          0          0   IO-APIC-fasteoi   ata_piix, ata_piix
 22:          0          0          0          0          0          0          0     136174   IO-APIC-fasteoi   HDA Intel
 23:          0         69          0          0          0          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb2

```

```

blackie@ubuntu:~$ dmesg | less
[   16.150066] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[   16.150095] cx8800 0000:07:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.150326] cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected], frontend(s): 0
[   16.150328] cx88[0]: TV tuner type 44, Radio tuner type -1
...
[   16.352494] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.352500] nvidia 0000:01:00.0: setting latency timer to 64
[   16.352567] NVRM: loading NVIDIA UNIX x86 Kernel Module  190.53  Tue Dec  8 18:51:41 PST 2009
[   16.360585] tuner-simple 0-0060: creating new instance
[   16.360587] tuner-simple 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   16.363011] cx88[0]/0: found at 0000:07:01.0, rev: 3, irq: 16, latency: 64, mmio: 0xfa000000
[   16.363018] IRQ 16/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.363049] cx88[0]/0: registered device video0 [v4l2]
[   16.363061] cx88[0]/0: registered device vbi0
[   16.891442] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   17.704031] zc3xx: probe 2wr ov vga 0x0000


```

What can I do to get the volume back? Is the problem related to irq conflicts? Can I assign dedicated irq to each card?

This is my new motherboard "asus P7P55D PRO"
Thanks in advance.

---

### Post by Blackie_Chan on 2010-01-25
The problem had nothing to do with IRQ, it was an issue with my audio drivers. [This]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359") fixed my problem.

---

