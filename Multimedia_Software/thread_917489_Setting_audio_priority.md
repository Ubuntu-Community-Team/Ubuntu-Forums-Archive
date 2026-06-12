---
title: "Setting audio priority"
date: 2008-09-11
forum: Multimedia Software
---

### Post by fauzie on 2008-09-11
Hi, I'm having problems with sound production with Hardy. I'm using the rt-kernel. I have many problems with sound dropping out. I wonder if I can somehow get a better performance.

cat /proc/interrupt

           CPU0       
  0:    7093439   IO-APIC-edge      timer
  1:       6570   IO-APIC-edge      i8042
  3:          5   IO-APIC-edge    
  4:          5   IO-APIC-edge    
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          1   IO-APIC-fasteoi   acpi
 12:     719747   IO-APIC-edge      i8042
 14:      29230   IO-APIC-edge      libata
 15:      75436   IO-APIC-edge      libata
 16:     913381   IO-APIC-fasteoi   EMU10K1, nvidia
 17:          2   IO-APIC-fasteoi   ohci1394
 19:         72   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, ehci_hcd:usb4
 21:      21943   IO-APIC-fasteoi   eth0
NMI:          0   Non-maskable interrupts
LOC:    5629520   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
SPU:          0   Spurious interrupts
ERR:          0
MIS:          0

I noticed that the sound (EMU10K1 shares the same IRQ with the video (nvidia). Is it a problem? Is there any way to change this? I found that most of the sound problem is related to video. Sounds are dropping out when the computer does a video-related task. I noticed the CPU is still low arround 40-50% when the sound is droping.

Thanks.

---

### Post by fauzie on 2008-09-12
Output of

lspci -v

00:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs SB0240 Audigy 2 Platinum 6.1
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at c000 [size=64]
	Capabilities: [dc] Power Management version 2

Is latency 32 good enough?
How do I change the IRQ???

---

### Post by obley on 2008-09-14
unfortunately,  I do not know how to answer your question but i noticed you have the very same sound card I do. I can't get any sound at all out of it. Did you have to do any tweaking to get it to work?

sorry to hijack your thread.

---

### Post by fauzie on 2008-09-14
Open a terminal, run alsamixer

Everything is muted by default. Just turn on everything there. That's all I did.

---

### Post by fauzie on 2008-09-14
I forgot one more thing.

If you have another sound card (on board??) that you don't use you need to turn it off from the BIOS. Otherwise ALSA might get confused and use it instead of your Audigy.

---

### Post by obley on 2008-09-15
> **fauzie said:**
> Open a terminal, run alsamixer

Everything is muted by default. Just turn on everything there. That's all I did.

Thank you. I think I did that like 15 times, only after I tweaked this and rewrote that. I just did a clean install and boom.. it works this time.

thanks!

---

