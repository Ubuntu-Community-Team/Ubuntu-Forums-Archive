---
title: "NETDEV WATCHDOG error message in log"
date: 2011-07-31
forum: Networking &amp; Wireless
---

### Post by Hedgehog1 on 2011-07-31
Greetings all!

I have finally hit on an issue I could not solve myself.  This started about 2 or 3 weeks ago:

When doing bit torrent downloads, I eventually lose the wired network connection in about 5-15 minutes.  This only happens when Deluge is running.  I can surf for hours, our connect up the the work WAN for hours and this does not seem to happen.

Until these last two weeks, Deluge has been fast and solid.  Here is the error from the log:

```
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020039] ------------[ cut here ]------------
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020060] WARNING: at /build/buildd/linux-2.6.38/net/sched/sch_generic.c:256 dev_watchdog+0x2a0/0x2b0()
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020067] Hardware name: MS-7623
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020073] NETDEV WATCHDOG: eth0 (atl1c): transmit queue 0 timed out
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020077] Modules linked in: binfmt_misc pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv vesafb snd_hda_codec_hdmi snd_hda_codec_via joydev ppdev snd_hda_intel snd_hda_codec nvidia(P) snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq psmouse snd_timer serio_raw snd_seq_device edac_core k10temp edac_mce_amd sp5100_tco snd i2c_piix4 soundcore snd_page_alloc parport_pc lp parport usbhid hid firewire_ohci usb_storage firewire_core uas crc_itu_t pata_atiixp ahci libahci atl1c
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020154] Pid: 0, comm: kworker/0:0 Tainted: P            2.6.38-10-generic #46-Ubuntu
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020160] Call Trace:
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020164]  <IRQ>  [<ffffffff81065cbf>] ? warn_slowpath_common+0x7f/0xc0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020184]  [<ffffffff81065db6>] ? warn_slowpath_fmt+0x46/0x50
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020193]  [<ffffffff814ef710>] ? dev_watchdog+0x2a0/0x2b0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020202]  [<ffffffff81013ae9>] ? sched_clock+0x9/0x10
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020210]  [<ffffffff8108eb08>] ? sched_clock_cpu+0xa8/0x110
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020219]  [<ffffffff814ef470>] ? dev_watchdog+0x0/0x2b0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020228]  [<ffffffff810749b4>] ? call_timer_fn+0x44/0x130
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020236]  [<ffffffff814ef470>] ? dev_watchdog+0x0/0x2b0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020244]  [<ffffffff81076004>] ? run_timer_softirq+0x134/0x280
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020252]  [<ffffffff8102c91d>] ? lapic_next_event+0x1d/0x30
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020260]  [<ffffffff8106d508>] ? __do_softirq+0xa8/0x1c0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020269]  [<ffffffff8109847f>] ? tick_program_event+0x1f/0x30
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020276]  [<ffffffff8100cf1c>] ? call_softirq+0x1c/0x30
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020283]  [<ffffffff8100ea45>] ? do_softirq+0x65/0xa0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020290]  [<ffffffff8106d725>] ? irq_exit+0x85/0x90
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020299]  [<ffffffff815cb430>] ? smp_apic_timer_interrupt+0x70/0x9b
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020306]  [<ffffffff8100c9d3>] ? apic_timer_interrupt+0x13/0x20
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020311]  <EOI>  [<ffffffff81076bfd>] ? get_next_timer_interrupt+0x8d/0x120
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020327]  [<ffffffff81037f0b>] ? native_safe_halt+0xb/0x10
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020334]  [<ffffffff81014801>] ? default_idle+0x41/0xe0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020343]  [<ffffffff8100a266>] ? cpu_idle+0xa6/0xf0
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020351]  [<ffffffff815bcba3>] ? start_secondary+0xbc/0xbe
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.020357] ---[ end trace bc9f7ac1b8ae20a9 ]---
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.062524] atl1c 0000:02:00.0: irq 42 for MSI/MSI-X
Jul 31 18:20:06 marcs-desktop kernel: [ 1539.062607] atl1c 0000:02:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
```

If anyone could point me in the right direction to solve this; I would really appreciate it.

***The Hedge***

:KS

---

### Post by nm_geo on 2011-07-31
Hey Hedge how goes it?  

I see that is a Natty kernel .. Have you tried to run the Deluge bit torrent in a previous kernel.. Just a thought not an answer..

I moved my Natty install up to the 3.0 versions long ago .. More experimenting LOL

---

### Post by Hedgehog1 on 2011-07-31
Greetings nm_geo!

I have been lost in my own code cutoff at work and not been able to spend as much time in the forums just lately.

I am only running the 3.0 kernel in my OO testing partition.

Using the older kernel is a good idea.  Of course, I cleaned it out a bit ago (silly me).

---

### Post by nm_geo on 2011-07-31
Well you could go get it .. But i was looking at 

 NETDEV WATCHDOG: eth0 (atl1c): transmit queue 0 timed out

And launch pad has lot of issues not specific Deluge but quite a few others  .. You might try there too.

---

### Post by Hedgehog1 on 2011-11-03
Well, I finally tracked this down.

The NIC card that is built into the motherboard was crashing during really heavy traffic - when it happened on both sides of the desktop (Ubuntu and Windows) I knew it wasn't just a Linux thing.

So, 32 bucks later I have a nice Intel NIC card and the on-board NIC turned off.

It works SOOO much better than the old one. :D

***The Hedge***

:KS

---

