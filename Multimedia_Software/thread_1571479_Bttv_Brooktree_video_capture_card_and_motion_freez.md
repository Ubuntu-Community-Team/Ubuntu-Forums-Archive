---
title: "Bttv Brooktree video capture card and motion freeze system"
date: 2010-09-09
forum: Multimedia Software
---

### Post by moboticdes on 2010-09-09
I have a BT878 video capture card which freezes completely ubuntu (no mouse, no video updating, can't ping machine can't CTRL+f1 or anything).
Apparently it happened when playing with xawtv after a random number of seconds, now I discovered it happens as soon as I start motion (video surveillance program).

below what I tried so far:
- I watched the logs but they have nothing interesting because as it freezes it writes nothing to the logs.
- tried on both Ubuntu 10.04 and ubuntu 9.10 but always the same, also kernel version doesn't matter
- tried booting with acpi=off but nothing
- I have a working configuration on another machine running ubuntu 9.10, tried to swap the two Bttv cards but always the same: on the other machine all fine on mine it freezes
- checked it isn't a pci riser card problem however the other computer works fine with riser card
- tried setting differently the PCI assignments from BIOS but nothing
- tried it isn't correlated with X server so tried shutting down x server and running motion from tty, but nothing always the same
- as I have only one pci slot I cannot swap anything, anyway the pci-e slot is empty and so there's nothing else which can be conflicting
-the irq is shared with the usb controller, however changing from bios so that the bttv card is alone on its channel didn't change the problem.
-tried setting higher pci latencies from BIOS however nothing..

I'm out of possible tests..
so far the only thing which comes to my mind is that it's related with the motherboard which I bought new to create a second home surveillance computer, it's a Asrock G31M-VS2... however it looks crazy that this motherboard which is brand new doesn't work with an old bttv pci card and the other one works well with the same software configuration!

---

### Post by moboticdes on 2010-09-09
I tried putting the following options at boot:

 irqpool pci=noacpi noapic nolapic acpi=off

now when I boot up and execute motion I get an interesting error, I have to copy it by hand anyway it is:

[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
[80.750405]
[80.750405] HARDWARE ERROR
[80.750405] CPU 1: Machine Check Exception:      5 Bank 5: b200121020080400
[80.750405] RIP !INEXACT! 60:<00000000c01a993> {mwait_idle+0x63/0xf0}
[80.750405] TSC 4ce4de85b0
[80.750405] PROCESSOR 0:1067a TIME 1284068658 SOCKET 0 APIC 1
CPU 1: Machine Check Exception:      5 Bank 5: b200121020080400
[80.750405] RIP !INEXACT! 60:<00000000c01a993> {mwait_idle+0x63/0xf0}
[80.750405] TSC 4ce4de85b0
[80.750405] PROCESSOR 0:1067a TIME 1284068658 SOCKET 0 APIC 1
[80.750405] Some CPUs didn't answer in synchronization
[80.750405] This is not a software problem!
[80.750405] Run Through mcelog --ascii to decode and contact your hardware vendor
[80.750405] Machine check: Processor Context corrupt
[80.750405] Kernel Panic -not syncing: Fatal Machine check on current CPU
[80.750405] Pid:0, comm: swapper Tainted: G M 2.6.31-14-generic #48-Ubuntu

---

