---
title: "&quot;null pointer exception&quot; Ubuntu vp702x Oneiric"
date: 2012-02-07
forum: Multimedia Software
---

### Post by dscheeringa on 2012-02-07
Just upgraded to Oneiric Ubuntu 11.10, All is well until I decided to use VP702x USB DVB-S. Now the system tries to download the firmware and experiences a "Null pointer Exception".
This is the info from the system:
LSB Version: core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-
Distributor ID: Ubuntu
Description: Ubuntu 11.10
Release: 11.10
Codename: oneiric
Linux Nolan 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux

Following is the error from dmesg...

[ 36.697175] dvb-usb: found a 'TwinhanDTV StarBox DVB-S USB2.0 (VP7021)' in cold state, will try to load a firmware

[ 39.902451] dvb-usb: downloading firmware from file 'dvb-usb-vp702x-02.fw'
[ 39.971738] dvb-usb: found a 'TwinhanDTV StarBox DVB-S USB2.0 (VP7021)' in warm state.
[ 39.971754] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 39.971893] DVB: registering new adapter (TwinhanDTV StarBox DVB-S USB2.0 (VP7021))
[ 39.972397] usb 1-4: USB disconnect, device number 2
[ 39.972434] BUG: unable to handle kernel NULL pointer dereference at (null)
[ 39.972443] IP: [<c152cfda>] __mutex_lock_slowpath+0x8a/0x120
[ 39.972461] *pde = 10cff067 *pte = 00000000
[ 39.972467] Oops: 0002 [#1] SMP
[ 39.972474] Modules linked in: ppdev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm dcdbas snd_seq_midi snd_rawmidi arc4 snd_seq_midi_event
[ 39.972548]
[ 39.972553] Pid: 568, comm: modprobe Not tainted 3.0.0-15-generic #26-Ubuntu Dell Computer Corporation Dimension 4550 /
[ 39.972562] EIP: 0060:[<c152cfda>] EFLAGS: 00010246 CPU: 0
[ 39.972568] EIP is at __mutex_lock_slowpath+0x8a/0x120
[ 39.972572] EAX: 00000000 EBX: d077c6e0 ECX: d077c6e8 EDX: d0e19d1c
[ 39.972576] ESI: d077c6e4 EDI: 00000000 EBP: d0e19d34 ESP: d0e19d10
[ 39.972580] DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[ 39.972585] Process modprobe (pid: 568, ti=d0e18000 task=d178d940 task.ti=d0e18000)
[ 39.972588] Stack:
[ 39.972591] 00000020 d077c6e8 d178d940 d077c6e8 00000000 0001a627 d077c6e0 d071e944
[ 39.972602] d071e000 d0e19d44 c152ccc4 00000006 d071e944 d0e19d70 f09ad236 d0e19d70
[ 39.972612] f0a222b3 f0a324a8 d071e944 f09b07a0 d077c6e0 d071e8dc d071e944 d071e92c
[ 39.972622] Call Trace:
[ 39.972630] [<c152ccc4>] mutex_lock+0x24/0x40
[ 39.972640] [<f09ad236>] vp702x_read_mac_addr+0x26/0x90 [dvb_usb_vp702x]
[ 39.972654] [<f0a222b3>] ? dvb_register_adapter+0x113/0x1a0 [dvb_core]
[ 39.972665] [<f09b6253>] dvb_usb_adapter_dvb_init+0x63/0x180 [dvb_usb]
[ 39.972672] [<f09b56eb>] dvb_usb_adapter_init+0x8b/0x250 [dvb_usb]
[ 39.972680] [<f09b5999>] dvb_usb_init+0x89/0xf0 [dvb_usb]
[ 39.972687] [<f09b5b44>] dvb_usb_device_init+0x144/0x200 [dvb_usb]
[ 39.972696] [<c10263e8>] ? default_spin_lock_flags+0x8/0x10
[ 39.972704] [<f09ad0a5>] vp702x_usb_probe+0x35/0xb0 [dvb_usb_vp702x]
[ 39.972714] [<c13bbe2c>] usb_probe_interface+0xac/0x1a0
[ 39.972724] [<c134702d>] really_probe+0x4d/0x150
[ 39.972730] [<c134f4d9>] ? pm_runtime_barrier+0x49/0xb0
[ 39.972736] [<c134726a>] driver_probe_device+0x3a/0x60
[ 39.972744] [<c1347321>] __driver_attach+0x91/0xa0
[ 39.972751] [<c1347290>] ? driver_probe_device+0x60/0x60
[ 39.972756] [<c13463a9>] bus_for_each_dev+0x49/0x70
[ 39.972762] [<c1346e61>] driver_attach+0x21/0x30
[ 39.972768] [<c1347290>] ? driver_probe_device+0x60/0x60
[ 39.972774] [<c1346b3f>] bus_add_driver+0x17f/0x260
[ 39.972780] [<c13477f6>] driver_register+0x66/0x110
[ 39.972786] [<c13baea1>] usb_register_driver+0x71/0x140
[ 39.972794] [<f079401b>] vp702x_usb_module_init+0x1b/0x1000 [dvb_usb_vp702x]
[ 39.972803] [<f0794000>] ? 0xf0793fff
[ 39.972811] [<c1001125>] do_one_initcall+0x35/0x170
[ 39.972819] [<f0794000>] ? 0xf0793fff
[ 39.972828] [<c1082c5d>] sys_init_module+0xad/0x210
[ 39.972834] [<c152e2a4>] syscall_call+0x7/0xb
[ 39.972837] Code: 20 63 7f bd 90 8d 74 26 00 8d 73 04 89 f0 e8 be 0e 00 00 8d 43 08 89 45 e0 8b 43 0c 8d 55 e8 8b 4d e0 89 53 0c 89 45 ec
[ 39.972876] 10 8b 45 e4 ba ff ff ff ff 89 45 f0 89 d0 87 03 83 f8 01 74
[ 39.972897] EIP: [<c152cfda>] __mutex_lock_slowpath+0x8a/0x120 SS:ESP 0068:d0e19d10
[ 39.972905] CR2: 0000000000000000
[ 39.972910] ---[ end trace f188b3f321061bbc ]---

I have seen some other variants of linux having a similar problem.  Has anyone else running Oneiric experienced this?

dscheeringa

---

