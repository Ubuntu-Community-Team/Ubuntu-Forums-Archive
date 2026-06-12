---
title: "Null pointer dereference"
date: 2008-09-29
forum: Mythbuntu
---

### Post by rstuart on 2008-09-29
Hi All,

After applying Ubuntu updates to my mythbuntu box (one of which was the new 2.6.24-19 kernel image), I can no longer watch TV (as a side note, this is really annoying because I literally only just got my remote working :( ). Every time I try to watch tv, it says it can't connect to the backend.

So I decided to run the myth-setup to make sure everything was ok. When I try to add, edit a capture card, myth-setup hangs. The following also appears in syslog:

```

Sep 29 20:20:01 danny /USR/SBIN/CRON[6517]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Sep 29 20:21:24 danny kernel: [  654.386509] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
Sep 29 20:21:24 danny kernel: [  654.386520]  [dvb_core:dvb_frontend_open+0x230/0x2a0] :dvb_core:dvb_frontend_open+0x230/0x2a0
Sep 29 20:21:24 danny kernel: [  654.386542] PGD 1ddec067 PUD 1ddc9067 PMD 0 
Sep 29 20:21:24 danny kernel: [  654.386547] Oops: 0000 [1] SMP 
Sep 29 20:21:24 danny kernel: [  654.386550] CPU 0 
Sep 29 20:21:24 danny kernel: [  654.386552] Modules linked in: af_packet ipv6 cpufreq_powersave cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table video output container sbs sbshc dock battery iptable_filter ip_tables x_tables ac sbp2 lp mt2266 lirc_imon(F) lirc_dev dvb_usb_dib0700 dib7000p dib7000m dvb_usb dvb_core joydev dib3000mc dibx000_common dib0070 saa7134_alsa snd_hda_intel snd_pcm_oss snd_mixer_oss snd_hwdep snd_seq_dummy snd_pcm snd_page_alloc snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event saa7134 snd_seq compat_ioctl32 snd_timer snd_seq_device videobuf_dma_sg videobuf_core ir_kbd_i2c snd ir_common i2c_nforce2 videodev nvidia(P) v4l2_common v4l1_compat button psmouse serio_raw shpchp pci_hotplug soundcore i2c_core parport_pc parport evdev k8temp pcspkr ext3 jbd mbcache usb_storage sg sd_mod usbhid hid libusual sata_nv pata_amd pata_acpi floppy ohci1394 ieee1394 forcedeth ata_generic ohci_hcd ehci_hcd libata scsi_mod usbcore thermal processor fan fbcon tileblit 
Sep 29 20:21:24 danny kernel: ont bitblit softcursor fuse
Sep 29 20:21:24 danny kernel: [  654.386611] Pid: 6704, comm: mythtv-setup.re Tainted: PF       2.6.24-19-generic #1
Sep 29 20:21:24 danny kernel: [  654.386614] RIP: 0010:[dvb_core:dvb_frontend_open+0x230/0x2a0]  [dvb_core:dvb_frontend_open+0x230/0x2a0] :dvb_core:dvb_frontend_open+0x230/0x2a0
Sep 29 20:21:24 danny kernel: [  654.386623] RSP: 0018:ffff81001dce1db8  EFLAGS: 00010246
Sep 29 20:21:24 danny kernel: [  654.386624] RAX: 0000000000000000 RBX: 0000000000000000 RCX: ffff81003ab24de0
Sep 29 20:21:24 danny kernel: [  654.386626] RDX: ffffffff88c03f45 RSI: ffff81003ce96000 RDI: ffffffff88bff3a0
Sep 29 20:21:24 danny kernel: [  654.386628] RBP: ffff81003ce96000 R08: ffff81003b8cedb0 R09: 0000000000000000
Sep 29 20:21:24 danny kernel: [  654.386630] R10: 0000000000000000 R11: ffff81003bf76db8 R12: ffff81003b19c800
Sep 29 20:21:24 danny kernel: [  654.386632] R13: ffff810010078240 R14: ffff81003ab24de0 R15: ffff81003b19c800
Sep 29 20:21:24 danny kernel: [  654.386635] FS:  00007f0ea20de7c0(0000) GS:ffffffff805b9000(0000) knlGS:0000000000000000
Sep 29 20:21:24 danny kernel: [  654.386637] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Sep 29 20:21:24 danny kernel: [  654.386638] CR2: 0000000000000000 CR3: 000000001ddd5000 CR4: 00000000000006e0
Sep 29 20:21:24 danny kernel: [  654.386640] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Sep 29 20:21:24 danny kernel: [  654.386642] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Sep 29 20:21:24 danny kernel: [  654.386644] Process mythtv-setup.re (pid: 6704, threadinfo ffff81001dce0000, task ffff810023b9f7a0)
Sep 29 20:21:24 danny kernel: [  654.386646] Stack:  0000000000000000 ffff81003bcc60d0 ffff81003b19c9b0 0000000000000000
Sep 29 20:21:24 danny kernel: [  654.386651]  ffff810010078240 ffffffff88c0d120 ffff81003bcc60d0 ffff810010078240
Sep 29 20:21:24 danny kernel: [  654.386654]  ffffffff802b5dd0 ffffffff88bf76dc ffffffff88c0e020 0000000000000000
Sep 29 20:21:24 danny kernel: [  654.386657] Call Trace:
Sep 29 20:21:24 danny kernel: [  654.386673]  [chrdev_open+0x0/0x1d0] chrdev_open+0x0/0x1d0
Sep 29 20:21:24 danny kernel: [  654.386680]  [dvb_core:dvb_device_open+0xcc/0x140] :dvb_core:dvb_device_open+0xcc/0x140
Sep 29 20:21:24 danny kernel: [  654.386685]  [chrdev_open+0xc1/0x1d0] chrdev_open+0xc1/0x1d0
Sep 29 20:21:24 danny kernel: [  654.386696]  [__dentry_open+0xdb/0x200] __dentry_open+0xdb/0x200
Sep 29 20:21:24 danny kernel: [  654.386705]  [do_filp_open+0x3a/0x50] do_filp_open+0x3a/0x50
Sep 29 20:21:24 danny kernel: [  654.386717]  [get_unused_fd_flags+0x77/0x120] get_unused_fd_flags+0x77/0x120
Sep 29 20:21:24 danny kernel: [  654.386726]  [do_sys_open+0x5a/0xf0] do_sys_open+0x5a/0xf0
Sep 29 20:21:24 danny kernel: [  654.386734]  [system_call+0x7e/0x83] system_call+0x7e/0x83
Sep 29 20:21:24 danny kernel: [  654.386747] 
Sep 29 20:21:24 danny kernel: [  654.386748] 
Sep 29 20:21:24 danny kernel: [  654.386748] Code: 8b 08 31 c0 e8 17 56 65 f7 48 3d 00 f0 ff ff 77 1d 48 89 c7 
Sep 29 20:21:24 danny kernel: [  654.386755] RIP  [dvb_core:dvb_frontend_open+0x230/0x2a0] :dvb_core:dvb_frontend_open+0x230/0x2a0
Sep 29 20:21:24 danny kernel: [  654.386763]  RSP <ffff81001dce1db8>
Sep 29 20:21:24 danny kernel: [  654.386765] CR2: 0000000000000000
Sep 29 20:21:24 danny kernel: [  654.386773] ---[ end trace b58afee20014b695 ]---

```

Obviously a bug somewhere in the kernel I guess? Any idea where to go from here? The obvious solution to me was to move back to an earlier kernel image. But the mythbuntu-desktop depends on the meta packages in Ubuntu for the latest kernel image, headers etc. which in turn obviously depend on the latest kernel and I don't know enough about the packaging system to get around that. Any ideas?

Cheers

---

### Post by stevanbt on 2008-09-29
Hi,
Two things spring to mind...

Does your system work ok when you pick the previous kernel in Grub?  And have you re-applied any drivers/modules for the new kernel?

Thanks, Steve.

---

### Post by rstuart on 2008-09-29
> **stevanbt said:**
> 
Does your system work ok when you pick the previous kernel in Grub?  And have you re-applied any drivers/modules for the new kernel?


It doesn't appear in grub so I installed the generic image, headers, ubuntu modules and restricted modules for 2.6.24-18 and it boots fine. It lets me attempt to add a capture card but neither syslog or dmesg report finding any of my capture cards nor does my remote work anymore. Is there something else I need to do to install a previous kernel?

No, I haven't re-applied any drivers or modules. The only program I had to compile from scratch was lirc which for my remote which I compiled to /usr/local/sbin/lirc and un-installed the original. The remote worked fine under the new kernel.

Cheers

---

