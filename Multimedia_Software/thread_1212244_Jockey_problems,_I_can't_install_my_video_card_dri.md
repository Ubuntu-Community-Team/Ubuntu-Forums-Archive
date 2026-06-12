---
title: "Jockey problems, I can't install my video card driver!!!!"
date: 2009-07-13
forum: Multimedia Software
---

### Post by Scipione on 2009-07-13
I am using kubuntu 9.04, in may PC I have Asus ah 3650 video card using ATI radeon hd 3650 GPU. The problem cames when I try to activate my GPU driver; When I start the jockey do: is looking for drivers, then start downloading and it .... freeze! I mean It stop at "downloading and installing driver..." doing NOTHING!!!.   Finley it stop trying download and gave me an error. That is the error rapport:

Application: Jockey (), signal SIGSEGV
[Current thread is 0 (LWP 9222)]

Thread 2 (Thread 0xb34e7b90 (LWP 9225)):
#0  0xb7f0e430 in __kernel_vsyscall ()
#1  0xb7e14ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb4bd4beb in ?? () from /lib/libdbus-1.so.3
#3  0xb4bcccd7 in ?? () from /lib/libdbus-1.so.3
#4  0xb4bcaebf in ?? () from /lib/libdbus-1.so.3
#5  0xb4bb592e in ?? () from /lib/libdbus-1.so.3
#6  0xb4bb7ec2 in ?? () from /lib/libdbus-1.so.3
#7  0xb4bc51f1 in dbus_pending_call_block () from /lib/libdbus-1.so.3
#8  0xb4bb6e9a in dbus_connection_send_with_reply_and_block () from /lib/libdbus-1.so.3
#9  0xb4be72e3 in ?? () from /var/lib/python-support/python2.6/_dbus_bindings.so
#10 0x080de562 in PyEval_EvalFrameEx ()
#11 0x080e00b8 in PyEval_EvalCodeEx ()
#12 0x081688c6 in ?? ()
#13 0x0806111a in PyObject_Call ()
#14 0x080db1cd in PyEval_EvalFrameEx ()
#15 0x080e00b8 in PyEval_EvalCodeEx ()
#16 0x081688c6 in ?? ()
#17 0x0806111a in PyObject_Call ()
#18 0x0806801a in ?? ()
#19 0x0806111a in PyObject_Call ()
#20 0x08068b65 in ?? ()
#21 0x0806111a in PyObject_Call ()
#22 0x080db1cd in PyEval_EvalFrameEx ()
#23 0x080e00b8 in PyEval_EvalCodeEx ()
#24 0x081688c6 in ?? ()
#25 0x0806111a in PyObject_Call ()
#26 0x0806801a in ?? ()
#27 0x0806111a in PyObject_Call ()
#28 0x08068b65 in ?? ()
#29 0x0806111a in PyObject_Call ()
#30 0x080db1cd in PyEval_EvalFrameEx ()
#31 0x080df587 in PyEval_EvalFrameEx ()
#32 0x080df587 in PyEval_EvalFrameEx ()
#33 0x080e00b8 in PyEval_EvalCodeEx ()
#34 0x081687df in ?? ()
#35 0x0806111a in PyObject_Call ()
#36 0x0806801a in ?? ()
#37 0x0806111a in PyObject_Call ()
#38 0x080d8922 in PyEval_CallObjectWithKeywords ()
#39 0x0810ca58 in ?? ()
#40 0xb7ee94ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#41 0xb7e1f49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7d396c0 (LWP 9222)):
[KCrash Handler]
#6  0xb67c4f7a in QWidget::metric (this=0xa734fd0, m=QPaintDevice::PdmDpiY) at kernel/qwidget_x11.cpp:2548
#7  0xb6956029 in QFont (this=0xbfd2a92c, font=@0xbfd2a96c, pd=0xa734fd8) at ../../include/QtGui/../../src/gui/painting/qpaintdevice.h:96
#8  0xb6783f67 in QWidgetPrivate::updateFont (this=0xa763770, font=@0xbfd2a96c) at kernel/qwidget.cpp:4428
#9  0xb6783e98 in QWidgetPrivate::resolveFont (this=0xa763770) at ../../include/QtGui/private/../../../src/gui/kernel/qwidget_p.h:272
#10 0xb678fa0b in QWidget::setParent (this=0xa734fd0, parent=0x0, f={i = -1076712912}) at kernel/qwidget.cpp:9195
#11 0xb678fe7e in QWidget::setParent (this=0xbfd2a92c, parent=0xbfd2a934) at kernel/qwidget.cpp:9120
#12 0xb6795d16 in QWidgetAction::releaseWidget (this=0xa716e20, widget=0xa734fd0) at kernel/qwidgetaction.cpp:208
#13 0xb6baa75a in ~QMenu (this=0xa71b068) at widgets/qmenu.cpp:1365
#14 0xb52bbcbf in ~KMenu (this=0xa71b068) at /build/buildd/kde4libs-4.2.2/kdeui/widgets/kmenu.cpp:173
#15 0xb526055d in ~KSystemTrayIcon (this=0xa73cab8) at /build/buildd/kde4libs-4.2.2/kdeui/util/ksystemtrayicon.cpp:81
#16 0xb56e1e71 in sipKSystemTrayIcon::~sipKSystemTrayIcon () from /usr/lib/python2.6/dist-packages/PyKDE4/kdeui.so
#17 0xb7990e3f in QObjectPrivate::deleteChildren (this=0xa722208) at kernel/qobject.cpp:1854
#18 0xb678666b in ~QWidget (this=0xa721ec8) at kernel/qwidget.cpp:1373
#19 0xb6c4e776 in ~QDialog (this=0xa721ec8) at dialogs/qdialog.cpp:298
#20 0xb7448cb5 in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#21 0xb73ecf8c in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#22 0xb73ecfce in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so
#23 0xb76365a3 in ?? () from /usr/lib/python2.6/dist-packages/sip.so
#24 0x080a90d5 in ?? ()
#25 0x0808e184 in ?? ()
#26 0x080a915b in ?? ()
#27 0x0808cb61 in ?? ()
#28 0x0808ee69 in PyDict_SetItem ()
#29 0x080909c1 in _PyModule_Clear ()
#30 0x080f17a2 in PyImport_Cleanup ()
#31 0x080fd90d in Py_Finalize ()
#32 0x080fd371 in ?? ()
#33 0x080fd55d in PyErr_PrintEx ()
#34 0x080fd7c2 in PyErr_Print ()
#35 0x080fe392 in PyRun_SimpleFileExFlags ()
#36 0x0805c882 in Py_Main ()
#37 0x0805b972 in main ()



What can I do? Thank

---

