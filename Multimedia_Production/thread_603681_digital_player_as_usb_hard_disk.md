---
title: "digital player as usb hard disk"
date: 2007-11-05
forum: Multimedia Production
---

### Post by g.a. on 2007-11-05
Hi,

I have a 8GB  digital player Oregon Scientific model MP680.

From winxp it is seen as a simple usb hard-drive.

I thought it was the same under kubuntu 7.04 but it is not.

The player seems to connect and unconnect continuously. What kind of information should I check to verify if this is a configuration problem of my automount process or if this hardware is simply not compatible with linux?

thanks,
g.

---

### Post by kidders on 2007-11-06
Hi there,

A small number of media players don't use standard "disk mode" interfaces, in which case Linux support may be a problem. I'm not sure about your particular one.

When having difficulty, my advice would always be to dump your graphical UI for a while, and try to perform a few basic tasks with a terminal. Knowing which specific things fail, and exactly *how* they fail, will help forum users diagnose your problem more quickly. I suggest following logically through gaining access to your player; for instance...

[LIST]
[*]Plug out your player, and run "dmesg" to look at your kernel messages.
[*]Plug it back in, run "dmesg" again, and see how the new messages compare to what you would expect, when connecting a standard hard disk, for instance.
[*]Take a look in /dev for nodes that seem like they might point to your media player. You might, for example, find things called "sde", "sde1", "sde2"...
[*]Try to mount one of the new /dev entries that ends in a number. When you do this from a console, no output = good news.
[*]If you *do* get error messages, you could try taking another look at "dmesg" for messages about "superblocks" and such.[/LIST]Anyhow, you get the idea. Whatever you try, document it (and the output it generates). People familiar with the Linux platform can often get a lot out of error messages.

I hope that helps.

---

### Post by g.a. on 2007-11-07
thanks for your reply. yes, dmesg contains a lot of messages (for who is able to understand them... ;). i tried to google from some of these messages but i'm not expert enough to understand the problem. below this mail I attach the dmesg lines corresponding to the moment when i attach the usb device. as you can read, the digital player continuously starts the boot procedure until i unplug the usb cable.

thanks in advance again,
g.

[22467.116000] usb 4-3: new high speed USB device using ehci_hcd and address 6
[22467.432000] usb 4-3: configuration #1 chosen from 1 choice
[22467.432000] scsi5 : SCSI emulation for USB Mass Storage devices
[22467.432000] usb-storage: device found at 6
[22467.432000] usb-storage: waiting for device to settle before scanning
[22472.432000] usb-storage: device scan complete
[22472.432000] scsi 5:0:0:0: Direct-Access     OSI      HDD Jukebox      0100 PQ: 0 ANSI: 4
[22472.440000] SCSI device sdb: 15615133 512-byte hdwr sectors (7995 MB)
[22472.444000] sdb: Write Protect is off
[22472.444000] sdb: Mode Sense: 03 00 00 00
[22472.444000] sdb: assuming drive cache: write through
[22472.452000] SCSI device sdb: 15615133 512-byte hdwr sectors (7995 MB)
[22472.456000] sdb: Write Protect is off
[22472.456000] sdb: Mode Sense: 03 00 00 00
[22472.456000] sdb: assuming drive cache: write through
[22472.456000]  sdb:<6>usb 4-3: USB disconnect, address 6
[22474.600000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[22474.600000]  printing eip:
[22474.600000] c0258415
[22474.600000] *pde = 1e337067
[22474.600000] Oops: 0000 [#1]
[22474.600000] SMP
[22474.600000] Modules linked in: usb_storage libusual snd_rtctimer binfmt_misc rfcomm l2cap bluetooth ppdev speedstep_centrino cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_stats freq_table cpufreq_powersave pcc_acpi dev_acpi tc1100_wmi sony_acpi video container asus_acpi backlight sbs i2c_ec i2c_core battery button ac dock ppp_generic slhc nls_utf8 ntfs nls_iso8859_1 nls_cp437 vfat fat ipv6 sbp2 lp fuse pcmcia joydev ipw2100 ieee80211 ieee80211_crypt snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq yenta_socket rsrc_nonstatic parport_pc parport pcmcia_core intel_agp psmouse serio_raw pcspkr iTCO_wdt iTCO_vendor_support agpgart evdev tsdev snd_timer snd_seq_device shpchp pci_hotplug snd soundcore snd_page_alloc af_packet ext3 jbd mbcache sg sr_mod cdrom sd_mod generic usbhid hid ata_piix e100 mii ohci1394 ieee1394 ata_generic libata scsi_mod ehci_hcd uhci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[22474.600000] CPU:    0
[22474.600000] EIP:    0060:[<c0258415>]    Not tainted VLI
[22474.600000] EFLAGS: 00010202   (2.6.20-16-generic #2)
[22474.600000] EIP is at make_class_name+0x35/0xa0
[22474.600000] eax: 00000000   ebx: ffffffff   ecx: ffffffff   edx: 0000000b
[22474.600000] esi: e08d7c91   edi: 00000000   ebp: 00000000   esp: de6d5e50
[22474.600000] ds: 007b   es: 007b   ss: 0068
[22474.600000] Process khubd (pid: 1972, ti=de6d4000 task=dfe51030 task.ti=de6d4000)
[22474.600000] Stack: c7158204 e08e9ec0 c71581fc c7158204 e08e9e40 c0258691 00000000 e08e9ec8
[22474.600000]        c71581fc dcee9400 00000246 ffffffed c0258718 c7158000 e08d1a50 c7158000
[22474.600000]        dcee9400 e08cf12b dcee9430 dcee9400 e08c9825 dcee96f4 d8e2d218 e0e23f60
[22474.600000] Call Trace:
[22474.600000]  [<c0258691>] class_device_del+0xa1/0x120
[22474.600000]  [<c0258718>] class_device_unregister+0x8/0x10
[22474.600000]  [<e08d1a50>] __scsi_remove_device+0x30/0x80 [scsi_mod]
[22474.600000]  [<e08cf12b>] scsi_forget_host+0x4b/0x60 [scsi_mod]
[22474.600000]  [<e08c9825>] scsi_remove_host+0x55/0xe0 [scsi_mod]
[22474.600000]  [<e0e15cae>] storage_disconnect+0xe/0x20 [usb_storage]
[22474.600000]  [<e0881d20>] usb_unbind_interface+0x50/0xa0 [usbcore]
[22474.600000]  [<c02579a8>] __device_release_driver+0x68/0xa0
[22474.600000]  [<c0257ed3>] device_release_driver+0x23/0x40
[22474.600000]  [<c025731c>] bus_remove_device+0x5c/0x90
[22474.600000]  [<c0255772>] device_del+0x152/0x1b0
[22474.600000]  [<e087f1ee>] usb_disable_device+0x7e/0xe0 [usbcore]
[22474.600000]  [<e087b597>] usb_disconnect+0x97/0x130 [usbcore]
[22474.600000]  [<e087c2ff>] hub_thread+0x26f/0xc20 [usbcore]
[22474.600000]  [<c013ae00>] autoremove_wake_function+0x0/0x50
[22474.600000]  [<e087c090>] hub_thread+0x0/0xc20 [usbcore]
[22474.600000]  [<c013ac4a>] kthread+0xba/0xf0
[22474.600000]  [<c013ab90>] kthread+0x0/0xf0
[22474.600000]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[22474.600000]  =======================
[22474.600000] Code: ff ff 89 6c 24 10 31 ed 89 d9 89 74 24 08 89 c6 89 7c 24 0c 89 c7 89 e8 89 14 24 f2 ae f7 d1 49 8b 04 24 89 ca 89 d9 8b 38 89 e8 <f2> ae f7 d1 49 8d 44 0a 02 ba d0 00 00 00 e8 d8 ac f1 ff ba f4
[22474.600000] EIP: [<c0258415>] make_class_name+0x35/0xa0 SS:ESP 0068:de6d5e50
[22474.600000]  <6>sd 5:0:0:0: SCSI error: return code = 0x00010000
[22474.600000] end_request: I/O error, dev sdb, sector 0
[22474.600000] Buffer I/O error on device sdb, logical block 0
[22474.600000] Buffer I/O error on device sdb, logical block 1
[22474.600000] Buffer I/O error on device sdb, logical block 2
[22474.600000] Buffer I/O error on device sdb, logical block 3
[22474.600000] Buffer I/O error on device sdb, logical block 4
[22474.600000] Buffer I/O error on device sdb, logical block 5
[22474.600000] Buffer I/O error on device sdb, logical block 6
[22474.600000] Buffer I/O error on device sdb, logical block 7
[22474.600000] Buffer I/O error on device sdb, logical block 0
[22474.600000] Buffer I/O error on device sdb, logical block 1
[22474.600000] ldm_validate_partition_table(): Disk read failed.
[22474.600000] Dev sdb: unable to read RDB block 0
[22474.600000]  unknown partition table
[22474.600000] sd 5:0:0:0: Attached scsi removable disk sdb
[22474.600000] sd 5:0:0:0: Attached scsi generic sg2 type 0
[22474.720000] sdb : READ CAPACITY failed.
[22474.720000] sdb : status=0, message=00, host=1, driver=00
[22474.720000] sdb : sense not available.
[22474.724000] sdb: Write Protect is off
[22474.724000] sdb: Mode Sense: 00 00 00 00
[22474.724000] sdb: assuming drive cache: write through
[22474.724000] sdb : READ CAPACITY failed.
[22474.724000] sdb : status=0, message=00, host=1, driver=00
[22474.724000] sdb : sense not available.
[22474.724000] sdb: Write Protect is off
[22474.724000] sdb: Mode Sense: 00 00 00 00
[22474.724000] sdb: assuming drive cache: write through
[22474.724000] sdb : READ CAPACITY failed.
[22474.724000] sdb : status=0, message=00, host=1, driver=00
[22474.724000] sdb : sense not available.
[22474.724000] sdb: Write Protect is off
[22474.724000] sdb: Mode Sense: 00 00 00 00
[22474.724000] sdb: assuming drive cache: write through
[22474.724000] sdb : READ CAPACITY failed.
[22474.724000] sdb : status=0, message=00, host=1, driver=00
[22474.724000] sdb : sense not available.
[22474.724000] sdb: Write Protect is off
[22474.724000] sdb: Mode Sense: 00 00 00 00
[22474.724000] sdb: assuming drive cache: write through
[22474.748000] sdb : READ CAPACITY failed.
[22474.748000] sdb : status=0, message=00, host=1, driver=00
[22474.748000] sdb : sense not available.
[22474.748000] sdb: Write Protect is off
[22474.748000] sdb: Mode Sense: 00 00 00 00
[22474.748000] sdb: assuming drive cache: write through
[22474.748000] sdb : READ CAPACITY failed.
[22474.748000] sdb : status=0, message=00, host=1, driver=00
[22474.748000] sdb : sense not available.
[22474.748000] sdb: Write Protect is off
[22474.748000] sdb: Mode Sense: 00 00 00 00
[22474.748000] sdb: assuming drive cache: write through
[22474.764000] sdb : READ CAPACITY failed.
[22474.764000] sdb : status=0, message=00, host=1, driver=00
[22474.764000] sdb : sense not available.
[22474.764000] sdb: Write Protect is off
[22474.764000] sdb: Mode Sense: 00 00 00 00
[22474.764000] sdb: assuming drive cache: write through
[22474.764000] sdb : READ CAPACITY failed.
[22474.764000] sdb : status=0, message=00, host=1, driver=00
[22474.764000] sdb : sense not available.
[22474.764000] sdb: Write Protect is off
[22474.764000] sdb: Mode Sense: 00 00 00 00
[22474.764000] sdb: assuming drive cache: write through
[22476.784000] sdb : READ CAPACITY failed.
[22476.784000] sdb : status=0, message=00, host=1, driver=00
[22476.784000] sdb : sense not available.
[22476.784000] sdb: Write Protect is off
[22476.784000] sdb: Mode Sense: 00 00 00 00
[22476.784000] sdb: assuming drive cache: write through
[22476.784000] sdb : READ CAPACITY failed.
[22476.784000] sdb : status=0, message=00, host=1, driver=00
[22476.784000] sdb : sense not available.
[22476.784000] sdb: Write Protect is off
[22476.784000] sdb: Mode Sense: 00 00 00 00
[22476.784000] sdb: assuming drive cache: write through
[22478.812000] sdb : READ CAPACITY failed.
[22478.812000] sdb : status=0, message=00, host=1, driver=00
[22478.812000] sdb : sense not available.
[22478.816000] sdb: Write Protect is off
[22478.816000] sdb: Mode Sense: 00 00 00 00
[22478.816000] sdb: assuming drive cache: write through
[22478.832000] sdb : READ CAPACITY failed.
[22478.832000] sdb : status=0, message=00, host=1, driver=00
[22478.832000] sdb : sense not available.
[22478.836000] sdb: Write Protect is off
[22478.836000] sdb: Mode Sense: 00 00 00 00
[22478.836000] sdb: assuming drive cache: write through
[22480.860000] sdb : READ CAPACITY failed.
[22480.860000] sdb : status=0, message=00, host=1, driver=00
[22480.860000] sdb : sense not available.
[22480.864000] sdb: Write Protect is off
[22480.864000] sdb: Mode Sense: 00 00 00 00
[22480.864000] sdb: assuming drive cache: write through
[22480.876000] sdb : READ CAPACITY failed.
[22480.876000] sdb : status=0, message=00, host=1, driver=00
[22480.876000] sdb : sense not available.
[22480.880000] sdb: Write Protect is off
[22480.880000] sdb: Mode Sense: 00 00 00 00
[22480.880000] sdb: assuming drive cache: write through
[22482.900000] sdb : READ CAPACITY failed.
[22482.900000] sdb : status=0, message=00, host=1, driver=00
[22482.900000] sdb : sense not available.
[22482.900000] sdb: Write Protect is off
[22482.900000] sdb: Mode Sense: 00 00 00 00
[22482.900000] sdb: assuming drive cache: write through
[22482.916000] sdb : READ CAPACITY failed.
[22482.916000] sdb : status=0, message=00, host=1, driver=00
[22482.916000] sdb : sense not available.
[22482.920000] sdb: Write Protect is off
[22482.920000] sdb: Mode Sense: 00 00 00 00
[22482.920000] sdb: assuming drive cache: write through
[22484.936000] sdb : READ CAPACITY failed.
[22484.936000] sdb : status=0, message=00, host=1, driver=00
[22484.936000] sdb : sense not available.
[22484.940000] sdb: Write Protect is off
[22484.940000] sdb: Mode Sense: 00 00 00 00
[22484.940000] sdb: assuming drive cache: write through
[22484.952000] sdb : READ CAPACITY failed.
[22484.952000] sdb : status=0, message=00, host=1, driver=00
[22484.952000] sdb : sense not available.
[22484.956000] sdb: Write Protect is off
[22484.956000] sdb: Mode Sense: 00 00 00 00
[22484.956000] sdb: assuming drive cache: write through
[22486.972000] sdb : READ CAPACITY failed.
[22486.972000] sdb : status=0, message=00, host=1, driver=00
[22486.972000] sdb : sense not available.
[22486.976000] sdb: Write Protect is off
[22486.976000] sdb: Mode Sense: 00 00 00 00
[22486.976000] sdb: assuming drive cache: write through
[22486.988000] sdb : READ CAPACITY failed.
[22486.988000] sdb : status=0, message=00, host=1, driver=00
[22486.988000] sdb : sense not available.
[22486.988000] sdb: Write Protect is off
[22486.988000] sdb: Mode Sense: 00 00 00 00
[22486.988000] sdb: assuming drive cache: write through
[22489.008000] sdb : READ CAPACITY failed.
[22489.008000] sdb : status=0, message=00, host=1, driver=00
[22489.008000] sdb : sense not available.
[22489.012000] sdb: Write Protect is off
[22489.012000] sdb: Mode Sense: 00 00 00 00
[22489.012000] sdb: assuming drive cache: write through
[22489.024000] sdb : READ CAPACITY failed.
[22489.024000] sdb : status=0, message=00, host=1, driver=00
[22489.024000] sdb : sense not available.
[22489.028000] sdb: Write Protect is off
[22489.028000] sdb: Mode Sense: 00 00 00 00
[22489.028000] sdb: assuming drive cache: write through
[22491.048000] sdb : READ CAPACITY failed.
[22491.048000] sdb : status=0, message=00, host=1, driver=00
[22491.048000] sdb : sense not available.
[22491.052000] sdb: Write Protect is off
[22491.052000] sdb: Mode Sense: 00 00 00 00
[22491.052000] sdb: assuming drive cache: write through
[22491.068000] sdb : READ CAPACITY failed.
[22491.068000] sdb : status=0, message=00, host=1, driver=00
[22491.068000] sdb : sense not available.
[22491.072000] sdb: Write Protect is off
[22491.072000] sdb: Mode Sense: 00 00 00 00
[22491.072000] sdb: assuming drive cache: write through
[22493.088000] sdb : READ CAPACITY failed.
[22493.088000] sdb : status=0, message=00, host=1, driver=00
[22493.088000] sdb : sense not available.
[22493.092000] sdb: Write Protect is off
[22493.092000] sdb: Mode Sense: 00 00 00 00
[22493.092000] sdb: assuming drive cache: write through
[22493.092000] sdb : READ CAPACITY failed.
[22493.092000] sdb : status=0, message=00, host=1, driver=00
[22493.092000] sdb : sense not available.
[22493.092000] sdb: Write Protect is off
[22493.092000] sdb: Mode Sense: 00 00 00 00
[22493.092000] sdb: assuming drive cache: write through
[22495.116000] sdb : READ CAPACITY failed.
[22495.116000] sdb : status=0, message=00, host=1, driver=00
[22495.116000] sdb : sense not available.
[22495.120000] sdb: Write Protect is off
[22495.120000] sdb: Mode Sense: 00 00 00 00
[22495.120000] sdb: assuming drive cache: write through
[22495.132000] sdb : READ CAPACITY failed.
[22495.132000] sdb : status=0, message=00, host=1, driver=00
[22495.132000] sdb : sense not available.
[22495.136000] sdb: Write Protect is off
[22495.136000] sdb: Mode Sense: 00 00 00 00
[22495.136000] sdb: assuming drive cache: write through

---

### Post by kidders on 2007-11-07
Hey again,

Without wanting to get into the (decidedly uninteresting) detail of what all these messages mean, the part to draw your attention to is...```
[22474.600000] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[22474.600000]  printing eip:
[22474.600000] c0258415
[22474.600000] *pde = 1e337067
[22474.600000] Oops: 0000 [#1]
```Every Linux user is sensitive to the word "oops" ... it's a term used to describe a fundamental failure in low-level logic. Typically, it either points to a relatively serious hardware failure or a big bug in your OS. Most users never see this sort of error.

I would suggest the following...[LIST]
[*]Try to replicate the problem once more, just to be 100% sure it really exists. Write down some details about what was running, some dmesg output (including the stack trace), etc. Don't try to reproduce the bug more than one more time ... it's just not a good idea.
[*]Reboot your machine immediately. To be safe, you shouldn't really trust *anything* your box does after an oops ... even writing to your hard disk ... so the next thing you type should be **sudo shutdown -r now. **If you don't, your system may become unstable & start botching things up.
[*]I'm inclined to think your problem is a bug in Ubuntu. To verify, try running a LiveCD from another unrelated distro (ie _not_ a Debian derivative), and see if your media player will work properly.
[*]If it does, you definitely don't have a hardware problem, so you can feel free to file a bug & watch the Ubuntu devs fix it for you. If you check, you may find one's already been filed about this issue.[/LIST]Sorry I can't offer you a better suggestion. Naturally, you *need* your media player to play nice with your computer ... if Mandriva, Red Hat, Gentoo, etc. can talk to it without tangling themselves up in knots, I would suggest switching distro ... at least for a little while. Earlier versions of Ubuntu (eg Feisty, Edgy) might also be worth a quick test.

---

### Post by g.a. on 2007-11-09
thanks for your reply, I made a quick test with the laptop of my desk neighbor with kubuntu 7.10 and it seems that the device is not installed even with the newer version.

it does not receive a kernel oops message but the device keeps turning on and off and dmesg shows that linux is continuously trying to mount it without success.

since the device is recognized from winxp what conclusion can be drawn?

thank,
g.

---

### Post by kidders on 2007-11-09
Hmm...

I think it's still worth looking at the possibility of a bug of some sort. If only I knew more about your specific player. :-( Have you found anything in Linux bug databases to shed any light on things? It's always reassuring to know you're not the *only* person in the whole world who's had this problem, because if you are, the cause is almost certainly not a bug.

Aside from a bug in Linux, other possibilities include a problem with the media player's filesystem that Windows just doesn't happen to be as sensitive to as Linux is ... then again, your player may be completely incompatible with Linux. Windows might be using a device-specific driver to access it.

---

### Post by g.a. on 2007-11-09
well, i do not know if I'm the only one with this problem but probably I'm the only one with this digital player...

I have found a bug that seems to be similar:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98701](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/98701)

I was tented to report it as a possible bug with the same information asked to that user, i.e., dmesg output and the output of lsusb -v command.

I'm attaching those file to this post as text files.

best,
g.

---

### Post by kidders on 2007-11-09
Yep... there's certainly a similarity. Bugs confirmed by multiple sources tend to get higher priority, so if you'd like to see this problem solved more quickly, you could add your voice to the bug report.

Sorry I wasn't able to give you a more clean-cut solution, by the way. :-(

---

### Post by g.a. on 2007-11-12
thanks a lot, I have posted it in the launchpad, 

best,
g.

---

