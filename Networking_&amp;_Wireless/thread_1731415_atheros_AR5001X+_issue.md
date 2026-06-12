---
title: "atheros AR5001X+ issue"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by phar0z on 2011-04-17
It used to work so good, until I upgraded my hardware.
I've tried several stuff like ath5k, madwifi and ndiswrapper:

```
root@linux:/home/pieterjan# lspci | grep Ethernet
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
01:06.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
```

```
root@linux:/home/pieterjan# modprobe ath5k

[  178.630581] Modules linked in: ath5k(+) mac80211 ath cfg80211 led_class usbhid hid nls_iso8859_1 nls_cp437 vfat fat snd_hda_codec_nvhdmi binfmt_misc ath_pci snd_hda_codec_via wlan ath_hal snd_hda_intel snd_hda_codec snd_seq_midi snd_hwdep snd_rawmidi snd_pcm snd_seq_midi_event nouveau snd_seq snd_timer snd_seq_device ttm ppdev drm_kms_helper snd parport_pc asus_atk0110 drm agpgart k10temp i2c_algo_bit soundcore snd_page_alloc i2c_nforce2 lp parport usb_storage pata_amd sata_nv forcedeth [last unloaded: ath5k]
[  178.630602] Pid: 1754, comm: modprobe Not tainted 2.6.35-22-generic #33-Ubuntu
[  178.630604] Call Trace:
[  178.630609]  [<c014ac52>] warn_slowpath_common+0x72/0xa0
[  178.630612]  [<c0263343>] ? proc_register+0x103/0x1e0
[  178.630614]  [<c0263343>] ? proc_register+0x103/0x1e0
[  178.630616]  [<c014ad23>] warn_slowpath_fmt+0x33/0x40
[  178.630618]  [<c0263343>] proc_register+0x103/0x1e0
[  178.630621]  [<c0263808>] proc_mkdir_mode+0x38/0x60
[  178.630623]  [<c0263844>] proc_mkdir+0x14/0x20
[  178.630626]  [<c01ab3fb>] register_handler_proc+0xeb/0x110
[  178.630629]  [<c01a8d07>] __setup_irq+0x197/0x2e0
[  178.630632]  [<c020c441>] ? kmem_cache_alloc_notrace+0x91/0xb0
[  178.630638]  [<fe92d930>] ? ath5k_intr+0x0/0x360 [ath5k]
[  178.630640]  [<c01a95c4>] request_threaded_irq+0xc4/0x170
[  178.630643]  [<c0156936>] ? round_jiffies+0x16/0x20
[  178.630648]  [<fe92fc1e>] ath5k_pci_probe+0x2d1/0x89a [ath5k]
[  178.630651]  [<c027165d>] ? sysfs_add_one+0x1d/0x110
[  178.630653]  [<c027100a>] ? sysfs_addrm_finish+0x1a/0xb0
[  178.630656]  [<c036b9b3>] local_pci_probe+0x13/0x20
[  178.630658]  [<c036c968>] pci_device_probe+0x68/0x90
[  178.630661]  [<c0400550>] really_probe+0x50/0x150
[  178.630663]  [<c0407bc7>] ? pm_runtime_barrier+0x57/0xb0
[  178.630665]  [<c040068c>] driver_probe_device+0x3c/0x60
[  178.630667]  [<c0400731>] __driver_attach+0x81/0x90
[  178.630669]  [<c03ffb53>] bus_for_each_dev+0x53/0x80
[  178.630671]  [<c040041e>] driver_attach+0x1e/0x20
[  178.630672]  [<c04006b0>] ? __driver_attach+0x0/0x90
[  178.630674]  [<c03ffde5>] bus_add_driver+0xd5/0x280
[  178.630676]  [<c036c8a0>] ? pci_device_remove+0x0/0x40
[  178.630678]  [<c0400a2a>] driver_register+0x6a/0x130
[  178.630680]  [<c036cba5>] __pci_register_driver+0x45/0xb0
[  178.630683]  [<fb23201b>] init_ath5k_pci+0x1b/0x33 [ath5k]
[  178.630686]  [<c0101132>] do_one_initcall+0x32/0x1a0
[  178.630689]  [<fb232000>] ? init_ath5k_pci+0x0/0x33 [ath5k]
[  178.630692]  [<c0180c2b>] sys_init_module+0x9b/0x1e0
[  178.630695]  [<c02169c5>] ? sys_close+0x75/0xc0
[  178.630698]  [<c05c90a4>] syscall_call+0x7/0xb
[  178.630700] ---[ end trace 7d7ef0e77fe04718 ]---
[  178.640857] ath5k phy1: failed to wakeup the MAC Chip
[  178.640868] ath5k 0000:01:06.0: PCI INT A disabled
[  178.640872] ath5k: probe of 0000:01:06.0 failed with error -5
```

Then I've tried with madwifi:

```
root@linux:/home/pieterjan# rmmod ath_pci
```

```
root@linux:/home/pieterjan# modprobe ath_pci && iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pr 17 11:18:08 linux kernel: [  230.328571] ath5k 0000:01:06.0: PCI INT A disabled
Apr 17 11:18:08 linux kernel: [  230.328583] ath5k: probe of 0000:01:06.0 failed with error -5
Apr 17 11:18:41 linux kernel: [  263.002305] ath_pci 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
Apr 17 11:18:41 linux kernel: [  263.006468] MadWifi: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
Apr 17 11:18:41 linux kernel: [  263.006480] ath_pci 0000:01:06.0: PCI INT A disabled

pr 17 11:18:08 linux kernel: [  230.328571] ath5k 0000:01:06.0: PCI INT A disabled
Apr 17 11:18:08 linux kernel: [  230.328583] ath5k: probe of 0000:01:06.0 failed with error -5
Apr 17 11:18:41 linux kernel: [  263.002305] ath_pci 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
Apr 17 11:18:41 linux kernel: [  263.006468] MadWifi: unable to attach hardware: 'Hardware didn't respond as expected' (HAL status 3)
Apr 17 11:18:41 linux kernel: [  263.006480] ath_pci 0000:01:06.0: PCI INT A disabled
```

Also tried ath9k:

```
root@linux:/home/pieterjan# modprobe ath9k
```

```
Apr 17 11:19:37 linux kernel: [  318.598504]  [<c025df27>] ? proc_reg_read+0x67/0xa0
Apr 17 11:19:37 linux kernel: [  318.598513]  [<c0218dff>] ? vfs_read+0x9f/0x190
Apr 17 11:19:37 linux kernel: [  318.598521]  [<c025dec0>] ? proc_reg_read+0x0/0xa0
Apr 17 11:19:37 linux kernel: [  318.598529]  [<c0218f32>] ? sys_read+0x42/0x70
Apr 17 11:19:37 linux kernel: [  318.598538]  [<c05c90a4>] ? syscall_call+0x7/0xb
Apr 17 11:19:37 linux kernel: [  318.598543] Code: 57 0f 1f 44 00 00 85 c9 89 c7 74 07 89 d0 f2 ae 75 01 4f 89 f8 5f 5d c3 90 8d 74 26 00 55 89 e5 0f 1f 44 00 00 89 c1 89 c8 eb 06 <80> 38 00 74 07 40 4a 83 fa ff 75 f4 29 c8 5d c3 90 90 55 89 e5 
Apr 17 11:19:37 linux kernel: [  318.598620] EIP: [<c0359aae>] strnlen+0xe/0x20 SS:ESP 0068:f4383e34
Apr 17 11:19:37 linux kernel: [  318.598632] CR2: 00000000fe4f90ee
Apr 17 11:19:37 linux kernel: [  318.598638] ---[ end trace 7d7ef0e77fe04719 ]---
Apr 17 11:19:39 linux kernel: [  320.678554] ath9k: Driver unloaded
```

Ndiswrapper is also unsuccessful :(

```
root@linux:/home/pieterjan# lsmod | grep ndis
ndiswrapper           182830  0 
```


```
root@linux:/home/pieterjan# ndiswrapper -l
net5211 : driver installed
	device (168C:0013) present (alternate driver: ath5k)
```

Although it says hardware present ..



```
Apr 17 13:21:29 linux kernel: [  102.979661] ndiswrapper (ntoskernel_exit:2677): object f6bb4a20(2) was not freed, freeing it now
Apr 17 13:21:30 linux pulseaudio[1523]: ratelimit.c: 16 events suppressed
Apr 17 13:21:44 linux kernel: [  118.091609] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Apr 17 13:21:44 linux kernel: [  118.113548] ndiswrapper: driver net5211 (,11/15/2006,5.1.1.9) loaded
Apr 17 13:21:44 linux kernel: [  118.113912] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
Apr 17 13:21:44 linux kernel: [  118.113969] ndiswrapper (ZwClose:2197): closing handle 0xf691d328 not implemented
Apr 17 13:21:44 linux kernel: [  118.114410] ndiswrapper (NdisWriteErrorLogEntry:190): log: C000138B, count: 4, return_address: ff4369b2
Apr 17 13:21:44 linux kernel: [  118.114418] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf2a12c00
Apr 17 13:21:44 linux kernel: [  118.114424] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x19
Apr 17 13:21:44 linux kernel: [  118.114429] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf8652000
Apr 17 13:21:44 linux kernel: [  118.114435] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf8652000
Apr 17 13:21:44 linux kernel: [  118.114451] ndiswrapper (mp_init:219): couldn't initialize device: C0010006
Apr 17 13:21:44 linux kernel: [  118.114459] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
Apr 17 13:21:44 linux kernel: [  118.114470] ndiswrapper (mp_halt:262): device f52a7480 is not initialized - not halting
Apr 17 13:21:44 linux kernel: [  118.114476] ndiswrapper: device eth%d removed
Apr 17 13:21:44 linux kernel: [  118.114490] ndiswrapper 0000:01:06.0: PCI INT A disabled
Apr 17 13:21:44 linux kernel: [  118.114506] ndiswrapper: probe of 0000:01:06.0 failed with error -22
Apr 17 13:21:44 linux kernel: [  118.114597] usbcore: registered new interface driver ndiswrapper
```

I've noticed someone fixed a similair issues with config_pciaspm=y, but I already have that config. Can anyone help me out? Thanks!

---

