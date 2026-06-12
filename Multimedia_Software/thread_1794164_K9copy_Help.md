---
title: "K9copy Help"
date: 2011-06-30
forum: Multimedia Software
---

### Post by mld9373 on 2011-06-30
Let me began saying thank you for your help.
I am a newbie to Linux, I've only been using Linux now for about 8 months.
I have several DVD Movie that I am trying to back for personal use only.
I have several grandchildren that like to watch the DVD's,but they also like to play with them. I've told my wife not to let the kid's play with them,but you know how that work's.
So I am trying to use K9copy to make back up of the movie's.K9copy runs for a couple of minuets then it crashes. here is one of the crash reports.

 p, li { white-space: pre-wrap; }  Application: k9copy (k9copy), signal: Segmentation fault
 [Current thread is 1 (Thread 0x7f7f104dc780 (LWP 1802)]
 
 Thread 4 (Thread 0x7f7f01a1a700 (LWP 18031)):
 #0  0x00007f7f08c3cd9d in __pthread_mutex_unlock_usercnt (mutex=0x10dd33 at pthread_mutex_unlock.c:52
 #1  __pthread_mutex_unlock (mutex=0x10dd33 at pthread_mutex_unlock.c:290
 #2  0x00007f7f0876d13a in g_main_context_iterate (context=0x10dd330, block=<value optimized out>, dispatch=1, self=<value optimized out>) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:3094
 #3  0x00007f7f0876d9f2 in g_main_loop_run (loop=0x10dd310) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:3299
 #4  0x00007f7f02379c44 in gdbus_shared_thread_func (data=<value optimized out>) at /build/buildd/glib2.0-2.28.6/./gio/gdbusprivate.c:276
 #5  0x00007f7f087943e4 in g_thread_create_proxy (data=0x10dd410) at /build/buildd/glib2.0-2.28.6/./glib/gthread.c:1897
 #6  0x00007f7f08c38d8c in start_thread (arg=0x7f7f01a1a700) at pthread_create.c:304
 #7  0x00007f7f0b80d04d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
 #8  0x0000000000000000 in ?? ()
 
 Thread 3 (Thread 0x7f7eeeece700 (LWP 18039)):
 #0  0x00007f7f08c3cd9d in __pthread_mutex_unlock_usercnt (mutex=0x13b252 at pthread_mutex_unlock.c:52
 #1  __pthread_mutex_unlock (mutex=0x13b252 at pthread_mutex_unlock.c:290
 #2  0x00007f7f0876c84e in g_main_context_check (context=0x13b2520, max_priority=2147483647, fds=<value optimized out>, n_fds=<value optimized out>) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:2959
 #3  0x00007f7f0876d122 in g_main_context_iterate (context=0x13b2520, block=<value optimized out>, dispatch=1, self=<value optimized out>) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:3088
 #4  0x00007f7f0876d639 in g_main_context_iteration (context=0x13b2520, may_block=1) at /build/buildd/glib2.0-2.28.6/./glib/gmain.c:3154
 #5  0x00007f7f0d0f8446 in QEventDispatcherGlib:rocessEvents(QFlags<QEventLoop:rocessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #6  0x00007f7f0d0cc882 in QEventLoop:rocessEvents(QFlags<QEventLoop:rocessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #7  0x00007f7f0d0ccabc in QEventLoop::exec(QFlags<QEventLoop:rocessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #8  0x00007f7f0cfe3924 in QThread::exec() () from /usr/lib/libQtCore.so.4
 #9  0x00007f7f0d0aec2f in ?? () from /usr/lib/libQtCore.so.4
 #10 0x00007f7f0cfe6175 in ?? () from /usr/lib/libQtCore.so.4
 #11 0x00007f7f08c38d8c in start_thread (arg=0x7f7eeeece700) at pthread_create.c:304
 #12 0x00007f7f0b80d04d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
 #13 0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7f7eec15e700 (LWP 30685)):
 #0  pthread_cond_wait@@GLIBC_2.3.2 () at ../nptl/sysdeps/unix/sysv/linux/x86_64/pthread_cond_wait.S:162
 #1  0x00007f7f0cfe682b in QWaitCondition::wait(QMutex*, unsigned long) () from /usr/lib/libQtCore.so.4
 #2  0x00000000004f8ac3 in ?? ()
 #3  0x00000000004f9773 in ?? ()
 #4  0x00000000004fb011 in ?? ()
 #5  0x00000000004fb25e in ?? ()
 #6  0x00000000004fb581 in ?? ()
 #7  0x00007f7f0cfe6175 in ?? () from /usr/lib/libQtCore.so.4
 #8  0x00007f7f08c38d8c in start_thread (arg=0x7f7eec15e700) at pthread_create.c:304
 #9  0x00007f7f0b80d04d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
 #10 0x0000000000000000 in ?? ()




can someone help me to get K9copy to work or advice on how to back up a DVD with another program.




                                                                                         thank's

---

### Post by handy on 2011-06-30
Unless you are trying to backup one of the rare (in my experience) DVDs that have tough copy protection, DVDShrink installs very easily & runs perfectly in Wine. It is simple to use & automatically shrinks the DVD so that it can be burned onto a 4.3GB single density disk. Which are much cheaper than the 8GB dual density type.

If you have a bit of a search on the web, it won't take to long to find DVDShrink, which is legally free ware.

After you have ripped & shrunk the DVD, then use whatever software to burn the movie DVD. The menu selections should make it obvious which choice to make.

---

