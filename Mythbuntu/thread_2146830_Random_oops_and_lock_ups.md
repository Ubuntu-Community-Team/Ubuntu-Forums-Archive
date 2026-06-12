---
title: "Random oops and lock ups"
date: 2013-05-19
forum: Mythbuntu
---

### Post by daninca on 2013-05-19
I rebuilt my mythtv box a few months back and have been getting random lock ups ever since.  I swapped out every piece of hardware (different brands of tuners, Nvidia and Intel video cards, motherboards, hard drives, AMD and Intel CPUs) since then, but the problems persist.  I finally figured out how to use netconsole get the full oops information.

How do I figure out what's going wrong?

Here is the start of the oops (full log file attached):
[14054.526851] BUG: unable to handle kernel NULL pointer dereference at 0000000000000001
[14054.526887] IP: [<ffffffff81165e4a>] kmem_cache_alloc+0x5a/0x140
[14054.526910] PGD 36eab067 PUD 36eaa067 PMD 0 
[14054.526928] Oops: 0000 [#1] SMP 
[14054.526942] CPU 3 
[14054.526948] Modules linked in: netconsole configfs tda18271 s5h1411 autofs4 snd_hda_codec_hdmi snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq ir_lirc_codec lirc_dev ir_mce_kbd_decoder ir_sony_decoder ir_jvc_decoder ir_rc6_decoder ir_rc5_decoder snd_timer ir_nec_decoder rc_rc6_mce mceusb rc_core snd_seq_device usbhid saa7164 hid snd dvb_core v4l2_common videodev mac_hid i915 drm_kms_helper drm v4l2_compat_ioctl32 tveeprom i2c_algo_bit psmouse soundcore mei(C) video snd_page_alloc serio_raw ppdev parport_pc nfsd nfs lockd fscache auth_rpcgss nfs_acl sunrpc lp parport usb_storage r8169
[14054.527253] 
[14054.527260] Pid: 5084, comm: mythpreviewgen Tainted: G         C   3.2.0-43-generic #68-Ubuntu To Be Filled By O.E.M. To Be Filled By O.E.M./B75 Pro3-M
[14054.527299] RIP: 0010:[<ffffffff81165e4a>]  [<ffffffff81165e4a>] kmem_cache_alloc+0x5a/0x140
[14054.527377] RSP: 0018:ffff8800b34e9d60  EFLAGS: 00010202
[14054.527410] RDX: 0000000000009b0b RSI: 0000000000016640 RDI: ffff880215c02800
[14054.527427] RBP: ffff8800b34e9db0 R08: ffff88021e396640 R09: ffff88020ce0cd90
[14054.527445] R10: 0000000000000007 R11: 0000000000016bb0 R12: ffff880215c02800
[14054.527463] R13: 0000000000000001 R14: ffffffff81087ef4 R15: 00000000000000d0
[14054.527481] FS:  00007f3697956780(0000) GS:ffff88021e380000(0000) knlGS:0000000000000000
[14054.527501] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[14054.527515] CR2: 0000000000000001 CR3: 00000000b3554000 CR4: 00000000001406e0
[14054.527533] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[14054.527551] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[14054.527569] Process mythpreviewgen (pid: 5084, threadinfo ffff8800b34e8000, task ffff88020eab5c00)
[14054.527590] Stack:
[14054.527597]  ffff8800b34e9db0 ffffffff8105789c 0000000000000286 00000003810e41f2
[14054.527623]  ffff8800b34e9d90 ffff88020fb25c00 ffffffff81c28120 00007f3678e959d0
[14054.527647]  0000000000000000 ffff8800b34e9f58 ffff8800b34e9de0 ffffffff81087ef4
[14054.527672] Call Trace:
[14054.527682]  [<ffffffff8105789c>] ? task_fork_fair+0xdc/0x160
[14054.527699]  [<ffffffff81087ef4>] alloc_pid+0x24/0x200
[14054.527715]  [<ffffffff810669e4>] copy_process.part.18+0x904/0xe30
[14054.527734]  [<ffffffff81662690>] ? do_page_fault+0x210/0x520
[14054.527750]  [<ffffffff81066f87>] copy_process+0x77/0x80
[14054.527774]  [<ffffffff810670da>] do_fork+0xfa/0x2f0
[14054.527789]  [<ffffffff8101d658>] sys_clone+0x28/0x30
[14054.527804]  [<ffffffff816673e3>] stub_clone+0x13/0x20
[14054.527818]  [<ffffffff816670c2>] ? system_call_fastpath+0x16/0x1b
[14054.527834] Code: 00 4d 8b 04 24 65 4c 03 04 25 50 da 00 00 49 8b 50 08 4d 8b 28 4d 85 ed 0f 84 d8 00 00 00 49 63 44 24 20 49 8b 34 24 48 8d 4a 01 <49> 8b 5c 05 00 4c 89 e8 65 48 0f c7 0e 0f 94 c0 84 c0 74 c2 4d 
[14054.528099] RIP  [<ffffffff81165e4a>] kmem_cache_alloc+0x5a/0x140
[14054.528116]  RSP <ffff8800b34e9d60>
[14054.528126] CR2: 0000000000000001
[14054.555688] BUG: unable to handle kernel NULL pointer dereference at 0000000000000001
[14054.555723] IP: [<ffffffff81165e4a>] kmem_cache_alloc+0x5a/0x140
[14054.555745] PGD 0 

uname -a: 
Linux vonbraun 3.2.0-43-generic #68-Ubuntu SMP Wed May 15 03:33:33 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

lspci:
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 5 (rev c4)
00:1c.5 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 6 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Multimedia controller: Philips Semiconductors SAA7164 (rev 81)
02:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

grep "model name" /proc/cpuinfo 
model name	: Intel(R) Core(TM) i3-3220 CPU @ 3.30GHz

---

### Post by K31jySofI on 2013-07-04
I had the same problem with my i3-3225 and gigabyte B75M-D3P motherboad with 2x4 GB RAM. During a three week period it always crashed within 3 days.

dmesg showed trouble allocating mtrr.
memtest used timing for the the ram as 6-6-6-20 for one and 11-11-11-30 for the other (11-11-11-30 is printed on the ramsticks). No memory error in 20 runs for both of the sticks.

Selecting several of the available mtrr settings did not help.

I *think* I have removed the problem (no oopses in seven day now). Unfortunately I did three things at once trying to fix it:

1) Increased the memory for the internal HD4000 graphics to 1024M
2) Moved the sticks from DDR3_1/DDR3_2 to DDR3_3/DDR3_4
3) Turned off both serial ports and the parallel port

After this mtrr found a suitable setting by itself and no crashes yet.


Tue Jul 16. ...and no. The computer froze again. No output from netconsole or /proc/kmsg. And no response from the sysrqkey combinatons.

---

