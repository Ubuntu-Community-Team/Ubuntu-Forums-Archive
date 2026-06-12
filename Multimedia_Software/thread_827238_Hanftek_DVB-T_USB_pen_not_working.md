---
title: "Hanftek DVB-T USB pen not working"
date: 2008-06-12
forum: Multimedia Software
---

### Post by matc on 2008-06-12
Recently I bought a DVB-T USB pen (ID 15f4:0015 HanfTek
) to view a little TV, but unfortunately linux doesn't seem to fully support it properly (although it is marked as supported in linuxtv.org)

What happens when I plug it in:

Laptop (Ubuntu 8.04 - Kernel 2.6.24-XX-generic)
------------------------------------
- Pen is detected and loaded
- Kaffeine can do a channel scan the first time and finds a signal rate <15% and no channels are detected
- If scanned a second time, nothing is found
- if unplugging and replugging the device, dmesg nags about missig firmware for the device
- if using the command line tool 'scan', the whole usb interface hangs(e.g. lsusb never returns) and dmesg shows a crash:
[  251.658003] Pid: 6952, comm: scan Not tainted (2.6.24-18-generic #1)
[  251.658006] EIP: 0060:[<ee89fee4>] EFLAGS: 00210206 CPU: 0
[  251.658038] EIP is at usb_kill_urb+0x14/0xd0 [usbcore]
[  251.658040] EAX: 00000000 EBX: 14de7414 ECX: 00200202 EDX: d4d18000
[  251.658043] ESI: dd99ba4c EDI: ffffffea EBP: 00000001 ESP: d4d19df4
[  251.658046]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[  251.658049] Process scan (pid: 6952, ti=d4d18000 task=d4e205c0 task.ti=d4d18000)
[  251.658052] Stack: 00000000 d4e205c0 c0140c40 d4d19e00 d4d19e00 00000021 dd99ba4c eee098dc
[  251.658059]        dd99ba4c 00000014 eee099a5 eee0a3b0 00000014 dd99b724 00000001 eef01000
[  251.658065]        eee090e3 eee1cb0d 00000012 00000000 00000000 eef01000 eee1d875 dd99b9cc
[  251.658071] Call Trace:
[  251.658092]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[  251.658114]  [<eee098dc>] usb_urb_kill+0x1c/0x40 [dvb_usb]
[  251.658130]  [<eee099a5>] usb_urb_submit+0x55/0x60 [dvb_usb]
[  251.658149]  [<eee090e3>] dvb_usb_ctrl_feed+0x93/0x120 [dvb_usb]
[  251.658155]  [<eee1cb0d>] dvb_demux_feed_add+0x1d/0xb0 [dvb_core]
[  251.658184]  [<eee1d875>] dmx_section_feed_start_filtering+0xc5/0x160 [dvb_core]
[  251.658211]  [<eee1b271>] dvb_dmxdev_filter_start+0x201/0x390 [dvb_core]
[  251.658231]  [<c018b3a6>] shmem_check_acl+0x36/0x60
[  251.658252]  [<eee1b53c>] dvb_demux_do_ioctl+0x13c/0x3b0 [dvb_core]
[  251.658273]  [<eee23f75>] dvb_ringbuffer_init+0x25/0x30 [dvb_core]
[  251.658301]  [<eee1a0e7>] dvb_usercopy+0x67/0x140 [dvb_core]
[  251.658351]  [<c018ffa5>] nameidata_to_filp+0x35/0x40
[  251.658360]  [<c0194990>] chrdev_open+0x0/0x190
[  251.658369]  [<c0190000>] do_filp_open+0x50/0x60
[  251.658395]  [<eee1abb8>] dvb_demux_ioctl+0x18/0x20 [dvb_core]
[  251.658412]  [<eee1b400>] dvb_demux_do_ioctl+0x0/0x3b0 [dvb_core]
[  251.658429]  [<c019dff8>] do_ioctl+0x78/0x90
[  251.658444]  [<c019e23e>] vfs_ioctl+0x22e/0x2b0
[  251.658451]  [<c01900ce>] do_sys_open+0xbe/0xe0
[  251.658464]  [<c019e316>] sys_ioctl+0x56/0x70
[  251.658476]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[  251.658495]  [<c0310000>] unix_dgram_recvmsg+0x50/0x2d0
[  251.658513]  =======================
[  251.658514] Code: 8b 48 2c b2 d5 85 c9 74 e7 b2 98 e9 67 fe ff ff 8d b4 26 00 00 00 00 56 53 89 c3 83 ec 14 e8 14 ad a7 d1 85 db 0f 84 ad 00 00 00 <8b> 43 28 85 c0 0f 84 a2 00 00 00 8b 43 2c 85 c0 0f 84 97 00 00
[  251.658544] EIP: [<ee89fee4>] usb_kill_urb+0x14/0xd0 [usbcore] SS:ESP 0068:d4d19df4
[  251.658567] ---[ end trace 528e15b054b45a4a ]---


Computer 2 (8.04 - Kernel 2.6.22 - does not boot with 2.6.24-XX-generic)
--------------------------------------------------------
- Usb layer driver can not configure the pen at all and assign it a USb address

Computer 2 (running Win2K + delivered DVB-SW)
----------------------------------------------
- Stick works + can play 5 TV channels (out of 28 promised...)



Can anybody give me a hint what I'm doing wrong?????
Not being able to use it under Linux sucks....

---

### Post by xc3RnbFO8P on 2008-06-12
What sort off antenna are you using?

---

### Post by matc on 2008-06-13
It is simply a short antenna delivered with the DVB stick. But since i'm about 5 km away from the transmitter it shouldn't be a problem.


However, I'd be happy if it worked at all under linux...

---

### Post by xc3RnbFO8P on 2008-06-13
See if got this driver **dvb-usb-umt-010-02.fw**
if not get it [here]("http://www.linuxtv.org/downloads/firmware/")
First copy the driver to /lib/firmaware/2.6.24-xx-generic
restart and try ,not working.
Copy driver to /lib/firmaware, etc.

---

### Post by matc on 2008-06-13
Didn't change anything.

At first connection on the laptop  I get to scan the channels with kaffeine and seem to find some with 81% signal strength nut SNR of 1% (which doesn't make kaffeine recognize channels), and after unplugging the stick the whole usb control crashes:

[  534.607832] usb 3-3: USB disconnect, address 3
[  534.608295] BUG: unable to handle kernel paging request at virtual address 0dea643c
[  534.608301] printing eip: ee89fee4 *pde = 00000000
[  534.608306] Oops: 0000 [#1] SMP
[  534.608310] Modules linked in: dvb_pll mt352 dvb_usb_umt_010 dvb_usb_dibusb_common dib3000mc dibx000_common dvb_usb dvb_core i2c_core af_packet p80211 nf_conntrack_irc i915 drm nf_conntrack_ftp xt_state xt_limit ipt_LOG iptable_mangle iptable_nat nf_nat nf_conntrack_ipv4 nf_conntrack binfmt_misc rfcomm l2cap bluetooth ppdev ipv6 snd_atiixp_modem snd_via82xx_modem snd_intel8x0m cpufreq_ondemand cpufreq_conservative cpufreq_stats cpufreq_userspace cpufreq_powersave container dock sbs sbshc iptable_filter ip_tables x_tables aes_i586 dm_crypt dm_mod p4_clockmod speedstep_lib freq_table parport_pc lp parport arc4 ecb blkcipher pcmcia joydev p54pci p54common yenta_socket mac80211 rsrc_nonstatic pcmcia_core cfg80211 snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss video output snd_pcm snd_mixer_oss snd_seq_dummy serio_raw psmouse snd_seq_oss snd_seq_midi battery snd_rawmidi snd_seq_midi_event ac button snd_seq snd_timer snd_seq_device intel_agp agpgart shpchp pci_hotplug iTCO_wdt iTCO_vendor_support snd soundcore evdev snd_page_alloc pcspkr ext3 jbd mbcache sg sr_mod cdrom sd_mod pata_acpi ata_generic 8139too ata_piix 8139cp mii libata ehci_hcd uhci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[  534.608391]
[  534.608394] Pid: 1490, comm: khubd Not tainted (2.6.24-18-generic #1)
[  534.608397] EIP: 0060:[<ee89fee4>] EFLAGS: 00010206 CPU: 0
[  534.608427] EIP is at usb_kill_urb+0x14/0xd0 [usbcore]
[  534.608429] EAX: 00000000 EBX: 0dea6414 ECX: ec250ee0 EDX: ebf04000
[  534.608432] ESI: d98eca4c EDI: d98ec000 EBP: 00000001 ESP: ebf05e68
[  534.608435]  DS: 007b ES: 007b FS: 00d8 GS: 0000 SS: 0068
[  534.608438] Process khubd (pid: 1490, ti=ebf04000 task=ebf2d700 task.ti=ebf04000)
[  534.608441] Stack: ec250ee0 c04191d0 eee09e8a 00000282 eee09e8a 00000021 d98eca4c eee0a8dc
[  534.608448]        d98ec724 d98eca4c eee0a909 d98ec724 d98ec000 eee09395 eed51346 d98fa41c
[  534.608454]        eed51e80 00000000 eee09420 d98fa41c eed51e80 d98fa400 ee8a36b0 cdc35400
[  534.608460] Call Trace:
[  534.608482]  [<eee09e8a>] dvb_usb_adapter_dvb_exit+0x3a/0x60 [dvb_usb]
[  534.608496]  [<eee09e8a>] dvb_usb_adapter_dvb_exit+0x3a/0x60 [dvb_usb]
[  534.608509]  [<eee0a8dc>] usb_urb_kill+0x1c/0x40 [dvb_usb]
[  534.608521]  [<eee0a909>] usb_urb_exit+0x9/0x50 [dvb_usb]
[  534.608533]  [<eee09395>] dvb_usb_exit+0x45/0xa0 [dvb_usb]
[  534.608547]  [<eee09420>] dvb_usb_device_exit+0x30/0x50 [dvb_usb]
[  534.608562]  [<ee8a36b0>] usb_unbind_interface+0x50/0xb0 [usbcore]
[  534.608601]  [<c0282404>] __device_release_driver+0x64/0xa0
[  534.608617]  [<c0282873>] device_release_driver+0x23/0x40
[  534.608626]  [<c0281cdb>] bus_remove_device+0x4b/0x70
[  534.608634]  [<c02802b5>] device_del+0x135/0x250
[  534.608648]  [<ee8a07f0>] usb_disable_device+0x80/0xf0 [usbcore]
[  534.608684]  [<ee89c3d8>] usb_disconnect+0x98/0x130 [usbcore]
[  534.608724]  [<ee89d857>] hub_thread+0x447/0xcb0 [usbcore]
[  534.608757]  [<c02180e5>] rb_erase+0x185/0x280
[  534.608793]  [<c0140c40>] autoremove_wake_function+0x0/0x40
[  534.608810]  [<ee89d410>] hub_thread+0x0/0xcb0 [usbcore]
[  534.608840]  [<c0140982>] kthread+0x42/0x70
[  534.608843]  [<c0140940>] kthread+0x0/0x70
[  534.608852]  [<c0105677>] kernel_thread_helper+0x7/0x10
[  534.608867]  =======================
[  534.608868] Code: 8b 48 2c b2 d5 85 c9 74 e7 b2 98 e9 67 fe ff ff 8d b4 26 00 00 00 00 56 53 89 c3 83 ec 14 e8 14 ad a7 d1 85 db 0f 84 ad 00 00 00 <8b> 43 28 85 c0 0f 84 a2 00 00 00 8b 43 2c 85 c0 0f 84 97 00 00
[  534.608898] EIP: [<ee89fee4>] usb_kill_urb+0x14/0xd0 [usbcore] SS:ESP 0068:ebf05e68
[  534.608920] ---[ end trace dfd7d8bc1b6f746a ]---


There seems to be a serious bug in dvb or the kernel. Would it be worth filing a bug?

---

### Post by jonoxer on 2008-08-21
Hi matc,

Did you ever get a resolution to this? I just bought the exact same tuner thinking it was a different model, and although it doesn't crash the USB subsystem it also just doesn't work. I've been through all the loading firmware steps and nothing seems to help.

Cheers    :-)

Jonathan

---

### Post by matc on 2008-08-22
No, I solved it by buying a Hauppauge Nova-T stick which worked out of the box (only had to recompile kernel and linuxtv drivers.... Why on earth do I always have to modify stuff to get it working ?)

Maybe they should stop marking this stick as supported on linuxtv.org, sice this was the reason for me to buy it...

---

### Post by jonoxer on 2008-08-22
Mmm, that sucks. This is the second tuner I've bought to try to get MythTV working, and they've both failed. After being very frustrated with a Winfast DTV-2000H PCI card I bought the USB stick because, like you, I saw it listed on linuxtv.org. Now I've got yet another unusable tuner and I'll have to buy a *third* one. Grrrr.

---

