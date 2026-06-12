---
title: "Mythfrontend not responding to keyboard....."
date: 2008-07-20
forum: Multimedia Software
---

### Post by mbobak on 2008-07-20
Hi,

When I run mythfrontend, it seems to startup error free. However, it does not respond to any keyboard input....at all. Keyboard works fine everywhere else, except on input to mythfrontend.

So, I ran 'strace mythfrontend.real 2> strace.out', and I discovered the following, looping over and over:
Code:
time(NULL)                              = 1216504657
gettimeofday({1216504657, 338798}, NULL) = 0
gettimeofday({1216504657, 338861}, NULL) = 0
read(3, 0x828658c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1216504657, 338940}, NULL) = 0
select(28, [3 4 5 7 27], [], [], {0, 13373}) = 0 (Timeout)
gettimeofday({1216504657, 355614}, NULL) = 0
time(NULL)                              = 1216504657
gettimeofday({1216504657, 355698}, NULL) = 0
gettimeofday({1216504657, 355766}, NULL) = 0
read(3, 0x828658c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1216504657, 355820}, NULL) = 0
select(28, [3 4 5 7 27], [], [], {0, 10493}) = 0 (Timeout)
gettimeofday({1216504657, 366675}, NULL) = 0


The problem here is apparently: 
```
read(3, 0x828658c, 4096)                = -1 EAGAIN (Resource temporarily unavailable)
```


Tracing backwards in the strace output, I find:
```
socket(PF_FILE, SOCK_STREAM, 0)         = 3
connect(3, {sa_family=AF_FILE, path="/tmp/.X11-unix/X0"}, 110) = 0
getpeername(3, {sa_family=AF_FILE, path="/tmp/.X11-unix/X0"}, [20]) = 0
uname({sys="Linux", node="jupiter", ...}) = 0
access("/home/mjb/.Xauthority", R_OK)   = 0
open("/home/mjb/.Xauthority", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0600, st_size=171, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb4a12000
read(4, "\1\0\0\7jupiter\0\00210\0\22MIT-MAGIC-COOKI"..., 4096) = 171
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb4a12000, 4096)                = 0
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
```



So, I'm a little rusty here, and not exactly sure what's going on. Can anyone offer a clue?

Oh, by the way, I noticed that by using the mouse scrollwheel, I can scroll through the main menu.

But, the keyboard still doesn't work, and using the mouse to click or double-click doesn't actually make a menu selection, so, I still can't actually do anything....

Help!

-Mark

PS Ubuntu 8.04, i686, running latest myth version.

---

