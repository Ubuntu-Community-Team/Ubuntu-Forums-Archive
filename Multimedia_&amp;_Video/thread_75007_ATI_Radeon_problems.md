---
title: "ATI Radeon problems"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by kimmoi on 2005-10-13
I used to have Debian "etch" but moved to ubuntu because of better support(IMHO). I just installed breezy 5.1 and got everything else working fine but DRI freezes X. this also happens with the default kernel driver and fglrx

so I have to use
Option "no_dri" "yes"

this is the only way X doesn't freeze and I can use my computer.
everything used to work under debian "etch" or "sarge"

with Option "no_dri" "no" fglrxinfo shows everythink ok but X freezes very frequently and I have to hardboot. without the fglrx driver this happens when opengl kicks in.

any suggestions what to do? I think I have tried every option imaginable.

some info:
AMD Athlon XP2400+
512Mb Ram
Radeon 8500LE (R200)

I can post all logs if needed. just pm or mail me
edit: yes I did read those posts from other forums btw. and tried that dri fix etc..

---

### Post by Burnerman_X on 2005-10-13
same here ;(
X freezes here too

Radeon 8500LE too ;(

I "solved" it changing the driver "flglrx" to "vesa" =/

---

### Post by jarrett.wold on 2005-10-13
I have a Radeon 7000/VE (RV100 Chipset), it appears that gl is broken.  DRI appears to load and work properly.  However, my experience in this is minimal.  

```

$ export MESA_DEBUG=1
$ glxgears
cpu vendor: AuthenticAMD
cpu name: AMD Duron(tm) Processor
MMX cpu detected.
3DNow! cpu detected.
Mesa warning: couldn't open libtxc_dxtn.so, software DXTn compression/decompression unavailable
Illegal instruction

```

The strace isn't much more enlightening:

```

$ strace glxgears
execve("/usr/bin/glxgears", ["glxgears"], [/* 31 vars */]) = 0
uname({sys="Linux", node="ubuntu", ...}) = 0
brk(0)                                  = 0x804d000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7efa000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ef9000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ef8000
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=60490, ...}) = 0
old_mmap(NULL, 60490, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7ee9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGL.so.1", O_RDONLY)   = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260*\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=407720, ...}) = 0
old_mmap(NULL, 415988, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e83000
old_mmap(0xb7ee2000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5e000) = 0xb7ee2000
old_mmap(0xb7ee8000, 2292, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7ee8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGLU.so.1", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240#\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=483084, ...}) = 0
old_mmap(NULL, 481888, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e0d000
old_mmap(0xb7e82000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x75000) = 0xb7e82000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libglut.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\245\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=167540, ...}) = 0
old_mmap(NULL, 166692, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7de4000
old_mmap(0xb7e07000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23000) = 0xb7e07000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@3\0\000"..., 512) = 512fstat64(3, {st_mode=S_IFREG|0644, st_size=136720, ...}) = 0
old_mmap(NULL, 139152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7dc2000
old_mmap(0xb7de3000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x20000) = 0xb7de3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220O\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1226096, ...}) = 0
old_mmap(NULL, 1236380, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c94000
old_mmap(0xb7dbc000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x127000) = 0xb7dbc000
old_mmap(0xb7dc0000, 7580, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7dc0000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libX11.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\r\1"..., 512) = 512fstat64(3, {st_mode=S_IFREG|0644, st_size=780384, ...}) = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c93000
old_mmap(NULL, 784476, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bd3000
old_mmap(0xb7c90000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xbc000) = 0xb7c90000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXext.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p&\0\000"..., 512) = 512fstat64(3, {st_mode=S_IFREG|0644, st_size=51908, ...}) = 0
old_mmap(NULL, 51068, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bc6000
old_mmap(0xb7bd2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc000) = 0xb7bd2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200H\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=86676, ...}) = 0
old_mmap(NULL, 71160, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bb4000
old_mmap(0xb7bc3000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe000) = 0xb7bc3000
old_mmap(0xb7bc4000, 5624, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7bc4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXxf86vm.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\v\0"..., 512) = 512fstat64(3, {st_mode=S_IFREG|0644, st_size=15872, ...}) = 0
old_mmap(NULL, 18816, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7baf000
old_mmap(0xb7bb3000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0xb7bb3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\v\0"..., 512) = 512fstat64(3, {st_mode=S_IFREG|0644, st_size=8252, ...}) = 0
old_mmap(NULL, 11064, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bac000
old_mmap(0xb7bae000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb7bae000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdrm.so.1", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\33"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=23032, ...}) = 0
old_mmap(NULL, 27112, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ba5000
old_mmap(0xb7bab000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5000) = 0xb7bab000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\304"..., 512) = 512fstat64(3, {st_mode=S_IFREG|0644, st_size=919540, ...}) = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ba4000
old_mmap(NULL, 941944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7abe000
old_mmap(0xb7b9a000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xdc000) = 0xb7b9a000
old_mmap(0xb7b9f000, 20344, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7b9f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\30\0"..., 512) = 512fstat64(3, {st_mode=S_IFREG|0644, st_size=40764, ...}) = 0
old_mmap(NULL, 43912, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ab3000
old_mmap(0xb7abd000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9000) = 0xb7abd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXau.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\f\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=7648, ...}) = 0
old_mmap(NULL, 10640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ab0000
old_mmap(0xb7ab2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb7ab2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\17"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9636, ...}) = 0
old_mmap(NULL, 12664, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7aac000
old_mmap(0xb7aaf000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0xb7aaf000
close(3)                                = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7aab000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7aaa000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7aaa6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
munmap(0xb7ee9000, 60490)               = 0
set_tid_address(0xb7aaa708)             = 7485
rt_sigaction(SIGRTMIN, {0xb7bb83d0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7bb8450, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
_sysctl({{CTL_KERN, KERN_VERSION, 0, 20d91, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0}, 2, 0xbf80e9dc, 31, (nil), 0}) = 0
brk(0)                                  = 0x804d000
brk(0x806e000)                          = 0x806e000
uname({sys="Linux", node="ubuntu", ...}) = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
uname({sys="Linux", node="ubuntu", ...}) = 0
uname({sys="Linux", node="ubuntu", ...}) = 0
connect(3, {sa_family=AF_FILE, path="/tmp/.X11-unix/X0"}, 19) = 0
uname({sys="Linux", node="ubuntu", ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
access("/home/jarrettwold/.Xauthority", R_OK) = 0
open("/home/jarrettwold/.Xauthority", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0600, st_size=117, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ef7000
read(4, "\1\0\0\6ubuntu\0\0010\0\22MIT-MAGIC-COOKIE-"..., 4096) = 117
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7ef7000, 4096)                = 0
writev(3, [{"l\0\v\0\0\0\22\0\20\0\0\0", 12}, {"MIT-MAGIC-COOKIE-1", 18}, {"\0\0", 2}, {"\22P\275\17;Y\17\313t\r\244\242\16VC\373", 16}], 4) = 48
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
read(3, "\1\0\v\0\0\0\223\0", 8)        = 8
read(3, "\320\303\237\3\0\0`\3\377\377\37\0\0\1\0\0\24\0\377\377"..., 588) = 588write(3, "7\0\5\0\0\0`\3H\0\0\0\10\0\0\0\377\377\377\0b\0\5\0\f\0"..., 64) = 64
read(3, "\1\0\2\0\0\0\0\0\1\203\0\0\24\0\0\0\24\0\0\0\0\0\0\0\254"..., 32) = 32
read(3, "\1\10\3\0\214\6\0\0\37\0\0\0\0\0\0\0000\32\0\0\30\0\0\0"..., 32) = 32
readv(3, [{"*Box.background:\t#efebe7\n*Box.fo"..., 6704}, {"", 0}], 2) = 6704
write(3, "\203\0\1\0", 4)               = 4
read(3, "\1\0\4\0\0\0\0\0\377\377?\0\4\0\0\0\4\0\0\0\0\0\0\0\300"..., 32) = 32
writev(3, [{"b\0\5\0\t\0`\3", 8}, {"XKEYBOARD", 9}, {"\0\0\0", 3}], 3) = 20
read(3, "\1\0\5\0\0\0\0\0\1\225n\257\24\0\0\0\24\0\0\0\0\0\0\0\300"..., 32) = 32write(3, "\225\0\2\0\1\0\0\0", 8)       = 8
read(3, "\1\1\6\0\0\0\0\0\1\0\0\0\0\0\0\0\10\0\0\0\10\0\0\0\0\0"..., 32) = 32
writev(3, [{"b\0\3\0\3\0\0\0", 8}, {"GLX", 3}, {"\0", 1}], 3) = 12
read(3, "\1\0\7\0\0\0\0\0\1\220M\234\f\0\0\0\f\0\0\0\0\0\0\0\324"..., 32) = 32
write(3, "\220\7\3\0\1\0\0\0\4\0\0\0", 12) = 12
read(3, "\1\300\10\0\0\0\0\0\1\0\0\0\2\0\0\0<\0\0\0P`\242\10\350"..., 32) = 32
writev(3, [{"b\7\5\0\v\0\0\0", 8}, {"XFree86-DRI", 11}, {"\0", 1}], 3) = 20
read(3, "\1\0\t\0\0\0\0\0\1\200\0\200\24\0\0\0\24\0\0\0\0\0\0\0"..., 32) = 32
write(3, "\200\0\1\0", 4)               = 4
read(3, "\1\0\n\0\0\0\0\0\4\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(3, "\200\1\2\0\0\0\0\0", 8)       = 8
read(3, "\1\352\v\0\0\0\0\0\1\300\253\10#\215\345\267\0\0\0\0\204"..., 32) = 32
write(3, "\200\4\2\0\0\0\0\0", 8)       = 8
read(3, "\1\352\f\0\2\0\0\0\4\0\0\0\0\0\0\0\1\0\0\0\6\0\0\0\"\0"..., 32) = 32
readv(3, [{"radeon", 6}, {"\0\0", 2}], 2) = 8
geteuid32()                             = 1000
getuid32()                              = 1000
futex(0xb7baeb34, FUTEX_WAKE, 2147483647) = 0
open("/usr/lib/dri/radeon_dri.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \355\1"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=2263736, ...}) = 0
old_mmap(NULL, 2406892, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb785e000
old_mmap(0xb7a70000, 98304, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x211000) = 0xb7a70000
old_mmap(0xb7a88000, 137708, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7a88000
mprotect(0xbf80e000, 4096, PROT_READ|PROT_WRITE|PROT_EXEC|PROT_GROWSDOWN) = 0
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=60490, ...}) = 0
old_mmap(NULL, 60490, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7ee9000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libexpat.so.1", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\"\0"..., 512) = 512fstat64(4, {st_mode=S_IFREG|0644, st_size=125168, ...}) = 0
old_mmap(NULL, 124076, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb783f000
old_mmap(0xb785b000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1c000) = 0xb785b000
close(4)                                = 0
mprotect(0xb785e000, 2170880, PROT_READ|PROT_WRITE) = 0
mprotect(0xb785e000, 2170880, PROT_READ|PROT_EXEC) = 0
munmap(0xb7ee9000, 60490)               = 0
write(3, "\220\23\3\0\0\0\0\0\2\0\0\0", 12) = 12
read(3, "\1\0\r\0\1\0\0\0\0\0\0\0\4\0\0\0\0\20\0\0\10\300\253\10"..., 32) = 32
read(3, "1.2\0", 4)                     = 4
write(3, "\220\23\3\0\0\0\0\0\3\0\0\0", 12) = 12
read(3, "\1\0\16\0+\0\0\0\0\0\0\0\253\0\0\0\0\20\0\0\10\300\253"..., 32) = 32
read(3, "GLX_ARB_multisample GLX_EXT_visu"..., 171) = 171
read(3, "\10", 1)                       = 1
write(3, "\220\21\4\0\4\0\1\0\3\0\0\0\0\0\0\0", 16) = 16
read(3, "\1\0\17\0\300\1\0\0\20\0\0\0\34\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(3, "\v\200\0\0#\0\0\0\23\200\0\0#\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0$\0\0\0\23\200\0\0$\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0%\0\0\0\23\200\0\0%\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0&\0\0\0\23\200\0\0&\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0\'\0\0\0\23\200\0\0\'\0\0\0\22\200\0\0\1\0\0"..., 224) = 224
read(3, "\v\200\0\0(\0\0\0\23\200\0\0(\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0)\0\0\0\23\200\0\0)\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0*\0\0\0\23\200\0\0*\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0+\0\0\0\23\200\0\0+\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0,\0\0\0\23\200\0\0,\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0-\0\0\0\23\200\0\0-\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0.\0\0\0\23\200\0\0.\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0/\0\0\0\23\200\0\0/\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0000\0\0\0\23\200\0\0000\0\0\0\22\200\0\0\1\0"..., 224) = 224
read(3, "\v\200\0\0001\0\0\0\23\200\0\0001\0\0\0\22\200\0\0\1\0"..., 224) = 224
read(3, "\v\200\0\0002\0\0\0\23\200\0\0002\0\0\0\22\200\0\0\1\0"..., 224) = 224
write(3, "\200\2\2\0\0\0\0\0", 8)       = 8
read(3, "\1\352\20\0\4\0\0\0\0\340\272\360\0\0\0\0\20\0\0\0\204"..., 32) = 32
readv(3, [{"pci:0000:01:00.0", 16}, {"", 0}], 2) = 16
geteuid32()                             = 1000
stat64("/dev/dri", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
stat64("/dev/dri/card0", {st_mode=S_IFCHR|0660, st_rdev=makedev(226, 0), ...}) = 0
open("/dev/dri/card0", O_RDWR)          = 4
ioctl(4, DECODER_SET_PICTURE, 0xbf80e450) = -1 EACCES (Permission denied)
ioctl(4, DECODER_GET_CAPABILITIES, 0xbf80e454) = 0
ioctl(4, DECODER_GET_CAPABILITIES, 0xbf80e454) = 0
ioctl(4, DECODER_GET_STATUS or DEVFSDIOC_SET_EVENT_MASK, 0xbf80e76c) = 0
ioctl(4, DEVFSDIOC_GET_PROTO_REV, 0x8054ed0) = 0
ioctl(4, DEVFSDIOC_GET_PROTO_REV, 0x8054ed0) = 0
write(3, "\200\v\3\0\0\0\0\0\6\0\0\0", 12) = 12
read(3, "\1\352\21\0\0\0\0\0\1\0\0\0#\215\345\267\0\0\0\0\204>\16"..., 32) = 32
write(3, "\200\4\2\0\0\0\0\0", 8)       = 8
read(3, "\1\352\22\0\2\0\0\0\4\0\0\0\0\0\0\0\1\0\0\0\6\0\0\0\"\0"..., 32) = 32
readv(3, [{"radeon", 6}, {"00", 2}], 2) = 8
write(3, "\200\n\2\0\0\0\0\0", 8)       = 8
read(3, "\1\352\23\0\31\0\0\0\0\0\0\210\0\0\0\0\0\0\0\0\0\0\0\4"..., 32) = 32
read(3, "YQ\0\0\0\5\0\0\0\4\0\0\30\0\0\0 \0\0\0\0\0\0\0\1\0\0\0"..., 100) = 100
mmap2(NULL, 67108864, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0x88000) = 0xb383f000mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0xf0bae) = 0xb383d000
ioctl(4, 0xc0086451, 0xbf80e6a4)        = 0
ioctl(4, 0xc0086451, 0xbf80e6a4)        = 0
mmap2(NULL, 524288, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0x80000) = 0xb37bd000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0x90101) = 0xb37bc000
ioctl(4, 0xc00c6419, 0xbf80e640)        = 0
ioctl(4, 0xc00c6419, 0xbf80e640)        = 0
mmap2(NULL, 5111808, PROT_READ|PROT_WRITE, MAP_SHARED, 4, 0x90302) = 0xb30dc000
ioctl(4, 0x400c6459, 0xbf80e698)        = 0
futex(0xb7ee8784, FUTEX_WAKE, 2147483647) = 0
mmap2(NULL, 266240, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb309b000
write(3, "\220\24\371\2\1\0\0\0\4\0\0\0\322\v\0\0GL_ARB_depth_te"..., 3360) = 3360
read(3, "\1\352\33\0\0\0\0\0\3\0\0\0p\334\252\10(\0\0\0)\0\0\0 "..., 32) = 32
open("/etc/drirc", O_RDONLY)            = -1 ENOENT (No such file or directory)
open("/home/jarrettwold/.drirc", O_RDONLY) = -1 ENOENT (No such file or directory)
brk(0x8098000)                          = 0x8098000
write(2, "cpu vendor: ", 12cpu vendor: )            = 12
write(2, "AuthenticAMD", 12AuthenticAMD)            = 12
write(2, "\n", 1
)                       = 1
write(2, "cpu name: ", 10cpu name: )              = 10
write(2, "AMD Duron(tm) Processor", 23AMD Duron(tm) Processor) = 23
write(2, "\n", 1
)                       = 1
write(2, "MMX cpu detected.\n", 18MMX cpu detected.
)     = 18
write(2, "3DNow! cpu detected.\n", 213DNow! cpu detected.
)  = 21
open("/etc/ld.so.cache", O_RDONLY)      = 5
fstat64(5, {st_mode=S_IFREG|0644, st_size=60490, ...}) = 0
old_mmap(NULL, 60490, PROT_READ, MAP_PRIVATE, 5, 0) = 0xb308c000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/cmov", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/tls/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/tls/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/cmov", 0xbf80e044)     = -1 ENOENT (No such file or directory)
open("/lib/tls/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/cmov", 0xbf80e044)    = -1 ENOENT (No such file or directory)
open("/lib/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686", 0xbf80e044)         = -1 ENOENT (No such file or directory)
open("/lib/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/cmov", 0xbf80e044)         = -1 ENOENT (No such file or directory)
open("/lib/libtxc_dxtn.so", O_RDONLY)   = -1 ENOENT (No such file or directory)
stat64("/lib", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
open("/usr/lib/tls/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls", 0xbf80e044)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/cmov", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/cmov", 0xbf80e044)     = -1 ENOENT (No such file or directory)
open("/usr/lib/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib", {st_mode=S_IFDIR|0755, st_size=45056, ...}) = 0
open("/usr/lib/i486-linux-gnu/tls/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/i686", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/tls/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/tls", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/i686", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/usr/lib/i486-linux-gnu/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i486-linux-gnu", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/i686", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/tls/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/tls", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/i686/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/i686", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/cmov/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu/cmov", 0xbf80e044) = -1 ENOENT (No such file or directory)
open("/lib/i486-linux-gnu/libtxc_dxtn.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i486-linux-gnu", 0xbf80e044) = -1 ENOENT (No such file or directory)
munmap(0xb308c000, 60490)               = 0
write(2, "Mesa warning: couldn\'t open libt"..., 96Mesa warning: couldn't open libtxc_dxtn.so, software DXTn compression/decompression unavailable
) = 96
mmap2(NULL, 806912, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb2fd6000
brk(0x80b9000)                          = 0x80b9000
brk(0x80dd000)                          = 0x80dd000
brk(0x8100000)                          = 0x8100000
brk(0x8123000)                          = 0x8123000
brk(0x8144000)                          = 0x8144000
brk(0x8167000)                          = 0x8167000
brk(0x818a000)                          = 0x818a000
brk(0x81ae000)                          = 0x81ae000
brk(0x81d1000)                          = 0x81d1000
brk(0x81f4000)                          = 0x81f4000
brk(0x8217000)                          = 0x8217000
mmap2(NULL, 184320, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb2fa9000
gettimeofday({1129227205, 752332}, NULL) = 0
write(3, "\220\3\6\0\4\0`\3\'\0\0\0\0\0\0\0\0\0\0\0\1B_d\10p\2\0"..., 44) = 44
read(3, "\1\352\36\0\0\0\0\0\0\0\0\0\4\0`\3\0\0\0\0\'\0\0\0\0\0"..., 32) = 32
write(3, "\200\t\3\0\0\0\0\0\2\0`\3", 12) = 12
read(3, "\25\337\36\0\2\0`\3\2\0`\3\2404\300\0\0\0\0\0\0\337\216"..., 32) = 32
read(3, "\26\0\36\0\2\0`\3\2\0`\3\0\0\0\0\4\0\27\0,\1,\1\0\0\0\0"..., 32) = 32
read(3, "\23\352\36\0\2\0`\3\2\0`\3\0\0\0\0\230\352\223\277\217"..., 32) = 32
read(3, "\f=\36\0\2\0`\3\0\0\0\0,\1,\1\0\0W\10\4\0000\0000\0\0\0"..., 32) = 32
read(3, "\1\352\37\0\5\0\0\0\0\0\0\0\7\5\0\0\4\0000\0,\1,\1\1\0"..., 32) = 32
read(3, "\1\0\0\0", 4)                  = 4
read(3, "\4\0000\0000\1\\\1", 8)        = 8
read(3, "\4\0000\0000\1\\\1", 8)        = 8
futex(0xb7ee7470, FUTEX_WAKE, 2147483647) = 0
ioctl(4, 0x4008642a, 0xbf80ea14)        = 0
ioctl(3, FIONREAD, [0])                 = 0
gettimeofday({1129227206, 26902}, {300, 0}) = 0
--- SIGILL (Illegal instruction) @ 0 (0) ---
+++ killed by SIGILL +++

```

---

### Post by kimmoi on 2005-10-14
not happy.
using radeon without acceleration ;(
maybe I should by a new card but why?

---

### Post by jarrett.wold on 2005-10-14
I've been pining around and seeing a ton of info regarding similar breakage with kernel 2.4.20.

Some random stuff in the mailing list entries I can't verify (Duron 750):

export MESA_NO_3DNOW='Y'

If you running intel x86.  Run glxgears again.  If that works, it's some obscure thing about the lib's trying to render 3DNow code on an Intel processor.

If it doesn't work:

unset MESA_NO_3DNOW

It would be nice if there was a way (sans excessive debugging) to figure out if this breakage is due to DRI or Mesa. 

I'll keep digging.

---

### Post by sebseb on 2005-10-14
I get the same here 'illegal instruction' error on a 700mhz K7 + Matrox G400, and filed a bugreport: [https://bugzilla.ubuntu.com/show_bug.cgi?id=17379](https://bugzilla.ubuntu.com/show_bug.cgi?id=17379)

It seems to be an AMD-only problem, right?

Oh btw, I tried booting an plain 386 kernel and the problem persisted.

---

### Post by Golgoth on 2005-10-14
Hi,

First, sorry for my english! I'm french...

I don't know if it is the same problem: X freezes...

some info:
Mobility Radeon 9600
driver fglrx "made in ubuntu" (8.16.20)
agp chipset: intel
proc: Intel P4

I have freeze only when I use Firefox or an other browser on some websites. It's random: immediatly or after several try but always on the same websites...

I thought it was firefox, but try epiphany... and still freezing
I thought it was gecko but try opera... and still freezing

I completly reinstall my breezy and I don't have any freeze with the "ati" driver.

Since I reinstall the "fglrx" to play to enemy territory, I have again a freezy badger...

---

### Post by jarrett.wold on 2005-10-15
I've cc'd in bugzilla.  If anyone wants more details, tell me what you want run and I'll provide the data.

---

### Post by SilverTab on 2005-10-15
[QUOTE=Golgoth]Hi,

First, sorry for my english! I'm french...

I don't know if it is the same problem: X freezes...

some info:
Mobility Radeon 9600
driver fglrx "made in ubuntu" (8.16.20)
agp chipset: intel
proc: Intel P4

I have freeze only when I use Firefox or an other browser on some websites. It's random: immediatly or after several try but always on the same websites...

I thought it was firefox, but try epiphany... and still freezing
I thought it was gecko but try opera... and still freezing

I completly reinstall my breezy and I don't have any freeze with the "ati" driver.

Since I reinstall the "fglrx" to play to enemy territory, I have again a freezy badger...[/QUOTE]


mm so you are able to get the ATI drivers to work with the 9600?? Damn...seems like the 9550 is the only one with no fixed yet...I thought 9600 had the same problems...

BTW: the freezy badger joke was hillarious...I spilled my coke on the keyboard...no kidding...

---

### Post by Golgoth on 2005-10-15
[QUOTE=Burnerman_X]same here ;(
X freezes here too

Radeon 8500LE too ;(

I "solved" it changing the driver "flglrx" to "vesa" =/[/QUOTE]

The owners of these GPU: 

R100
    Radeon 7200
RV100
    Radeon 7000(VE), M6
RS100
    Radeon IGP320(M)
RV200
    Radeon 7500, M7, FireGL 7800
RS200
    Radeon IGP330(M)/IGP340(M)
RS250
    Radeon Mobility 7000 IGP
R200
    Radeon 8500, 9100, FireGL 8800/8700
RV250
    Radeon 9000PRO/9000, M9
RS300
    Radeon 9100 IGP
RS350
    Radeon 9200 IGP
RV280
    Radeon 9200PRO/9200/9200SE, M9+

should use the "radeon" driver instead of the "fglrx".
It supports 3D rendering...

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo gedit /etc/X11/xorg.conf

In module section, add:
Section "Extensions"
 Option "RENDER" "Enable" 
EndSection

In device section replace "ati" by "radeon" and add these option...

Driver           "radeon"
Option          "AGPMode" "4"
Option         "AGPSize" "64" # default: 8
Option         "RingSize" "8"
Option         "BufferSize" "2"
Option         "EnablePageFlip" "true"
Option         "EnableDepthMoves" "true"
Option         "RenderAccel" "true"

hope it will help

---

### Post by hiruzzolo on 2005-10-17
Hi! I have the same problem and I have a Radeon 7000/VE (RV100 Chipset)! In breezy I tried the last advice about radeon driver but it didn't worked! I had this problem also in hoary and it is very very annoying! The strange thing is that other distros work good but I am too much a newbie to compare the settings and solve the problem.. What can we do?:(

---

### Post by M4l3k on 2005-10-17
Hi Golgoth,

I too own a Radeon card and have experienced many problems foolishly trying to install fglrx by all possible means. As a consequence, I have re-installed a couple of times my Breezy and now comes your piece of advice. It sounds very good and I am really looking forward to try that when I get home. I would however understand how you figured out that? What are your sources?

Best Regards

M4l3k

PS: your english is ok...for a Frenchman! ;-)

[QUOTE=Golgoth]The owners of these GPU: 

R100
    Radeon 7200
RV100
    Radeon 7000(VE), M6
RS100
    Radeon IGP320(M)
RV200
    Radeon 7500, M7, FireGL 7800
RS200
    Radeon IGP330(M)/IGP340(M)
RS250
    Radeon Mobility 7000 IGP
R200
    Radeon 8500, 9100, FireGL 8800/8700
RV250
    Radeon 9000PRO/9000, M9
RS300
    Radeon 9100 IGP
RS350
    Radeon 9200 IGP
RV280
    Radeon 9200PRO/9200/9200SE, M9+

should use the "radeon" driver instead of the "fglrx".
It supports 3D rendering...

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo gedit /etc/X11/xorg.conf

In module section, add:
Section "Extensions"
 Option "RENDER" "Enable" 
EndSection

In device section replace "ati" by "radeon" and add these option...

Driver           "radeon"
Option          "AGPMode" "4"
Option         "AGPSize" "64" # default: 8
Option         "RingSize" "8"
Option         "BufferSize" "2"
Option         "EnablePageFlip" "true"
Option         "EnableDepthMoves" "true"
Option         "RenderAccel" "true"

hope it will help[/QUOTE]

---

### Post by Golgoth on 2005-10-17
[QUOTE=M4l3k]Hi Golgoth,

I too own a Radeon card and have experienced many problems foolishly trying to install fglrx by all possible means. As a consequence, I have re-installed a couple of times my Breezy and now comes your piece of advice. It sounds very good and I am really looking forward to try that when I get home. I would however understand how you figured out that? What are your sources?

Best Regards

M4l3k

PS: your english is ok...for a Frenchman! ;-)[/QUOTE]

it comes from the [french wiki]("http://wiki.ubuntu-fr.org/materiel/ati"). Hope it will work for you!

It works on my other computer with a radeon 7500.

---

### Post by Golgoth on 2005-10-17
[QUOTE=hiruzzolo]Hi! I have the same problem and I have a Radeon 7000/VE (RV100 Chipset)! In breezy I tried the last advice about radeon driver but it didn't worked! I had this problem also in hoary and it is very very annoying! The strange thing is that other distros work good but I am too much a newbie to compare the settings and solve the problem.. What can we do?:([/QUOTE]

try to customize the options...

---

### Post by hiruzzolo on 2005-10-17
Sorry, Golgoth, how can I customize them? Tnx for your reply.

BTW, I found this page about the driver we are tryng to use maybe it could be useful to a more expert person: [http://www.x.org/X11R6.8.2/doc/radeon.4.html](http://www.x.org/X11R6.8.2/doc/radeon.4.html)

---

### Post by Golgoth on 2005-10-18
If you want to use the radeon driver, you have to remove all the "fdlrx" stuff with synaptic...

especially: xorg-driver-fglrx et fglrx-control

and don't forget to remove fglrx from the file: /etc/module !

---

### Post by SilverTab on 2005-10-18
[QUOTE=Golgoth]If you want to use the radeon driver, you have to remove all the "fdlrx" stuff with synaptic...

especially: xorg-driver-fglrx et fglrx-control

and don't forget to remove fglrx from the file: /etc/module ![/QUOTE]


ok I want to try that out...but: after I remove xorg-driver-fglrx and fglrx-control, is there any driver that I need to install to use 'radeon'

---

### Post by SilverTab on 2005-10-18
BTW Golgoth: any way I can contact you?? AIM, ICQ etc...
i'm french too...want to ask you some questions about this issue!
STP ;)

---

### Post by Golgoth on 2005-10-18
[QUOTE=SilverTab]BTW Golgoth: any way I can contact you?? AIM, ICQ etc...
i'm french too...want to ask you some questions about this issue!
STP ;)[/QUOTE]

;)

---

### Post by Golgoth on 2005-10-18
et toi c'est quoi ton adresse?!

---

### Post by marcus_brodi on 2005-10-24
Any news for this issue ?
I already filed a bug on malone last week ([https://launchpad.net/distros/ubuntu/+sources/xorg/+bug/3286](https://launchpad.net/distros/ubuntu/+sources/xorg/+bug/3286) ).

I tried the ATI fglrx but it freezes my computer :/

I'm using radeon 8500 and an AMD 1.2Ghz TB

**UPDATE**: Ok, following this:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=15036](http://bugzilla.ubuntu.com/show_bug.cgi?id=15036)

meaning installing:
[http://people.ubuntu.com/~daniels/libgl1-mesa-dri_6.3.2-0ubuntu7_i386.deb](http://people.ubuntu.com/~daniels/libgl1-mesa-dri_6.3.2-0ubuntu7_i386.deb)

fixes the problem

---

### Post by xuefengwang101 on 2005-10-24
i have the problem,sorry for my english i am a chinese 
i also freeze my X after several minutes after install the fglrx driver
and i cannot do anything with it and have to hardboot
and then 
the same things happens agian

---

### Post by hiruzzolo on 2005-10-25
Hi! I had this problem too with a radeon 7000.. I found some interesting pages online about this kind of bug:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=10579](https://bugzilla.ubuntu.com/show_bug.cgi?id=10579)
[https://bugs.freedesktop.org/show_bug.cgi?id=1912](https://bugs.freedesktop.org/show_bug.cgi?id=1912)
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=152648](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=152648)
The problems seems to be probably in xorg 6.8.2, so I would like to try to use other version (like 6.8.1 as someone did in redhat forum, or like 6.9 or 7.0 rc).. I hope someone can help me with it or can have some ideas reading those pages..

---

