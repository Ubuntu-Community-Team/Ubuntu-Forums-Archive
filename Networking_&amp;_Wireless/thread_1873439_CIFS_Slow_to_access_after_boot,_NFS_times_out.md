---
title: "CIFS Slow to access after boot, NFS times out"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by Garibaldi3489 on 2011-11-01
I recently configured a CIFS share and an NFS share on my Ubuntu 10.04.3 Server install as follows in /etc/fstab:
```
10.xxx.xxx.xxx:/mnt/storage/mynfs      /mnt/mynfs        nfs     defaults        0       0             

//10.xxx.xxx.xxx/mycifs       /mnt/mycifs      cifs    defaults,username=myuser,password=mypass,uid=myuid,gid=mygid    0 0
```

At boot-time there are some errors listed for these mounts (even though the IPs are available), but both end up mounted by the time I get to the login shell.
```
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 70446/1463504 files, 5556011/5848320 blocks
/dev/sda1: clean, 212/62248 files, 45287/248832 blocks
init: statd-mounting main process (585) killed by TERM signal^M
mount.nfs: DNS resolution failed for 10.xxx.xxx.xxx: Name or service not known
mount.nfs: DNS resolution failed for 10.xxx.xxx.xxx: Name or service not known
mountall: mount /mnt/mynfs [597] terminated with status 32
mount.nfs: DNS resolution failed for 10.xxx.xxx.xxx: Name or service not known
mountall: mount /mnt/mynfs [620] terminated with status 32
bad user name "myuser"
mountall: mount /mnt/mycifs [598] terminated with status 1
bad user name "myuser"
init: ureadahead-other main process (709) terminated with status 4^M
init: ureadahead-other main process (711) terminated with status 4^M
init: ureadahead-other main process (712) terminated with status 4^M
init: ureadahead-other main process (720) terminated with status 4^M
init: ureadahead-other main process (721) terminated with status 4^M
init: ureadahead-other main process (722) terminated with status 4^M
init: ureadahead-other main process (723) terminated with status 4^M
init: ureadahead-other main process (724) terminated with status 4^M
init: ureadahead-other main process (725) terminated with status 4^M
init: ureadahead-other main process (726) terminated with status 4^M
init: ureadahead-other main process (727) terminated with status 4^M
init: ureadahead-other main process (728) terminated with status 4^M
init: ureadahead-other main process (730) terminated with status 4^M
 * Starting AppArmor profiles       ^[[80G ^M^[[74G[ OK ]
 * Starting web server apache2       ^[[80G ^M^[[74G[ OK ]
.....
```

After logging in, if I try to "ls /mnt/mycifs" it blocks for around 30 seconds before returning the directory listing. Subsequent reads to the mount are fast and normal. An strace of the "ls /mnt/mycifs" is as follows (the line in bold is where it gets stuck):
```
execve("/bin/ls", ["ls", "/mnt/mycifs"], [/* 17 vars */]) = 0
brk(0)                                  = 0x1856000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ffe429b0000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=14556, ...}) = 0
mmap(NULL, 14556, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7ffe429ac000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/librt.so.1", O_RDONLY)       = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220!\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31744, ...}) = 0
mmap(NULL, 2128848, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7ffe4258b000
mprotect(0x7ffe42592000, 2093056, PROT_NONE) = 0
mmap(0x7ffe42791000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7ffe42791000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libselinux.so.1", O_RDONLY)  = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20Y\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=117592, ...}) = 0
mmap(NULL, 2217480, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7ffe4236d000
mprotect(0x7ffe42389000, 2093056, PROT_NONE) = 0
mmap(0x7ffe42588000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b000) = 0x7ffe42588000
mmap(0x7ffe4258a000, 1544, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7ffe4258a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libacl.so.1", O_RDONLY)      = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\35\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31208, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ffe429ab000
mmap(NULL, 2126288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7ffe42165000
mprotect(0x7ffe4216c000, 2093056, PROT_NONE) = 0
mmap(0x7ffe4236b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7ffe4236b000
close(3)                                = 0
....
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
mmap(NULL, 2454, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7ffe4287d000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7ffe4287c000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=256324, ...}) = 0
mmap(NULL, 256324, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7ffe4283d000
close(3)                                = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=65, ws_col=238, ws_xpixel=0, ws_ypixel=0}) = 0
**stat("/mnt/mycifs", {st_mode=S_IFDIR|0777, st_size=0, ...}) = 0**
open("/mnt/mycifs", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 3
fcntl(3, F_GETFD)                       = 0x1 (flags FD_CLOEXEC)
getdents(3, /* 65 entries */, 32768)    = 2432
getdents(3, /* 0 entries */, 32768)     = 0
close(3)                                = 0
fstat(1, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7ffe4283c000
write(1, "xxxxxx.html"..., .....) = 141
close(1)                                = 0
munmap(0x7ffe4283c000, 4096)            = 0
close(2)                                = 0
exit_group(0)                           = ?
```
After trying this ls command on the CIFS mount the following error is posted to dmesg:
```
CIFS VFS: No response for cmd 50 mid 13
```

Similarly, if I try to "ls /mnt/mynfs" it blocks forever, never returning the directory listing. Again, here is the strace output (line where it gets stuck in bold):
```
.....
open("/usr/lib/locale/en_US.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_COLLATE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1170770, ...}) = 0
mmap(NULL, 1170770, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f952e933000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_TIME", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
mmap(NULL, 2454, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f952e932000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f952e931000
close(3)                                = 0
open("/usr/lib/locale/en_US.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en_US.utf8/LC_CTYPE", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=256324, ...}) = 0
mmap(NULL, 256324, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f952e8f2000
close(3)                                = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=65, ws_col=238, ws_xpixel=0, ws_ypixel=0}) = 0
[b]stat("/mnt/mynfs", {st_mode=S_IFDIR|0755, st_size=3896, ...}) = 0
open("/mnt/mynfs", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC[/b]
```

After booting, if I simply "umount /mnt/mycifs && mount /mnt/mycifs" or "umount /mnt/mynfs && ount /mnt/mynfs" then both mounts are completely fine and list directories quickly and normally. It appears that something funny is happening to the mountpoints at boot-time, though the network is accessible and these shares end up getting mounted.

I could resolve this issue by adding some umount/mount commands to /etc/rc.local, but I would like to resolve the source of the problem rather than add that hack if possible. I have also tried adding the _netdev boot option to /etc/fstab with no improved behavior. Any ideas on why this is occuring and what else I can try to debug it?

Thanks

---

