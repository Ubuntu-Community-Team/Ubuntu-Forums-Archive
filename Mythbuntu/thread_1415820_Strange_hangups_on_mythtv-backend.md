---
title: "Strange hangups on mythtv-backend"
date: 2010-02-25
forum: Mythbuntu
---

### Post by framathon on 2010-02-25
Hello everyone,

I am encountering hangups with my MythTV backend that i can't explain, it's strange because it was working fine a week ago. 

But now every morning i find the box completly unresponsive and if i try to reboot it will show up an error when loading:
VFS: Unable to mount root fs yada yada...

When in it's in this state, I tried editing my boot options to change my root fs selection from UUID based to /dev/sdX without any success. I can try rebooting as many times as i want or try any grub options, it just won't find my partition.

But if i power down the system for a couple seconds and restart it, then it will boot up fine like nothing happened

What could cause this behavior ? It's a complete mystery to me.


I would like to understand why the backend freezes, i couldn't see any relevant information/errors in the mythtv-backend.log. I looked in my /var/log/messages too and saw a couple of errors about "smbd Tainted" but i am not sure if it's a cause or a consequence, i can post them if needed.

--------------

Now on some more technical details:

Motherboard: Gigabyte GA-X48-DQ6
CPU:         Intel QuadCore (QX6???)
8gb RAM: 2x 2gb of Corsair and 2x 2gb of OCZ. (I ram memtest for several hours before i installed mythbuntu without troubles)
2x WinTV Nova-TD-500
NVIDIA 9500 card. (or 8500 ? cheap fanless card with vdpau support)
Power suppy backed up with UPS.

The boot drive is a brand new 250gb disk with 0 smart warnings and he never complained of anything. (ext4)

I have a 1Tb dedicated disk for mythtv recording (JFS)

And 4 x 1.5Tb raid5 array as a samba share. (mdadm - ext3)

Noteworthy: all sata channels are configured as AHCI in the bios.

--------------------
As for the software:

The server only runs mythtv-backend, samba shares and sabnzbd as a daemon.

I am using mythbuntu 9.10 64bit with mythtv 0.22-fixes autobuild

team-vdpau nvidia drivers (i don't use the backend to watch anything anymore, so i'll probably uninstall the restricted drivers)

----------------------
The last updated things:

Before i had partitionned my mythtv  hardisk witha 200gb boot partition and a 800gb data partition. But it was a slow 5400rpm WD Green disk so the system was a bit too slow. Especially when i ssh to the box while recordings were in progress. So i installed a new 250gb and used clonezilla to duplicate the filesystem. And now have a dedicated disk for the OS.

I reinstalled grub2 after this clone, then downgraded it to legacy grub after my first VFS: no root fs... error. But it didn't fix it.

I install all the mythtv / nvidia / ubuntu updates as they come by.

-------------------------

I am by no means a Linux guru but i do have some basic knowledge. What i would like is some help on how to track the root cause and fix it once and for all. My action plan so far will be:

1. Rerun memcheck86 for 8hours+
2. Disable AHCI and fallback to IDE mode
3. Remove/Purge all restricted nvidia drivers

4. ... need help ...

5. Reinstall a 32bit version ?

What else can i add to this plan to fix this ?

---

### Post by framathon on 2010-02-25
Here is part of /var/log/messages during a hang:

```
Feb 25 00:32:53 htpc kernel: [16012.679430] CPU 3
Feb 25 00:32:53 htpc kernel: [16012.679432] Modules linked in: binfmt_misc nvidia(P) jfs snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm dvb_usb_dib0700 dib7000p dib7000m snd_seq_dummy dvb_usb snd_seq_oss dvb_core dib3000mc dibx000_common dib0070 snd_seq_midi iptable_filter snd_rawmidi snd_seq_midi_event ppdev snd_seq snd_timer parport_pc snd_seq_device ip_tables x_tables joydev psmouse serio_raw snd x38_edac soundcore snd_page_alloc edac_core lp parport raid10 raid456 raid6_pq async_xor async_memcpy async_tx raid1 raid0 multipath linear dm_raid45 xor ohci1394 usbhid ieee1394 r8169 mii
Feb 25 00:32:53 htpc kernel: [16012.679490] Pid: 7057, comm: smbd Tainted: P           2.6.31-19-generic #56-Ubuntu X48-DQ6
Feb 25 00:32:53 htpc kernel: [16012.679493] RIP: 0010:[<ffffffff810da4c4>]  [<ffffffff810da4c4>] find_get_page+0x34/0xa0
Feb 25 00:32:53 htpc kernel: [16012.679503] RSP: 0018:ffff8801b1a8dc88  EFLAGS: 00010203
Feb 25 00:32:53 htpc kernel: [16012.679506] RAX: 001fffffffffffff RBX: ffff8800738c9d70 RCX: ffff8801b7197c70
Feb 25 00:32:53 htpc kernel: [16012.679510] RDX: 0000000000000000 RSI: 0000000000049b69 RDI: 0020000000000000
Feb 25 00:32:53 htpc kernel: [16012.679513] RBP: ffff8801b1a8dc98 R08: 0000000000000002 R09: ffffea0000cef820
Feb 25 00:32:53 htpc kernel: [16012.679516] R10: 0000000049b6457a R11: 0000000000000001 R12: 0000000000049b69
Feb 25 00:32:53 htpc kernel: [16012.679519] R13: 0000000000049b69 R14: ffff88020f8bb480 R15: 0000000000000000
Feb 25 00:32:53 htpc kernel: [16012.679523] FS:  00007f858ce71710(0000) GS:ffff88002808e000(0000) knlGS:0000000000000000
Feb 25 00:32:53 htpc kernel: [16012.679526] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Feb 25 00:32:53 htpc kernel: [16012.679529] CR2: 00007f221e1c1000 CR3: 00000001e1c21000 CR4: 00000000000006e0
Feb 25 00:32:53 htpc kernel: [16012.679532] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb 25 00:32:53 htpc kernel: [16012.679536] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb 25 00:32:53 htpc kernel: [16012.679539] Process smbd (pid: 7057, threadinfo ffff8801b1a8c000, task ffff8800b24316b0)
Feb 25 00:32:53 htpc kernel: [16012.679544]  ffffea0000cef818 ffff8800738c9d68 ffff8801b1a8dd28 ffffffff810db7a1
Feb 25 00:32:53 htpc kernel: [16012.679549] <0> 0000000000049b69 0000000000001000 ffff8801b1a8de48 0000000000000000
Feb 25 00:32:53 htpc kernel: [16012.679555] <0> 0000000000049b6d 0000000000049b68 ffff88020f8bb4f0 ffff8800738c9c50
Feb 25 00:32:53 htpc kernel: [16012.679567]  [<ffffffff810db7a1>] T.768+0x151/0x440
Feb 25 00:32:53 htpc kernel: [16012.679571]  [<ffffffff810dbb46>] generic_file_aio_read+0xb6/0x1d0
Feb 25 00:32:53 htpc kernel: [16012.679577]  [<ffffffff8111f222>] do_sync_read+0xf2/0x130
Feb 25 00:32:53 htpc kernel: [16012.679582]  [<ffffffff8115af8b>] ? posix_test_lock+0xdb/0xe0
Feb 25 00:32:53 htpc kernel: [16012.679588]  [<ffffffff810789c0>] ? autoremove_wake_function+0x0/0x40
Feb 25 00:32:53 htpc kernel: [16012.679595]  [<ffffffff81220b91>] ? security_file_permission+0x11/0x20
Feb 25 00:32:53 htpc kernel: [16012.679599]  [<ffffffff8111f805>] vfs_read+0xb5/0x1a0
Feb 25 00:32:53 htpc kernel: [16012.679604]  [<ffffffff8111ff3a>] sys_pread64+0x7a/0x90
Feb 25 00:32:53 htpc kernel: [16012.679610]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b
Feb 25 00:32:53 htpc kernel: [16012.679662]  RSP <ffff8801b1a8dc88>
Feb 25 00:32:53 htpc kernel: [16012.679666] ---[ end trace b1105b4bf9dd807f ]---
Feb 25 03:17:08 htpc kernel: [25867.608022] python[7484] general protection ip:4cede0 sp:7fff9a70e538 error:0 in python2.6[400000+20f000]
Feb 25 06:25:02 htpc kernel: Kernel logging (proc) stopped.
Feb 25 06:25:02 htpc rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1193" x-info="http://www.rsyslog.com"] exiting on signal 15.

```

The server was still running fine at 00:32 so this error didn't bring him down.  

3:17 should be the time where i stopped using the remote frontend (can be before or after, don't remember)

6:25 i was sound asleep and don't know what happened.


The mythvbackend logs tells us more:

```
2010-02-25 06:24:23.606 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/htpc/1052_20100223200844.mpg. File doesn't exist.  Database metadata will not be removed.
=====================================
= pre-shutdown check =
=-----------------------------------=
No lock on samba shares
sabnzbd is running...
SABnzbd is idle.
 06:25:01 up 10:19,  0 users,  load average: 0.00, 0.00, 0.00
Noone is logged in, ok to shut down.
2010-02-25 06:25:02.043 CheckShutdownServer returned - OK to shutdown
2010-02-25 06:25:02.104 Running the command to set the next scheduled wakeup time :-
                                                sudo sh -c "/usr/bin/setwakeup.sh 1267115800"
2010-02-25 06:25:02.177 Running the command to shutdown this computer :-
                                                sudo shutdown -h now

```

Its first time i see him actually trying to shutdown the computer before a hang, still is unexplained because if I "sudo shutdown -h now", the computer don't hang and just powersoff until the next scheduled wakeup alarm.

And last week it was shuting down / restarting when scheduled without any issues....
I guess shutdown unmounts all filesystems so there won't be any shutdown logs that could show what went wrong ?

---

### Post by SiHa on 2010-02-26
What happens if you change the shutdown command to ```
sudo shutdown -h -P now
```

IIRC from the shutdown manpages: "-h will bring down the system and leave it up to the system to either halt or shutdown"
"-P explicitly tells the system to shutdown" 

Not sure why the behaviour of your system has changed, or why the "-h" works from the commandline, but I believe the above is the 'proper' method of shutting down.

---

