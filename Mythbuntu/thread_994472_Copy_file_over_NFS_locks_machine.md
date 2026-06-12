---
title: "Copy file over NFS locks machine"
date: 2008-11-26
forum: Mythbuntu
---

### Post by tbaca on 2008-11-26
I am working on a new 8.10 X86-64 system to replace my present system.  I wanted to copy over the video files from the original sysmte to the new system, so I mounted the storage systemt via NFS onto the new system.  I started to copy the video files.  About half way through the new systemt locked-up.  I could not log in or execute a restart; I had to power cycle the machine.  I have tried to copy the files several times, always causin the new machine (8.10) to hard lock.

I found the following in the log:

[SIZE="2"]Nov 26 14:45:25 Server kernel: [ 3487.513499] Modules linked in: af_packet binfmt_misc lirc_serial lirc_dev rfcomm bridge stp bnep sco l2ca
p bluetooth nfsd auth_rpcgss exportfs ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpuf
req_conservative video output sbs sbshc pci_slot container battery nfs lockd nfs_acl sunrpc iptable_filter ip_tables x_tables ac lp loop ip
v6 snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event nvidia(P) snd_seq
snd_timer tpm_infineon i2c_core snd_seq_device psmouse parport_pc tpm evdev intel_agp iTCO_wdt serio_raw parport shpchp pcspkr tpm_bios pci
_hotplug iTCO_vendor_support wmi button heci snd soundcore snd_page_alloc xfs sr_mod cdrom sd_mod crc_t10dif sg ata_piix pata_acpi ehci_hcd
 sata_sil24 ata_generic uhci_hcd libata e1000e usbcore scsi_mod dock raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipa
th linear md_mod thermal processor fan fbcon tileblit
Nov 26 14:45:25 Server kernel: font bitblit softcursor fuse
Nov 26 14:45:25 Server kernel: [ 3487.513502] CPU 3:
Nov 26 14:45:25 Server kernel: [ 3487.513502] Modules linked in: af_packet binfmt_misc lirc_serial lirc_dev rfcomm bridge stp bnep sco l2ca
p bluetooth nfsd auth_rpcgss exportfs ppdev acpi_cpufreq cpufreq_userspace cpufreq_stats cpufreq_powersave cpufreq_ondemand freq_table cpuf
req_conservative video output sbs sbshc pci_slot container battery nfs lockd nfs_acl sunrpc iptable_filter ip_tables x_tables ac lp loop ip
v6 snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event nvidia(P) snd_seq
snd_timer tpm_infineon i2c_core snd_seq_device psmouse parport_pc tpm evdev intel_agp iTCO_wdt serio_raw parport shpchp pcspkr tpm_bios pci
_hotplug iTCO_vendor_support wmi button heci snd soundcore snd_page_alloc xfs sr_mod cdrom sd_mod crc_t10dif sg ata_piix pata_acpi ehci_hcd
 sata_sil24 ata_generic uhci_hcd libata e1000e usbcore scsi_mod dock raid10 raid456 async_xor async_memcpy async_tx xor raid1 raid0 multipa
th linear md_mod thermal processor fan fbcon tileblit
Nov 26 14:45:25 Server kernel: font bitblit softcursor fuse
Nov 26 14:45:25 Server kernel: [ 3487.513502] Pid: 8898, comm: cp Tainted: P          2.6.27-7-generic #1
Nov 26 14:45:25 Server kernel: [ 3487.513502] RIP: 0010:[<ffffffff802ac0b1>]  [<ffffffff802ac0b1>] find_get_pages+0x71/0x110
Nov 26 14:45:25 Server kernel: [ 3487.513502] RSP: 0018:ffff880067855378  EFLAGS: 00000286
Nov 26 14:45:25 Server kernel: [ 3487.513502] RAX: ffff880031a79d88 RBX: ffff8800678553b8 RCX: 0000000000000003
Nov 26 14:45:25 Server kernel: [ 3487.513502] RDX: 0000000000000004 RSI: 0000000000000000 RDI: ffffe200003884c0
Nov 26 14:45:25 Server kernel: [ 3487.513502] RBP: ffff8800678552f8 R08: ffffe20000388488 R09: 000000000000000e
Nov 26 14:45:25 Server kernel: [ 3487.513502] R10: 0000000000000025 R11: 0000000000027966 R12: ffff88007b006738
Nov 26 14:45:25 Server kernel: [ 3487.513502] R13: ffff88007b006700 R14: 01ffffffa0098d20 R15: ffff8800678552f8
Nov 26 14:45:25 Server kernel: [ 3487.513502] FS:  00007f84789f1770(0000) GS:ffff88007d802e80(0000) knlGS:0000000000000000
Nov 26 14:45:25 Server kernel: [ 3487.513502] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Nov 26 14:45:25 Server kernel: [ 3487.513502] CR2: 00007f40b1c77000 CR3: 00000000678f8000 CR4: 00000000000006e0
Nov 26 14:45:25 Server kernel: [ 3487.513502] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Nov 26 14:45:25 Server kernel: [ 3487.513502] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Nov 26 14:45:25 Server kernel: [ 3487.513502]
Nov 26 14:45:25 Server kernel: [ 3487.513502] Call Trace:
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ac083>] ? find_get_pages+0x43/0x110
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802b6b94>] ? pagevec_lookup+0x24/0x30
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffffa024601d>] ? xfs_cluster_write+0xad/0x180 [xfs]
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffffa0246588>] ? xfs_page_state_convert+0x498/0x760 [xfs]
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffffa02469b1>] ? xfs_vm_writepage+0x71/0x120 [xfs]
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802b9474>] ? pageout+0x124/0x280
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ab1da>] ? page_waitqueue+0xa/0x90
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802b9a7d>] ? shrink_page_list+0x34d/0x530
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802b9e02>] ? shrink_inactive_list+0x1a2/0x4b0
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ba18b>] ? shrink_zone+0x7b/0x160
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ba2fd>] ? shrink_zones+0x8d/0x150
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ba446>] ? do_try_to_free_pages+0x86/0x2e0
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ba797>] ? try_to_free_pages+0x67/0x70
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802b92a0>] ? isolate_pages_global+0x0/0x50
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802b2a69>] ? __alloc_pages_internal+0x239/0x520
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802d58cd>] ? alloc_pages_current+0xad/0x110
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ac617>] ? __page_cache_alloc+0x67/0x80
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ad253>] ? __grab_cache_page+0x63/0xb0
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff80316dc9>] ? block_write_begin+0x89/0xf0
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffffa024547a>] ? xfs_vm_write_begin+0x2a/0x30 [xfs]
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffffa0245040>] ? xfs_get_blocks+0x0/0x20 [xfs]
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ab93c>] ? generic_perform_write+0xbc/0x1c0
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802ad6a2>] ? generic_file_buffered_write+0x92/0x170
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffffa024e2e3>] ? xfs_write+0x6b3/0x9b0 [xfs]
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffffa0249c98>] ? xfs_file_aio_write+0x58/0x60 [xfs]
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802e97d9>] ? do_sync_write+0xf9/0x140
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff8026afaf>] ? hrtimer_start+0xdf/0x1b0
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff80267050>] ? autoremove_wake_function+0x0/0x40
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff80386bc1>] ? aa_file_permission+0x21/0xf0
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff80386ce8>] ? apparmor_file_permission+0x28/0x30
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff80361786>] ? security_file_permission+0x16/0x20
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802e9e9b>] ? vfs_write+0xcb/0x130
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff802e9ff5>] ? sys_write+0x55/0x90
Nov 26 14:45:25 Server kernel: [ 3487.513502]  [<ffffffff8021285a>] ? system_call_fastpath+0x16/0x1b
Nov 26 14:45:25 Server kernel: [ 3487.513502]
Nov 26 15:50:24 Server syslogd 1.5.0#2ubuntu6: restart.
[/SIZE]

I am stuck.

---

