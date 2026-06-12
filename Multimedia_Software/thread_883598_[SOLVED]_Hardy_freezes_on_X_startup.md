---
title: "[SOLVED] Hardy freezes on X startup"
date: 2008-08-08
forum: Multimedia Software
---

### Post by Marcin Nawrocki on 2008-08-08
I've got kubuntu 8.04.1 64bit working on AMD x2 3800, 2Gb ram, ASROCK agp mainboard. System used to work perfectly with NVIDIA card.
Now I've got ATI 3850. I installed drivers from ubuntu repository.
Everytning seems to be fine, but X session hangs every time.
There is no error in Xorg.0.log file.
There are some warnings:
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(WW) fglrx(0): could not detect X server version (query_status=-3)
I guess they are irrelevant.

What I found is the information in the syslog about software bug:

Aug  7 01:32:37 kubunciak kernel:  sd_mod pata_amd ata_generic usbhid hid floppy pata_acpi sata_nv ehci_hcd libata scsi_mod forcedeth ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Aug  7 01:32:37 kubunciak kernel: [   79.837264] Pid: 7875, comm: Xorg Tainted: P        2.6.24-20-generic #1
Aug  7 01:32:37 kubunciak kernel: [   79.837267] RIP: 0010:[fglrx:_ZN7PM4Ring4rptrEv+0x0/0x10]  [fglrx:_ZN7PM4Ring4rptrEv+0x0/0x10] :fglrx:_ZN7PM4Ring4rptrEv+0x0/0x10
Aug  7 01:32:37 kubunciak kernel: [   79.837354] RSP: 0018:ffff81007d2d99a0  EFLAGS: 00200286
Aug  7 01:32:37 kubunciak kernel: [   79.837356] RAX: ffffc2000033b084 RBX: 00000000007ffff9 RCX: 0000000000000000
Aug  7 01:32:37 kubunciak kernel: [   79.837358] RDX: ffffc20000ee0020 RSI: ffffc20000ee0020 RDI: ffffc2000123dc80
Aug  7 01:32:37 kubunciak kernel: [   79.837361] RBP: 0000000000000000 R08: ffffffff882d7870 R09: 0000000000000043
Aug  7 01:32:37 kubunciak kernel: [   79.837363] R10: 0000000000401603 R11: 0000000000400000 R12: ffffffff88278d99
Aug  7 01:32:37 kubunciak kernel: [   79.837366] R13: ffffc20000ebe130 R14: ffff81007b252358 R15: 0000000000000000
Aug  7 01:32:37 kubunciak kernel: [   79.837369] FS:  00007f0554eea6e0(0000) GS:ffffffff805b9000(0000) knlGS:00000000f7df58c0
Aug  7 01:32:37 kubunciak kernel: [   79.837372] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug  7 01:32:37 kubunciak kernel: [   79.837374] CR2: 00000000006145e8 CR3: 000000007b1ab000 CR4: 00000000000006e0
Aug  7 01:32:37 kubunciak kernel: [   79.837377] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug  7 01:32:37 kubunciak kernel: [   79.837379] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug  7 01:32:37 kubunciak kernel: [   79.837382] 
Aug  7 01:32:37 kubunciak kernel: [   79.837382] Call Trace:
Aug  7 01:32:37 kubunciak kernel: [   79.837449]  [fglrx:_ZN4Asic16Is_WPTR_equ_RPTR19ConditionSuccessfulEv+0x38/0x60] :fglrx:_ZN4Asic16Is_WPTR_equ_RPTR19ConditionSuccessfulEv+0x38/0x60
Aug  7 01:32:37 kubunciak kernel: [   79.837518]  [fglrx:_ZN4Asic9WaitUntil15WaitForCompleteEv+0x1f/0xb0] :fglrx:_ZN4Asic9WaitUntil15WaitForCompleteEv+0x1f/0xa0
Aug  7 01:32:37 kubunciak kernel: [   79.837588]  [fglrx:_ZN8AsicR60016ASICIdleInternalEN4Asic15idle_WaitMethodE+0xa2/0x1e0] :fglrx:_ZN8AsicR60016ASICIdleInternalEN4Asic15idle_WaitMethodE+0xa2/0x1e0
Aug  7 01:32:37 kubunciak kernel: [   79.837659]  [fglrx:_ZN7PM4Ring8PM4queueEPPj+0x3f/0x100] :fglrx:_ZN7PM4Ring8PM4queueEPPj+0x3f/0xb0
Aug  7 01:32:37 kubunciak kernel: [   79.837730]  [fglrx:_ZN8AsicR60021initializeMicroEngineEv+0x13b/0x150] :fglrx:_ZN8AsicR60021initializeMicroEngineEv+0x13b/0x150
Aug  7 01:32:37 kubunciak kernel: [   79.837797]  [fglrx:_ZN4Asic7PM4idleENS_15idle_WaitMethodE+0x55/0x90] :fglrx:_ZN4Asic7PM4idleENS_15idle_WaitMethodE+0x55/0x90
Aug  7 01:32:37 kubunciak kernel: [   79.837864]  [fglrx:_ZN4Asic9assertPM4Eb+0xf8/0x250] :fglrx:_ZN4Asic9assertPM4Eb+0xf8/0x250
Aug  7 01:32:37 kubunciak kernel: [   79.837932]  [fglrx:_ZN8AsicR6009assertPM4Eb+0x32/0x70] :fglrx:_ZN8AsicR6009assertPM4Eb+0x32/0x50
Aug  7 01:32:37 kubunciak kernel: [   79.837993]  [fglrx:CMMQS_Initialize+0x133/0x2c0] :fglrx:CMMQS_Initialize+0x133/0x160
Aug  7 01:32:37 kubunciak kernel: [   79.838044]  [fglrx:firegl_cmmqs_init+0x48e/0x610] :fglrx:firegl_cmmqs_init+0x48e/0x540
Aug  7 01:32:37 kubunciak kernel: [   79.838169]  [fglrx:firegl_cmmqs_createdriver+0x104/0x1f0] :fglrx:firegl_cmmqs_createdriver+0x104/0x120
Aug  7 01:32:37 kubunciak kernel: [   79.838221]  [fglrx:firegl_cmmqs_createdriver+0x0/0x1f0] :fglrx:firegl_cmmqs_createdriver+0x0/0x120
Aug  7 01:32:37 kubunciak kernel: [   79.838268]  [fglrx:firegl_ioctl+0x1b6/0x230] :fglrx:firegl_ioctl+0x1b6/0x230
Aug  7 01:32:37 kubunciak kernel: [   79.838285]  [do_ioctl+0x7d/0xa0] do_ioctl+0x7d/0xa0
Aug  7 01:32:37 kubunciak kernel: [   79.838291]  [vfs_ioctl+0x220/0x2c0] vfs_ioctl+0x220/0x2c0
Aug  7 01:32:37 kubunciak kernel: [   79.838297]  [vfs_write+0x14e/0x190] vfs_write+0x14e/0x190
Aug  7 01:32:37 kubunciak kernel: [   79.838304]  [sys_ioctl+0x91/0xb0] sys_ioctl+0x91/0xb0
Aug  7 01:32:37 kubunciak kernel: [   79.838313]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Aug  7 01:32:37 kubunciak kernel: [   79.838327] 
Aug  7 01:32:49 kubunciak kernel: [   91.633866] **BUG: soft lockup - CPU#0 stuck for 11s! [Xorg:7875]**
Aug  7 01:32:49 kubunciak kernel: [   91.633869] CPU 0:

Any help?

---

