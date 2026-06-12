---
title: "Ubuntu 10.10 eth0 (atl1c): transmit queue 0 timed out AR8131"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by alecasagrande on 2012-11-20
Hi, i'm using ubuntu 10.10 (32 bits) with a NIC AR8131. Yesterday i found this logs in the kernel log. I'm not sure but it seems that the machine reboots, I have several logs of an application running in that machine.

Any ideas?

Kernel Upgrade?
Driver?

Thanks

Alejandro


Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000511] -----------[ cut here ]-----------
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000525] WARNING: at /build/buildd/linux-2.6.35/net/sched/sch_generic.c:258 dev_watchdog+0x1fd/0x210()
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000530] Hardware name: System Product Name
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000534] NETDEV WATCHDOG: eth0 (atl1c): transmit queue 0 timed out
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000537] Modules linked in: binfmt_misc dm_crypt snd_hda_codec_realtek snd_hda_intel snd_hda_codec asus_atk0110 snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device led_class ppdev parport_pc snd psmouse serio_raw soundcore snd_page_alloc lp parport usbhid hid dm_raid45 xor i915 drm_kms_helper drm intel_agp i2c_algo_bit video output atl1c agpgart ramzswap(C) lzo_compress
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000594] Pid: 0, comm: swapper Tainted: G C 2.6.35-32-generic #67-Ubuntu
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000598] Call Trace:
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000608] [<c014b792>] warn_slowpath_common+0x72/0xa0
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000614] [<c0511a0d>] ? dev_watchdog+0x1fd/0x210
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000619] [<c0511a0d>] ? dev_watchdog+0x1fd/0x210
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000625] [<c014b863>] warn_slowpath_fmt+0x33/0x40
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000630] [<c0511a0d>] dev_watchdog+0x1fd/0x210
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000637] [<c0162a26>] ? insert_work+0x66/0xb0
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000644] [<c012d268>] ? default_spin_lock_flags+0x8/0x10
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000649] [<c0162ce6>] ? __queue_work+0x36/0x50
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000655] [<c0511810>] ? dev_watchdog+0x0/0x210
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000661] [<c0158a3f>] call_timer_fn+0x2f/0xf0
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000667] [<c012268b>] ? lapic_next_event+0x1b/0x20
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000673] [<c01750fb>] ? clockevents_program_event+0x8b/0x140
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000679] [<c0159cb4>] run_timer_softirq+0x104/0x210
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000685] [<c0176562>] ? tick_dev_program_event+0x42/0x150
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000690] [<c0511810>] ? dev_watchdog+0x0/0x210
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000700] [<c0151e9c>] __do_softirq+0x9c/0x1b0
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000703] [<c016cf2e>] ? sched_clock_tick+0x5e/0x90
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000706] [<c0151ff5>] do_softirq+0x45/0x50
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000709] [<c0152165>] irq_exit+0x65/0x70
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000712] [<c05d35db>] smp_apic_timer_interrupt+0x5b/0x8a
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000716] [<c05cd3e5>] apic_timer_interrupt+0x31/0x38
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000720] [<c010a8a6>] ? mwait_idle+0x56/0xb0
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000723] [<c0101fbc>] cpu_idle+0x8c/0xd0
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000727] [<c05c7c49>] start_secondary+0x10c/0x112
Nov 19 19:31:57 ServidorLSD kernel: [ 7242.000729] --[ end trace 782ee66402ebca1d ]--
Nov 19 19:31:58 ServidorLSD kernel: [ 7242.168742] atl1c 0000:01:00.0: irq 44 for MSI/MSI-X
Nov 19 19:31:58 ServidorLSD kernel: [ 7242.168821] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>
Nov 19 19:46:13 ServidorLSD kernel: [ 8097.160924] atl1c 0000:01:00.0: irq 44 for MSI/MSI-X
Nov 19 19:46:13 ServidorLSD kernel: [ 8097.161003] atl1c 0000:01:00.0: atl1c: eth0 NIC Link is Up<100 Mbps Full Duplex>

---

