---
title: "Puzzling installation problem"
date: 2012-09-14
forum: Mythbuntu
---

### Post by kmyst01 on 2012-09-14
I've been trying to install Mythbuntu 12.04 on a new system that has a RAID 5 array (fakeraid) and I've run into a rather strange issue.

**Background:**
I wanted to set the box up with encrypted LVM and have the root partition as XFS.  I just can't seem to make it work.  If I use JFS or ext4 everything is lovely.  XFS, however, gives no joy.

**Method:**
1) I boot up from the CD and try out the live cd instead of install.
2) Connect to wireless network.
3) Open up a terminal.
4) sudo apt-get -y install lvm2
5) sudo cryptsetup -y --cipher aes-xts-plain --key-size 512 luksFormat /dev/mapper/nvidia_dgcchii
6) sudo cryptsetup luksOpen /dev/mapper/nvidia_dgcchii raid5_encrypted
7) sudo pvcreate /dev/mapper/raid5_encrypted
8.) sudo vgcreate /dev/mapper/raid5_encrypted media
9) sudo lvcreate -n swap -L 4GB media
10) sudo lvcreate -n root -l 100%FREE media
11) sudo mkswap /dev/media/swap
12 sudo mkfs -t xfs /dev/media/root
13) Run installer for Mythbuntu
14) When I get to the partition segment of the installer I pick Do Something Else
15) I change /dev/media/root to be XFS, don't format, mount as / **(I've also told it to format and ommitted steps 11 & 12)**
16) Pick the location /dev/mapper/nvidia_dgcchii to install GRUB2
17) Proceed with the installation.

Problem:
After it copies all the files and starts the installation the installer immediately crashes.  Going to the terminal and running dmesg produces the following:

```
<snip>
[   41.473469] cfg80211: Regulatory domain changed to country: US
[   41.473470] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   41.473473] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   41.473475] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   41.473477] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.473479] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.473481] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   41.473483] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   52.232012] wlan0: no IPv6 routers present
[  941.433446] XFS (dm-3): Mounting Filesystem
[  941.565068] XFS (dm-3): Ending clean mount
[  942.015484] XFS (dm-3): Mounting Filesystem
[  942.016403] XFS (dm-3): Ending clean mount
[  942.808496] XFS (dm-3): Mounting Filesystem
[  942.809177] XFS (dm-3): Ending clean mount
[  943.132382] XFS (dm-3): Mounting Filesystem
[  943.133040] XFS (dm-3): Ending clean mount
[  943.771371] XFS (dm-3): Mounting Filesystem
[  943.772243] XFS (dm-3): Ending clean mount
[  944.092576] XFS (dm-3): Mounting Filesystem
[  944.093225] XFS (dm-3): Ending clean mount
[  944.402731] NTFS driver 2.1.30 [Flags: R/O MODULE].
[  944.467545] QNX4 filesystem 0.2.3 registered.
[ 1069.319380] XFS (dm-3): Mounting Filesystem
[ 1069.393432] XFS (dm-3): Ending clean mount
[ 1072.395570] Adding 4194300k swap on /dev/mapper/media-swap.  Priority:-1 extents:1 across:4194300k 
[ 1242.333678] XFS (dm-3): metadata I/O error: block 0x2a00 ("xfs_trans_read_buf") error 5 buf count 4096
[ 1242.333904] XFS (dm-3): metadata I/O error: block 0x2a00 ("xfs_trans_read_buf") error 5 buf count 4096
[ 1242.375050] ffff880004273000: a0 66 e0 00 3b 60 59 8c 13 bf 26 25 93 63 f8 14  .f..;`Y...&%.c..
[ 1242.375066] XFS (dm-3): Internal error xfs_da_do_buf(2) at line 2097 of file /build/buildd/linux-3.2.0/fs/xfs/xfs_da_btree.c.  Caller 0xffffffffa032ef21
[ 1242.375071] 
[ 1242.375079] Pid: 13712, comm: python2.7 Not tainted 3.2.0-23-generic #36-Ubuntu
[ 1242.375084] Call Trace:
[ 1242.375219]  [<ffffffffa02fb6bf>] xfs_error_report+0x3f/0x50 [xfs]
[ 1242.375280]  [<ffffffffa032ef21>] ? xfs_da_read_buf+0x21/0x30 [xfs]
[ 1242.375327]  [<ffffffffa02fb72e>] xfs_corruption_error+0x5e/0x90 [xfs]
[ 1242.375384]  [<ffffffffa032ee15>] xfs_da_do_buf+0x585/0x630 [xfs]
[ 1242.375441]  [<ffffffffa032ef21>] ? xfs_da_read_buf+0x21/0x30 [xfs]
[ 1242.375489]  [<ffffffffa030020d>] ? xfs_iget_cache_miss+0xdd/0x230 [xfs]
[ 1242.375546]  [<ffffffffa032ef21>] xfs_da_read_buf+0x21/0x30 [xfs]
[ 1242.375604]  [<ffffffffa0335d4a>] xfs_dir2_leaf_addname+0x28a/0x750 [xfs]
[ 1242.375663]  [<ffffffffa0331ae2>] xfs_dir_createname+0x182/0x1a0 [xfs]
[ 1242.375716]  [<ffffffffa030dd0d>] xfs_create+0x55d/0x680 [xfs]
[ 1242.375765]  [<ffffffffa03040aa>] xfs_vn_mknod+0x7a/0x1a0 [xfs]
[ 1242.375813]  [<ffffffffa0304200>] xfs_vn_create+0x10/0x20 [xfs]
[ 1242.375824]  [<ffffffff811843a4>] vfs_create+0xb4/0x120
[ 1242.375831]  [<ffffffff81185f79>] do_last+0x5c9/0x730
[ 1242.375838]  [<ffffffff81187481>] path_openat+0xd1/0x3f0
[ 1242.375849]  [<ffffffff81318c77>] ? __strncpy_from_user+0x27/0x60
[ 1242.375856]  [<ffffffff811878c2>] do_filp_open+0x42/0xa0
[ 1242.375864]  [<ffffffff81318ce1>] ? strncpy_from_user+0x31/0x40
[ 1242.375871]  [<ffffffff81182c0a>] ? do_getname+0x10a/0x180
[ 1242.375879]  [<ffffffff8165c46e>] ? _raw_spin_lock+0xe/0x20
[ 1242.375887]  [<ffffffff81194b67>] ? alloc_fd+0xf7/0x150
[ 1242.375895]  [<ffffffff81176f6d>] do_sys_open+0xed/0x220
[ 1242.375901]  [<ffffffff811770c0>] sys_open+0x20/0x30
[ 1242.375909]  [<ffffffff81664a82>] system_call_fastpath+0x16/0x1b
[ 1242.375915] XFS (dm-3): Corruption detected. Unmount and run xfs_repair
[ 1242.375927] XFS (dm-3): Internal error xfs_trans_cancel at line 1925 of file /build/buildd/linux-3.2.0/fs/xfs/xfs_trans.c.  Caller 0xffffffffa030da0a
[ 1242.375932] 
[ 1242.375937] Pid: 13712, comm: python2.7 Not tainted 3.2.0-23-generic #36-Ubuntu
[ 1242.375941] Call Trace:
[ 1242.375990]  [<ffffffffa02fb6bf>] xfs_error_report+0x3f/0x50 [xfs]
[ 1242.376017]  [<ffffffffa030da0a>] ? xfs_create+0x25a/0x680 [xfs]
[ 1242.376200]  [<ffffffffa034c7b5>] xfs_trans_cancel+0xe5/0x110 [xfs]
[ 1242.376252]  [<ffffffffa030da0a>] xfs_create+0x25a/0x680 [xfs]
[ 1242.376301]  [<ffffffffa03040aa>] xfs_vn_mknod+0x7a/0x1a0 [xfs]
[ 1242.376350]  [<ffffffffa0304200>] xfs_vn_create+0x10/0x20 [xfs]
[ 1242.376357]  [<ffffffff811843a4>] vfs_create+0xb4/0x120
[ 1242.376364]  [<ffffffff81185f79>] do_last+0x5c9/0x730
[ 1242.376371]  [<ffffffff81187481>] path_openat+0xd1/0x3f0
[ 1242.376379]  [<ffffffff81318c77>] ? __strncpy_from_user+0x27/0x60
[ 1242.376387]  [<ffffffff811878c2>] do_filp_open+0x42/0xa0
[ 1242.376395]  [<ffffffff81318ce1>] ? strncpy_from_user+0x31/0x40
[ 1242.376401]  [<ffffffff81182c0a>] ? do_getname+0x10a/0x180
[ 1242.376408]  [<ffffffff8165c46e>] ? _raw_spin_lock+0xe/0x20
[ 1242.376415]  [<ffffffff81194b67>] ? alloc_fd+0xf7/0x150
[ 1242.376422]  [<ffffffff81176f6d>] do_sys_open+0xed/0x220
[ 1242.376428]  [<ffffffff811770c0>] sys_open+0x20/0x30
[ 1242.376435]  [<ffffffff81664a82>] system_call_fastpath+0x16/0x1b
[ 1242.376445] XFS (dm-3): xfs_do_force_shutdown(0x8) called from line 1926 of file /build/buildd/linux-3.2.0/fs/xfs/xfs_trans.c.  Return address = 0xffffffffa034c7ce
[ 1242.382082] XFS (dm-3): Corruption of in-memory data detected.  Shutting down filesystem
[ 1242.382094] XFS (dm-3): Please umount the filesystem and rectify the problem(s)
[ 1252.192042] XFS (dm-3): xfs_log_force: error 5 returned.
[ 1282.272065] XFS (dm-3): xfs_log_force: error 5 returned.
[ 1312.352051] XFS (dm-3): xfs_log_force: error 5 returned.
```For some reason, as I've said, choosing ext4 or JFS works perfectly fine and the installation goes smoothly.  Granted, I have some more work in the terminal (chroot and pull down lvm2, setup /etc/crypttab, etc.).  I have NO idea why XFS causes the installer to hiccup.

I do know umounting the XFS partition and running xfs_repair makes me remount to replay the journal and I umount again and run xfs_repair again and it goes through cleanly.  I've even tried rerunning the installer again and it bombs with the above dmesg output.  Something seems to be wrong with XFS. 

Does anybody know what the issue may be?  Should I be providing options to mkfs -t xfs??  If XFS is recommended why's it die so horribly in this configuration?  Google has failed me on finding out any information.  I've had a setup like this is the past on Ubuntu Server 10.10 and I know it works, so I assume there is some issue with setting up 12.04 in this manner.  As I noted above, it is happy with JFS and ext4.

Any help/suggestions would be appreciated.  And, yes, I know this configuration isn't exactly default/status quo...but I want it set up this way.  Encrypted LVM appeals to my tinfoil hat tendencies! ;)

---

### Post by opensshd on 2012-09-14
[ 1242.375915] XFS (dm-3): Corruption detected. Unmount and run xfs_repair

xfs_repair

?

---

### Post by kmyst01 on 2012-09-14
Yup, that's the issue.  When it happens you get I/O errors since you can't write to the drive at that point.  Hence, umount and xfs_repair.  After that you can write to the drive but installing causes the issue to happen again...its a vicious cycle. :)

---

### Post by opensshd on 2012-09-14
I can find no help >< Lots of stuff relating to 2.6 kernel on this kinda bug.. but i don't think thats your issue.

Only thing I can think of that might be helpful is this I found of people experiencing similar error msgs:

"The cause of the problem appears to have been growing from from a small xfs partition (2gig) to a large xfs partition (16tb). xfs does not adjust its allocation group size when you grow the file system it will use the size from the original creation one.

I am sure that this may have been preventable if we had of specified the allocation group size when creating the initial partition."

Good luck, got me :|

---

### Post by kmyst01 on 2012-09-14
Hmmm....interesting.  I can find no help as well.  It's just bizarre.  I could accept it if it were a hardware issue like a failing drive....but these are brand new and I've installed the OS a handful of different ways and everything is lovely unless XFS is used.  I'll continue testing, but I'm out of options trying to figure this out.

---

### Post by kmyst01 on 2012-09-14
OK..I decided to go deeper down the rabbit hole.  I removed all logical volumes and volume groups.  Did a pvremove on the LUKS encrypted container, used dmraid and removed the metadata....might be forgetting something else but essentially I undid everything I had done.  Then I rebooted.

Of course my array was gone so I had to go into the RAID setup utility and make a new one.  Boot up the live CD and commenced to install.  When it came to the partition section I chose to manually do it and made / an XFS filesystem. 

It actually installed up to the point of installing grub but the dmesg output was absolutely crammed with XFS problems like above, only limited to the xfs_trans_buff or whatever.  Point being XFS on my array is very very unhappy.  It hates me.

So, I've eliminated LUKS and LVM from the equation....still having an issue.  Not the *same* issue....just related.

---

