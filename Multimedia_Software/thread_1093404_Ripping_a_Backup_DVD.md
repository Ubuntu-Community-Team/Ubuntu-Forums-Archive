---
title: "Ripping a Backup DVD"
date: 2009-03-11
forum: Multimedia Software
---

### Post by neverett on 2009-03-11
I'm having difficulties ripping "Click" with Adam Sandler.  I want to backup the DVD, and I've been unsuccessful thus far.  I have had several other successful backups of protected DVDs, but this one rips about 800 MB then just stops and Brasero says there has been an "error reading the DVD (no error)".  Anyone else having a similar problem.  I really like Brasero and want to make it work.  Thanks for any help in advance!

Forgot... I'm using 8.10.

---

### Post by wolfen69 on 2009-03-11
have you tried K9copy?

---

### Post by neverett on 2009-03-11
I have tried it.  I have attached the crash log.  It appears to crash k9copy.  On Brasero it just plain quits.  Let me know if anyone has any insight as to what could be the problem.

```

Application: k9copy (k9copy), signal SIGSEGV
0x00007ff63e97c6e1 in nanosleep () from /lib/libc.so.6
[Current thread is 0 (LWP 948)]

Thread 3 (Thread 0x41bf5950 (LWP 949)):
#0  0x00007ff63e9b34b2 in select () from /lib/libc.so.6
#1  0x00007ff640aeb006 in ?? () from /usr/lib/libQtCore.so.4
#2  0x00007ff640a22362 in ?? () from /usr/lib/libQtCore.so.4
#3  0x00007ff63d0df3ea in start_thread () from /lib/libpthread.so.0
#4  0x00007ff63e9bacbd in clone () from /lib/libc.so.6
#5  0x0000000000000000 in ?? ()

Thread 2 (Thread 0x4272c950 (LWP 1654)):
#0  0x00007ff63d0e32d9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
#1  0x00007ff640a23349 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#2  0x00000000004ca936 in ?? ()
#3  0x00000000004cb2fb in ?? ()
#4  0x00000000004cc27d in ?? ()
#5  0x00000000004cc45c in ?? ()
#6  0x00000000004cc751 in ?? ()
#7  0x00007ff640a22362 in ?? () from /usr/lib/libQtCore.so.4
#8  0x00007ff63d0df3ea in start_thread () from /lib/libpthread.so.0
#9  0x00007ff63e9bacbd in clone () from /lib/libc.so.6
#10 0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7ff642771730 (LWP 948)):
[KCrash Handler]
#5  0x00007ff640a1d341 in QMutex::lock () from /usr/lib/libQtCore.so.4
#6  0x00007ff640a1f762 in QThread::isRunning () from /usr/lib/libQtCore.so.4
#7  0x000000000042ba1b in _start ()

```

---

### Post by neverett on 2009-03-14
Anyone?  *bump*

---

### Post by mc4man on 2009-03-14
With k9, probably main title only, don't keep original menus
(in all likelihood it's the kde4 interface that 'crashing', try just closing out the crash box, k9 may continue on.

---

### Post by RD1 on 2009-03-14
I'm embarrassed to say, the best program I've found for this is a Windows program. Install DVDShrink with WINE.

---

