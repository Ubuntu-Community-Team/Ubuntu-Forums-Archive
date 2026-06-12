---
title: "Alsa-driver won't update"
date: 2008-06-20
forum: Multimedia Software
---

### Post by freakwillie on 2008-06-20
[COLOR="Red"][SIZE="3"][EDIT] Nevermind, I figured it out.[/SIZE][/COLOR]

Hello everybody,

So I'm trying to upgrade my alsa-driver to the latest 1.07rc2 version from source and am facing some difficulties.

I proceeded as the following, inspired by a script I found on the forum:

```
tar -xjf alsa-driver-1.0.17rc2.tar.bz2
mkdir -p /usr/src/alsa      
mv alsa-driver-1.0.17rc2 /usr/src/alsa
cd /usr/src/alsa/alsa-driver*
sudo su
./configure --with-cards=hda-intel --prefix=/usr --with-kernel=/lib/modules/2.6.24-19-generic/build
make
make install
```

And then after reboot:

```
sudo su
mkdir /lib/modules/2.6.24-19-generic/kernel/sound/pci/hda/
cp -v /lib/modules/2.6.2*/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.2*/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cp -v /usr/src/alsa/alsa-driver*/modules/* /lib/modules/2.6.2*/kernel/sound/
```

The funny thing is that the alsa-utils and alsa-lib are accused to be 1.0.7rc2 after a simple ./configure, make, make install procedure, while the alsa-driver won't do the same. That's probably due to the fact it already comes with the kernel. I'm very layman to ALSA and all I know is what I learned in my researches trying to make my internal mic work.

Here's some extra info: 

Output of cat /proc/asound/version
```
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun  5 2008 for kernel 2.6.24-19-generic (SMP).
```

alsa-info.sh output:
[http://pastebin.ca/1051795]("http://pastebin.ca/1051795")

I'll gladly post anything else that's needed to help debug the problem.

Thanks in advance for any possible help.

---

### Post by freakwillie on 2008-06-20
Well, yeah... nobody answered. Still I have made some more stuff that I need to post here.

I compiled a new kernel without alsa module, the latest stable release in kernel.org, 2.6.25.7.

Now I get no output for 
```
modprobe -l |grep alsa
```

When I try to make the alsa-driver-1.0.7rc2 after I do a ./configure like the following:
```
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-2.6.25.7-custom/
```

I get a LOT of errors, here is the output:

```
include/linux/kdev_t.h:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sysv_encode_dev’
include/linux/kdev_t.h:80: error: expected ‘)’ before ‘dev’
include/linux/kdev_t.h:85: error: expected ‘)’ before ‘dev’
In file included from include/linux/fs.h:278,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/dcache.h:84: error: expected specifier-qualifier-list before ‘atomic_t’
include/linux/dcache.h:136: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h: In function ‘__d_drop’:
include/linux/dcache.h:202: error: ‘struct dentry’ has no member named ‘d_flags’
include/linux/dcache.h:203: error: ‘struct dentry’ has no member named ‘d_flags’
include/linux/dcache.h:204: error: ‘struct dentry’ has no member named ‘d_hash’
include/linux/dcache.h: In function ‘d_drop’:
include/linux/dcache.h:211: error: ‘struct dentry’ has no member named ‘d_lock’
include/linux/dcache.h:213: error: ‘struct dentry’ has no member named ‘d_lock’
include/linux/dcache.h:214: error: ‘spinlock_t’ has no member named ‘raw_lock’
include/linux/dcache.h: In function ‘dname_external’:
include/linux/dcache.h:219: error: ‘struct dentry’ has no member named ‘d_name’
include/linux/dcache.h:219: error: ‘struct dentry’ has no member named ‘d_iname’
include/linux/dcache.h: At top level:
include/linux/dcache.h:225: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:226: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:227: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:232: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:233: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:234: warning: ‘struct super_block’ declared inside parameter list
include/linux/dcache.h:236: warning: ‘struct super_block’ declared inside parameter list
include/linux/dcache.h:240: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:245: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:246: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h:265: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h: In function ‘d_add’:
include/linux/dcache.h:267: warning: passing argument 2 of ‘d_instantiate’ from incompatible pointer type
include/linux/dcache.h: At top level:
include/linux/dcache.h:279: warning: ‘struct inode’ declared inside parameter list
include/linux/dcache.h: In function ‘d_add_unique’:
include/linux/dcache.h:283: warning: passing argument 2 of ‘d_instantiate_unique’ from incompatible pointer type
include/linux/dcache.h: In function ‘dget’:
include/linux/dcache.h:325: error: ‘struct dentry’ has no member named ‘d_count’
include/linux/dcache.h: In function ‘d_unhashed’:
include/linux/dcache.h:341: error: ‘struct dentry’ has no member named ‘d_flags’
include/linux/dcache.h: In function ‘dget_parent’:
include/linux/dcache.h:348: error: ‘struct dentry’ has no member named ‘d_lock’
include/linux/dcache.h:349: error: ‘struct dentry’ has no member named ‘d_parent’
include/linux/dcache.h:350: error: ‘struct dentry’ has no member named ‘d_lock’
include/linux/dcache.h: In function ‘d_mountpoint’:
include/linux/dcache.h:358: error: ‘struct dentry’ has no member named ‘d_mounted’
In file included from include/linux/fs.h:279,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/namei.h: At top level:
include/linux/namei.h:73: warning: ‘struct inode’ declared inside parameter list
In file included from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fs.h:313: warning: ‘struct inode’ declared inside parameter list
include/linux/fs.h:314: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:315: error: expected declaration specifiers or ‘...’ before ‘ssize_t’
include/linux/fs.h:349: error: expected specifier-qualifier-list before ‘umode_t’
In file included from include/linux/fs.h:368,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/quota.h:44: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qid_t’
include/linux/quota.h:45: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘qsize_t’
include/linux/quota.h:104: error: expected specifier-qualifier-list before ‘__u64’
include/linux/quota.h:125: error: expected specifier-qualifier-list before ‘__u64’
In file included from include/linux/quota.h:167,
                 from include/linux/fs.h:368,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/dqblk_xfs.h:51: error: expected specifier-qualifier-list before ‘__s8’
include/linux/dqblk_xfs.h:138: error: expected specifier-qualifier-list before ‘__u64’
include/linux/dqblk_xfs.h:144: error: expected specifier-qualifier-list before ‘__s8’
In file included from include/linux/fs.h:368,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/quota.h:184: error: expected specifier-qualifier-list before ‘__u32’
include/linux/quota.h:251: error: expected specifier-qualifier-list before ‘atomic_t’
include/linux/quota.h:279: warning: ‘struct inode’ declared inside parameter list
include/linux/quota.h:280: warning: ‘struct inode’ declared inside parameter list
include/linux/quota.h:281: error: expected declaration specifiers or ‘...’ before ‘qsize_t’
include/linux/quota.h:281: warning: ‘struct inode’ declared inside parameter list
include/linux/quota.h:282: warning: ‘struct inode’ declared inside parameter list
include/linux/quota.h:283: error: expected declaration specifiers or ‘...’ before ‘qsize_t’
include/linux/quota.h:283: warning: ‘struct inode’ declared inside parameter list
include/linux/quota.h:284: warning: ‘struct inode’ declared inside parameter list
include/linux/quota.h:285: warning: ‘struct inode’ declared inside parameter list
include/linux/quota.h:300: error: expected declaration specifiers or ‘...’ before ‘qid_t’
include/linux/quota.h:301: error: expected declaration specifiers or ‘...’ before ‘qid_t’
include/linux/quota.h:304: error: expected declaration specifiers or ‘...’ before ‘qid_t’
include/linux/quota.h:305: error: expected declaration specifiers or ‘...’ before ‘qid_t’
In file included from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fs.h:414: error: expected specifier-qualifier-list before ‘size_t’
include/linux/fs.h:418: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_copy_from_user_atomic’
include/linux/fs.h:420: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_copy_from_user’
include/linux/fs.h:422: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:423: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_single_seg_count’
include/linux/fs.h:428: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:428: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h: In function ‘iov_iter_init’:
include/linux/fs.h:432: error: ‘struct iov_iter’ has no member named ‘iov_offset’
include/linux/fs.h:433: error: ‘struct iov_iter’ has no member named ‘count’
include/linux/fs.h:433: error: ‘count’ undeclared (first use in this function)
include/linux/fs.h:433: error: ‘written’ undeclared (first use in this function)
include/linux/fs.h:435: error: too many arguments to function ‘iov_iter_advance’
include/linux/fs.h: At top level:
include/linux/fs.h:438: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iov_iter_count’
include/linux/fs.h:466: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:469: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:476: error: expected specifier-qualifier-list before ‘ssize_t’
include/linux/fs.h:491: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:495: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:524: error: expected specifier-qualifier-list before ‘dev_t’
In file included from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fs.h:585:5: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h:599: error: expected specifier-qualifier-list before ‘atomic_t’
include/linux/fs.h:693: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘i_size_read’
include/linux/fs.h:695:5: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h:704:7: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h:721: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:723:5: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h:727:7: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h: In function ‘i_size_write’:
include/linux/fs.h:732: error: ‘struct inode’ has no member named ‘i_size’
include/linux/fs.h:732: error: ‘i_size’ undeclared (first use in this function)
include/linux/fs.h: In function ‘iminor’:
include/linux/fs.h:738: error: ‘const struct inode’ has no member named ‘i_rdev’
include/linux/fs.h: In function ‘imajor’:
include/linux/fs.h:743: error: ‘const struct inode’ has no member named ‘i_rdev’
include/linux/fs.h: At top level:
include/linux/fs.h:752: error: expected specifier-qualifier-list before ‘uid_t’
include/linux/fs.h:767: error: expected specifier-qualifier-list before ‘loff_t’
include/linux/fs.h:792: error: expected specifier-qualifier-list before ‘atomic_t’
include/linux/fs.h:825:5: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h:827:7: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h:849: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:850: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:851: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:852: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:856: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:857: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:858: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:859: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:860: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:861: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:862: warning: ‘struct file_lock’ declared inside parameter list
include/linux/fs.h:863: warning: ‘struct file_lock’ declared inside parameter list
In file included from include/linux/nfs.h:130,
                 from include/linux/nfs_fs_i.h:6,
                 from include/linux/fs.h:867,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/sunrpc/msg_prot.h:18: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rpc_authflavor_t’
include/linux/sunrpc/msg_prot.h:102: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rpc_fraghdr’
In file included from include/linux/nfs_fs_i.h:6,
                 from include/linux/fs.h:867,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/nfs.h: In function ‘nfs_compare_fh’:
include/linux/nfs.h:148: error: too many arguments to function ‘memcmp’
include/linux/nfs.h: In function ‘nfs_copy_fh’:
include/linux/nfs.h:154: error: too many arguments to function ‘memcpy’
In file included from include/linux/fs.h:867,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/nfs_fs_i.h: At top level:
include/linux/nfs_fs_i.h:14: error: expected specifier-qualifier-list before ‘u32’
In file included from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fs.h:880: error: expected specifier-qualifier-list before ‘loff_t’
In file included from include/linux/fs.h:905,
                 from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fcntl.h:4:23: error: asm/fcntl.h: No such file or directory
include/linux/fcntl.h:49:5: warning: "BITS_PER_LONG" is not defined
In file included from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fs.h:907: warning: ‘struct flock’ declared inside parameter list
include/linux/fs.h:909: warning: ‘struct flock’ declared inside parameter list
In file included from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fs.h:911:5: warning: "BITS_PER_LONG" is not defined
include/linux/fs.h:922: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:923: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:943: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:944: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:966: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘f_getown’
include/linux/fs.h:983: error: expected specifier-qualifier-list before ‘dev_t’
include/linux/fs.h:1080: error: expected declaration specifiers or ‘...’ before ‘dev_t’
include/linux/fs.h:1124: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1124: error: expected declaration specifiers or ‘...’ before ‘u64’
include/linux/fs.h:1133: warning: ‘struct gendisk’ declared inside parameter list
include/linux/fs.h:1134: warning: ‘struct gendisk’ declared inside parameter list
include/linux/fs.h:1149: error: expected specifier-qualifier-list before ‘size_t’
include/linux/fs.h:1173: error: expected specifier-qualifier-list before ‘loff_t’
include/linux/fs.h:1209: error: expected declaration specifiers or ‘...’ before ‘dev_t’
include/linux/fs.h:1219: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:1220: error: expected specifier-qualifier-list before ‘ssize_t’
include/linux/fs.h:1230: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘rw_copy_check_uvector’
include/linux/fs.h:1235: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_read’
include/linux/fs.h:1236: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_write’
include/linux/fs.h:1237: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_readv’
include/linux/fs.h:1239: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_writev’
include/linux/fs.h:1268: error: expected specifier-qualifier-list before ‘ssize_t’
include/linux/fs.h: In function ‘inc_nlink’:
include/linux/fs.h:1361: error: ‘struct inode’ has no member named ‘i_nlink’
include/linux/fs.h: In function ‘drop_nlink’:
include/linux/fs.h:1383: error: ‘struct inode’ has no member named ‘i_nlink’
include/linux/fs.h: In function ‘clear_nlink’:
include/linux/fs.h:1396: error: ‘struct inode’ has no member named ‘i_nlink’
include/linux/fs.h: In function ‘inode_inc_iversion’:
include/linux/fs.h:1415: error: ‘struct inode’ has no member named ‘i_lock’
include/linux/fs.h:1416: error: ‘struct inode’ has no member named ‘i_version’
include/linux/fs.h:1417: error: ‘struct inode’ has no member named ‘i_lock’
include/linux/fs.h: In function ‘file_accessed’:
include/linux/fs.h:1423: error: ‘struct file’ has no member named ‘f_flags’
include/linux/fs.h:1423: error: ‘O_NOATIME’ undeclared (first use in this function)
include/linux/fs.h: At top level:
include/linux/fs.h:1508: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1508: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h: In function ‘__mandatory_lock’:
include/linux/fs.h:1517: error: ‘struct inode’ has no member named ‘i_mode’
include/linux/fs.h: In function ‘mandatory_lock’:
include/linux/fs.h:1527: error: ‘struct inode’ has no member named ‘i_sb’
include/linux/fs.h: At top level:
include/linux/fs.h:1537: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1537: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:1541: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h: In function ‘locks_verify_truncate’:
include/linux/fs.h:1543: error: ‘struct inode’ has no member named ‘i_flock’
include/linux/fs.h:1546: error: ‘size’ undeclared (first use in this function)
include/linux/fs.h:1546: error: ‘struct inode’ has no member named ‘i_size’
include/linux/fs.h:1546: error: ‘struct inode’ has no member named ‘i_size’
include/linux/fs.h:1547: error: ‘struct inode’ has no member named ‘i_size’
include/linux/fs.h:1547: error: ‘struct inode’ has no member named ‘i_size’
include/linux/fs.h:1548: error: ‘struct inode’ has no member named ‘i_size’
include/linux/fs.h:1549: error: too many arguments to function ‘locks_mandatory_area’
include/linux/fs.h: In function ‘break_lease’:
include/linux/fs.h:1555: error: ‘struct inode’ has no member named ‘i_flock’
include/linux/fs.h: At top level:
include/linux/fs.h:1562: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1588: warning: parameter names (without types) in function declaration
include/linux/fs.h:1589: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1592: error: expected ‘)’ before ‘unsigned’
include/linux/fs.h:1605: warning: ‘struct gendisk’ declared inside parameter list
include/linux/fs.h:1607: error: expected declaration specifiers or ‘...’ before ‘mode_t’
include/linux/fs.h:1612: warning: ‘struct gendisk’ declared inside parameter list
include/linux/fs.h:1613: warning: ‘struct gendisk’ declared inside parameter list
include/linux/fs.h:1622: error: expected ‘)’ before ‘*’ token
include/linux/fs.h:1623: error: expected ‘)’ before ‘unsigned’
include/linux/fs.h:1627: error: expected ‘)’ before ‘unsigned’
include/linux/fs.h:1628: error: expected declaration specifiers or ‘...’ before ‘off_t’
include/linux/fs.h:1635: error: expected ‘)’ before ‘char’
include/linux/fs.h:1640: error: expected declaration specifiers or ‘...’ before ‘off_t’
include/linux/fs.h:1645: error: expected declaration specifiers or ‘...’ before ‘umode_t’
include/linux/fs.h:1645: error: expected declaration specifiers or ‘...’ before ‘dev_t’
include/linux/fs.h:1670: warning: ‘struct gendisk’ declared inside parameter list
include/linux/fs.h: In function ‘invalidate_remote_inode’:
include/linux/fs.h:1687: error: ‘struct inode’ has no member named ‘i_mode’
include/linux/fs.h:1687: error: ‘struct inode’ has no member named ‘i_mode’
include/linux/fs.h:1688: error: ‘struct inode’ has no member named ‘i_mode’
include/linux/fs.h:1689: error: ‘struct inode’ has no member named ‘i_mapping’
include/linux/fs.h: At top level:
include/linux/fs.h:1700: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1700: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1704: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1704: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h: In function ‘put_write_access’:
include/linux/fs.h:1726: error: ‘struct inode’ has no member named ‘i_writecount’
include/linux/fs.h: In function ‘allow_write_access’:
include/linux/fs.h:1731: error: ‘struct dentry’ has no member named ‘d_inode’
include/linux/fs.h: At top level:
include/linux/fs.h:1746: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘find_inode_number’
In file included from include/linux/poll.h:11,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/fs.h:1751: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘default_llseek’
include/linux/fs.h:1753: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘vfs_llseek’
include/linux/fs.h:1758: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘iunique’
include/linux/fs.h:1805: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1805: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:1806: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_aio_read’
include/linux/fs.h:1807: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_aio_write’
include/linux/fs.h:1808: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_aio_write_nolock’
include/linux/fs.h:1810: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_direct_write’
include/linux/fs.h:1812: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_buffered_write’
include/linux/fs.h:1814: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_sync_read’
include/linux/fs.h:1815: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘do_sync_write’
include/linux/fs.h:1817: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:1820: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_splice_read’
include/linux/fs.h:1822: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_splice_write’
include/linux/fs.h:1824: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_splice_write_nolock’
include/linux/fs.h:1826: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_splice_sendpage’
include/linux/fs.h:1828: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1829: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:1833: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘no_llseek’
include/linux/fs.h:1834: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_file_llseek’
include/linux/fs.h:1835: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘remote_llseek’
include/linux/fs.h:1847: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1854: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__blockdev_direct_IO’
include/linux/fs.h:1865: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blockdev_direct_IO’
include/linux/fs.h:1874: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blockdev_direct_IO_no_locking’
include/linux/fs.h:1883: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘blockdev_direct_IO_own_locking’
include/linux/fs.h:1909: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1910: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1911: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘inode_get_bytes’
include/linux/fs.h:1912: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1930: warning: parameter names (without types) in function declaration
include/linux/fs.h:1935: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dcache_dir_lseek’
include/linux/fs.h:1949: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1952: error: expected declaration specifiers or ‘...’ before ‘loff_t’
include/linux/fs.h:1956: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘generic_read_dir’
include/linux/fs.h:1965: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_read_from_buffer’
include/linux/fs.h:1982: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘parent_ino’
include/linux/fs.h:2002: error: expected specifier-qualifier-list before ‘ssize_t’
include/linux/fs.h:2009: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:2010: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_transaction_read’
include/linux/fs.h:2014: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h: In function ‘simple_transaction_set’:
include/linux/fs.h:2016: error: ‘struct file’ has no member named ‘private_data’
include/linux/fs.h:2025: error: ‘struct simple_transaction_argresp’ has no member named ‘size’
include/linux/fs.h:2025: error: ‘n’ undeclared (first use in this function)
include/linux/fs.h: At top level:
include/linux/fs.h:2065: error: expected declaration specifiers or ‘...’ before ‘u64’
include/linux/fs.h:2065: error: expected declaration specifiers or ‘...’ before ‘u64’
include/linux/fs.h:2068: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_attr_read’
include/linux/fs.h:2070: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘simple_attr_write’
include/linux/fs.h:2096: error: expected declaration specifiers or ‘...’ before ‘size_t’
include/linux/fs.h:2096: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/poll.h:13:25: error: asm/uaccess.h: No such file or directory
In file included from /usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:26,
                 from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
include/linux/poll.h: In function ‘get_fd_set’:
include/linux/poll.h:95: error: implicit declaration of function ‘copy_from_user’
include/linux/poll.h:95: error: ‘EFAULT’ undeclared (first use in this function)
include/linux/poll.h:97: error: too many arguments to function ‘memset’
include/linux/poll.h: In function ‘set_fd_set’:
include/linux/poll.h:105: error: implicit declaration of function ‘__copy_to_user’
include/linux/poll.h: In function ‘zero_fd_set’:
include/linux/poll.h:112: error: too many arguments to function ‘memset’
include/linux/poll.h: At top level:
include/linux/poll.h:117: error: expected declaration specifiers or ‘...’ before ‘s64’
include/linux/poll.h:119: error: expected declaration specifiers or ‘...’ before ‘s64’
include/linux/poll.h:119: warning: ‘struct pollfd’ declared inside parameter list
In file included from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:32:
/usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:32: error: expected declaration specifiers or ‘...’ before ‘loff_t’
/usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/hwdep.h:33: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from /usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:33:
/usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/info.h:71: error: expected specifier-qualifier-list before ‘mode_t’
/usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/info.h: In function ‘snd_info_set_text_ops’:
/usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/info.h:138: error: ‘struct snd_info_entry’ has no member named ‘private_data’
/usr/src/alsa/alsa-driver-1.0.17rc2/include/sound/info.h:139: error: ‘struct snd_info_entry’ has no member named ‘c’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: At top level:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: unknown field ‘count’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: implicit declaration of function ‘ATOMIC_INIT’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: (near initialization for ‘register_mutex’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: unknown field ‘wait_lock’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: unknown field ‘raw_lock’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: ‘__RAW_SPIN_LOCK_UNLOCKED’ undeclared here (not in a function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: (near initialization for ‘(anonymous)’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: (near initialization for ‘register_mutex’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: unknown field ‘wait_list’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: extra brace group at end of initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: (near initialization for ‘register_mutex’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: ‘struct mutex’ has no member named ‘wait_list’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: error: ‘struct mutex’ has no member named ‘wait_list’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:40: warning: (near initialization for ‘register_mutex’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:58: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘snd_hwdep_llseek’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:66: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘snd_hwdep_read’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:75: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘snd_hwdep_write’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_open’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:100: error: ‘ENXIO’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:102: error: ‘ENODEV’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:108: error: ‘EFAULT’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:110: error: ‘current’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:115: error: ‘EBUSY’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:121: error: ‘EAGAIN’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:122: error: ‘struct file’ has no member named ‘f_flags’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:122: error: ‘O_NONBLOCK’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:128: error: implicit declaration of function ‘set_mb’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:141: error: ‘struct file’ has no member named ‘private_data’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_release’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:156: error: ‘ENXIO’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:157: error: ‘struct file’ has no member named ‘private_data’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_poll’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:175: error: ‘struct file’ has no member named ‘private_data’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_info’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:186: error: too many arguments to function ‘memset’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:191: error: implicit declaration of function ‘copy_to_user’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:192: error: ‘EFAULT’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_dsp_status’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:203: error: ‘ENXIO’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:204: error: too many arguments to function ‘memset’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:209: error: ‘EFAULT’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_dsp_load’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:220: error: ‘ENXIO’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:221: error: too many arguments to function ‘memset’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:223: error: ‘EFAULT’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:226: error: ‘EBUSY’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:227: error: implicit declaration of function ‘access_ok’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:227: error: ‘VERIFY_READ’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:227: error: ‘struct snd_hwdep_dsp_image’ has no member named ‘length’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_ioctl’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:239: error: ‘struct file’ has no member named ‘private_data’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:243: error: implicit declaration of function ‘put_user’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:253: error: ‘ENOTTY’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_mmap’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:258: error: ‘struct file’ has no member named ‘private_data’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:261: error: ‘ENXIO’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_control_ioctl’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:273: error: implicit declaration of function ‘get_user’
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:274: error: ‘EFAULT’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:302: error: ‘ENXIO’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: At top level:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:338: error: unknown field ‘llseek’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:338: error: ‘snd_hwdep_llseek’ undeclared here (not in a function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:338: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:338: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:339: error: unknown field ‘read’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:339: error: ‘snd_hwdep_read’ undeclared here (not in a function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:339: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:339: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:340: error: unknown field ‘write’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:340: error: ‘snd_hwdep_write’ undeclared here (not in a function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:340: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:340: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:341: error: unknown field ‘open’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:341: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:341: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:342: error: unknown field ‘release’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:342: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:342: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:343: error: unknown field ‘poll’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:343: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:343: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:348: error: unknown field ‘ioctl’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:348: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:348: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:350: error: unknown field ‘mmap’ specified in initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:350: warning: excess elements in struct initializer
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:350: warning: (near initialization for ‘snd_hwdep_f_ops’)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_new’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:380: warning: assignment makes pointer from integer without a cast
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:383: error: ‘ENOMEM’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_dev_register’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:426: error: ‘EBUSY’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_dev_disconnect’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:468: error: ‘EINVAL’ undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c: In function ‘snd_hwdep_proc_init’:
/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.c:504: error: ‘struct snd_info_entry’ has no member named ‘c’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.17rc2/acore/hwdep.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.17rc2/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.17rc2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.25.7-custom'
make: *** [compile] Error 2

```

I apologize for the huge amount of debugging, but I have no idea how to interpretate that.

---

### Post by xc3RnbFO8P on 2008-06-20
How?

---

### Post by freakwillie on 2008-06-20
I ran the ./configure without the --with-kernel option, I think that's for kernels with ALSA already on it.

---

