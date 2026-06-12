---
title: "amarok PID: 3074 Signal: 11 (Segmentation fault)"
date: 2010-03-22
forum: Multimedia Software
---

### Post by sinurge on 2010-03-22
Have installed amarok and also updated as of today all my amarok files bt whenever i run it a get the error btw am on lucid beta

Executable: amarok PID: 3074 Signal: 11 (Segmentation fault)

when i run it from the command line i get the following error.

amarok(3190)/kdecore (KSycoca) KSycocaPrivate:OpenDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-brian/ksycoca4"
amarok(3190)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::instance: instance(): ... initialised
amarok(3190)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readConfig: readConfig(): local zone= "Asia/Kolkata"
amarok(3190)/kdecore (K*TimeZone*) KSystemTimeZonesPrivate::readZoneTab: readZoneTab( "/usr/share/zoneinfo/zone.tab" )
TagLib: MPEG::Header:****() -- Invalid sample rate.
TagLib: MPEG::Header:****() -- Invalid sample rate.
TagLib: ID3v2.4 no longer supports the frame type TRDA.  It will be discarded from the tag.
TagLib: ID3v2.4 no longer supports the frame type TIME.  It will be discarded from the tag.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
amarok(3190)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(3190)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(3190)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
amarok(3190)/libplasma Plasma::ThemePrivate::config: using theme for app "amarok"
QGraphicsLinearLayout::removeAt: invalid index 1
<unknown program name>(3189)/: Communication problem with  "amarok" , it probably crashed. 
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.amarok was not provided by any .service files" " 

KCrash: Application 'amarok' crashing...
sock_file=/home/brian/.kde/socket-zack-lucid/kdeinit4__0


Adding some more information copied from the crash handler screen

 p, li { white-space: pre-wrap; }  plication: Amarok (amarok), signal: Segmentation fault
 [Current thread is 1 (Thread 0xb69c89b0 (LWP 3397))]
 
 Thread 9 (Thread 0xb4aa6b70 (LWP 3401)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x00951342 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0x0880c9c4 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
 #3  0x04761ce7 in ?? () from /usr/lib/libxine.so.1
 Backtrace stopped: previous frame inner to this frame (corrupt stack?)
 
 Thread 8 (Thread 0xb42a5b70 (LWP 3402)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x087f1b56 in poll () from /lib/tls/i686/cmov/libc.so.6
 #2  0x0853a32b in g_poll () from /lib/libglib-2.0.so.0
 #3  0x0852ce5c in ?? () from /lib/libglib-2.0.so.0
 #4  0x0852d268 in g_main_context_iteration () from /lib/libglib-2.0.so.0
 #5  0x064f159f in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #6  0x064c3ff9 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #7  0x064c444a in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
 #8  0x063c05a8 in QThread::exec() () from /usr/lib/libQtCore.so.4
 #9  0x04629a5a in ?? () from /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
 #10 0x063c332e in ?? () from /usr/lib/libQtCore.so.4
 #11 0x0094c96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
 #12 0x087ff9de in clone () from /lib/tls/i686/cmov/libc.so.6
 
 Thread 7 (Thread 0xafaa3b70 (LWP 3408)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x087f1b56 in poll () from /lib/tls/i686/cmov/libc.so.6
 #2  0x048f5a8f in ?? () from /usr/lib/xine/plugins/1.27/xineplug_ao_out_alsa.so
 Backtrace stopped: previous frame inner to this frame (corrupt stack?)
 
 Thread 6 (Thread 0xaf2a2b70 (LWP 3409)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x00951015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0x0880c96d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0x047729ee in ?? () from /usr/lib/libxine.so.1
 Backtrace stopped: previous frame inner to this frame (corrupt stack?)
 
 Thread 5 (Thread 0xaeaa1b70 (LWP 3410)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x00951015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0x0880c96d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0x047729ee in ?? () from /usr/lib/libxine.so.1
 Backtrace stopped: previous frame inner to this frame (corrupt stack?)
 
 Thread 4 (Thread 0xb3aa4b70 (LWP 3411)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x00951015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0x0880c96d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0x047729ee in ?? () from /usr/lib/libxine.so.1
 Backtrace stopped: previous frame inner to this frame (corrupt stack?)
 
 Thread 3 (Thread 0xb2ffab70 (LWP 3412)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x00951015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0x0880c96d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0x047729ee in ?? () from /usr/lib/libxine.so.1
 Backtrace stopped: previous frame inner to this frame (corrupt stack?)
 
 Thread 2 (Thread 0xb2198b70 (LWP 3414)):
 #0  0x00210422 in __kernel_vsyscall ()
 #1  0x00951015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
 #2  0x0880c96d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
 #3  0x030959d7 in ?? () from /usr/lib/libQtWebKit.so.4
 #4  0x03095a21 in ?? () from /usr/lib/libQtWebKit.so.4
 #5  0x0094c96e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
 #6  0x087ff9de in clone () from /lib/tls/i686/cmov/libc.so.6
 
 Thread 1 (Thread 0xb69c89b0 (LWP 3397)):
 [KCrash Handler]
 #6  0x021c8a52 in ?? () from /usr/lib/libQtGui.so.4
 #7  0x021cf07f in ?? () from /usr/lib/libQtGui.so.4
 #8  0x021cf2b7 in ?? () from /usr/lib/libQtGui.so.4
 #9  0x021ce89e in ?? () from /usr/lib/libQtGui.so.4
 #10 0x021ceab9 in ?? () from /usr/lib/libQtGui.so.4
 #11 0x021a7ec7 in QGraphicsScene::items() const () from /usr/lib/libQtGui.so.4
 #12 0x021ae719 in QGraphicsScene::itemsBoundingRect() const () from /usr/lib/libQtGui.so.4
 #13 0x021b58fd in QGraphicsScene::sceneRect() const () from /usr/lib/libQtGui.so.4
 #14 0x021d873d in QGraphicsView::sceneRect() const () from /usr/lib/libQtGui.so.4
 #15 0x015f1669 in Plasma::viewFor(QGraphicsItem const*) () from /usr/lib/libplasma.so.3
 #16 0x016aeb20 in Plasma::WebView::itemChange(QGraphicsItem::GraphicsItemChange, QVariant const&) () from /usr/lib/libplasma.so.3
 #17 0x021b89e2 in QGraphicsScene::addItem(QGraphicsItem*) () from /usr/lib/libQtGui.so.4
 #18 0x021b8947 in QGraphicsScene::addItem(QGraphicsItem*) () from /usr/lib/libQtGui.so.4
 #19 0x02186fca in QGraphicsItemPrivate::setParentItemHelper(QGraphicsItem*, QVariant const*, QVariant const*) () from /usr/lib/libQtGui.so.4
 #20 0x0218764f in QGraphicsItem::setParentItem(QGraphicsItem*) () from /usr/lib/libQtGui.so.4
 #21 0x015ab4d3 in Plasma::Containment::addApplet(Plasma::Applet*, QPointF const&, bool) () from /usr/lib/libplasma.so.3
 #22 0x015abbcd in ?? () from /usr/lib/libplasma.so.3
 #23 0x015abe49 in Plasma::Containment::addApplet(QString const&, QList<QVariant> const&, QRectF const&) () from /usr/lib/libplasma.so.3
 #24 0x0569a8db in ?? () from /usr/lib/kde4/amarok_containment_vertical.so
 #25 0x0569ae14 in ?? () from /usr/lib/kde4/amarok_containment_vertical.so
 #26 0x00af403b in Context::ContextView::loadConfig() () from /usr/lib/libamaroklib.so.1
 #27 0x00af5811 in Context::ContextView::showHome() () from /usr/lib/libamaroklib.so.1
 #28 0x00f43a6d in MainWindow::createContextView(Plasma::Containment*) () from /usr/lib/libamaroklib.so.1
 #29 0x00f45d26 in MainWindow::qt_metacall(QMetaObject::Call, int, void**) () from /usr/lib/libamaroklib.so.1
 #30 0x064cac3a in QMetaObject::metacall(QObject*, QMetaObject::Call, int, void**) () from /usr/lib/libQtCore.so.4
 #31 0x064d9375 in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/libQtCore.so.4
 #32 0x015bb8a3 in Plasma::Corona::containmentAdded(Plasma::Containment*) () from /usr/lib/libplasma.so.3
 #33 0x015c0c3d in ?? () from /usr/lib/libplasma.so.3
 #34 0x015bdb02 in Plasma::Corona::addContainment(QString const&, QList<QVariant> const&) () from /usr/lib/libplasma.so.3
 #35 0x00af2adb in Context::ContextScene::loadDefaultSetup() () from /usr/lib/libamaroklib.so.1
 #36 0x00f46b0b in MainWindow::init() () from /usr/lib/libamaroklib.so.1
 #37 0x00f48f7a in MainWindow::MainWindow() () from /usr/lib/libamaroklib.so.1
 #38 0x00f11ac2 in App::continueInit() () from /usr/lib/libamaroklib.so.1
 #39 0x00f16349 in App::App() () from /usr/lib/libamaroklib.so.1
 #40 0x0804fffc in _start ()

---

