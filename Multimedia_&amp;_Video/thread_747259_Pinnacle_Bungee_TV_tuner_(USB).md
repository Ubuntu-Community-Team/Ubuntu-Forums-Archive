---
title: "Pinnacle Bungee TV tuner (USB)"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by fb2007 on 2008-04-06
Can somebody tell how to make my usb tv tuner from pinnacle working. It is a Bungee USB tv tuner with mpeg2 encoding.

---

### Post by xc3RnbFO8P on 2008-04-06
Try this:
[http://ubuntuforums.org/showthread.php?t=745944]("http://ubuntuforums.org/showthread.php?t=745944")

---

### Post by xc3RnbFO8P on 2008-04-06
Mistake

---

### Post by fb2007 on 2008-04-06
Thanks for quick reply. I did as you sugested, but I don't see any 'Digital TV button' in keffeine. When I try to do 'lsusb' terminal window freezes (I use gutsy).

But 'mdesg' gives:
```

[  219.952000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  220.100000] usb 2-1: configuration #1 chosen from 1 choice
[  220.168000] usbvision_probe: Pinnacle PCTV Bungee USB (PAL) FM found
[  220.168000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000027
[  220.168000]  printing eip:
[  220.168000] f9107ca8
[  220.168000] *pde = 00000000
[  220.168000] Oops: 0000 [#1]
[  220.168000] SMP 
[  220.168000] Modules linked in: usbvision v4l2_common ipv6 af_packet vmnet(P) vmblock(P) vmmon(P) vmvirtualnic(P) vm_bridge(P) vm_main(PF) hypervisor(P) binfmt_misc rfcomm l2cap bluetooth nfsd exportfs lockd sunrpc ppdev acpi_cpufreq cpufreq_ondemand cpufreq_userspace cpufreq_powersave cpufreq_conservative cpufreq_stats freq_table container button ac dock battery sbs video sbp2 parport_pc lp parport arc4 ecb blkcipher snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi joydev snd_seq_midi_event iwl4965 pcmcia nvidia(P) iwlwifi_mac80211 snd_seq snd_timer snd_seq_device sdhci tifm_7xx1 compat_ioctl32 videodev mmc_core tifm_core cfg80211 v4l1_compat i2c_core yenta_socket rsrc_nonstatic snd serio_raw pcmcia_core iTCO_wdt iTCO_vendor_support psmouse shpchp pci_hotplug soundcore intel_agp agpgart snd_page_alloc evdev ext3 jbd mbcache sg sr_mod cdrom sd_mod usbhid hid ata_piix ohci1394 ieee1394 ehci_hcd ata_generic libata scsi_mod r8169 uhci_hcd usbcore thermal processor fan fuse apparmor commoncap
[  220.168000] CPU:    1
[  220.168000] EIP:    0060:[<f9107ca8>]    Tainted: PF      VLI
[  220.168000] EFLAGS: 00010206   (2.6.22-14-generic #1)
[  220.168000] EIP is at usbvision_probe+0xe8/0x800 [usbvision]
[  220.168000] eax: 00000024   ebx: 000006c8   ecx: 00000096   edx: 00000000
[  220.168000] esi: f4209c00   edi: f911240c   ebp: 0000003e   esp: f4149db4
[  220.168000] ds: 007b   es: 007b   fs: 00d8  gs: 0033  ss: 0068
[  220.168000] Process modprobe (pid: 6377, ti=f4148000 task=f44899f0 task.ti=f4148000)
[  220.168000] Stack: f910b992 f91098a6 f910b72c c01c405f f4209f54 c02f31d8 f4209c00 f5efd400 
[  220.168000]        f911240c f88aadc7 0011240c 00000024 00000000 f5efd400 f911240c f91107c0 
[  220.168000]        f88abf66 f4209c00 f5efd418 00000000 f91107f0 f5efd4d0 c02611ae c037db40 
[  220.168000] Call Trace:
[  220.168000]  [<c01c405f>] sysfs_make_dirent+0x2f/0x50
[  220.168000]  [<c02f31d8>] mutex_lock+0x8/0x20
[  220.168000]  [<f88aadc7>] usb_match_one_id+0x27/0xb0 [usbcore]
[  220.168000]  [<f88abf66>] usb_probe_interface+0x96/0xe0 [usbcore]
[  220.168000]  [<c02611ae>] driver_probe_device+0x8e/0x190
[  220.168000]  [<c026141e>] __driver_attach+0x9e/0xa0
[  220.168000]  [<c026059b>] bus_for_each_dev+0x3b/0x60
[  220.168000]  [<c0261026>] driver_attach+0x16/0x20
[  220.168000]  [<c0261380>] __driver_attach+0x0/0xa0
[  220.168000]  [<c026096a>] bus_add_driver+0x8a/0x1b0
[  220.168000]  [<f88ab9de>] usb_register_driver+0x8e/0x110 [usbcore]
[  220.168000]  [<c01492e0>] __link_module+0x0/0x20
[  220.168000]  [<f8f76065>] usbvision_init+0x65/0x169 [usbvision]
[  220.168000]  [<c0135457>] blocking_notifier_call_chain+0x17/0x20
[  220.168000]  [<c014a7f1>] sys_init_module+0x151/0x1a00
[  220.168000]  [<c01fb43f>] prio_tree_insert+0x1f/0x250
[  220.168000]  [<c01041d2>] sysenter_past_esp+0x6b/0xa9
[  220.168000]  [<c02f0000>] clip_ioctl+0x3a0/0x510
[  220.168000]  =======================
[  220.168000] Code: 24 08 e8 ac 0f 02 c7 8b 93 0c 18 11 f9 85 d2 0f 88 dc 04 00 00 8b 86 dc 01 00 00 8b 44 90 10 8b 00 8b 40 0c 83 c0 24 89 44 24 2c <0f> b6 40 03 83 e0 03 83 e8 01 0f 85 54 06 00 00 8b 44 24 2c 80 
[  220.168000] EIP: [<f9107ca8>] usbvision_probe+0xe8/0x800 [usbvision] SS:ESP 0068:f4149db4

```

This is anything that prints out after TV tuner is pluged in.

Can you help me even further?

---

### Post by xc3RnbFO8P on 2008-04-06
How old is this computer?

---

### Post by fb2007 on 2008-04-06
Is a laptop maybe a year old. It's a pentium core 2 Duo 2.0 GHz, 3gb ram, nvidia graphics 512mb ram. 

As it goes for TV tuner is an older one. Maybe 2003. As I told above Pinnacle Bungee on USB without FM radio.

Why?

---

### Post by xc3RnbFO8P on 2008-04-07
Try This: [http://pctvgtk.sourceforge.net/]("http://pctvgtk.sourceforge.net/")

---

### Post by fb2007 on 2008-04-07
Thanks. 

But how do I compile drivers from  [HTML]http://www.paranoyaxc.de/bungee/bungee.html [/HTML]?

---

