---
title: "AVerMedia Volar TV Tuner Crash"
date: 2011-03-29
forum: Multimedia Software
---

### Post by adam.webb on 2011-03-29
I am trying to get my AVerMedia Volar TV Tuner (A808) working on Ubuntu 10.10. 

When plugging in the USB dongle, I get the message 
> Mar 29 20:21:59 gamma kernel: [  192.267657] dvb-usb: AVerMedia AVerTV DVB-T Volar successfully initialized and connected. in the Kernel (which I've retrieved with a dmesg in the terminal).

When I open any program to try and use the adapter, as soon as it starts "scanning", the program claims not to get any signal. On looking at the kernel output > [  376.436066] BUG: unable to handle kernel NULL pointer dereference at 0000000000000012
[  376.436085] IP: [<ffffffff8143e4be>] i2c_transfer+0x1e/0xf0
[  376.436106] PGD 4d014067 PUD 4d015067 PMD 0 
[  376.436118] Oops: 0000 [#1] SMP 
[  376.436126] last sysfs file: /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1b/PNP0C0A:00/power_supply/BAT1/charge_full
[  376.436138] CPU 1 
[  376.436143] Modules linked in: mt2060 dvb_usb_dib0700 dib7000p dib0090 dib7000m dib0070 dvb_usb dib8000 dvb_core dib3000mc dibx000_common binfmt_misc vboxnetadp vboxnetflt vboxdrv parport_pc ppdev snd_hda_codec_realtek arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event joydev uvcvideo radeon ath5k mac80211 ath ttm videodev v4l1_compat snd_seq v4l2_compat_ioctl32 drm_kms_helper rt2870sta(C) cfg80211 drm snd_timer psmouse serio_raw pcmcia i2c_algo_bit snd_seq_device shpchp i2c_piix4 edac_core edac_mce_amd video snd yenta_socket pcmcia_rsrc crc_ccitt pcmcia_core soundcore lm63 snd_page_alloc output k8temp lp parport xfs exportfs 8139too sdhci_pci sdhci led_class 8139cp mii pata_atiixp sata_sil
[  376.436289] 
[  376.436299] Pid: 2148, comm: kaffeine Tainted: G         C  2.6.35-28-generic #49-Ubuntu Navarro/TravelMate 5510 
[  376.436307] RIP: 0010:[<ffffffff8143e4be>]  [<ffffffff8143e4be>] i2c_transfer+0x1e/0xf0
[  376.436320] RSP: 0018:ffff88005079bad8  EFLAGS: 00010296
[  376.436327] RAX: 00000000ffffffa1 RBX: 00000000000000eb RCX: 0000000000000000
[  376.436334] RDX: 0000000000000002 RSI: ffff88005079bb28 RDI: 0000000000000002
[  376.436341] RBP: ffff88005079bb18 R08: ffff88007afc63c0 R09: 000000000e008d80
[  376.436347] R10: dead000000200200 R11: dead000000100100 R12: 0000000000000000
[  376.436354] R13: 0000000000000001 R14: 0000000000000002 R15: ffff880037904000
[  376.436363] FS:  00007f4eadfeb760(0000) GS:ffff880001f00000(0000) knlGS:00000000f6a17a90
[  376.436370] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[  376.436376] CR2: 0000000000000012 CR3: 000000004d013000 CR4: 00000000000006e0
[  376.436383] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  376.436390] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  376.436397] Process kaffeine (pid: 2148, threadinfo ffff88005079a000, task ffff880050645b80)
[  376.436403] Stack:
[  376.436407]  ffff8800622696c0 ffff88007a4945a0 0000000000000020 00000000000000eb
[  376.436418] <0> 0000000000000000 0000000000000001 ffffc900039d7000 ffff880037904000
[  376.436430] <0> ffff88005079bb78 ffffffffa050d27e 0000000200000010 ffff88005079bb58
[  376.436444] Call Trace:
[  376.436461]  [<ffffffffa050d27e>] dib7000p_read_word+0x6e/0xc0 [dib7000p]
[  376.436474]  [<ffffffffa050effb>] dib7000p_pid_filter_ctrl+0x2b/0xa0 [dib7000p]
[  376.436488]  [<ffffffffa02362ee>] ? usb_urb_submit+0x3e/0x84 [dvb_usb]
[  376.436506]  [<ffffffffa0723db9>] stk70x0p_pid_filter_ctrl+0x19/0x1c [dvb_usb_dib0700]
[  376.436518]  [<ffffffffa0235632>] dvb_usb_ctrl_feed+0x152/0x170 [dvb_usb]
[  376.436529]  [<ffffffffa0235683>] dvb_usb_start_feed+0x13/0x20 [dvb_usb]
[  376.436553]  [<ffffffffa048ca07>] dmx_ts_feed_start_filtering+0x67/0xf0 [dvb_core]
[  376.436571]  [<ffffffffa0488d63>] dvb_dmxdev_start_feed+0xd3/0x130 [dvb_core]
[  376.436589]  [<ffffffffa048a67e>] dvb_dmxdev_filter_start+0x2ee/0x3e0 [dvb_core]
[  376.436607]  [<ffffffffa048a905>] dvb_dmxdev_pes_filter_set+0x195/0x1b0 [dvb_core]
[  376.436624]  [<ffffffffa048ad61>] dvb_demux_do_ioctl+0x441/0x580 [dvb_core]
[  376.436641]  [<ffffffffa0488aff>] dvb_usercopy+0xbf/0x1a0 [dvb_core]
[  376.436657]  [<ffffffffa048a920>] ? dvb_demux_do_ioctl+0x0/0x580 [dvb_core]
[  376.436669]  [<ffffffff81161f21>] ? do_filp_open+0x241/0x660
[  376.436680]  [<ffffffff81101d67>] ? unlock_page+0x27/0x30
[  376.436697]  [<ffffffffa04893ef>] dvb_demux_ioctl+0x4f/0x80 [dvb_core]
[  376.436707]  [<ffffffff811634cd>] vfs_ioctl+0x3d/0xd0
[  376.436716]  [<ffffffff81163da1>] do_vfs_ioctl+0x81/0x340
[  376.436725]  [<ffffffff811640e1>] sys_ioctl+0x81/0xa0
[  376.436738]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b
[  376.436744] Code: e8 d8 6c f4 ff c9 c3 eb 04 90 90 90 90 55 48 89 e5 41 57 41 56 41 55 41 54 53 48 83 ec 18 0f 1f 44 00 00 b8 a1 ff ff ff 41 89 d6 <48> 8b 57 10 48 89 fb 49 89 f5 48 83 3a 00 0f 84 8e 00 00 00 65 
[  376.436833] RIP  [<ffffffff8143e4be>] i2c_transfer+0x1e/0xf0
[  376.436844]  RSP <ffff88005079bad8>
[  376.436849] CR2: 0000000000000012
[  376.436856] ---[ end trace 5f0aa96f88871ae4 ]---

I then have to force the said program to close. 

Does anyone have any suggestions as to how to fix this? 

cheers

Adam

---

