---
title: "rhythmbox stopped working"
date: 2008-04-22
forum: Multimedia Software
---

### Post by justin_acklin on 2008-04-22
I just installed 8.04 (my first linux to run in many years.)
Rhythmbox worked fine the first time I ran it, could see my ipod, was really neat.

That was last night.  Today I try and start rhythmbox and it hangs.  When I strace it loops on:
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=19, events=POLLIN}, {fd=20, events=POLLIN}], 10, 0) = 0
read(3, 0x6e7884, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=19, events=POLLIN}, {fd=20, events=POLLIN, revents=POLLIN}], 10, 6100) = 1
read(20, "l\4\1\1\35\0\0\0\323\0\0\0\211\0\0\0\1\1o\0\25\0\0\0/o"..., 2048) = 189
read(20, 0x12484c0, 2048)               = -1 EAGAIN (Resource temporarily unavailable)
read(3, 0x6e7884, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}, {fd=19, events=POLLIN}, {fd=20, events=POLLIN}], 10, 0) = 0
read(3, 0x6e7884, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI, revents=POLLIN}, {fd=19, events=POLLIN}, {fd=20, events=POLLIN}], 10, 6095) = 1
read(10, "\1\3\0\1\1\0\0\0", 8)         = 8
read(10, "\0\1\2\000117f", 8)           = 8
select(4, [3], [3], NULL, NULL)         = 2 (in [3], out [3])
read(3, "\241 \365\0\3\0@\3W\1\0\0\0\0\0\0\n\0\0\0\0\0\0\0\0\0\0"..., 4096) = 64
writev(3, [{"\33\6\2\0\0\0\0\0", 8}], 1) = 8
read(3, 0x6e7884, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{" \6\2\0\0\0\0\0", 8}], 1)  = 8
read(3, 0x6e7884, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
open("/home/justin/.gnome2/rhythmbox-XNVuSk", O_RDWR|O_CREAT|O_EXCL, 0600) = 17
unlink("/home/justin/.gnome2/rhythmbox-XNVuSk") = 0
close(17)                               = 0
write(10, "\1\f\1\0\16\0\0\0\1\0\0\0\0\0\0\0\f\0\0\0CloneCommand"..., 120) = 120
write(10, "\1\f\1\0\33\0\0\0\1\0\0\0,\177\0\0\16\0\0\0RestartComm"..., 224) = 224
open("/home/justin/.gnome2/rhythmbox/playlists.xml.tmp", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 17
fstat(17, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2ce5759000
write(17, "<?xml version=\"1.0\"?>\n<rhythmdb-"..., 1105) = 1105
close(17)                               = 0
munmap(0x7f2ce5759000, 4096)            = 0
rename("/home/justin/.gnome2/rhythmbox/playlists.xml.tmp", "/home/justin/.gnome2/rhythmbox/playlists.xml") = 0
clone(child_stack=0x428a6170, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0x428a69e0, tls=0x428a6950, child_tidptr=0x428a69e0) = 22109
futex(0x7f2cddbb7388, 0x81 /* FUTEX_??? */, 1) = 1
futex(0x849e90, 0x81 /* FUTEX_??? */, 1) = 1
futex(0x9273c4, 0x80 /* FUTEX_??? */, 1) = -1 EAGAIN (Resource temporarily unavailable)
futex(0x849e90, 0x81 /* FUTEX_??? */, 1) = 0
write(10, "\1\10\1\0\0\0\0\0", 8)       = 8
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI}, {fd=11, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN}, {fd=19, events=POLLIN}, {fd=20, events=POLLIN}, {fd=10, events=POLLIN|POLLPRI}], 10, 0) = 0
uname({sys="Linux", node="justin-ubuntu", ...}) = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\1\30\17\0)\0@\3;\1\0\0\0\0\0\0\310\0\310\0\0\0\1\0!\0"..., 732}], 1) = 732
read(3, 0x6e7884, 4096)                 = -1 EAGAIN (Resource temporarily unavailable)
read(3, "\34\0\372\0)\0@\3\373\0\0\0006w\37\0\0\223i\1\0\0\0\0\0"..., 4096) = 448
read(3,  <unfinished ...>


Anyone have suggestions??

---

### Post by mattspel on 2009-11-29
maybe try re-installing rythmbox. it's in the repositories. there could also be something wrong with your music.

---

