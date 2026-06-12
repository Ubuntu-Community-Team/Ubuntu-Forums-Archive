---
title: "Internet Connection Drops Out Periodically"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by martin1977 on 2011-10-29
I'm having problems with an Intel PRO/1000 GT Network Adapter plugged into an Acer Z68 motherboard on a system running Kubuntu 11.10 Oneiric.

After a few minutes, sometimes an hour, the network connection drops out with the following message:

Oct 29 20:17:42 titan1 kernel: [10148.510903] irq 16: nobody cared (try booting with the "irqpoll" option)
Oct 29 20:17:42 titan1 kernel: [10148.510911] Pid: 0, comm: swapper Tainted: G        WC  3.0.0-12-generic #20-Ubuntu
Oct 29 20:17:42 titan1 kernel: [10148.510913] Call Trace:
Oct 29 20:17:42 titan1 kernel: [10148.510915]  <IRQ>  [<ffffffff810cf8ad>] __report_bad_irq+0x3d/0xe0
Oct 29 20:17:42 titan1 kernel: [10148.510927]  [<ffffffff810cfcd5>] note_interrupt+0x135/0x180
Oct 29 20:17:42 titan1 kernel: [10148.510931]  [<ffffffff810cdcc9>] handle_irq_event_percpu+0xa9/0x220
Oct 29 20:17:42 titan1 kernel: [10148.510935]  [<ffffffff810cde8e>] handle_irq_event+0x4e/0x80
Oct 29 20:17:42 titan1 kernel: [10148.510939]  [<ffffffff810d0604>] handle_fasteoi_irq+0x64/0xf0
Oct 29 20:17:42 titan1 kernel: [10148.510943]  [<ffffffff8100c252>] handle_irq+0x22/0x40
Oct 29 20:17:42 titan1 kernel: [10148.510947]  [<ffffffff815f3d2a>] do_IRQ+0x5a/0xe0
Oct 29 20:17:42 titan1 kernel: [10148.510951]  [<ffffffff815ea413>] common_interrupt+0x13/0x13
Oct 29 20:17:42 titan1 kernel: [10148.510953]  <EOI>  [<ffffffff814aad78>] ? poll_idle+0x38/0x80
Oct 29 20:17:42 titan1 kernel: [10148.510960]  [<ffffffff814aad53>] ? poll_idle+0x13/0x80
Oct 29 20:17:42 titan1 kernel: [10148.510964]  [<ffffffff814ab062>] cpuidle_idle_call+0xa2/0x1d0
Oct 29 20:17:42 titan1 kernel: [10148.510969]  [<ffffffff8100920b>] cpu_idle+0xab/0x100
Oct 29 20:17:42 titan1 kernel: [10148.510974]  [<ffffffff815b803e>] rest_init+0x72/0x74
Oct 29 20:17:42 titan1 kernel: [10148.510978]  [<ffffffff81ad0c2b>] start_kernel+0x3d4/0x3df
Oct 29 20:17:42 titan1 kernel: [10148.510984]  [<ffffffff81ad0388>] x86_64_start_reservations+0x132/0x136
Oct 29 20:17:42 titan1 kernel: [10148.510988]  [<ffffffff81ad0140>] ? early_idt_handlers+0x140/0x140
Oct 29 20:17:42 titan1 kernel: [10148.510993]  [<ffffffff81ad0459>] x86_64_start_kernel+0xcd/0xdc
Oct 29 20:17:42 titan1 kernel: [10148.510995] handlers:
Oct 29 20:17:42 titan1 kernel: [10148.511011] [<ffffffffa016e6c0>] e1000_intr
Oct 29 20:17:42 titan1 kernel: [10148.511013] Disabling IRQ #16

Any ideas what this means and how I can resolve or at least debug the problem?

Regards, Martin

---

### Post by martin1977 on 2011-10-31
This seems to be aproblem with Asus Sandybridge motherboards???

[http://www.spinics.net/lists/kernel/msg1249467.html](http://www.spinics.net/lists/kernel/msg1249467.html)
[https://lkml.org/lkml/2011/6/30/197](https://lkml.org/lkml/2011/6/30/197)

Any help appreciated.

Martin

---

### Post by martin1977 on 2011-10-31
This thread also...

[http://ubuntuforums.org/showthread.php?t=1676491](http://ubuntuforums.org/showthread.php?t=1676491)

---

### Post by martin1977 on 2011-11-17
I have resolved this issue by purchasing a pci-e (pci express) Ethernet adapter for the second adapter. 

The problem is reported to be with the pci-e to pci bridge on Asus and other Sandybridge motherboards.  I'm not sure whether this is a hardware, bios or kernel issue - just relieved that I've found a fix!

---

