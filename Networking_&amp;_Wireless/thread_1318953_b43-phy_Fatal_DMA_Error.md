---
title: "b43-phy Fatal DMA Error"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Jekshadow on 2009-11-08
My DMESG relating to b43:

```
[  481.548026] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  481.548046] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[  481.670506] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[  481.686023] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[  481.841099] phy0: Selected rate control algorithm 'minstrel'
[  481.842866] Registered led device: b43-phy0::tx
[  481.842910] Registered led device: b43-phy0::rx
[  481.842950] Registered led device: b43-phy0::radio
[  481.843074] Broadcom 43xx driver loaded [ Features: PML, Firmware-ID: FW13 ]
[  481.962895] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[  481.970861] b43 ssb0:0: firmware: requesting b43/lp0initvals15.fw
[  481.980002] b43 ssb0:0: firmware: requesting b43/lp0bsinitvals15.fw
[  482.122892] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  495.994382] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  497.924922] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  497.924955] b43-phy0: Controller RESET (DMA error) ...
[  498.260337] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  512.071321] b43-phy0: Controller restarted
[  512.091056] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  512.091071] b43-phy0: Controller RESET (DMA error) ...
[  512.420483] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

My card PCI ID: 14e4:4315

---

### Post by Kevbert on 2009-11-08
Please take a look at [[COLOR="Red"]this.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1266620&highlight=14e4%3A4315")

---

### Post by Jekshadow on 2009-11-08
> **Kevbert said:**
> Please take a look at [[COLOR="Red"]this.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1266620&highlight=14e4%3A4315")

Thanks, I had gone through the process of compiling compat-wireless from source, and compiling and then running b43-fwcutter. My wifi now works well.

---

### Post by Jekshadow on 2009-11-08
Nevermind... It worked for a second, but is giving the same error again, after following the guide for karmic.

And when I try to remove the b43 module (sudo modprobe -r b43), it gives me this error in my dmesg:

```
[  269.191403] b43-phy0: Controller RESET (DMA error) ...
[  269.530315] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  273.712604] CE: hpet increasing min_delta_ns to 15000 nsec
[  283.333712] b43-phy0: Controller restarted
[  283.523009] BUG: unable to handle kernel NULL pointer dereference at (null)
[  283.523022] IP: [<ffffffff81073d78>] insert_work+0x68/0xc0
[  283.523040] PGD dcc54067 PUD dcd1c067 PMD 0 
[  283.523050] Oops: 0002 [#1] SMP 
[  283.523058] last sysfs file: /sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0/ieee80211/phy0/rfkill1/uevent
[  283.523066] CPU 1 
[  283.523071] Modules linked in: hidp binfmt_misc ppdev bridge stp bnep snd_hda_codec_idt snd_hda_intel snd_hda_codec sha256_generic snd_hwdep cryptd joydev aes_x86_64 aes_generic cbc arc4 ecb snd_pcm_oss snd_mixer_oss snd_pcm dell_wmi b43(-) snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi dell_laptop snd_seq_midi_event dm_crypt psmouse mac80211 snd_seq uvcvideo snd_timer cfg80211 lp sdhci_pci iptable_filter parport serio_raw ip_tables snd_seq_device videodev dcdbas sdhci led_class btusb v4l1_compat snd x_tables v4l2_compat_ioctl32 ricoh_mmc soundcore snd_page_alloc dm_raid45 xor usbhid ohci1394 tg3 ieee1394 ssb pcmcia pcmcia_core video output intel_agp
[  283.523194] Pid: 2471, comm: modprobe Not tainted 2.6.31-14-generic #48-Ubuntu XPS M1330                       
[  283.523201] RIP: 0010:[<ffffffff81073d78>]  [<ffffffff81073d78>] insert_work+0x68/0xc0
[  283.523213] RSP: 0018:ffff8800dcc35c68  EFLAGS: 00010082
[  283.523218] RAX: 0000000000000000 RBX: ffff8801178bb690 RCX: ffff8801178bb698
[  283.523224] RDX: 0000000000000001 RSI: 0000000000000003 RDI: ffff88002801f018
[  283.523229] RBP: ffff8800dcc35c98 R08: 0000000000000000 R09: 0000000000000001
[  283.523235] R10: fecb32e7e33b7407 R11: ffff88010944a8f4 R12: ffff88002801f000
[  283.523241] R13: 0000000000000000 R14: 0000000000000000 R15: 0000000000bd1b28
[  283.523249] FS:  00007f16991b26f0(0000) GS:ffff88002803d000(0000) knlGS:0000000000000000
[  283.523255] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  283.523260] CR2: 0000000000000000 CR3: 00000000dcd2b000 CR4: 00000000000006e0
[  283.523266] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  283.523272] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  283.523279] Process modprobe (pid: 2471, threadinfo ffff8800dcc34000, task ffff880112c80000)
[  283.523284] Stack:
[  283.523287]  ffff8800dcc35c78 ffffffff81036419 ffff88002801f000 0000000000000286
[  283.523297] <0> ffff8801178bb690 0000000000000000 ffff8800dcc35cc8 ffffffff810741c1
[  283.523308] <0> ffff880119925400 ffff8801178ba360 ffff8801178bb690 ffff880119910380
[  283.523320] Call Trace:
[  283.523333]  [<ffffffff81036419>] ? default_spin_lock_flags+0x9/0x10
[  283.523343]  [<ffffffff810741c1>] __queue_work+0x31/0x50
[  283.523351]  [<ffffffff8107425d>] queue_work_on+0x3d/0x50
[  283.523359]  [<ffffffff810742aa>] queue_work+0x1a/0x20
[  283.523398]  [<ffffffffa01cdd2c>] ieee80211_queue_work+0x2c/0x40 [mac80211]
[  283.523425]  [<ffffffffa0243aeb>] b43_led_brightness_set+0x2b/0x30 [b43]
[  283.523437]  [<ffffffff81406438>] led_trigger_set+0xe8/0xf0
[  283.523446]  [<ffffffff814064fa>] led_trigger_unregister+0xba/0xc0
[  283.523477]  [<ffffffffa01ce77d>] ieee80211_led_exit+0x1d/0x90 [mac80211]
[  283.523504]  [<ffffffffa01b50f1>] ieee80211_unregister_hw+0xc1/0xf0 [mac80211]
[  283.523523]  [<ffffffffa0227529>] b43_remove+0xb9/0xc0 [b43]
[  283.523544]  [<ffffffffa003e76b>] ssb_device_remove+0x2b/0x50 [ssb]
[  283.523556]  [<ffffffff81320a73>] __device_release_driver+0x53/0xb0
[  283.523565]  [<ffffffff81320b98>] driver_detach+0xc8/0xd0
[  283.523577]  [<ffffffff8131fbb5>] bus_remove_driver+0x95/0xc0
[  283.523585]  [<ffffffff8132116a>] driver_unregister+0x5a/0x90
[  283.523603]  [<ffffffffa003ec6d>] ssb_driver_unregister+0xd/0x10 [ssb]
[  283.523624]  [<ffffffffa0243e14>] b43_exit+0x10/0x17 [b43]
[  283.523634]  [<ffffffff8108f328>] sys_delete_module+0x1a8/0x280
[  283.523645]  [<ffffffff8107cf29>] ? up_read+0x9/0x10
[  283.523654]  [<ffffffff8152bf74>] ? do_page_fault+0x194/0x370
[  283.523664]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
[  283.523669] Code: e0 48 83 c8 01 48 89 03 48 8b 42 08 48 8d 4b 08 49 8d 7c 24 18 be 03 00 00 00 48 89 4a 08 48 89 53 08 ba 01 00 00 00 48 89 43 10 <48> 89 08 31 c9 e8 ae 6a fd ff 48 8b 5d e0 4c 8b 65 e8 4c 8b 6d 
[  283.523755] RIP  [<ffffffff81073d78>] insert_work+0x68/0xc0
[  283.523765]  RSP <ffff8800dcc35c68>
[  283.523769] CR2: 0000000000000000
[  283.523776] ---[ end trace 117f210cb85ca18a ]---
```

---

### Post by chenxiaolong on 2009-11-09
I have no idea why it happens, but when it does, I have to physically take out the wireless card and touch all the pins (either with my finger or a paperclip) and put it back in for it to work. I'm guessing it's resetting some sort of RAM on the card. 

Anyway, I get the same error if I do a hard reboot or if I download a large file for a long time. I'm using a Dell Studio 1555 with the Dell 1397 Wireless (14e4:4315).

---

### Post by DarkAngel88 on 2009-12-20
Any news on how to solve this issue?

---

