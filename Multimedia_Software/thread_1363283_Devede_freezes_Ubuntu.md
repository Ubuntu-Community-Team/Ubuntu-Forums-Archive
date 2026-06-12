---
title: "Devede freezes Ubuntu"
date: 2009-12-24
forum: Multimedia Software
---

### Post by cplinux on 2009-12-24
Hi!

I'm having the following hardware:
Asus P5N-T Deluxe
Quad Core 2.4GHZ
4x2GB DDR2
5 disks (1. Ubuntu, 2.+3. Raid1 mdadm, 4.+5. Raid1 mdadm)

I'm using Ubuntu 9.10 (Koala), Linux wks01-ubuntu 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux.

I'm having a really strange problem, when i try to convert 2 avi files onto a Video DVD using Devede, it sometimes freezes the whole system. Means, that no input device works anymore, so the only way to get back control is pushing the reset or power button.

I've tested a bit and leaving unchecked the "multi-core options" and writing the output on my first hard disk (no raid) it seems to work.
It looks to me that wether it's this multi-core option or it's the fact that the machine has a lot of input/output that makes the machine freeze.

So, maybe it's a problem with mdadm?
After one of those tests that crashed the system (writing output onto one of the raid arrays), mdadm started a resync of the corresponding raid after reboot - with minimal data loss.
Are there known problems with IO on mdadm?

I've found this in my logs:
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069779] BUG: Bad page state in process mencoder  pfn:1438f3
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069785] page:ffffea00046c7528 flags:0200000000000000 count:8 mapcount:0 mapping:(null) index:0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069788] Pid: 5035, comm: mencoder Tainted: P           2.6.31-16-generic #53-Ubuntu
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069791] Call Trace:
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069799]  [<ffffffff810df304>] bad_page+0xd4/0x130
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069802]  [<ffffffff810dfa0c>] prep_new_page+0x2c/0x170
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069806]  [<ffffffff810e008d>] get_page_from_freelist+0x2dd/0x5d0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069809]  [<ffffffff810e093d>] __alloc_pages_nodemask+0xdd/0x150
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069812]  [<ffffffff8110ceb2>] alloc_pages_current+0x82/0xd0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069815]  [<ffffffff81112098>] new_slab+0x238/0x300
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069818]  [<ffffffff81114ee9>] __slab_alloc+0x169/0x2d0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069822]  [<ffffffff81144bb7>] ? alloc_buffer_head+0x17/0x50
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069825]  [<ffffffff8111548d>] kmem_cache_alloc+0x13d/0x150
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069827]  [<ffffffff81144bb7>] alloc_buffer_head+0x17/0x50
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069830]  [<ffffffff81145516>] alloc_page_buffers+0x36/0x100
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069833]  [<ffffffff811455fd>] create_empty_buffers+0x1d/0xc0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069836]  [<ffffffff81148536>] __block_prepare_write+0x406/0x560
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069839]  [<ffffffff8111bb50>] ? mem_cgroup_cache_charge+0xb0/0x140
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069843]  [<ffffffff811b4a50>] ? ext4_da_get_block_prep+0x0/0x100
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069845]  [<ffffffff8114882f>] block_write_begin+0x5f/0x100
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069848]  [<ffffffff811b6fbd>] ext4_da_write_begin+0x12d/0x260
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069850]  [<ffffffff811b4a50>] ? ext4_da_get_block_prep+0x0/0x100
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069854]  [<ffffffff8104a87e>] ? __wake_up+0x4e/0x70
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069857]  [<ffffffff810da182>] generic_perform_write+0xb2/0x1d0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069861]  [<ffffffff811e0f0b>] ? ext4_xattr_get+0x5b/0x90
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069864]  [<ffffffff810dafb3>] generic_file_buffered_write+0x83/0x140
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069867]  [<ffffffff810dc930>] __generic_file_aio_write_nolock+0x240/0x470
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069870]  [<ffffffff81134583>] ? touch_atime+0x33/0x150
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069873]  [<ffffffff810dcc80>] generic_file_aio_write+0x70/0xf0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069876]  [<ffffffff811ae3b9>] ext4_file_write+0x49/0x160
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069880]  [<ffffffff8111f002>] do_sync_write+0xf2/0x130
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069883]  [<ffffffff81078b30>] ? autoremove_wake_function+0x0/0x40
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069887]  [<ffffffff81010875>] ? __switch_to+0x315/0x370
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069891]  [<ffffffff81220a81>] ? security_file_permission+0x11/0x20
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069894]  [<ffffffff8111f2e8>] vfs_write+0xb8/0x1a0
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069897]  [<ffffffff8111fd9c>] sys_write+0x4c/0x80
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069901]  [<ffffffff8152a289>] ? do_device_not_available+0x9/0x10
Dec 24 10:57:39 wks01-ubuntu kernel: [ 3749.069904]  [<ffffffff81012002>] system_call_fastpath+0x16/0x1b

For the moment i'm writing the output to the first disk, so it's a workaround.

But maybe there are other people having the same issues?

Christian
(cplinux)

---

### Post by cplinux on 2009-12-24
Ok, it's not a workaround. It's been working twice. The third time, it froze my Ubuntu and I had to reset.

Is there any mean to get it working?
I just need something to produce a DVD structure (vob files) from avi or mpeg.

Ok, finally my tests show me the following:
Devede as well as e.g. ManDVD freeze the whole system as soon as you try to create the iso image.
I assume this has something to do with the hard disk load caused by this.

Another strange issue is that if I use one of these tools to create a dvd and afterwards want to shutdown my computer, it even hangs there.
I have to switch it off keeping pressed the power button for some seconds.

Any help appreciated.

Christian
(cplinux)

---

### Post by cplinux on 2009-12-25
More information, when shutting down I have a lot of these messages:
Dec 20 18:42:25 wks01-ubuntu kernel: [27166.742491] BUG: soft lockup - CPU#2 stuck for 61s! [rm:2942]
Dec 20 18:43:31 wks01-ubuntu kernel: [27232.242490] BUG: soft lockup - CPU#2 stuck for 61s! [rm:2942]
Dec 20 18:44:36 wks01-ubuntu kernel: [27297.742490] BUG: soft lockup - CPU#2 stuck for 61s! [rm:2942]
Dec 20 18:45:42 wks01-ubuntu kernel: [27363.242490] BUG: soft lockup - CPU#2 stuck for 61s! [rm:2942]
Dec 23 20:45:18 wks01-ubuntu kernel: [ 3233.043741] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:46:24 wks01-ubuntu kernel: [ 3298.543740] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:47:29 wks01-ubuntu kernel: [ 3364.033739] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:48:35 wks01-ubuntu kernel: [ 3429.533740] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:49:40 wks01-ubuntu kernel: [ 3495.033740] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:50:46 wks01-ubuntu kernel: [ 3560.533740] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:51:51 wks01-ubuntu kernel: [ 3626.033740] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:52:57 wks01-ubuntu kernel: [ 3691.533740] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:54:02 wks01-ubuntu kernel: [ 3757.023741] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:55:08 wks01-ubuntu kernel: [ 3822.523740] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:56:13 wks01-ubuntu kernel: [ 3888.023739] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:57:19 wks01-ubuntu kernel: [ 3953.523738] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:58:24 wks01-ubuntu kernel: [ 4019.023739] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 23 20:59:30 wks01-ubuntu kernel: [ 4084.523738] BUG: soft lockup - CPU#3 stuck for 61s! [python:2732]
Dec 25 00:12:33 wks01-ubuntu kernel: [12080.671243] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:13:38 wks01-ubuntu kernel: [12146.171240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:14:44 wks01-ubuntu kernel: [12211.671239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:15:49 wks01-ubuntu kernel: [12277.171242] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:16:55 wks01-ubuntu kernel: [12342.671240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:18:00 wks01-ubuntu kernel: [12408.161240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:19:06 wks01-ubuntu kernel: [12473.661239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:20:11 wks01-ubuntu kernel: [12539.161241] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:21:17 wks01-ubuntu kernel: [12604.661240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:22:22 wks01-ubuntu kernel: [12670.161240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:23:28 wks01-ubuntu kernel: [12735.661239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:24:33 wks01-ubuntu kernel: [12801.151239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:25:39 wks01-ubuntu kernel: [12866.651239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:26:44 wks01-ubuntu kernel: [12932.151239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:27:50 wks01-ubuntu kernel: [12997.651240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:28:55 wks01-ubuntu kernel: [13063.151240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:30:01 wks01-ubuntu kernel: [13128.651239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:31:06 wks01-ubuntu kernel: [13194.141238] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:32:12 wks01-ubuntu kernel: [13259.641240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:33:17 wks01-ubuntu kernel: [13325.141239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:34:23 wks01-ubuntu kernel: [13390.641239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:35:28 wks01-ubuntu kernel: [13456.141239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:36:34 wks01-ubuntu kernel: [13521.631239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:37:39 wks01-ubuntu kernel: [13587.131239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:38:45 wks01-ubuntu kernel: [13652.631241] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:39:50 wks01-ubuntu kernel: [13718.131240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:40:56 wks01-ubuntu kernel: [13783.631240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:42:01 wks01-ubuntu kernel: [13849.131242] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:43:07 wks01-ubuntu kernel: [13914.621239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:44:12 wks01-ubuntu kernel: [13980.121239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:45:18 wks01-ubuntu kernel: [14045.621238] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:46:23 wks01-ubuntu kernel: [14111.121239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:47:29 wks01-ubuntu kernel: [14176.621239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:48:34 wks01-ubuntu kernel: [14242.121240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:49:40 wks01-ubuntu kernel: [14307.611239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:50:45 wks01-ubuntu kernel: [14373.111239] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:51:51 wks01-ubuntu kernel: [14438.611240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:52:56 wks01-ubuntu kernel: [14504.111241] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:54:02 wks01-ubuntu kernel: [14569.611241] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:55:07 wks01-ubuntu kernel: [14635.101241] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:56:13 wks01-ubuntu kernel: [14700.601242] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:57:18 wks01-ubuntu kernel: [14766.101241] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]
Dec 25 00:58:24 wks01-ubuntu kernel: [14831.601240] BUG: soft lockup - CPU#1 stuck for 61s! [gvfsd-trash:5490]

---

### Post by cplinux on 2009-12-25
I hope it's ok if I provide some information here. It looks really like weird bug.
Is it possible that it has something to do with the ext4 file system?
I've just deactivated compiz as I found some hints in several other forums, but I don't think that it has to do something with my nvidia card.

---

### Post by cplinux on 2009-12-25
Kernel log excerpt:

Dec 25 19:46:33 wks01-ubuntu kernel: [ 9101.209676] BUG: unable to handle kernel paging request at ffffffff0000000b
Dec 25 19:46:58 wks01-ubuntu kernel: [ 9126.811243] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:48:04 wks01-ubuntu kernel: [ 9192.311241] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:49:09 wks01-ubuntu kernel: [ 9257.811241] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:49:10 wks01-ubuntu kernel: [ 9258.082024] kernel BUG at /build/buildd/linux-2.6.31/fs/ext4/inode.c:2388!
Dec 25 19:50:15 wks01-ubuntu kernel: [ 9323.301241] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:50:57 wks01-ubuntu kernel: [ 9365.784399] BUG: unable to handle kernel paging request at ffffffff00000003
Dec 25 19:51:20 wks01-ubuntu kernel: [ 9388.801241] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:52:26 wks01-ubuntu kernel: [ 9454.301241] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:53:31 wks01-ubuntu kernel: [ 9519.801240] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:54:37 wks01-ubuntu kernel: [ 9585.301241] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:55:42 wks01-ubuntu kernel: [ 9650.801239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:56:48 wks01-ubuntu kernel: [ 9716.291239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:57:53 wks01-ubuntu kernel: [ 9781.791240] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 19:58:59 wks01-ubuntu kernel: [ 9847.291239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:00:04 wks01-ubuntu kernel: [ 9912.791239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:01:10 wks01-ubuntu kernel: [ 9978.291239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:02:15 wks01-ubuntu kernel: [10043.781240] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:03:21 wks01-ubuntu kernel: [10109.281240] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:04:26 wks01-ubuntu kernel: [10174.781239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:05:32 wks01-ubuntu kernel: [10240.281239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:06:37 wks01-ubuntu kernel: [10305.781239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:07:43 wks01-ubuntu kernel: [10371.281239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:08:48 wks01-ubuntu kernel: [10436.771239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:09:54 wks01-ubuntu kernel: [10502.271239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:10:59 wks01-ubuntu kernel: [10567.771239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:12:05 wks01-ubuntu kernel: [10633.271239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:13:10 wks01-ubuntu kernel: [10698.771239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:14:16 wks01-ubuntu kernel: [10764.271239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:15:21 wks01-ubuntu kernel: [10829.761239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:16:27 wks01-ubuntu kernel: [10895.261239] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]
Dec 25 20:17:32 wks01-ubuntu kernel: [10960.761240] BUG: soft lockup - CPU#1 stuck for 61s! [kswapd0:47]

---

### Post by cplinux on 2009-12-25
_**I'VE FOUND THE SOLUTION!**_

Now i'm using an older kernel:
Linux wks01-ubuntu _**2.6.31-15-generic**_ #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

The system seems to run stable now, have created some dvds with DeVeDe without any freezes! No more messages in the logs.

So i'll keep attention a bit when downloading updates in the future!

---

### Post by cplinux on 2009-12-26
I have to add that it's not 100% solved, but the system stays much more stable.
I hope that there will be a new kernel without these bugs soon ...

---

### Post by Shazaam on 2009-12-26
Not an answer but have you tried the "Magic SysRQ" key combo to reboot a locked up system? Hold down your Alt plus SysRQ (Print Screen) keys and type in (ignore the period) reisub. This should reboot your pc without data loss which can occour when you hit the reset/power buttons.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by cplinux on 2009-12-26
Yes I retried them several times (Alt+SysRQ+e, Alt+SysRQ+u, Alt+SysRQ+i, Alt+SysRQ+b), but no way.

But I think I may have found the reason for the freeze now.

In fact i'm having 2 RAID1 arrays. As filesystem I chose ext4.
As soon as I write/copy data on one of those arrays, mdadm starts rebuilds. Maybe that's the reason for the strange kernel messages, too.
Reason enough for me to reformat the disks with ext3.

I'm testing this the next few days and I'll keep you up-2-date about my results.

---

### Post by cplinux on 2009-12-27
Still freezes. No way to get it solved.
I'll create another set of backups and after that I switch distribution or back to vista.

Christian
(cplinux)

---

### Post by cplinux on 2009-12-29
I've installed Fedora 12 on the same hardware, rebuilt my raid array and everything works well.
Sorry, i'd have preferred Ubuntu, but if it does not run stable on my hardware, there's no choice.

---

### Post by cplinux on 2010-02-20
Hi!

Finally I found a solution.
The errors come neither from Devede nor from Ubuntu directly. The errors occur due to bad s-ata drivers in the kernel.

In the meantime I've installed Fedora. There the system does not freeze entireley - so the behaviour is better as I can still shutdown or reboot - but the problem stayed.

I've found out that it's due to the drivers in the kernel - a general problem.

2 steps to solve it:

1. Edit your grub configuratino and add **libata.force=noncq** to the kernel line
2. Open a root shell and execute this command to the corresponding harddrives: **hdparm -W0 /dev/sd?** (replace ? by your drive/partition, e.g. sda1)

After a reboot and the final resync everything seems to work as it should!

cplinux

---

