---
title: "Amarok 2 crashes immediately after plugin installation"
date: 2009-04-20
forum: Multimedia Software
---

### Post by tijmz on 2009-04-20
Hi all,

I just upgraded to Jaunty RC, which caused me to finally switch to Amarok 2 as well. After toying with it, I installed a plugin that caused the program to crash. Because the plugin stays on, Amarok now crashes upon starting.

Is there a config file somewhere that allows me to turn off the plugin, or a way to run the script manager by itself? I want to get rid of the setting, but have no idea how to do so. Even complete reinstallation didn't work.

---

### Post by kruppe on 2009-04-21
I have exactly the same problem.

Installed about 3 plugins. On restarting Amarok 2 - it dies after flashing the startup screen and flashing the interface once.

I miss it, dearly and it's only been a day :(

---

### Post by kruppe on 2009-04-21
Thanks for the suggestion.

Initially I thought the DB crashed because my music database was too big.

I just nuked the 

~/.kde/share/apps/amarok/scripts/

folder contents - all except the pax_global_header file

and Amarok is up and scanning my music database again.

Will have to reinstall plugins one by one and check them for sanity.

Funny they don't have a better catching system for this.

Hope this helps. :popcorn:

---

### Post by nvjopsddhapnv on 2009-07-19
I am using ubuntu 8.10 os. Recently I have installed amarok2 and it crashes 2 times whenever I tried to open some online streaming station like last.fm podcast etc ...

the crash report is ...

Application: Amarok (amarok), signal SIGABRT
[Current thread is 0 (LWP 12549)]

Thread 19 (Thread 0xb25eeb90 (LWP 12550)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a53a2 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b80a44 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb315267f in ?? () from /usr/lib/libxine.so.1

Thread 18 (Thread 0xb1b88b90 (LWP 12556)):
#0  0xb807a431 in __kernel_vsyscall ()
#1  0xb6b6233b in read () from /lib/tls/i686/cmov/libc.so.6
#2  0xb32de482 in ?? () from /usr/lib/libasound.so.2
#3  0xb32db9cd in snd_ctl_read () from /usr/lib/libasound.so.2
#4  0xb32d7d9f in snd_hctl_handle_events () from /usr/lib/libasound.so.2
#5  0xb32e3ea1 in snd_mixer_handle_events () from /usr/lib/libasound.so.2
#6  0xb1de7fe4 in ?? () from /usr/lib/xine/plugins/1.24/xineplug_ao_out_alsa.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 17 (Thread 0xb1186b90 (LWP 12557)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb3164853 in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 16 (Thread 0xb07ffb90 (LWP 12558)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb6b80d43 in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6b05c5d in ?? () from /lib/tls/i686/cmov/libc.so.6
Backtrace stopped: previous frame identical to this frame (corrupt stack?)

Thread 15 (Thread 0xafad3b90 (LWP 12560)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb6b6ac01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb317e590 in xine_usec_sleep () from /usr/lib/libxine.so.1
#3  0x00000000 in ?? ()

Thread 14 (Thread 0xa3fa8b90 (LWP 12561)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb31562e4 in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 13 (Thread 0xa35dab90 (LWP 12562)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb31562e4 in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 12 (Thread 0xa2dd9b90 (LWP 12563)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb3167944 in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 11 (Thread 0xa1b95b90 (LWP 12564)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb6b6ac01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f42150 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#4  0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xa138db90 (LWP 12566)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e736f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb5b54bfb in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5b5852c in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5b5349b in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5b5866f in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#12 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#13 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#14 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#15 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#16 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#17 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#18 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#19 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#20 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#21 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#22 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#23 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#24 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#25 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#26 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#27 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#28 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#29 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#30 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#31 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#32 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#33 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#34 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#35 0xb5b567ad in ?? () from /usr/lib/libthreadweaver.so.4
#36 0xb5b56925 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#37 0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#38 0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#39 0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xa0b8cb90 (LWP 12567)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e736f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb5b54bfb in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5b5852c in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5b5349b in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5b5866f in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5b567ad in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5b56925 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#11 0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#12 0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xa038bb90 (LWP 12568)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e736f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb5b54bfb in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5b5852c in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5b5349b in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5b5866f in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#12 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#13 0xb5b567ad in ?? () from /usr/lib/libthreadweaver.so.4
#14 0xb5b56925 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#15 0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#16 0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0x9e80fb90 (LWP 12572)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e736f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb5b54bfb in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5b5852c in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5b5349b in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5b5866f in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#12 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#13 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#14 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#15 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#16 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#17 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#18 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#19 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#20 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#21 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#22 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#23 0xb5b58691 in ?? () from /usr/lib/libthreadweaver.so.4
#24 0xb5b55c73 in ?? () from /usr/lib/libthreadweaver.so.4
#25 0xb5b567ad in ?? () from /usr/lib/libthreadweaver.so.4
#26 0xb5b56925 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#27 0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#28 0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#29 0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0x9ddffb90 (LWP 12581)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e736f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb78e264a in ?? () from /usr/lib/libQtGui.so.4
#5  0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#6  0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0x9d5feb90 (LWP 12582)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb6b80d43 in ?? () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6b05c5d in ?? () from /lib/tls/i686/cmov/libc.so.6
Backtrace stopped: previous frame identical to this frame (corrupt stack?)

Thread 4 (Thread 0x9cdfdb90 (LWP 12584)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e736f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb78e264a in ?? () from /usr/lib/libQtGui.so.4
#5  0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#6  0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0x9c5fcb90 (LWP 12585)):
#0  0xb69f0ef9 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#1  0xb7f8d497 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#2  0xb7f6152a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#3  0xb7f616ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#4  0xb7e6f419 in QThread::exec () from /usr/lib/libQtCore.so.4
#5  0xb7f4588b in ?? () from /usr/lib/libQtCore.so.4
#6  0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#7  0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

---

### Post by nvjopsddhapnv on 2009-07-19
Thread 2 (Thread 0x967d9b90 (LWP 12587)):
#0  0xb807a430 in __kernel_vsyscall ()
#1  0xb69a5075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6b809ed in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7e736f2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#4  0xb67e0532 in ?? () from /usr/lib/libQtNetwork.so.4
#5  0xb7e726ae in ?? () from /usr/lib/libQtCore.so.4
#6  0xb69a150f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb6b727ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb49686c0 (LWP 12549)):
[KCrash Handler]
#6  0xb807a430 in __kernel_vsyscall ()
#7  0xb6abc880 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6abe248 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb6afa10d in ?? () from /lib/tls/i686/cmov/libc.so.6
#10 0xb6b003f4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#11 0xb6b02456 in free () from /lib/tls/i686/cmov/libc.so.6
#12 0xb69620b1 in operator delete () from /usr/lib/libstdc++.so.6
#13 0xb7f618a5 in QEventLoop::~QEventLoop () from /usr/lib/libQtCore.so.4
#14 0xb7f710ff in QObjectPrivate::deleteChildren () from /usr/lib/libQtCore.so.4
#15 0xb7f79c43 in QObject::~QObject () from /usr/lib/libQtCore.so.4
#16 0xb7cdcc41 in KJob::~KJob () from /usr/lib/libkdecore.so.5
#17 0xb7cdba68 in KCompositeJob::~KCompositeJob () from /usr/lib/libkdecore.so.5
#18 0xb626ff18 in KIO::Job::~Job () from /usr/lib/libkio.so.5
#19 0xb626ff4d in KIO::FileCopyJob::~FileCopyJob () from /usr/lib/libkio.so.5
#20 0xb7f70dec in qDeleteInEventHandler () from /usr/lib/libQtCore.so.4
#21 0xb7f727a3 in QObject::event () from /usr/lib/libQtCore.so.4
#22 0xb74398ec in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#23 0xb744172e in QApplication::notify () from /usr/lib/libQtGui.so.4
#24 0xb7161d1d in KApplication::notify () from /usr/lib/libkdeui.so.5
#25 0xb7f62e61 in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#26 0xb7f63ae5 in QCoreApplicationPrivate::sendPostedEvents () from /usr/lib/libQtCore.so.4
#27 0xb7f63cdd in QCoreApplication::sendPostedEvents () from /usr/lib/libQtCore.so.4
#28 0xb7f8d82f in ?? () from /usr/lib/libQtCore.so.4
#29 0xb69ed6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#30 0xb69f0da3 in ?? () from /usr/lib/libglib-2.0.so.0
#31 0xb69f0f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#32 0xb7f8d478 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#33 0xb74d3ea5 in ?? () from /usr/lib/libQtGui.so.4
#34 0xb7f6152a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#35 0xb7f616ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#36 0xb7cdcad8 in KJob::exec () from /usr/lib/libkdecore.so.5
#37 0xb6d927fe in Meta::loadPlaylist () from /usr/lib/libamaroklib.so.1
#38 0xb6e01b83 in ?? () from /usr/lib/libamaroklib.so.1
#39 0xb6cf593f in Playlist::Controller::insertionHelper () from /usr/lib/libamaroklib.so.1
#40 0xb6cf7a47 in Playlist::Controller::insertOptioned () from /usr/lib/libamaroklib.so.1
#41 0xb6cd49c1 in ?? () from /usr/lib/libamaroklib.so.1
#42 0xb6cdaa11 in ?? () from /usr/lib/libamaroklib.so.1
#43 0xb7f77a60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#44 0xb7f787e2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#45 0xb6e36353 in AmarokMimeData::trackListSignal () from /usr/lib/libamaroklib.so.1
#46 0xb6e37830 in AmarokMimeData::getTrackListSignal () from /usr/lib/libamaroklib.so.1
#47 0xb6cd54bd in ?? () from /usr/lib/libamaroklib.so.1
#48 0xb6cd5620 in ?? () from /usr/lib/libamaroklib.so.1
#49 0xb6cda953 in ?? () from /usr/lib/libamaroklib.so.1
#50 0xb7f77a60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#51 0xb7f77e60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#52 0xb74335f1 in QAction::triggered () from /usr/lib/libQtGui.so.4
#53 0xb7433f5f in QAction::activate () from /usr/lib/libQtGui.so.4
#54 0xb7811564 in ?? () from /usr/lib/libQtGui.so.4
#55 0xb7811ff2 in QMenu::mouseReleaseEvent () from /usr/lib/libQtGui.so.4
#56 0xb7236fc5 in KMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.5
#57 0xb7491962 in QWidget::event () from /usr/lib/libQtGui.so.4
#58 0xb78142e9 in QMenu::event () from /usr/lib/libQtGui.so.4
#59 0xb74398ec in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#60 0xb74420e1 in QApplication::notify () from /usr/lib/libQtGui.so.4
#61 0xb7161d1d in KApplication::notify () from /usr/lib/libkdeui.so.5
#62 0xb7f62e61 in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#63 0xb744136e in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
#64 0xb74ab8de in ?? () from /usr/lib/libQtGui.so.4
#65 0xb74aa9e5 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#66 0xb74d47aa in ?? () from /usr/lib/libQtGui.so.4
#67 0xb69ed6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#68 0xb69f0da3 in ?? () from /usr/lib/libglib-2.0.so.0
#69 0xb69f0f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#70 0xb7f8d478 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#71 0xb74d3ea5 in ?? () from /usr/lib/libQtGui.so.4
#72 0xb7f6152a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#73 0xb7f616ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#74 0xb78140b1 in QMenu::exec () from /usr/lib/libQtGui.so.4
#75 0xb6cd83ef in ?? () from /usr/lib/libamaroklib.so.1
#76 0xb6d483df in ?? () from /usr/lib/libamaroklib.so.1
#77 0xb7491c6d in QWidget::event () from /usr/lib/libQtGui.so.4
#78 0xb77c8fd3 in QFrame::event () from /usr/lib/libQtGui.so.4
#79 0xb785f7df in QAbstractScrollArea::viewportEvent () from /usr/lib/libQtGui.so.4
#80 0xb790accf in QAbstractItemView::viewportEvent () from /usr/lib/libQtGui.so.4
#81 0xb79429e4 in QTreeView::viewportEvent () from /usr/lib/libQtGui.so.4
#82 0xb7861d85 in ?? () from /usr/lib/libQtGui.so.4
#83 0xb7f6204a in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
#84 0xb74398ca in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#85 0xb7441c55 in QApplication::notify () from /usr/lib/libQtGui.so.4
#86 0xb7161d1d in KApplication::notify () from /usr/lib/libkdeui.so.5

---

### Post by nvjopsddhapnv on 2009-07-19
#87 0xb7f62e61 in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#88 0xb744486e in QCoreApplication::sendSpontaneousEvent () from /usr/lib/libQtGui.so.4
#89 0xb74abe3f in ?? () from /usr/lib/libQtGui.so.4
#90 0xb74aa9e5 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#91 0xb74d47aa in ?? () from /usr/lib/libQtGui.so.4
#92 0xb69ed6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#93 0xb69f0da3 in ?? () from /usr/lib/libglib-2.0.so.0
#94 0xb69f0f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#95 0xb7f8d478 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#96 0xb74d3ea5 in ?? () from /usr/lib/libQtGui.so.4
#97 0xb7f6152a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#98 0xb7f616ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#99 0xb7cdcad8 in KJob::exec () from /usr/lib/libkdecore.so.5
#100 0xb6d927fe in Meta::loadPlaylist () from /usr/lib/libamaroklib.so.1
#101 0xb6e01b83 in ?? () from /usr/lib/libamaroklib.so.1
#102 0xb6cf593f in Playlist::Controller::insertionHelper () from /usr/lib/libamaroklib.so.1
#103 0xb6cf7a47 in Playlist::Controller::insertOptioned () from /usr/lib/libamaroklib.so.1
#104 0xb6cd49c1 in ?? () from /usr/lib/libamaroklib.so.1
#105 0xb6cdaa11 in ?? () from /usr/lib/libamaroklib.so.1
#106 0xb7f77a60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#107 0xb7f787e2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#108 0xb6e36353 in AmarokMimeData::trackListSignal () from /usr/lib/libamaroklib.so.1
#109 0xb6e37830 in AmarokMimeData::getTrackListSignal () from /usr/lib/libamaroklib.so.1
#110 0xb6cd54bd in ?? () from /usr/lib/libamaroklib.so.1
#111 0xb6cd5620 in ?? () from /usr/lib/libamaroklib.so.1
#112 0xb6cda953 in ?? () from /usr/lib/libamaroklib.so.1
#113 0xb7f77a60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#114 0xb7f77e60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#115 0xb74335f1 in QAction::triggered () from /usr/lib/libQtGui.so.4
#116 0xb7433f5f in QAction::activate () from /usr/lib/libQtGui.so.4
#117 0xb7811564 in ?? () from /usr/lib/libQtGui.so.4
#118 0xb7811ff2 in QMenu::mouseReleaseEvent () from /usr/lib/libQtGui.so.4
#119 0xb7236fc5 in KMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.5
#120 0xb7491962 in QWidget::event () from /usr/lib/libQtGui.so.4
#121 0xb78142e9 in QMenu::event () from /usr/lib/libQtGui.so.4
#122 0xb74398ec in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#123 0xb74420e1 in QApplication::notify () from /usr/lib/libQtGui.so.4
#124 0xb7161d1d in KApplication::notify () from /usr/lib/libkdeui.so.5
#125 0xb7f62e61 in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#126 0xb744136e in QApplicationPrivate::sendMouseEvent () from /usr/lib/libQtGui.so.4
#127 0xb74ab8de in ?? () from /usr/lib/libQtGui.so.4
#128 0xb74aa9e5 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#129 0xb74d47aa in ?? () from /usr/lib/libQtGui.so.4
#130 0xb69ed6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#131 0xb69f0da3 in ?? () from /usr/lib/libglib-2.0.so.0
#132 0xb69f0f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#133 0xb7f8d478 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#134 0xb74d3ea5 in ?? () from /usr/lib/libQtGui.so.4
#135 0xb7f6152a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#136 0xb7f616ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#137 0xb78140b1 in QMenu::exec () from /usr/lib/libQtGui.so.4
#138 0xb6cd83ef in ?? () from /usr/lib/libamaroklib.so.1
#139 0xb6d483df in ?? () from /usr/lib/libamaroklib.so.1
#140 0xb7491c6d in QWidget::event () from /usr/lib/libQtGui.so.4
#141 0xb77c8fd3 in QFrame::event () from /usr/lib/libQtGui.so.4
#142 0xb785f7df in QAbstractScrollArea::viewportEvent () from /usr/lib/libQtGui.so.4
#143 0xb790accf in QAbstractItemView::viewportEvent () from /usr/lib/libQtGui.so.4
#144 0xb79429e4 in QTreeView::viewportEvent () from /usr/lib/libQtGui.so.4
#145 0xb7861d85 in ?? () from /usr/lib/libQtGui.so.4
#146 0xb7f6204a in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
#147 0xb74398ca in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#148 0xb7441c55 in QApplication::notify () from /usr/lib/libQtGui.so.4
#149 0xb7161d1d in KApplication::notify () from /usr/lib/libkdeui.so.5
#150 0xb7f62e61 in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#151 0xb744486e in QCoreApplication::sendSpontaneousEvent () from /usr/lib/libQtGui.so.4
#152 0xb74abe3f in ?? () from /usr/lib/libQtGui.so.4
#153 0xb74aa9e5 in QApplication::x11ProcessEvent () from /usr/lib/libQtGui.so.4
#154 0xb74d47aa in ?? () from /usr/lib/libQtGui.so.4
#155 0xb69ed6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#156 0xb69f0da3 in ?? () from /usr/lib/libglib-2.0.so.0
#157 0xb69f0f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#158 0xb7f8d478 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4

---

### Post by nvjopsddhapnv on 2009-07-19
#159 0xb74d3ea5 in ?? () from /usr/lib/libQtGui.so.4
#160 0xb7f6152a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#161 0xb7f616ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#162 0xb7f63da5 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#163 0xb7439767 in QApplication::exec () from /usr/lib/libQtGui.so.4
#164 0x0804c042 in _start ()


whats going on

---

