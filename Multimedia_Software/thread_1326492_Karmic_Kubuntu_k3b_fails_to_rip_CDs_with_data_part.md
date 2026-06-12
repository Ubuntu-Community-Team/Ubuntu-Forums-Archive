---
title: "Karmic Kubuntu: k3b fails to rip CDs with data part"
date: 2009-11-14
forum: Multimedia Software
---

### Post by TroyMcClure on 2009-11-14
Hi there,

I reproducibly have the problem that ripping CDs with a data part results in a segmentation fault. Any ideas how to handle this, any known bugs? (searching did not reveal anything to me...)

By the way, I think the automated KDE bug report feature is nice, but could use some improvements: first of all, debug versions of the program are not installed by default, which is OK - but wouldn't it be possible to guide the user which debug packages to install? The stack trace should have enough info to do that... Furthermore, I can't manually locate the debug libs for k3b - where do I find them? Most packages come with debug symbols in a -dbg package, but there is no such package for k3b, or k3blibs. Without those symbols, the debug report scripts seems to be buggy - even if I check I can give information how to reproduce, the panel tells me it won't send the report. I don't even get asked about those textual inputs...

So, two things I'd like to get: a fix or a way how to rip my CDs with data part, and some infos on how to create a meaningful bug report for KDE apps.

Thanks for your support!

Cheers,
Martin

P.S.: Here's the stack trace, in case a developer reads this, missing the k3b debug symbols. 

My way to get here: 
1. load CD with data partition
2. click "rip audio cd"
3. select flac
4. click "start"
5. <kaboom>


Application: K3b (k3b), signal: Segmentation fault
[Current thread is 1 (Thread 0xb77e1920 (LWP 3412))]

Thread 2 (Thread 0xb57ffb70 (LWP 3542)):
#0  0x00e4f422 in __kernel_vsyscall ()
#1  0x00875142 in pthread_cond_timedwait@@GLIBC_2.3.2 () at ../nptl/sysdeps/unix/sysv/linux/i386/i686/../i486/pthread_cond_timedwait.S:179
#2  0x07d5a7e4 in __pthread_cond_timedwait (cond=0xb57ff244, mutex=0xb57ff274, abstime=0xb57ff2c0) at forward.c:152
#3  0x0345d81e in thread_sleep (ti=0x1) at thread/qthread_unix.cpp:297
#4  0x0345d9c0 in QThread::sleep (secs=2) at thread/qthread_unix.cpp:311
#5  0x001a62e9 in K3b::MediaCache::PollThread::run() () from /usr/lib/libk3b.so.6
#6  0x0345de32 in QThreadPrivate::start (arg=0x9006368) at thread/qthread_unix.cpp:188
#7  0x0087080e in start_thread (arg=0xb57ffb70) at pthread_create.c:300
#8  0x07d4d7ee in clone () at ../sysdeps/unix/sysv/linux/i386/clone.S:130

Thread 1 (Thread 0xb77e1920 (LWP 3412)):
[KCrash Handler]
#6  0x0813371d in _start ()

---

