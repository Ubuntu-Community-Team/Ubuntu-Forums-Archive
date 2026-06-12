---
title: "Customize TCP"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by cestevez on 2011-01-12
I'd like to make some changes to TCP. I should mention that I downloaded the kernel-source file and all these attempts are done inside the uncompressed (unpacked) directories of this file, unless otherwise specified.
The ideal solution for me is to create a whole new .c file (say tcp_new.c) and be able to load it with the sysctl command. I read that all I need to do is to include the tcp_new.o objective in the Makefile and run "make". That didn't work for me.
Then I tried to wipe the contents of an existing tcp protocol (tcp_yeah.c) and put my code in. When I did this and ran "make", it compiled (with some warnings) but when I use sysctl command (sysctl -w net.ipv4.tcp_congestion_control=yeah) it will not load the file I created but does load some tcp_yeah file in another location (unknown by me). I then searched for tcp_yeah and found a tcp_yeah.ko (outside the kernel-source directory), which I deleted and replaced by the tcp_yeah.ko file I compiled. That didn't work either. There are no other tcp_yeah.x files anywhere else in Linux. So I'm out of ideas. :confused:
Please help!

---

