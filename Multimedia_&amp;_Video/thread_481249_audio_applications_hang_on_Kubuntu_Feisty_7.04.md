---
title: "audio applications hang on Kubuntu Feisty 7.04"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by devicerandom on 2007-06-22
Hi,
I got a trouble with most audio applications on a Kubuntu Feisty box (fresh installed, no upgrade).

Basically, after a first time in which they seemed to work, they just hang. Firefox + Flash content with audio hangs. amaroK = hangs. I reproduced the error with the simple *aplay* trying to play an Ogg file. It hangs.

Turning off or on aRTs has no effect.

Below it is the final part of strace output on aplay:

---

close(3)                                = 0
munmap(0xb7bd1000, 76344)               = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=76344, ...}) = 0
mmap2(NULL, 76344, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7bd1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_nis.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=34352, ...}) = 0
mmap2(NULL, 37436, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ba7000
mmap2(0xb7baf000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7) = 0xb7baf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38416, ...}) = 0
mmap2(NULL, 41624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b9c000
mmap2(0xb7ba5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb7ba5000
close(3)                                = 0
munmap(0xb7bd1000, 76344)               = 0
open("/etc/group", O_RDONLY)            = 3
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
_llseek(3, 0, [0], SEEK_CUR)            = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=887, ...}) = 0
mmap2(NULL, 887, PROT_READ, MAP_SHARED, 3, 0) = 0xb7f41000
_llseek(3, 887, [887], SEEK_SET)        = 0
munmap(0xb7f41000, 887)                 = 0
close(3)                                = 0
open("/dev/snd/controlC0", O_RDONLY)    = 3
close(3)                                = 0
semget(5678293, 1, IPC_CREAT|0660)      = 1933313
semctl(1933313, 0, IPC_64|IPC_STAT, 0xbfcb52e8 ) = 0
semctl(1933313, 0, IPC_64|IPC_SET, 0xbfcb52e8 ) = -1 EPERM (Operation not permitted)
semop(1933313, 0xbfcb53be, 2          **<--it hangs here**

----

Also, here's all lspci output:


00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]

---

Any hint at understanding the problem is highly appreciated! :D

m.

---

### Post by devicerandom on 2007-06-25
Bump. (I hate to bump, usually, but... I promise I won't abuse)

---

### Post by icewater on 2007-08-16
i get this same error.  i'm not on kubuntu, just ubuntu with gnome.  feisty.

---

### Post by djgrant on 2008-02-14
I'm getting this as well. I have just switched to Ubuntu from Kubuntu and my audio was working this morning but now it is not and my strace looks the same.

---

