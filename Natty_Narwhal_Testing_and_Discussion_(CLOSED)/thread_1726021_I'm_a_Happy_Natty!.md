---
title: "I'm a Happy Natty!"
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by W00ster on 2011-04-10
A few weeks ago, I bought a new PC which was slated to become my new main workstation.

I had long been trawling the net to find a Linux killer machine. I settled on a Fortis Extreme from Zareason i7 Extreme Edition, 12Gb ram and an ATi HD5770 graphics adapter. This again is hooked up to my 15Tb Synology DS1511+ NAS via iscsi using ocfs2 as clustered file system.

The PC was delivered pre-configured and tested with 10.10. 
The first thing I noticed was free only reporting 8Gb of ram and soon it was followed by mysterious reboots, lockups and other strange behavior. After consulting with Zareason, I switched two sets of memory chips and the memory problem was resolved.

However, I continued to see strange lockups, reboots and other odd behavior I don't see on any of my other 10.10 machines, also connected to the same NAS using the same programs and all machines were up to date.  

The logs showed similar messages to:

```
Apr  7 22:57:33 Fortis kernel: [24833.679058] CPU 7 
Apr  7 22:57:33 Fortis kernel: [24833.679060] Modules linked in: xts gf128mul fpu ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs crc32c ib_iser rdma_cm ib_cm iw_cm ib_sa ib_mad ib_core ib_addr iscsi_tcp libiscsi_tcp libiscsi scsi_transport_iscsi xt_tcpudp iptable_filter ip_tables x_tables vboxnetadp vboxnetflt vboxdrv binfmt_misc sha256_generic aesni_intel cryptd aes_x86_64 aes_generic parport_pc ppdev dm_crypt arc4 snd_hda_codec_atihdmi snd_hda_codec_realtek snd_usb_audio snd_usbmidi_lib snd_seq_midi snd_hda_intel snd_hda_codec snd_rawmidi ath9k_htc snd_hwdep snd_pcm mac80211 led_class snd_seq_midi_event ath9k_common ath9k_hw snd_seq ath cfg80211 fglrx(P) snd_timer joydev snd_seq_device compat psmouse serio_raw snd i7core_edac edac_core soundcore snd_page_alloc f71882fg lp parport dm_raid45 xor hid_logitech ff_memless usbhid hid firewire_ohci firewire_core pata_jmicron ahci r8169 libahci crc_itu_t mii [last unloaded: crc32c]
Apr  7 22:57:33 Fortis kernel: [24833.679131] 
Apr  7 22:57:33 Fortis kernel: [24833.679135] Pid: 1205, comm: phy0 Tainted: P            2.6.35-28-generic #49-Ubuntu MSI X58 Pro-E (MS-7522)/MS-7522
Apr  7 22:57:33 Fortis kernel: [24833.679138] RIP: 0010:[<ffffffffa04c737d>]  [<ffffffffa04c737d>] ath9k_hw_ani_monitor+0x5d/0x560 [ath9k_hw]
Apr  7 22:57:33 Fortis kernel: [24833.679153] RSP: 0018:ffff88031b4ddd90  EFLAGS: 00010246
Apr  7 22:57:33 Fortis kernel: [24833.679155] RAX: 0000000000000000 RBX: ffff88032e3d8000 RCX: 0000000000000000
Apr  7 22:57:33 Fortis kernel: [24833.679158] RDX: 0000000000000000 RSI: 0000000000000282 RDI: ffff88032cd57818
Apr  7 22:57:33 Fortis kernel: [24833.679160] RBP: ffff88031b4dddb0 R08: 0000000000000000 R09: 0000000000000000
Apr  7 22:57:33 Fortis kernel: [24833.679163] R10: 00000000ffffffff R11: 0000000000000001 R12: ffff88032e3d81d8
Apr  7 22:57:33 Fortis kernel: [24833.679166] R13: ffff88032dc69b80 R14: 0000000000000000 R15: 000000000176f074
Apr  7 22:57:33 Fortis kernel: [24833.679169] FS:  0000000000000000(0000) GS:ffff880001ee0000(0000) knlGS:0000000000000000
Apr  7 22:57:33 Fortis kernel: [24833.679172] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Apr  7 22:57:33 Fortis kernel: [24833.679175] CR2: 00007f2ad5e2e000 CR3: 0000000001a2a000 CR4: 00000000000006e0
Apr  7 22:57:33 Fortis kernel: [24833.679178] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Apr  7 22:57:33 Fortis kernel: [24833.679180] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400


```When this happened, I could not reboot or shut down nor unmount any devices. The only way out, was to power cycle the machine and hope for better luck next time.

I then started to remove layer by layer of my added programs and drivers to see where it went wrong but I could not isolate the problem further then to the kernel and network drivers somehow did not work well with iscsi.

Friday, I decided to take the step and upgrade to 11.04.

So far, I have run for 2 days without a hiccup where I previously had problems keeping it running for any length of time!

So, it goes without saying - I am a **Happy Natty** at the moment!

Everything I had installed previously worked like a charm! There is a bit of jerkiness at full 1920x1080 video playback but I suspect the Ati drivers will get better soon.

I can not tell you how happy I am to finally have my Big Kahuna box working as intended! :D:guitar:

---

### Post by BrandyBear on 2011-04-10
i think what it was that your machine couldnt handle the Old(er) graphics But im happy for you that its all okay :D :popcorn:

---

