---
title: "Display settings crashes system settings!"
date: 2008-04-25
forum: Multimedia Software
---

### Post by spidertaker23 on 2008-04-25
I installed kubuntu 8.04 via wubi ... I don't know if this is related to using wubi to install it or not. But I can't get into display settings ... therefore I can't change my screen resolution ... which makes it unusable.

I just got kubuntu 8.04 kde-4 installed on my GT5404 ... intel main board D945GCL.

When I go into system settings then > Display settings ... system settings crash.

Here is my log:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb65f7a00 (LWP 6405)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7fd5410 in __kernel_vsyscall ()
[Current thread is 0 (process 6405)]

Thread 1 (Thread 0xb65f7a00 (LWP 6405)):
#0 0xb7fd5410 in __kernel_vsyscall ()
#1 0xb7094c90 in nanosleep () from /lib/tls/i686/cmov/libc.so.6
#2 0xb7094ac7 in sleep () from /lib/tls/i686/cmov/libc.so.6
#3 0xb7b987d0 in ?? () from /usr/lib/kde4/lib/libkdeui.so.5
#4 0x00000001 in ?? ()
#5 0x00000000 in ?? ()
#0 0xb7fd5410 in __kernel_vsyscall ()

---

### Post by foggydude on 2008-11-02
I have it too! after upgarde from 8.04 to 8.10...

also grandr wont install... the only way now is working in xorg.conf directly... and i dont know how:

my screen = 1280x720
even after removing line " virtual 1280 800", i ave to move my mouse up and down to see top and bottom of the screen. help please..... drivining me nuts

---

