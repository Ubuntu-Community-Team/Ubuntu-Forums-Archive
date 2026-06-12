---
title: "Nvidia IRQ problem"
date: 2007-10-04
forum: Multimedia &amp; Video
---

### Post by Jer_gorsline on 2007-10-04
Ok, This is an ongoing issue and I've exhausted just about every other thing I can think of.

When I play UT2004, or ManiaDrive, or any other 3d-accelerated game, it will run for about 2 minutes, then the system freezes. Hard reboot needed.

I have tracked it down to the system disabling the IRQ for my graphics card (see my Syslog below). In my attempts to solve this, I have installed the Nvida driver from the restricted repos, manually installed the one from the Nvidia site, reinstalled Feisty 386, installed Feisty AMD64 (Tried both 64 bit drivers, too) updated my bios, tried every boot command I've come across, and played with all kinds of bios settings.

The IRQ changes depending on what my settings are, but the system always gives the log messages for the IRQ that the video card is on. I've seen in other threads that this same series of events happens for other hardware, not just video cards, so I'm a little reluctant to think that my card is borked, especially since this problem occasionally doesn't reproduce if I'm playing UT2004 online as opposed to single player (this is a suspicion, not yet confirmed.) Also, the video card works just fine for other non-accelerated things, even movies, etc.

Any help or suggestions would be greatly appreciated.

Here's the details:

jer@Athena:~$ cat /proc/interrupts
           CPU0
  0:    1096332   IO-APIC-edge      timer
  1:          2   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  8:          0   IO-APIC-edge      rtc
  9:          0   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:      10497   IO-APIC-edge      ide0
 15:      38754   IO-APIC-edge      ide1
 16:       1377   IO-APIC-fasteoi   libata, EMU10K1
 17:          3   IO-APIC-fasteoi   ohci1394
 18:     334766   IO-APIC-fasteoi   nvidia
 20:          3   IO-APIC-fasteoi   ehci_hcd:usb2
 21:     463805   IO-APIC-fasteoi   eth0
 22:       9798   IO-APIC-fasteoi   libata
 23:     181940   IO-APIC-fasteoi   ohci_hcd:usb1
NMI:          0
LOC:    1096285
ERR:          0

And my syslog as the freeze happens (newest to oldest):

03/10/07 11:06:51 PM	Athena	kernel	[11042.954546] Disabling IRQ #18

03/10/07 11:06:51 PM	Athena	kernel	[11042.954353] [_end+133504581/2130489456] (nv_kern_isr+0x0/0x5e [nvidia])

03/10/07 11:06:51 PM	Athena	kernel	[11042.954351] handlers:

03/10/07 11:06:51 PM	Athena	kernel	[11042.954350] 

03/10/07 11:06:51 PM	Athena	kernel	[11042.954337]  [system_call+126/131] system_call+0x7e/0x83

03/10/07 11:06:51 PM	Athena	kernel	[11042.954331]  [sys_sched_yield+117/128] sys_sched_yield+0x75/0x80

03/10/07 11:06:51 PM	Athena	kernel	[11042.954312]  [schedule+333/2091] __sched_text_start+0x14d/0x82b

03/10/07 11:06:51 PM	Athena	kernel	[11042.954295]  <EOI>  [thread_return+161/245] thread_return+0xa1/0xf5

03/10/07 11:06:51 PM	Athena	kernel	[11042.954292]  [ret_from_intr+0/10] ret_from_intr+0x0/0xa

03/10/07 11:06:51 PM	Athena	kernel	[11042.954286]  [do_IRQ+137/256] do_IRQ+0x89/0x100

03/10/07 11:06:51 PM	Athena	kernel	[11042.954278]  [call_softirq+28/40] call_softirq+0x1c/0x28

03/10/07 11:06:51 PM	Athena	kernel	[11042.954273]  [handle_fasteoi_irq+202/288] handle_fasteoi_irq+0xca/0x120

03/10/07 11:06:51 PM	Athena	kernel	[11042.954262]  [note_interrupt+544/640] note_interrupt+0x220/0x280

03/10/07 11:06:51 PM	Athena	kernel	[11042.954235]  <IRQ>  [__report_bad_irq+53/144] __report_bad_irq+0x35/0x90

03/10/07 11:06:51 PM	Athena	kernel	[11042.954233] Call Trace:

03/10/07 11:06:51 PM	Athena	kernel	[11042.954232] 

03/10/07 11:06:51 PM	Athena	kernel	[11042.954227] irq 18: nobody cared (try booting with the "irqpoll" option)


The system is as follows:
Kubuntu 7.04 AMD-64 (problem exists in the 32-bit version as well)
MSI NEO Platinum Motherboard 
NForce chipset
MSI GeForce 6600GT PCI Express
I GB RAM
Various SATA and IDE disks (no RAID)
Numerous USB stuff

---

### Post by Jer_gorsline on 2007-10-04
OK, took the card out to see if it was a seating issue, and found the mount for the round fan in the heatsink had broken. It spun OK at low speeds, but at higher speeds it shook loose and stalled against the heatsink. Replaced the heatsink/fan and everything is OK.

So I guess that the IRQ error is from the card freezing when over heated. Odd symptom, but it makes sense.

---

