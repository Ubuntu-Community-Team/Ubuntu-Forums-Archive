---
title: "Encoded Ogg file has skipping during playback"
date: 2012-01-31
forum: Multimedia Software
---

### Post by Abnormal123 on 2012-01-31
I'm having problems ripping music CD's to ogg format. I've been experiencing intermitent CD drive speed problems. Sometimes, while ripping a CD, the read speed drops to around 2x.

I'm using Sound Juicer to extract the files. I tried Asunder but it failed to rip a single file. When I get the resulting ogg file, it plays but there are skips in it (I verified this with Audacity). I think it has to do something with the CD drive. Possibly the DMA controller;  don't know.

Here's some ouput from dmesg:

[  118.915046] ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x6 frozen
[  118.915057] ata2.00: irq_stat 0x48000001, interface fatal error
[  118.915066] ata2: SError: { UnrecovData 10B8B BadCRC }
[  118.915077] sr 1:0:0:0: [sr0] CDB: Volume set (in), Read cd: be 00 00 00 31 e2 00 00 1b f8 00 00
[  118.915111] ata2.00: cmd a0/00:00:00:10:f8/00:00:00:00:00/a0 tag 0 pio 63504 in
[  118.915114]          res 51/b4:03:00:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[  118.915122] ata2.00: status: { DRDY ERR }
[  118.915133] ata2: hard resetting link
[  119.404035] ata2: softreset failed (device not ready)
[  119.404046] ata2: applying SB600 PMP SRST workaround and retrying
[  119.576074] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  119.577215] ata2.00: configured for PIO0


CD drive info:

DVD-RAM writer
/0/100/11/1


product: CDDVDW SH-S223F
vendor: TSSTcorp
bus info: scsi@1:0.0.0
logical name: /dev/scd0
logical name: /dev/sr0
version: SB03
capabilities:
	support is removable,
	Audio CD playback,
	CD-R burning,
	CD-RW burning,
	DVD playback,
	DVD-R burning,
	DVD-RAM burning
configuration:
	ansiversion: 5
	status: ready

---

### Post by Abnormal123 on 2012-02-04
I ran the disk utility (palimpsest). When I try to run the read bechmark with a music cd mounted, I get the following messages in dmesg. I can't eject the cd after doing this and the benchmark just hangs. Any ideas?


[ 1092.329141] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1092.329147] sr 1:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[ 1092.329151] sr 1:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[ 1092.329157] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 01 00 00
[ 1092.329164] end_request: I/O error, dev sr0, sector 0
[ 1320.808034] INFO: task kworker/1:1:28 blocked for more than 120 seconds.
[ 1320.808044] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[ 1320.808051] kworker/1:1     D 00000000     0    28      2 0x00000000
[ 1320.808064]  f7591dc8 00000046 00000000 00000000 00000000 881b0145 f74c8000 c18b2d40
[ 1320.808078]  c18b2d40 7c0d7c51 000000fe f7846d40 f753e600 f74c8000 00000002 00000000
[ 1320.808092]  00000001 f753e600 c104a420 f6b2bb48 f753e600 c179f0c0 f7591dc8 c107a39b
[ 1320.808106] Call Trace:
[ 1320.808125]  [<c104a420>] ? try_to_wake_up+0x190/0x190
[ 1320.808136]  [<c107a39b>] ? ktime_get_ts+0xeb/0x120
[ 1320.808146]  [<c155ae25>] schedule+0x35/0x50
[ 1320.808153]  [<c155aeb8>] io_schedule+0x78/0xb0
[ 1320.808164]  [<c1275031>] get_request_wait+0xa1/0x170
[ 1320.808174]  [<c106f5a0>] ? add_wait_queue+0x50/0x50
[ 1320.808183]  [<c127516b>] blk_get_request+0x6b/0xa0
[ 1320.808192]  [<c138653d>] scsi_execute+0x2d/0x130
[ 1320.808200]  [<c1387879>] scsi_execute_req+0x89/0x110
[ 1320.808208]  [<c13a2e49>] sr_get_events+0x79/0xf0
[ 1320.808217]  [<c128f984>] ? rb_erase+0xb4/0x120
[ 1320.808225]  [<c13a2efb>] sr_check_events+0x3b/0x1d0
[ 1320.808235]  [<c1040b80>] ? finish_task_switch+0x40/0xc0
[ 1320.808246]  [<c13d8a3d>] cdrom_check_events+0x1d/0x40
[ 1320.808253]  [<c13a3316>] sr_block_check_events+0x16/0x20
[ 1320.808263]  [<c127ca5b>] disk_events_workfn+0x3b/0xe0
[ 1320.808271]  [<c106a721>] process_one_work+0x101/0x3a0
[ 1320.808278]  [<c106a78d>] ? process_one_work+0x16d/0x3a0
[ 1320.808287]  [<c155d0d9>] ? apic_timer_interrupt+0x31/0x38
[ 1320.808296]  [<c127ca20>] ? diskstats_show+0x3d0/0x3d0
[ 1320.808304]  [<c106a9e2>] process_scheduled_works+0x22/0x30
[ 1320.808311]  [<c106b37f>] worker_thread+0x21f/0x2d0
[ 1320.808318]  [<c106b160>] ? manage_workers.isra.28+0x110/0x110
[ 1320.808327]  [<c106ed9d>] kthread+0x6d/0x80
[ 1320.808335]  [<c106ed30>] ? flush_kthread_worker+0x80/0x80
[ 1320.808344]  [<c1563ffe>] kernel_thread_helper+0x6/0x10

---

### Post by Abnormal123 on 2012-02-04
This turned out to be a hardware issue, weird. All I did was blow some dust out of the case and changed the SATA cable to a new port on the SATA controller, and now it works perfectly. This was odd since I was able to install Ubuntu and Windows on using this drive. Anyways, at least it works now :)

---

