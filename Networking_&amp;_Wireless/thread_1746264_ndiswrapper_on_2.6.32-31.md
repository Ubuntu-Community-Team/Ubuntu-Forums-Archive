---
title: "ndiswrapper on 2.6.32-31"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by bibble235 on 2011-05-01
Hi,

I have managed to get rt2870 to work using ndiswrapper using 2.6.32-30. However on 2.6.32-31 I get the following error

 [  816.773704]  [<c012a768>] ? default_spin_lock_flags+0x8/0x10
 [  816.773718]  [<c058f74f>] ? _spin_lock_irqsave+0x2f/0x50
 [  816.773728]  [<c015bb3c>] ? lock_timer_base+0x2c/0x60
 [  816.773737]  [<c015c4c8>] ? try_to_del_timer_sync+0x68/0xb0
 [  816.773746]  [<c015c529>] ? del_timer_sync+0x19/0x20
 [  816.773756]  [<c058df22>] ? schedule_timeout+0x142/0x280
 [  816.773765]  [<c015bc20>] ? process_timeout+0x0/0x10
 [  816.773775]  [<c058f9c6>] ? _spin_unlock_bh+0x16/0x20
 [  816.773821]  [<f8811065>] ? KeWaitForMultipleObjects+0x165/0x440 [ndiswrapper]
 [  816.773833]  [<c04499ad>] ? usb_submit_urb+0xdd/0x240
 [  816.773842]  [<c058f9c6>] ? _spin_unlock_bh+0x16/0x20
 [  816.773878]  [<f881e40c>] ? wrap_submit_urb+0x6c/0xb0 [ndiswrapper]
 [  816.773914]  [<f881ebb5>] ? wrap_submit_irp+0x2f5/0xb80 [ndiswrapper]
 [  816.773924]  [<c058f9c6>] ? _spin_unlock_bh+0x16/0x20
 [  816.773960]  [<f880f783>] ? get_current_nt_thread+0x53/0x60 [ndiswrapper]
 [  816.773997]  [<f8813f9c>] ? IoQueueThreadIrp+0x1c/0x130 [ndiswrapper]
 [  816.774031]  [<f8814665>] ? IoAllocateIrp+0x65/0x80 [ndiswrapper]
 [  816.774067]  [<f881138c>] ? KeWaitForSingleObject+0x4c/0x60 [ndiswrapper]
 [  816.774117]  [<f8811c00>] ? allocate_init_mdl+0x170/0x1b0 [ndiswrapper]
 [  816.774158]  [<f881b286>] ? mp_init+0x66/0x210 [ndiswrapper]
 [  816.774193]  [<f881cccc>] ? NdisDispatchPnp+0x9c/0xbb0 [ndiswrapper]
 [  816.774202]  [<c058df8d>] ? schedule_timeout+0x1ad/0x280
 [  816.774237]  [<f881464f>] ? IoAllocateIrp+0x4f/0x80 [ndiswrapper]
 [  816.774272]  [<f8814665>] ? IoAllocateIrp+0x65/0x80 [ndiswrapper]
 [  816.774282]  [<c058f9c6>] ? _spin_unlock_bh+0x16/0x20
 [  816.774317]  [<f880f783>] ? get_current_nt_thread+0x53/0x60 [ndiswrapper]
 [  816.774352]  [<f8813f9c>] ? IoQueueThreadIrp+0x1c/0x130 [ndiswrapper]
 [  816.774362]  [<c058f937>] ? _spin_lock_bh+0x17/0x20
 [  816.774397]  [<f8813966>] ? IofCallDriver+0x56/0xc0 [ndiswrapper]
 [  816.774432]  [<f881545b>] ? IoSendIrpTopDev+0xbb/0x110 [ndiswrapper]
 [  816.774468]  [<f8815721>] ? pnp_start_device+0x41/0x90 [ndiswrapper]
 [  816.774503]  [<f8815a96>] ? wrap_pnp_start_device+0x1a6/0x280 [ndiswrapper]
 [  816.774540]  [<f8815c2e>] ? wrap_pnp_start_usb_device+0xbe/0xf0 [ndiswrapper]
 [  816.774552]  [<c0260ed9>] ? sysfs_find_dirent+0x29/0x40
 [  816.774564]  [<c021e035>] ? iput+0x25/0x60
 [  816.774574]  [<c026189b>] ? sysfs_addrm_finish+0x3b/0xf0
 [  816.774583]  [<c058e5b9>] ? mutex_lock+0x19/0x40
 [  816.774592]  [<c044cc0c>] ? usb_autopm_do_device+0x6c/0x100
 [  816.774602]  [<c044d750>] ? usb_probe_interface+0xc0/0x180
 [  816.774612]  [<c0262187>] ? sysfs_create_link+0x17/0x20
 [  816.774622]  [<c03e996d>] ? really_probe+0x4d/0x140
 [  816.774635]  [<c03f027e>] ? pm_runtime_barrier+0x4e/0xc0
 [  816.774644]  [<c03e9a9c>] ? driver_probe_device+0x3c/0x60
 [  816.774652]  [<c03e9b41>] ? __driver_attach+0x81/0x90
 [  816.774661]  [<c03e8f83>] ? bus_for_each_dev+0x53/0x80
 [  816.774670]  [<c03e983e>] ? driver_attach+0x1e/0x20
 [  816.774678]  [<c03e9ac0>] ? __driver_attach+0x0/0x90
 [  816.774686]  [<c03e9205>] ? bus_add_driver+0xd5/0x280
 [  816.774696]  [<c03e9e3a>] ? driver_register+0x6a/0x130
 [  816.774706]  [<c044d4f1>] ? usb_register_driver+0x81/0xf0
 [  816.774716]  [<c0260411>] ? sysfs_create_file+0x21/0x30
 [  816.774725]  [<c03e9fcb>] ? driver_create_file+0x1b/0x20
 [  816.774758]  [<f8808385>] ? loader_init+0xb5/0x150 [ndiswrapper]
 [  816.774792]  [<f8816337>] ? wrap_procfs_init+0x47/0xc0 [ndiswrapper]
 [  816.774819]  [<f820b07f>] ? wrapper_init+0x7f/0xb7 [ndiswrapper]
 [  816.774829]  [<c0101131>] ? do_one_initcall+0x31/0x190
 [  816.774855]  [<f820b000>] ? wrapper_init+0x0/0xb7 [ndiswrapper]
 [  816.774869]  [<c01830a0>] ? sys_init_module+0xb0/0x210
 [  816.774878]  [<c01033ec>] ? syscall_call+0x7/0xb
 [  816.774884] Code:  Bad EIP value.
 [  816.774892] EIP: [<000c5254>] 0xc5254 SS:ESP 0068:de577830
 [  816.774905] CR2: 00000000000c5254
 [  816.774913] ---[ end trace 4f8862f936cdc1db ]---

This is using ndiswrapper 1.56 modified to work with rt2870 [http://ubuntuforums.org/showthread.php?t=1731245]("http://ubuntuforums.org/showthread.php?t=1731245")

---

