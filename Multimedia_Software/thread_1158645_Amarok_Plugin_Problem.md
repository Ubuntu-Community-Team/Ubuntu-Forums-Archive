---
title: "Amarok Plugin Problem"
date: 2009-05-13
forum: Multimedia Software
---

### Post by handyguy on 2009-05-13
Amarok was working fine and everything when i loaded two plugins for it, both of the pidgin update message ones. Now whenever i try to run amarok it crashes after only showing the screen for a second. I am running 9.04 and it is fully updated. I am a complete newbie. Here is the KDE crash log:
Application: Amarok (amarok), signal SIGSEGV
[Current thread is 0 (LWP 8789)]

Thread 10 (Thread 0xb013eb90 (LWP 8790)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb77a3412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0d27ae3 in ?? () from /usr/lib/libxine.so.1

Thread 9 (Thread 0xaf8c1b90 (LWP 8791)):
#0  0xb43430ac in clock_gettime () from /lib/tls/i686/cmov/librt.so.1
#1  0xb69e506b in ?? () from /usr/lib/libQtCore.so.4
#2  0xb69e5241 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb69e3553 in ?? () from /usr/lib/libQtCore.so.4
#4  0xb43df6f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#5  0xb43dffdd in ?? () from /usr/lib/libglib-2.0.so.0
#6  0xb43e0268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#7  0xb69e3457 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#8  0xb69b606a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#9  0xb69b64aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#10 0xb68c0639 in QThread::exec () from /usr/lib/libQtCore.so.4
#11 0xb0d7520a in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#12 0xb68c396e in ?? () from /usr/lib/libQtCore.so.4
#13 0xb779f4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb66c949e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xab0bfb90 (LWP 8797)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb66beae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xaf937b19 in ?? () from /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 7 (Thread 0xaf0bab90 (LWP 8798)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb77a30e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0d38d8e in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 6 (Thread 0xae8b9b90 (LWP 8800)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb77a30e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb68c49b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5d24148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5d26eec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5d22d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5d26fea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5d246d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5d27009 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5d246d3 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5d24fbe in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5d255fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#12 0xb68c396e in ?? () from /usr/lib/libQtCore.so.4
#13 0xb779f4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb66c949e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xacbffb90 (LWP 8801)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb77a30e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb68c49b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5d24148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5d26eec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5d22d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5d26fea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5d246d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5d24fbe in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5d255fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#10 0xb68c396e in ?? () from /usr/lib/libQtCore.so.4
#11 0xb779f4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb66c949e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xac1f3b90 (LWP 8803)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb66c17b1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6995380 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb68c396e in ?? () from /usr/lib/libQtCore.so.4
#4  0xb779f4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb66c949e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xa09dfb90 (LWP 8806)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb77a30e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb68c49b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5d24148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5d26eec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5d22d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5d26fea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5d246d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5d24fbe in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5d255fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#10 0xb68c396e in ?? () from /usr/lib/libQtCore.so.4
#11 0xb779f4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb66c949e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xa01deb90 (LWP 8807)):
#0  0xb7f2d430 in __kernel_vsyscall ()
#1  0xb77a30e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb68c49b2 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
#3  0xb5d24148 in ?? () from /usr/lib/libthreadweaver.so.4
#4  0xb5d26eec in ?? () from /usr/lib/libthreadweaver.so.4
#5  0xb5d22d2b in ?? () from /usr/lib/libthreadweaver.so.4
#6  0xb5d26fea in ?? () from /usr/lib/libthreadweaver.so.4
#7  0xb5d246d3 in ?? () from /usr/lib/libthreadweaver.so.4
#8  0xb5d27009 in ?? () from /usr/lib/libthreadweaver.so.4
#9  0xb5d246d3 in ?? () from /usr/lib/libthreadweaver.so.4
#10 0xb5d24fbe in ?? () from /usr/lib/libthreadweaver.so.4
#11 0xb5d255fb in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
#12 0xb68c396e in ?? () from /usr/lib/libQtCore.so.4
#13 0xb779f4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#14 0xb66c949e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb2f41950 (LWP 8789)):
[KCrash Handler]
#6  0xb4b73733 in QFormInternal::domPropertyToVariant () from /usr/lib/libamarokplasma.so.2
#7  0xb4b18437 in QFormInternal::QAbstractFormBuilder::toVariant () from /usr/lib/libamarokplasma.so.2
#8  0xb4b31cfa in QFormInternal::QFormBuilder::applyProperties () from /usr/lib/libamarokplasma.so.2
#9  0xb4b0eefd in QFormInternal::FormBuilderPrivate::applyProperties () from /usr/lib/libamarokplasma.so.2
#10 0xb4b1b9eb in QFormInternal::QAbstractFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#11 0xb4b33248 in QFormInternal::QFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#12 0xb4b0d353 in QFormInternal::FormBuilderPrivate::create () from /usr/lib/libamarokplasma.so.2
#13 0xb4b1a704 in QFormInternal::QAbstractFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#14 0xb4b31a8b in QFormInternal::QFormBuilder::create () from /usr/lib/libamarokplasma.so.2
#15 0xb4b0d821 in QFormInternal::FormBuilderPrivate::create () from /usr/lib/libamarokplasma.so.2
#16 0x9f6f0ff6 in QFormInternal::QAbstractFormBuilder::load () from /usr/lib/kde4/plugins/script/libqtscript_uitools.so
#17 0x9f6d75fa in QUiLoader::load () from /usr/lib/kde4/plugins/script/libqtscript_uitools.so
#18 0x9f6d356c in ?? () from /usr/lib/kde4/plugins/script/libqtscript_uitools.so
#19 0xb5b3f08b in ?? () from /usr/lib/libQtScript.so.4
#20 0xb5b06832 in ?? () from /usr/lib/libQtScript.so.4
#21 0xb5b3617b in ?? () from /usr/lib/libQtScript.so.4
#22 0xb5b2a22b in ?? () from /usr/lib/libQtScript.so.4
#23 0xb5b17617 in QScriptEngine::evaluate () from /usr/lib/libQtScript.so.4
#24 0xb7ac0c13 in ScriptManager::slotRunScript () from /usr/lib/libamaroklib.so.1
#25 0xb7ac1a60 in ScriptManager::slotConfigChanged () from /usr/lib/libamaroklib.so.1
#26 0xb7ac32d2 in ScriptManager::findScripts () from /usr/lib/libamaroklib.so.1
#27 0xb7ac37a3 in ScriptManager::qt_metacall () from /usr/lib/libamaroklib.so.1
#28 0xb69cdca8 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#29 0xb69ce932 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#30 0xb69d30a7 in ?? () from /usr/lib/libQtCore.so.4
#31 0xb69d31cc in ?? () from /usr/lib/libQtCore.so.4
#32 0xb69c815f in QObject::event () from /usr/lib/libQtCore.so.4
#33 0xb6e88e9c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
#34 0xb6e9119e in QApplication::notify () from /usr/lib/libQtGui.so.4
#35 0xb7d7a94d in KApplication::notify () from /usr/lib/libkdeui.so.5
#36 0xb69b7a3b in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
#37 0xb69e6d71 in ?? () from /usr/lib/libQtCore.so.4
#38 0xb69e34e0 in ?? () from /usr/lib/libQtCore.so.4
#39 0xb43dcb88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#40 0xb43e00eb in ?? () from /usr/lib/libglib-2.0.so.0
#41 0xb43e0268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#42 0xb69e3438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#43 0xb6f2a365 in ?? () from /usr/lib/libQtGui.so.4
#44 0xb69b606a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#45 0xb69b64aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#46 0xb69b8959 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#47 0xb6e88d17 in QApplication::exec () from /usr/lib/libQtGui.so.4
#48 0x0814c4b2 in _start ()

---

