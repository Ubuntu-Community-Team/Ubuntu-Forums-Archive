---
title: "Network speed on gigabit card slows down after about 1 hour"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by MikeBenza on 2013-04-26
Hello,

I've got a gigabit network card on the private side of an Ubuntu machine acting as a NAT (among other things).  Right after the interface is brought up I can get about 33MBps (Megabytes -- i.e. near full performance of a gigabit network card on a PCI bus).  After about an hour it only gets 500KBps.

The ping time goes way up, as well.  A machine on the private network can ping the the private interface of the Ubuntu machine in < 1ms just after the interface is brought up.  After about an hour it's 50ms - 90ms.

The adapter is an Intel Pro/1000 GT Desktop adapter.  

I don't know if the drop off is gradual or quick -- I haven't measured that yet.  I also don't know the exact time.  It's somewhere between 30 and 90 minutes.  I do know it's related to the interface -- I've tried different clients on the private side, different network hardware on the private side.

Does anyone have any suggestions?

---

### Post by MikeBenza on 2013-05-02
I was able to quantify this a bit more and find what might be a specific cause.  I just can't figure out how to avoid whatever is causing it.

I ran "ping -c 86400 -D 192.168.1.76 > ping.log", which should ping another (idle) machine for a day and record the results. Some text mashing later I got a list of times.  It looks as expected for the network traffic, then at the end, things get funny.  I expect the spikes due to network saturation every 5-30 minutes.  See Graph1.png.

I decided to take a closer look at the end.  Enhance.  See Graph2.png. Yes, that's a sawtooth pattern, with some interruptions!  See Graph3.png.

I took a closer look at the data and found this:
```

[1367514798.683531] 64 bytes from 192.168.1.76: icmp_req=4419 ttl=128 time=98.0 ms
[1367514799.683537] 64 bytes from 192.168.1.76: icmp_req=4420 ttl=128 time=97.0 ms
[1367514800.683534] 64 bytes from 192.168.1.76: icmp_req=4421 ttl=128 time=96.0 ms
[1367514801.683530] 64 bytes from 192.168.1.76: icmp_req=4422 ttl=128 time=95.0 ms
[1367514802.683529] 64 bytes from 192.168.1.76: icmp_req=4423 ttl=128 time=94.0 ms
[1367514803.683530] 64 bytes from 192.168.1.76: icmp_req=4424 ttl=128 time=93.0 ms
[1367514804.683530] 64 bytes from 192.168.1.76: icmp_req=4425 ttl=128 time=92.0 ms
[1367514805.683527] 64 bytes from 192.168.1.76: icmp_req=4426 ttl=128 time=91.0 ms
[1367514806.683530] 64 bytes from 192.168.1.76: icmp_req=4427 ttl=128 time=90.0 ms
[1367514807.683527] 64 bytes from 192.168.1.76: icmp_req=4428 ttl=128 time=89.0 ms
[1367514808.683531] 64 bytes from 192.168.1.76: icmp_req=4429 ttl=128 time=88.0 ms
[1367514809.683530] 64 bytes from 192.168.1.76: icmp_req=4430 ttl=128 time=87.0 ms
[1367514810.683530] 64 bytes from 192.168.1.76: icmp_req=4431 ttl=128 time=86.0 ms
[1367514811.683531] 64 bytes from 192.168.1.76: icmp_req=4432 ttl=128 time=85.0 ms
[1367514812.683530] 64 bytes from 192.168.1.76: icmp_req=4433 ttl=128 time=84.0 ms
[1367514813.683531] 64 bytes from 192.168.1.76: icmp_req=4434 ttl=128 time=83.0 ms
[1367514814.683527] 64 bytes from 192.168.1.76: icmp_req=4435 ttl=128 time=82.0 ms
[1367514815.683530] 64 bytes from 192.168.1.76: icmp_req=4436 ttl=128 time=81.0 ms
[1367514816.683530] 64 bytes from 192.168.1.76: icmp_req=4437 ttl=128 time=80.0 ms
[1367514817.683531] 64 bytes from 192.168.1.76: icmp_req=4438 ttl=128 time=79.0 ms
[1367514818.683531] 64 bytes from 192.168.1.76: icmp_req=4439 ttl=128 time=78.0 ms
[1367514819.683530] 64 bytes from 192.168.1.76: icmp_req=4440 ttl=128 time=77.0 ms
[1367514820.683531] 64 bytes from 192.168.1.76: icmp_req=4441 ttl=128 time=76.0 ms
[1367514821.683530] 64 bytes from 192.168.1.76: icmp_req=4442 ttl=128 time=75.0 ms
[1367514822.683531] 64 bytes from 192.168.1.76: icmp_req=4443 ttl=128 time=74.0 ms
[1367514823.683528] 64 bytes from 192.168.1.76: icmp_req=4444 ttl=128 time=73.0 ms
[1367514824.683544] 64 bytes from 192.168.1.76: icmp_req=4445 ttl=128 time=72.0 ms
[1367514825.683530] 64 bytes from 192.168.1.76: icmp_req=4446 ttl=128 time=70.9 ms
[1367514826.683534] 64 bytes from 192.168.1.76: icmp_req=4447 ttl=128 time=70.0 ms
[1367514827.683537] 64 bytes from 192.168.1.76: icmp_req=4448 ttl=128 time=69.0 ms
[1367514828.683528] 64 bytes from 192.168.1.76: icmp_req=4449 ttl=128 time=68.0 ms
[1367514829.683529] 64 bytes from 192.168.1.76: icmp_req=4450 ttl=128 time=67.0 ms
[1367514830.683530] 64 bytes from 192.168.1.76: icmp_req=4451 ttl=128 time=66.0 ms
[1367514831.683537] 64 bytes from 192.168.1.76: icmp_req=4452 ttl=128 time=65.0 ms
[1367514832.683535] 64 bytes from 192.168.1.76: icmp_req=4453 ttl=128 time=64.0 ms

```

So the ping time is clearly decreasing 1ms per second.  Exactly. I mapped the timestamp (the bracketed number at the beginning of each line) to the local time for when this started (May 2 11:21:48), then looked in kern.log:
```

May  2 11:21:48 dcgw-s1 kernel: [160352.274894] irq 19: nobody cared (try booting with the "irqpoll" option)
May  2 11:21:48 dcgw-s1 kernel: [160352.274912] Pid: 0, comm: swapper/0 Tainted: P         C O 3.2.0-39-generic #62-Ubuntu
May  2 11:21:48 dcgw-s1 kernel: [160352.274914] Call Trace:
May  2 11:21:48 dcgw-s1 kernel: [160352.274914]  <IRQ>  [<ffffffff810dc5bd>] __report_bad_irq+0x3d/0xe0
May  2 11:21:48 dcgw-s1 kernel: [160352.274921]  [<ffffffff810dc845>] note_interrupt+0x135/0x190
May  2 11:21:48 dcgw-s1 kernel: [160352.274923]  [<ffffffff810da07a>] handle_irq_event_percpu+0xaa/0x210
May  2 11:21:48 dcgw-s1 kernel: [160352.274925]  [<ffffffff810da231>] handle_irq_event+0x51/0x80
May  2 11:21:48 dcgw-s1 kernel: [160352.274927]  [<ffffffff810dd29a>] handle_fasteoi_irq+0x6a/0x110
May  2 11:21:48 dcgw-s1 kernel: [160352.274930]  [<ffffffff81016282>] handle_irq+0x22/0x40
May  2 11:21:48 dcgw-s1 kernel: [160352.274933]  [<ffffffff81668aaa>] do_IRQ+0x5a/0xe0
May  2 11:21:48 dcgw-s1 kernel: [160352.274935]  [<ffffffff8165de2e>] common_interrupt+0x6e/0x6e
May  2 11:21:48 dcgw-s1 kernel: [160352.274936]  <EOI>  [<ffffffff8109d044>] ? tick_program_event+0x24/0x30
May  2 11:21:48 dcgw-s1 kernel: [160352.274941]  [<ffffffff8136d99d>] ? intel_idle+0xed/0x150
May  2 11:21:48 dcgw-s1 kernel: [160352.274942]  [<ffffffff8136d97f>] ? intel_idle+0xcf/0x150
May  2 11:21:48 dcgw-s1 kernel: [160352.274945]  [<ffffffff81508dd1>] cpuidle_idle_call+0xc1/0x280
May  2 11:21:48 dcgw-s1 kernel: [160352.274947]  [<ffffffff8101322a>] cpu_idle+0xca/0x120
May  2 11:21:48 dcgw-s1 kernel: [160352.274950]  [<ffffffff8162429e>] rest_init+0x72/0x74
May  2 11:21:48 dcgw-s1 kernel: [160352.274953]  [<ffffffff81cfcc08>] start_kernel+0x3b5/0x3c2
May  2 11:21:48 dcgw-s1 kernel: [160352.274954]  [<ffffffff81cfc388>] x86_64_start_reservations+0x132/0x136
May  2 11:21:48 dcgw-s1 kernel: [160352.274957]  [<ffffffff81cfc140>] ? early_idt_handlers+0x140/0x140
May  2 11:21:48 dcgw-s1 kernel: [160352.274959]  [<ffffffff81cfc459>] x86_64_start_kernel+0xcd/0xdc
May  2 11:21:48 dcgw-s1 kernel: [160352.274960] handlers:
May  2 11:21:48 dcgw-s1 kernel: [160352.274968] [<ffffffff8146e990>] ahci_interrupt
May  2 11:21:48 dcgw-s1 kernel: [160352.274988] [<ffffffffa00350e0>] e100_intr
May  2 11:21:48 dcgw-s1 kernel: [160352.274999] Disabling IRQ #19
```

Now, I know *what* is wrong.  I don't think it's a network card issue, since I swapped out the cards (I downgraded to a 100Mbps card just to see what would happen), though it's still a PCI card.

I bought a PCI Express gigabit card, but I'm wondering if I should even bother.  I'm not sure if this is a PCI bus issue or a mobo issue, or neither.  The motherboard is a ASUS P8Z68-V Pro.  The first network card is an [COLOR=#000000]Intel Pro/1000 GT Desktop adapter.  The second is a no-name brand 10/100 PCI adapter.

I searched through the logs and found the same message about the same interrupt from before I swapped out cards.  I also noticed some logs for IRQ 17, which sometimes came before the IRQ 19 message (above):

```
[/COLOR]

Apr 26 17:32:33 dcgw-s1 kernel: [95945.171186] irq 17: nobody cared (try booting with the "irqpoll" option)
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172010] Pid: 0, comm: swapper/2 Tainted: P         C O 3.2.0-39-generic #62-Ubuntu
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172012] Call Trace:
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172013]  <IRQ>  [<ffffffff810dc5bd>] __report_bad_irq+0x3d/0xe0
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172021]  [<ffffffff810dc845>] note_interrupt+0x135/0x190
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172023]  [<ffffffff810da07a>] handle_irq_event_percpu+0xaa/0x210
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172025]  [<ffffffff810da231>] handle_irq_event+0x51/0x80
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172028]  [<ffffffff810dd29a>] handle_fasteoi_irq+0x6a/0x110
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172031]  [<ffffffff81016282>] handle_irq+0x22/0x40
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172034]  [<ffffffff81668aaa>] do_IRQ+0x5a/0xe0
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172037]  [<ffffffff8165de2e>] common_interrupt+0x6e/0x6e
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172038]  <EOI>  [<ffffffff8108f319>] ? enqueue_hrtimer+0x39/0xc0
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172044]  [<ffffffff8136d99d>] ? intel_idle+0xed/0x150
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172046]  [<ffffffff8136d97f>] ? intel_idle+0xcf/0x150
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172049]  [<ffffffff81508dd1>] cpuidle_idle_call+0xc1/0x280
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172052]  [<ffffffff8101322a>] cpu_idle+0xca/0x120
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172055]  [<ffffffff8163b794>] start_secondary+0xd9/0xdb
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172056] handlers:
Apr 26 17:32:33 dcgw-s1 kernel: [95945.172874] [<ffffffffa007a370>] irq_handler
Apr 26 17:32:33 dcgw-s1 kernel: [95945.173689] Disabling IRQ #17

```

[COLOR=#000000]Since I switched out the ethernet cards, maybe it's an AHCI issue?  I searched around and someone suggested emailing the Linux kernel developers list.  Is disabling AHCI safe?  Does anyone have some insight?  What will booting with irqpoll do?[/COLOR]

---

### Post by MikeBenza on 2013-05-02
I moved the network card into a different PCI slot (and switched back to the gigabit card) and I got another disabled interrupt, with the corresponding increase in ping times. This time the interrupt is only handled by one thing: eth1.

```

May  2 17:25:08 dcgw-s1 kernel: [ 2699.614379] irq 18: nobody cared (try booting with the "irqpoll" option)
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614402] Pid: 0, comm: swapper/0 Tainted: P         C O 3.2.0-39-generic #62-Ubuntu
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614404] Call Trace:
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614405]  <IRQ>  [<ffffffff810dc5bd>] __report_bad_irq+0x3d/0xe0
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614412]  [<ffffffff810dc845>] note_interrupt+0x135/0x190
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614414]  [<ffffffff810da07a>] handle_irq_event_percpu+0xaa/0x210
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614416]  [<ffffffff810da231>] handle_irq_event+0x51/0x80
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614418]  [<ffffffff810dd29a>] handle_fasteoi_irq+0x6a/0x110
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614421]  [<ffffffff81016282>] handle_irq+0x22/0x40
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614423]  [<ffffffff81668aaa>] do_IRQ+0x5a/0xe0
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614426]  [<ffffffff8165de2e>] common_interrupt+0x6e/0x6e
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614427]  <EOI>  [<ffffffff8136d99d>] ? intel_idle+0xed/0x150
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614431]  [<ffffffff8136d97f>] ? intel_idle+0xcf/0x150
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614434]  [<ffffffff81508dd1>] cpuidle_idle_call+0xc1/0x280
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614436]  [<ffffffff8101322a>] cpu_idle+0xca/0x120
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614439]  [<ffffffff8162429e>] rest_init+0x72/0x74
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614442]  [<ffffffff81cfcc08>] start_kernel+0x3b5/0x3c2
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614444]  [<ffffffff81cfc388>] x86_64_start_reservations+0x132/0x136
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614446]  [<ffffffff81cfc140>] ? early_idt_handlers+0x140/0x140
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614448]  [<ffffffff81cfc459>] x86_64_start_kernel+0xcd/0xdc
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614449] handlers:
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614468] [<ffffffffa0063720>] e1000_intr
May  2 17:25:08 dcgw-s1 kernel: [ 2699.614479] Disabling IRQ #18

```

```

atlas@dcgw-s1:~$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3
  0:         60          0          0          0   IO-APIC-edge      timer
  1:          3          0          0          0   IO-APIC-edge      i8042
  8:          1          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:          4          0          0          0   IO-APIC-edge      i8042
 17:         22          0         60          0   IO-APIC-fasteoi   firewire_ohci
 18:     200001          0          0          0   IO-APIC-fasteoi   eth1
 19:          0          0          0          0   IO-APIC-fasteoi   ahci
 23:        291          0          0          0   IO-APIC-fasteoi   ehci_hcd:usb1, ehci_hcd:usb2
 40:          0          0          0          0   PCI-MSI-edge      PCIe PME
 41:          0          0          0          0   PCI-MSI-edge      PCIe PME
(...snip...)

```

I think this shows it's an issue with the hardware or the PCI bus?  Maybe it's specific to Intel network cards?  The no-name card used the e1000 driver, too, so I think it's the same or a related chipset.

---

### Post by MikeBenza on 2013-05-03
I'm a bit disappointed no one has replied.  It used to be that posts on Ubuntu forums got a lot more replies.

After digging in some more, I found this bug: [IRQ handling issues on sandy bridge board]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843709").

The short version is that this motherboard in combination with some PCI Ethernet cards makes Linux unhappy.  Apparently replacing with a PCIe card is the way to go.

I tried that yesterday with a cheap TP-Link NIC, but I couldn't get the Real Tek 8168 driver to work, so I just ordered the Intel PCIe card.

-------------------
Two weeks later:
I bought an Intel EXPI9301CTBLK Gigabit PCIe card and put it in.  It's been running at full-speed for two weeks now.  Problem solved

---

