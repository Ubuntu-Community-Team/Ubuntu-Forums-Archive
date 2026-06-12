---
title: "Skystar HD2 CA module not working"
date: 2010-07-22
forum: Multimedia Software
---

### Post by xandy on 2010-07-22
Hello everybody,

I have a problem to get running my Skystar HD2 CA module. There is bug but I dont know how to fix it.

I have Ubuntu 10.04 with latest kernel 2.6.32-23-generic and using s2-liplianin driver. With v4l-dvb it is ok system is stable but I can not watch scrambled channels.

This is from dmesg:

[   43.719006] BUG: unable to handle kernel NULL pointer dereference at 00000002
[   43.719014] IP: [<c025f3d1>] sysfs_open_file+0xc1/0x1c0
[   43.719023] *pde = 3cf17067 
[   43.719027] Oops: 0000 [#1] SMP 
[   43.719030] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/i2c-1/uevent
[   43.719033] Modules linked in: snd_hda_codec_analog fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd
_hwdep ir_sony_decoder snd_pcm_oss snd_mixer_oss ir_jvc_decoder snd_pcm snd_seq_dummy ir_rc6_decoder mantis snd_seq_oss ir_rc5_decoder lnbp21 
snd_seq_midi ir_nec_decoder mb86a16 snd_rawmidi ir_core snd_seq_midi_event snd_seq stb6100 tda10021 tda10023 stb0899 i915 snd_timer stv0299 sn
d_seq_device drm_kms_helper dell_wmi ppdev dcdbas drm snd parport_pc intel_agp psmouse serio_raw dvb_core i2c_algo_bit soundcore snd_page_allo
c agpgart video output lp parport usbhid hid ahci e1000e
[   43.719075] 
[   43.719078] Pid: 885, comm: udev-acl.ck Not tainted (2.6.32-23-generic #37-Ubuntu) OptiPlex 755                 
[   43.719081] EIP: 0060:[<c025f3d1>] EFLAGS: 00010206 CPU: 0
[   43.719085] EIP is at sysfs_open_file+0xc1/0x1c0
[   43.719087] EAX: 000081a4 EBX: efaf4700 ECX: 00000000 EDX: f494a000
[   43.719090] ESI: f1cdf2d0 EDI: 00000002 EBP: efb71e6c ESP: efb71e3c
[   43.719092]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   43.719095] Process udev-acl.ck (pid: 885, ti=efb70000 task=f2993300 task.ti=efb70000)
[   43.719097] Stack:
[   43.719099]  f2993300 f2993300 f2993300 00000101 f686bde8 f686bd80 efb71e5c f494a000
[   43.719105] <0> f1f49898 efaf4700 f494a000 f6869a00 efb71e94 c02067e5 c02f5d2d efb71e88
[   43.719110] <0> c02116de f4931a18 00000000 f4931a18 efaf4700 efb71ef0 efb71eb0 c0206a8d
[   43.719117] Call Trace:
[   43.719123]  [<c02067e5>] ? __dentry_open+0xe5/0x290
[   43.719128]  [<c02f5d2d>] ? security_inode_permission+0x1d/0x30
[   43.719132]  [<c02116de>] ? inode_permission+0x9e/0xb0
[   43.719136]  [<c0206a8d>] ? nameidata_to_filp+0x5d/0x70
[   43.719139]  [<c025f310>] ? sysfs_open_file+0x0/0x1c0
[   43.719143]  [<c02150a2>] ? do_filp_open+0x4d2/0x990
[   43.719146]  [<c0214a3a>] ? user_path_at+0x4a/0x80
[   43.719150]  [<c0353999>] ? copy_to_user+0x39/0x130
[   43.719155]  [<c0206545>] ? do_sys_open+0x55/0x160
[   43.719159]  [<c02066be>] ? sys_open+0x2e/0x40
[   43.719163]  [<c01033ec>] ? syscall_call+0x7/0xb
[   43.719165] Code: 8b 55 e0 83 c4 24 89 d0 5b 5e 5f 5d c3 90 8d 74 26 00 8b 4f 04 85 c9 74 d8 a8 01 74 14 8b 55 ec 0f b7 42 72 a9 24 01 00 0
0 74 c6 <8b> 17 85 d2 74 c0 ba d0 80 00 00 b8 98 46 76 c0 e8 0a e5 f9 ff 
[   43.719197] EIP: [<c025f3d1>] sysfs_open_file+0xc1/0x1c0 SS:ESP 0068:efb71e3c
[   43.719202] CR2: 0000000000000002
[   43.719206] ---[ end trace c7ff14953acd9105 ]---
[   43.759486] BUG: unable to handle kernel NULL pointer dereference at 00000002
[   43.759493] IP: [<c025f3d1>] sysfs_open_file+0xc1/0x1c0
[   43.759503] *pde = 3cfb2067 
[   43.759506] Oops: 0000 [#2] SMP 
[   43.759509] last sysfs file: /sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/i2c-1/uevent
[   43.759513] Modules linked in: snd_hda_codec_analog fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd
_hwdep ir_sony_decoder snd_pcm_oss snd_mixer_oss ir_jvc_decoder snd_pcm snd_seq_dummy ir_rc6_decoder mantis snd_seq_oss ir_rc5_decoder lnbp21 
snd_seq_midi ir_nec_decoder mb86a16 snd_rawmidi ir_core snd_seq_midi_event snd_seq stb6100 tda10021 tda10023 stb0899 i915 snd_timer stv0299 sn
d_seq_device drm_kms_helper dell_wmi ppdev dcdbas drm snd parport_pc intel_agp psmouse serio_raw dvb_core i2c_algo_bit soundcore snd_page_allo
c agpgart video output lp parport usbhid hid ahci e1000e
[   43.759554] 
[   43.759558] Pid: 893, comm: udev-acl.ck Tainted: G      D    (2.6.32-23-generic #37-Ubuntu) OptiPlex 755                 
[   43.759561] EIP: 0060:[<c025f3d1>] EFLAGS: 00010206 CPU: 0
[   43.759565] EIP is at sysfs_open_file+0xc1/0x1c0
[   43.759567] EAX: 000081a4 EBX: f4cdb700 ECX: 00000001 EDX: f494a000
[   43.759570] ESI: f1cdf2d0 EDI: 00000002 EBP: efb79e6c ESP: efb79e3c
[   43.759572]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[   43.759575] Process udev-acl.ck (pid: 893, ti=efb78000 task=f2996600 task.ti=efb78000)
[   43.759577] Stack:
[   43.759578]  f2996600 f2996600 f2996600 00000101 f686bde8 f686bd80 efb79e5c f494a000
[   43.759584] <0> f1f49898 f4cdb700 f494a000 f6869a00 efb79e94 c02067e5 c02f5d2d efb79e88
[   43.759590] <0> c02116de f4931a18 00000000 f4931a18 f4cdb700 efb79ef0 efb79eb0 c0206a8d
[   43.759597] Call Trace:
[   43.759602]  [<c02067e5>] ? __dentry_open+0xe5/0x290
[   43.759607]  [<c02f5d2d>] ? security_inode_permission+0x1d/0x30
[   43.759612]  [<c02116de>] ? inode_permission+0x9e/0xb0
[   43.759616]  [<c0206a8d>] ? nameidata_to_filp+0x5d/0x70
[   43.759619]  [<c025f310>] ? sysfs_open_file+0x0/0x1c0
[   43.759623]  [<c02150a2>] ? do_filp_open+0x4d2/0x990
[   43.759626]  [<c0214a3a>] ? user_path_at+0x4a/0x80
[   43.759630]  [<c0353999>] ? copy_to_user+0x39/0x130
[   43.759635]  [<c0206545>] ? do_sys_open+0x55/0x160
[   43.759638]  [<c02066be>] ? sys_open+0x2e/0x40
[   43.759642]  [<c01033ec>] ? syscall_call+0x7/0xb
[   43.759644] Code: 8b 55 e0 83 c4 24 89 d0 5b 5e 5f 5d c3 90 8d 74 26 00 8b 4f 04 85 c9 74 d8 a8 01 74 14 8b 55 ec 0f b7 42 72 a9 24 01 00 0
0 74 c6 <8b> 17 85 d2 74 c0 ba d0 80 00 00 b8 98 46 76 c0 e8 0a e5 f9 ff 
[   43.759677] EIP: [<c025f3d1>] sysfs_open_file+0xc1/0x1c0 SS:ESP 0068:efb79e3c
[   43.759682] CR2: 0000000000000002
[   43.759685] ---[ end trace c7ff14953acd9106 ]---

Sometimes my computer hangs.

Is there anybody who can help me?

Thank you!

---

