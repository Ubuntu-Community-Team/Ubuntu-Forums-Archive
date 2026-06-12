---
title: "Sound Card doesnt have an IRQ set? Help PLS?"
date: 2010-05-30
forum: Multimedia Software
---

### Post by frozonecom on 2010-05-30
so, I ran the command :

```
cat /proc/interrupts
```and I got,

```
           CPU0       
  0:     391762    XT-PIC-XT        timer
  1:       6276    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          2    XT-PIC-XT      
  4:          1    XT-PIC-XT      
  5:          1    XT-PIC-XT      
  6:       9153    XT-PIC-XT        uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, radeon, eth0
  7:          2    XT-PIC-XT      
  8:          0    XT-PIC-XT        rtc0
  9:        123    XT-PIC-XT        acpi
 10:      28385    XT-PIC-XT        ehci_hcd:usb1, ohci1394, tifm_7xx1, yenta, ipw2200
 11:          1    XT-PIC-XT      
 12:     252480    XT-PIC-XT        i8042
 14:      27701    XT-PIC-XT        ata_piix
 15:      23226    XT-PIC-XT        ata_piix
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:          6   Machine check polls
ERR:          1
MIS:          0

```

which means that it may be the reason why I am not getting sound in my ubuntu 10.04?

and 
```

sudo lspci -v
```

shows that the sound card is :

```
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 0064
    Flags: medium devsel, IRQ 10
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at d0000c00 (32-bit, non-prefetchable) [size=512]
    Memory at d0000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel modules: snd-intel8x0
```

which means that Intel ICH4 should have an IRQ assigned?

help pls.

---

### Post by Yellow Pasque on 2010-05-30
Try booting with irqpoll option. Press 'Esc' to access grub right after you start and add the word 'irqpoll' to the 'linux' line.
[https://help.ubuntu.com/community/GrubHowto#Modifying%20boot%20options%20in%20GRUB](https://help.ubuntu.com/community/GrubHowto#Modifying%20boot%20options%20in%20GRUB)

---

### Post by frozonecom on 2010-05-30
> **Temüjin said:**
> Try booting with irqpoll option. Press 'Esc' to access grub right after you start and add the word 'irqpoll' to the 'linux' line.
[https://help.ubuntu.com/community/GrubHowto#Modifying%20boot%20options%20in%20GRUB](https://help.ubuntu.com/community/GrubHowto#Modifying%20boot%20options%20in%20GRUB)


i dont understand your instructions, when do i press esc? right after i turn on my laptop?

---

