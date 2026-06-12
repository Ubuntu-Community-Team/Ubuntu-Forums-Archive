---
title: "System crashes using ivtv with MythTV"
date: 2011-10-09
forum: Multimedia Software
---

### Post by ravenp on 2011-10-09
Hi all,

I'm suffering from frequent system crashes with my MythTV system. I've recently upgraded the system with new hardware and changed from Ubuntu 10.04 to Ubuntu 11.04 and subsequently (in the hope this woul have cured my issue) to Ubuntu 11.10 (dev build).

My setup is:
Intel DH55TC motherboard - using integrated graphics with DVI out (i915 driver).
Intel Core i3 550.
Ubuntu 11.04/11.10 64-bit.
Hauppauge PVR-150 using IVTV.

All the hardware is new apart from the case and the Hauppauge PVR-150 PCI card. I never had any problems of this kind on my old 10.04 PC (which had the same PVR-150 card).

The system generally crashes whilst MythTV is recording TV using the PVR-150. When this happens the screen, mouse, mouse pointer and keyboard freeze, any SSH sessions become disconnected, and Apache/MythWeb no longer respond. I am unable to use CTRL/ALT/SysRq REISUB and have to forcefully power off the PC (which results in my MD RAID taking hours to rebuild after the next startup).

I set up the netconsole module so that I could capture any clues on my other PC. The captured kernel messages generally look something like this:

```

[    3.025356] ata2.01: failed to resume link (SControl 0)
[    2.939021] usb 2-1.4: unable to read config index 0 descriptor/start: -71
[    2.939032] usb 2-1.4: chopping to 0 config(s)
[    3.025703] ata2.01: failed to resume link (SControl 0)
[    3.025403] ata2.01: failed to resume link (SControl 0)
[ 6671.370199] BUG: unable to handle kernel paging request at ffff88012e727000
[ 6671.379210] IP: [<ffffffffa0250a20>] ivtv_buf_swap+0x20/0x30 [ivtv]
[ 6671.383788] PGD 1a04063 PUD 137ffa067 PMD 12d0e9063 PTE 800000012e727161
[ 6671.388354] Oops: 0003 [#1] SMP 
[ 6671.392911] CPU 1 
[ 6671.392936] Modules linked in: bnep rfcomm bluetooth binfmt_misc xfs tuner_simple tuner_types ir_lirc_codec snd_hda_codec_hdmi rc_hauppauge lirc_dev snd_hda_codec_realtek ir_sony_decoder ir_jvc_decoder ir_rc6_decoder wm8775 ir_rc5_decoder tda9887 ir_nec_decoder ir_kbd_i2c tda8290 rc_core tuner cx25840 snd_hda_intel i915 snd_hda_codec ivtv cx2341x snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device drm_kms_helper drm v4l2_common snd videodev psmouse mei(C) ppdev soundcore snd_page_alloc serio_raw v4l2_compat_ioctl32 tveeprom i2c_algo_bit video parport_pc netconsole configfs w83627ehf hwmon_vid lm75 coretemp lp parport raid10 raid456 async_raid6_recov async_pq usbhid hid raid6_pq async_xor e1000e xor async_memcpy async_tx raid1 raid0 multipath linear
[ 6671.417484] 
[ 6671.422289] Pid: 3222, comm: mythbackend Tainted: G         C  3.0.0-0300-generic #201107220917                  /DH55TC
[ 6671.427143] RIP: 0010:[<ffffffffa0250a20>]  [<ffffffffa0250a20>] ivtv_buf_swap+0x20/0x30 [ivtv]
[ 6671.431934] RSP: 0018:ffff8800b10d7d18  EFLAGS: 00010202
[ 6671.436633] RAX: 00000000554889e5 RBX: ffff88012fddc080 RCX: 00000000000c7004
[ 6671.441298] RDX: ffff88012e727000 RSI: 0000000000000282 RDI: ffff88012fddc080
[ 6671.445908] RBP: ffff8800b10d7d18 R08: ffff88012fb0155c R09: 0000000000000001
[ 6671.450427] R10: 0000000000000000 R11: 0000000000000003 R12: ffff88012ed60720
[ 6671.454955] R13: ffff88012ed609f0 R14: ffff88012ed60000 R15: ffff88012ed753f8
[ 6671.459397] FS:  00007fe6adecd700(0000) GS:ffff880137c20000(0000) knlGS:0000000000000000
[ 6671.463799] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[ 6671.468200] CR2: ffff88012e727000 CR3: 000000012f9b6000 CR4: 00000000000006e0
[ 6671.472558] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 6671.476846] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 6671.481041] Process mythbackend (pid: 3222, threadinfo ffff8800b10d6000, task ffff88007bc844d0)
[ 6671.485208] Stack:
[ 6671.489264]  ffff8800b10d7dc8 ffffffffa0245920 ffff88007bc844d0 ffff88012ed60780
[ 6671.493341]  ffff88012ed607c8 ffff88012ed607e8 ffff88012ed60a78 ffff88012ed60a98
[ 6671.497331]  ffff8800b10d7e1c 00000800ffffff9c 0000000000000000 ffff88007bc844d0
[ 6671.501346] Call Trace:
[ 6671.505347]  [<ffffffffa0245920>] ivtv_get_buffer+0x2b0/0x2e0 [ivtv]
[ 6671.509395]  [<ffffffff81084c40>] ? wake_up_bit+0x40/0x40
[ 6671.513453]  [<ffffffffa0246652>] ivtv_read+0x92/0x1d0 [ivtv]
[ 6671.517540]  [<ffffffffa02467e6>] ivtv_read_pos+0x56/0x90 [ivtv]
[ 6671.521636]  [<ffffffffa02468db>] ivtv_v4l2_read+0xbb/0xf0 [ivtv]
[ 6671.525644]  [<ffffffffa017f4b3>] v4l2_read+0xa3/0xc0 [videodev]
[ 6671.529658]  [<ffffffff8116b669>] vfs_read+0xc9/0x180
[ 6671.533666]  [<ffffffff8116bbd5>] sys_read+0x55/0x90
[ 6671.537567]  [<ffffffff815e8382>] system_call_fastpath+0x16/0x1b
[ 6671.541459] Code: 89 41 18 c9 c3 66 0f 1f 44 00 00 55 48 89 e5 66 66 66 66 90 8b 47 28 85 c0 74 17 31 c9 48 63 d1 48 03 57 20 83 c1 04 8b 02 0f c8 
[ 6671.541808]  02 39 4f 28 77 eb 1f 80 00 00 00 [ 6671.549980] RIP  [<ffffffffa0250a20>] ivtv_buf_swap+0x20/0x30 [ivtv]
[ 6671.554127]  RSP <ffff8800b10d7d18>
[ 6671.558260] CR2: ffff88012e727000
[ 6672.999432] show_signal_msg: 9 callbacks suppressed
[ 6673.003665] mythbackend[3209]: segfault at 7fe6cb3c5630 ip 00007fe6cb3c5630 sp 00007fe6b4ff0a08 error 15 in libglib-2.0.so.0.3000.0[7fe6cb37f000+f4000]
[ 6675.444387] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[ 6675.448800] ivtv0: Cause: the application is not reading fast enough.
[ 6675.549110] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[ 6675.553576] ivtv0: Cause: the application is not reading fast enough.
[ 6675.682103] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[ 6675.686632] ivtv0: Cause: the application is not reading fast enough.
[ 6676.350409] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[ 6676.354974] ivtv0: Cause: the application is not reading fast enough.
[ 6676.947342] ivtv0: All encoder MPG stream buffers are full. Dropping data.
[ 6676.951966] ivtv0: Cause: the application is not reading fast enough.

```

The common theme in all the crash reports is "BUG: unable to handle kernel paging request at" and mentions of "ivtv_buf_swap".

I've tried turning off Hyper-threading in the BIOS, upgrading to 11.10 dev, various kernel versions. The only way I can stop the crashes from happening is to blacklist ivtv in my /etc/modprobe.d/blacklist.conf file. But then I can't record TV which makes my MythTV PC pretty useless.

IVTV initialization messages (since I'm presuming the issue relates to IVTV) from the previous boot are:
```

Oct  9 17:33:58 ubuntu kernel: [    8.707207] ivtv: Start initialization, version 1.4.2
Oct  9 17:33:58 ubuntu kernel: [    8.707244] ivtv0: Initializing card 0
Oct  9 17:33:58 ubuntu kernel: [    8.707245] ivtv0: Autodetected Hauppauge card (cx23416 based)
Oct  9 17:33:58 ubuntu kernel: [    8.707322] ivtv 0000:01:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Oct  9 17:33:58 ubuntu kernel: [    8.765169] ivtv0: Autodetected Hauppauge WinTV PVR-150
Oct  9 17:33:58 ubuntu kernel: [    8.765170] ivtv0: Reopen i2c bus for IR-blaster support
Oct  9 17:33:58 ubuntu kernel: [    8.856218] cx25840 0-0044: cx25842-24 found @ 0x88 (ivtv i2c driver #0)
Oct  9 17:33:58 ubuntu kernel: [    9.563168] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
Oct  9 17:33:58 ubuntu kernel: [    9.878384] ir-kbd-i2c: i2c IR (Hauppauge WinTV PVR-150 detected at i2c-0/0-0071/ir0 [ivtv i2c driver #0]
Oct  9 17:33:58 ubuntu kernel: [   10.057444] ivtv0: Registered device video0 for encoder MPG (4096 kB)
Oct  9 17:33:58 ubuntu kernel: [   10.057464] ivtv0: Registered device video32 for encoder YUV (2048 kB)
Oct  9 17:33:58 ubuntu kernel: [   10.057482] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
Oct  9 17:33:58 ubuntu kernel: [   10.057499] ivtv0: Registered device video24 for encoder PCM (320 kB)
Oct  9 17:33:58 ubuntu kernel: [   10.057519] ivtv0: Registered device radio0 for encoder radio
Oct  9 17:33:58 ubuntu kernel: [   10.057520] ivtv0: Initialized card: Hauppauge WinTV PVR-150
Oct  9 17:33:58 ubuntu kernel: [   10.057540] ivtv: End initialization
Oct  9 17:33:58 ubuntu kernel: [   11.056258] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Oct  9 17:33:58 ubuntu kernel: [   11.264898] ivtv0: Encoder revision: 0x02060039

```

Does anyone have any suggestions or advice?
Thank you.

---

