---
title: "Amarok crashes on startup 9.10"
date: 2010-01-28
forum: Multimedia Software
---

### Post by jm8254og on 2010-01-28
I am using Ubuntu 9.10 and having trouble with Amarok.  It crashes on on startup.  I have read that the issue is not with Amarok but rather phonon.  Is there a solution?


Application: Amarok (amarok), signal: Segmentation fault
[Current thread is 1 (Thread 0xb68cb950 (LWP 13047))]

Thread 5 (Thread 0xb527bb70 (LWP 13054)):
#0  0x003e9422 in __kernel_vsyscall ()
#1  0x07fcb142 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x037168d4 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0x075519ff in ?? () from /usr/lib/libxine.so.1
#4  0x07fc680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0x037098de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb4a7ab70 (LWP 13055)):
#0  0x03029e06 in clock_gettime () from /lib/tls/i686/cmov/librt.so.1
#1  0x07a8fbf3 in QTimerInfoList::getTime (this=0x9520064, t=...) at kernel/qeventdispatcher_unix.cpp:339
#2  0x07a8fde1 in QTimerInfoList::updateCurrentTime (this=0x9520064) at kernel/qeventdispatcher_unix.cpp:297
#3  0x07a9088c in QTimerInfoList::timerWait (this=0x9520064, tm=...) at kernel/qeventdispatcher_unix.cpp:420
#4  0x07a8e210 in timerSourcePrepare (source=0x9520030, timeout=0xb4a7a0bc) at kernel/qeventdispatcher_glib.cpp:141
#5  0x02222f90 in g_main_context_prepare () from /lib/libglib-2.0.so.0
#6  0x02223351 in ?? () from /lib/libglib-2.0.so.0
#7  0x02223863 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#8  0x07a8e067 in QEventDispatcherGlib::processEvents (this=0x9550b98, flags=...) at kernel/qeventdispatcher_glib.cpp:329
#9  0x07a61c79 in QEventLoop::processEvents (this=0xb4a7a284, flags=) at kernel/qeventloop.cpp:149
#10 0x07a620ca in QEventLoop::exec (this=0xb4a7a284, flags=...) at kernel/qeventloop.cpp:201
#11 0x0796fb73 in QThread::exec (this=0x951d818) at thread/qthread.cpp:487
#12 0x02cb720a in ?? () from /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
#13 0x07972e32 in QThreadPrivate::start (arg=0x951d818) at thread/qthread_unix.cpp:188
#14 0x07fc680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x037098de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb40ffb70 (LWP 13056)):
#0  0x003e9422 in __kernel_vsyscall ()
#1  0x07fcae15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0371687d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0x075625ee in ?? () from /usr/lib/libxine.so.1
#4  0x07fc680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0x037098de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb38feb70 (LWP 13057)):
#0  0x003e9422 in __kernel_vsyscall ()
#1  0x07fcae15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0371687d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0x075625ee in ?? () from /usr/lib/libxine.so.1
#4  0x07fc680e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0x037098de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb68cb950 (LWP 13047)):
[KCrash Handler]
#6  0x00b4e5cc in Playlist::Model::Model(QObject*) () from /usr/lib/libamaroklib.so.1
#7  0x00b5035c in ?? () from /usr/lib/libamaroklib.so.1
#8  0x00b5046f in ?? () from /usr/lib/libamaroklib.so.1
#9  0x00b5048b in The::playlist() () from /usr/lib/libamaroklib.so.1
#10 0x00d88992 in StatusBar::StatusBar(QWidget*) () from /usr/lib/libamaroklib.so.1
#11 0x00e0ea8b in MainWindow::MainWindow() () from /usr/lib/libamaroklib.so.1
#12 0x00de735e in App::continueInit() () from /usr/lib/libamaroklib.so.1
#13 0x00de88f1 in App::App() () from /usr/lib/libamaroklib.so.1
#14 0x08051e3e in _start ()

---

### Post by delbyblue on 2010-02-21
Same problem for me and haven't found anything googling around. Sigh!

---

### Post by madtownmike1 on 2010-02-26
Same for me; it was working fine, then started failing. I think apt needs a backout procedure for updates. HP-UX had this, sure would come in handy in Linux.

---

