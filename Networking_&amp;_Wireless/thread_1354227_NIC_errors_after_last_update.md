---
title: "NIC errors after last update"
date: 2009-12-13
forum: Networking &amp; Wireless
---

### Post by MakOwner on 2009-12-13
Not sure if this is the right place for this or not, but hopefully somoene else has this hardware combo:

MSI motherboard using an onboard Realtek chipset NIC

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

I have two disks off the motherboard SATA controllers for OS and online data, an eSATA attached software raid array in RAID5 with mdadm.
I'm copying data off this disk array across a GB cat6 network onto an NFS export from an OpenFiler appliance.

Ubuntu 9.04, still haven't upgraded to 9.10.  
Desktop install.
Just applied an update outstanding from the update manager this morning.
Immediately after the update, traffic out of the box TO an NFS export from another box causes the onboard NIC to go off into lala-land.

As you can see I got at least one trace but it's happening *very* frequently.


This from dmesg:
[  651.988515] ------------[ cut here ]------------
[  651.988521] WARNING: at /build/buildd/linux-2.6.28/net/sched/sch_generic.c:226 dev_watchdog+0x219/0x230()
[  651.988525] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
[  651.988528] Modules linked in: nfs lockd nfs_acl sunrpc binfmt_misc bridge stp bnep video output input_polldev lp snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd iTCO_wdt iTCO_vendor_support soundcore nvidia(P) psmouse snd_page_alloc ppdev pcspkr serio_raw intel_agp agpgart parport_pc parport usbhid r8169 mii raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipath linear fbcon tileblit font bitblit softcursor
[  651.988606] Pid: 0, comm: swapper Tainted: P           2.6.28-17-generic #58-Ubuntu
[  651.988610] Call Trace:
[  651.988618]  [<c0139ba0>] warn_slowpath+0x60/0x80
[  651.988625]  [<c012c71c>] ? enqueue_entity+0x13c/0x360
[  651.988630]  [<c0132211>] ? enqueue_task_fair+0x31/0x70
[  651.988636]  [<c0156ad3>] ? getnstimeofday+0x53/0x110
[  651.988642]  [<c02cbb7d>] ? strlcpy+0x1d/0x60
[  651.988647]  [<c042e542>] ? netdev_drivername+0x32/0x40
[  651.988653]  [<c0443119>] dev_watchdog+0x219/0x230
[  651.988658]  [<c0156ad3>] ? getnstimeofday+0x53/0x110
[  651.988664]  [<c0119a73>] ? lapic_next_event+0x13/0x20
[  651.988670]  [<c0159cfa>] ? clockevents_program_event+0x9a/0x150
[  651.988676]  [<c0143bf0>] run_timer_softirq+0x130/0x200
[  651.988681]  [<c0442f00>] ? dev_watchdog+0x0/0x230
[  651.988685]  [<c0442f00>] ? dev_watchdog+0x0/0x230
[  651.988691]  [<c013f297>] __do_softirq+0x97/0x170
[  651.988696]  [<c0152e16>] ? hrtimer_interrupt+0x186/0x1b0
[  651.988701]  [<c013f3cd>] do_softirq+0x5d/0x60
[  651.988707]  [<c013f545>] irq_exit+0x55/0x90
[  651.988711]  [<c011a07b>] smp_apic_timer_interrupt+0x5b/0x90
[  651.988718]  [<c04fea53>] ? schedule+0x643/0x710
[  651.988723]  [<c0105318>] apic_timer_interrupt+0x28/0x30
[  651.988729]  [<c010b012>] ? mwait_idle+0x42/0x50
[  651.988733]  [<c010285d>] cpu_idle+0x6d/0xd0
[  651.988738]  [<c04fbede>] start_secondary+0xbe/0xf0
[  651.988742] ---[ end trace f256f5efcf51ec93 ]---
[  652.005343] r8169: eth0: link up
[  762.972025] nfs: server amd4200 not responding, still trying
[  772.010827] nfs: server amd4200 OK
[  892.016021] nfs: server amd4200 not responding, still trying
[  892.021306] nfs: server amd4200 OK
[ 1330.005272] r8169: eth0: link up
[ 1450.004046] nfs: server amd4200 not responding, still trying
[ 1450.012060] nfs: server amd4200 OK
[ 1570.016026] nfs: server amd4200 not responding, still trying
[ 1570.021350] nfs: server amd4200 OK

---

