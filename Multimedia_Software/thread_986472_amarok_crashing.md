---
title: "amarok crashing"
date: 2008-11-18
forum: Multimedia Software
---

### Post by richardspirit on 2008-11-18
After receiving some updates through my update manager today now suddenly amarok crashes every time as soon as it loads. Here is the debug info...its useless to me.

======== DEBUG INFORMATION  =======
Version:    1.4.10
Engine:     xine-engine
Build date: Oct 13 2008
CC version: 4.3.2
KDElibs:    3.5.10
Qt:         3.3.8b
TagLib:     1.5.0
CPU count:  1
NDEBUG:     true
==== file `which amarokapp` =======
/usr/bin/amarokapp: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped


==== (gdb) bt =====================
[Thread debugging using libthread_db enabled]
[New Thread 0xb53e96e0 (LWP 6757)]
[New Thread 0xafd2bb90 (LWP 6788)]
[New Thread 0xb16d8b90 (LWP 6785)]
[New Thread 0xb1ed9b90 (LWP 6784)]
[New Thread 0xb28a7b90 (LWP 6783)]
[New Thread 0xb32a9b90 (LWP 6782)]
[New Thread 0xb5076b90 (LWP 6781)]
[New Thread 0xb4875b90 (LWP 6778)]
0xb7fbe430 in __kernel_vsyscall ()
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb75ee60b in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x0804d6fa in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb71a11c3 in QListViewItem::height () from /usr/lib/libqt-mt.so.3
#5  0xb7d20daf in Playlist::reallyEnsureItemCentered ()
   from /usr/lib/libamarok.so.0
#6  0xb7d4012e in Playlist::qt_invoke () from /usr/lib/libamarok.so.0
#7  0xb70bd38a in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#8  0xb741cbfe in QSignal::signal () from /usr/lib/libqt-mt.so.3
#9  0xb70da22d in QSignal::activate () from /usr/lib/libqt-mt.so.3
#10 0xb70e15c3 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#11 0xb70584f5 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#12 0xb7059536 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#13 0xb79828a2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#14 0xb704dd13 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#15 0xb7003147 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#16 0xb7070f00 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#17 0xb7070dc6 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#18 0xb7058b8f in QApplication::exec () from /usr/lib/libqt-mt.so.3
#19 0x0804bf03 in ?? ()
#20 0xb7568685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#21 0x0804b4b1 in ?? ()
#0  0xb7fbe430 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75ee60b in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0x0804d6fa in Amarok::Crash::crashHandler ()
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb71a11c3 in QListViewItem::height () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#5  0xb7d20daf in Playlist::reallyEnsureItemCentered ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#6  0xb7d4012e in Playlist::qt_invoke () from /usr/lib/libamarok.so.0
No symbol table info available.
#7  0xb70bd38a in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#8  0xb741cbfe in QSignal::signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#9  0xb70da22d in QSignal::activate () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#10 0xb70e15c3 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#11 0xb70584f5 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#12 0xb7059536 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#13 0xb79828a2 in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#14 0xb704dd13 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#15 0xb7003147 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#16 0xb7070f00 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#17 0xb7070dc6 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#18 0xb7058b8f in QApplication::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#19 0x0804bf03 in ?? ()
No symbol table info available.
#20 0xb7568685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#21 0x0804b4b1 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 8 (Thread 0xb4875b90 (LWP 6778)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb6d66d09 in __lll_lock_wait () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6d62114 in _L_lock_89 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb6d61a42 in pthread_mutex_lock ()
   from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7641bb6 in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7376857 in QRecursiveMutexPrivate::lock () from /usr/lib/libqt-mt.so.3
#6  0xb7376494 in QMutex::lock () from /usr/lib/libqt-mt.so.3
#7  0xb7058662 in QApplication::lock () from /usr/lib/libqt-mt.so.3
#8  0xb7bd0ef1 in CollectionDB::makeShadowedImage ()
   from /usr/lib/libamarok.so.0
#9  0xb7be6818 in CollectionDB::albumImage () from /usr/lib/libamarok.so.0
#10 0xb7c2a1b8 in CurrentTrackJob::constructHTMLAlbums ()
   from /usr/lib/libamarok.so.0
#11 0xb7c2dfd3 in CurrentTrackJob::showHomeByAlbums ()
   from /usr/lib/libamarok.so.0
#12 0xb7c30211 in CurrentTrackJob::showHome () from /usr/lib/libamarok.so.0
#13 0xb7c308d3 in CurrentTrackJob::doJob () from /usr/lib/libamarok.so.0
#14 0xb7e3715b in ThreadManager::Thread::run () from /usr/lib/libamarok.so.0
#15 0xb70523cf in QThreadInstance::start () from /usr/lib/libqt-mt.so.3
#16 0xb6d6050f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0xb76337ee in clone () from /lib/tls/i686/cmov/libc.so.6
Thread 7 (Thread 0xb5076b90 (LWP 6781)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb6d643a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7641a44 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb3d8167f in ?? () from /usr/lib/libxine.so.1
Thread 6 (Thread 0xb32a9b90 (LWP 6782)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb7628f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb32ca532 in ?? () from /usr/lib/libpulse.so.0
#3  0xb32bc509 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0xb32bdcd3 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0xb32bdda4 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0xb32ca2e3 in ?? () from /usr/lib/libpulse.so.0
#7  0xb32eb8e2 in ?? () from /usr/lib/libpulse.so.0
#8  0xb6d6050f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb76337ee in clone () from /lib/tls/i686/cmov/libc.so.6
Thread 5 (Thread 0xb28a7b90 (LWP 6783)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb6d64075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb76419ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb3d93843 in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
Thread 4 (Thread 0xb1ed9b90 (LWP 6784)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb6d64075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb76419ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb3d852e4 in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
Thread 3 (Thread 0xb16d8b90 (LWP 6785)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb6d64075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb76419ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb3d96934 in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)
Thread 2 (Thread 0xafd2bb90 (LWP 6788)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb7623446 in access () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7375b51 in qt_file_access () from /usr/lib/libqt-mt.so.3
#3  0xb738b945 in QFile::exists () from /usr/lib/libqt-mt.so.3
#4  0xb7d00c2d in UrlUpdateJob::updateStatistics ()
   from /usr/lib/libamarok.so.0
#5  0xb7d01cbd in UrlUpdateJob::doJob () from /usr/lib/libamarok.so.0
#6  0xb7e3715b in ThreadManager::Thread::run () from /usr/lib/libamarok.so.0
#7  0xb70523cf in QThreadInstance::start () from /usr/lib/libqt-mt.so.3
#8  0xb6d6050f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb76337ee in clone () from /lib/tls/i686/cmov/libc.so.6
Thread 1 (Thread 0xb53e96e0 (LWP 6757)):
#0  0xb7fbe430 in __kernel_vsyscall ()
#1  0xb75ee60b in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0x0804d6fa in Amarok::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb71a11c3 in QListViewItem::height () from /usr/lib/libqt-mt.so.3
#5  0xb7d20daf in Playlist::reallyEnsureItemCentered ()
   from /usr/lib/libamarok.so.0
#6  0xb7d4012e in Playlist::qt_invoke () from /usr/lib/libamarok.so.0
#7  0xb70bd38a in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#8  0xb741cbfe in QSignal::signal () from /usr/lib/libqt-mt.so.3
#9  0xb70da22d in QSignal::activate () from /usr/lib/libqt-mt.so.3
#10 0xb70e15c3 in QSingleShotTimer::event () from /usr/lib/libqt-mt.so.3
#11 0xb70584f5 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#12 0xb7059536 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#13 0xb79828a2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#14 0xb704dd13 in QEventLoop::activateTimers () from /usr/lib/libqt-mt.so.3
#15 0xb7003147 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#16 0xb7070f00 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#17 0xb7070dc6 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#18 0xb7058b8f in QApplication::exec () from /usr/lib/libqt-mt.so.3
#19 0x0804bf03 in ?? ()
#20 0xb7568685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#21 0x0804b4b1 in ?? ()
#0  0xb7fbe430 in __kernel_vsyscall ()

---

### Post by richardspirit on 2008-11-18
You know I have been a strong supporter of Ubuntu for many years and raved about the community support...but I have to say recently there has been a lacking in both the OS and the support. I can't seem to get anybody to respond to any of my posts and my OS usability is going in the trash can. Please help so I am not forced back to Windows.

---

### Post by richardspirit on 2008-11-18
Well I guess that's that then. I will be looking for new distro to work with then.

---

