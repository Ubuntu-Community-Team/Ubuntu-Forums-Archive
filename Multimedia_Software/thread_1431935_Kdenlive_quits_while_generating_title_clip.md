---
title: "Kdenlive quits while generating title clip"
date: 2010-03-17
forum: Multimedia Software
---

### Post by afrodeity on 2010-03-17
I've [filed a bug]("http://www.kdenlive.org/mantis/view.php?id=1515"), but am wondering if anybody can see what is going wrong? Desperately need to use the application to get a project done. So this is all very fustratiing

```

Backtrace:
Application: Kdenlive (kdenlive), signal: Segmentation fault
[Current thread is 1 (Thread 0xb7848700 (LWP 23437))]

Thread 3 (Thread 0xb0aceb70 (LWP 24649)):
#0 0x00156422 in __kernel_vsyscall ()
#1 0x04e73c96 in poll () from /lib/tls/i686/cmov/libc.so.6
#2 0x089e5d80 in ?? () from /usr/lib/libxcb.so.1
#3 0x089e62eb in ?? () from /usr/lib/libxcb.so.1
#4 0x089e6687 in xcb_writev () from /usr/lib/libxcb.so.1
#5 0x084a12e9 in _XSend () from /usr/lib/libX11.so.6
#6 0x084a1480 in _XReply () from /usr/lib/libX11.so.6
#7 0x0847fa03 in _XGetWindowAttributes () from /usr/lib/libX11.so.6
#8 0x0847fb82 in XGetWindowAttributes () from /usr/lib/libX11.so.6
#9 0x02578424 in ?? () from /usr/local/lib/mlt/libmltsdl.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 2 (Thread 0xb02cdb70 (LWP 24650)):
#0 0x00156422 in __kernel_vsyscall ()
#1 0x002dde15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2 0x04e8e87d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3 0x02577c5c in ?? () from /usr/local/lib/mlt/libmltsdl.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 1 (Thread 0xb7848700 (LWP 23437)):
[KCrash Handler]
#6 0x006d0c87 in ?? () from /usr/local/lib/libmlt.so.2
#7 0x080e026b in Render::getFileProperties (this=0xa646718, xml=) at /build/buildd/kdenlive-0.7.7.1/src/renderer.cpp:613
#8 0x080e47bc in Render::qt_metacall (this=0xa646718, _c=QMetaObject::InvokeMetaMethod, _id=20, _a=0xbf9a9b6c) at /build/buildd/kdenlive-0.7.7.1/obj-i486-linux-gnu/src/cmake_bindir/renderer.moc:138
#9 0x01076263 in QMetaObject::activate(QObject*, int, int, void**) () from /usr/lib/libQtCore.so.4
#10 0x01076ec2 in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#11 0x080ad68d in ProjectList::getFileProperties (this=0xa346590, _t1=..., _t2=..., _t3=36, _t4=false) at /build/buildd/kdenlive-0.7.7.1/obj-i486-linux-gnu/src/cmake_bindir/projectlist.moc:245
#12 0x080b2bb3 in ProjectList::slotProcessNextClipInQueue (this=0xa346590) at /build/buildd/kdenlive-0.7.7.1/src/projectlist.cpp:848
#13 0x080bd072 in ProjectList::qt_metacall (this=0xa346590, _c=QMetaObject::InvokeMetaMethod, _id=77, _a=0xbf9a9d0c)
    at /build/buildd/kdenlive-0.7.7.1/obj-i486-linux-gnu/src/cmake_bindir/projectlist.moc:223
#14 0x01076263 in QMetaObject::activate(QObject*, int, int, void**) () from /usr/lib/libQtCore.so.4
#15 0x01076ec2 in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
#16 0x010b0667 in QTimer::timeout() () from /usr/lib/libQtCore.so.4
#17 0x0107b9ae in QTimer::timerEvent(QTimerEvent*) () from /usr/lib/libQtCore.so.4
#18 0x010703bf in QObject::event(QEvent*) () from /usr/lib/libQtCore.so.4
#19 0x02933f54 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#20 0x0293b67c in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#21 0x00d61bfa in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#22 0x010606cb in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#23 0x0108d7ce in ?? () from /usr/lib/libQtCore.so.4
#24 0x0108b0e0 in ?? () from /usr/lib/libQtCore.so.4
#25 0x09018e88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#26 0x0901c730 in ?? () from /lib/libglib-2.0.so.0
#27 0x0901c863 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#28 0x0108b02c in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#29 0x029d4be5 in ?? () from /usr/lib/libQtGui.so.4
#30 0x0105ec79 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#31 0x0105f0ca in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#32 0x0106153f in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#33 0x02933dd7 in QApplication::exec() () from /usr/lib/libQtGui.so.4
#34 0x080822fd in main (argc=1, argv=0xbf9aa704) at /build/buildd/kdenlive-0.7.7.1/src/main.cpp:86

Report to http://kdenlive.org/mantis [^]
```

---

