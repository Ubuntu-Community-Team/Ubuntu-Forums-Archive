---
title: "amarok crashes when stop button pushed - jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by d1ng3r on 2009-04-26
Hi,

I have read the article about ubuntu-bug, but cannot use it because it generates an error that I do not know how to repair.

I recently upgraded by installing ubuntu Jaunty AMD64. I installed amarok2:2.0.2 and am having the following problem:

Amarok Opens. When I try to play a file it doesn't play. It just restarts playing over and over again. There is not sound. When I click stop amarok crashes:
 p, li { white-space: pre-wrap; }  A Fatal Error Occurred
 The application Amarok (amarok) crashed and caused the signal 6 (SIGABRT).
Please help us improve the software you use by filing a report at [[COLOR=#0057ae]_http://bugs.kde.org_[/COLOR]]("http://bugs.kde.org/"). Useful details include how to reproduce the error, documents that were loaded, etc.

 p, li { white-space: pre-wrap; }  Application: Amarok (amarok), signal SIGABRT
 0x00007fd2c895dd21 in nanosleep () from /lib/libc.so.6
 [Current thread is 0 (LWP 6498)]
 
 Thread 14 (Thread 0x7fd2b9781950 (LWP 6499)):
 #0  0x00007fd2cb1ab56d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2bb4ccf91 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 13 (Thread 0x7fd2b8711950 (LWP 6500)):
 #0  0xffffffffff6001bb in ?? ()
 #1  0x00007fd2b8710d40 in ?? ()
 #2  0x00007fffd45fe5fc in ?? ()
 Backtrace stopped: previous frame identical to this frame (corrupt stack?)
 
 Thread 12 (Thread 0x7fd2b3afe950 (LWP 6506)):
 #0  0x00007fd2c8992496 in poll () from /lib/libc.so.6
 #1  0x00007fd2b7d0b969 in ?? () from /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so
 #2  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 11 (Thread 0x7fd2b78f9950 (LWP 6507)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2bb4de353 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 10 (Thread 0x7fd2b70f8950 (LWP 6510)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2c943f939 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
 #2  0x00007fd2c5cb45e4 in ?? () from /usr/lib/libthreadweaver.so.4
 #3  0x00007fd2c5cb6d93 in ?? () from /usr/lib/libthreadweaver.so.4
 #4  0x00007fd2c5cb6dac in ?? () from /usr/lib/libthreadweaver.so.4
 #5  0x00007fd2c5cb530f in ?? () from /usr/lib/libthreadweaver.so.4
 #6  0x00007fd2c5cb5769 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
 #7  0x00007fd2c943e952 in ?? () from /usr/lib/libQtCore.so.4
 #8  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #9  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #10 0x0000000000000000 in ?? ()
 
 Thread 9 (Thread 0x7fd2ab09f950 (LWP 6511)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2c943f939 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
 #2  0x00007fd2c5cb45e4 in ?? () from /usr/lib/libthreadweaver.so.4
 #3  0x00007fd2c5cb6d93 in ?? () from /usr/lib/libthreadweaver.so.4
 #4  0x00007fd2c5cb530f in ?? () from /usr/lib/libthreadweaver.so.4
 #5  0x00007fd2c5cb5769 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
 #6  0x00007fd2c943e952 in ?? () from /usr/lib/libQtCore.so.4
 #7  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #8  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #9  0x0000000000000000 in ?? ()
 
 Thread 8 (Thread 0x7fd2a2b6a950 (LWP 6514)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2c943f939 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
 #2  0x00007fd2c5cb45e4 in ?? () from /usr/lib/libthreadweaver.so.4
 #3  0x00007fd2c5cb6d93 in ?? () from /usr/lib/libthreadweaver.so.4
 #4  0x00007fd2c5cb530f in ?? () from /usr/lib/libthreadweaver.so.4
 #5  0x00007fd2c5cb5769 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
 #6  0x00007fd2c943e952 in ?? () from /usr/lib/libQtCore.so.4
 #7  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #8  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #9  0x0000000000000000 in ?? ()
 
 Thread 7 (Thread 0x7fd2a2369950 (LWP 6515)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2c943f939 in QWaitCondition::wait () from /usr/lib/libQtCore.so.4
 #2  0x00007fd2c5cb45e4 in ?? () from /usr/lib/libthreadweaver.so.4
 #3  0x00007fd2c5cb6d93 in ?? () from /usr/lib/libthreadweaver.so.4
 #4  0x00007fd2c5cb530f in ?? () from /usr/lib/libthreadweaver.so.4
 #5  0x00007fd2c5cb5769 in ThreadWeaver::Thread::run () from /usr/lib/libthreadweaver.so.4
 #6  0x00007fd2c943e952 in ?? () from /usr/lib/libQtCore.so.4
 #7  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #8  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #9  0x0000000000000000 in ?? ()
 
 Thread 6 (Thread 0x7fd297664950 (LWP 6516)):
 #0  0x00007fd2c8994742 in select () from /lib/libc.so.6
 #1  0x00007fd2bb4f60a4 in xine_usec_sleep () from /usr/lib/libxine.so.1
 #2  0x00007fd2bb4dadeb in ?? () from /usr/lib/libxine.so.1
 #3  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #4  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #5  0x0000000000000000 in ?? ()
 
 Thread 5 (Thread 0x7fd296a7a950 (LWP 6517)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2bb4d0afb in ?? () from /usr/lib/libxine.so.1
 #2  0x00007fd2bb4d6a6e in ?? () from /usr/lib/libxine.so.1
 #3  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #4  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #5  0x0000000000000000 in ?? ()
 
 Thread 4 (Thread 0x7fd2960ac950 (LWP 6518)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2bb4d0afb in ?? () from /usr/lib/libxine.so.1
 #2  0x00007fd2bb4d7b1e in ?? () from /usr/lib/libxine.so.1
 #3  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #4  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #5  0x0000000000000000 in ?? ()
 
 Thread 3 (Thread 0x7fd2958ab950 (LWP 6519)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2bb4e102b in ?? () from /usr/lib/libxine.so.1
 #2  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7fd28f582950 (LWP 6522)):
 #0  0x00007fd2cb1ab2e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007fd2bb4de353 in ?? () from /usr/lib/libxine.so.1
 #2  0x00007fd2cb1a73ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007fd2c899bfcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 1 (Thread 0x7fd2cc273760 (LWP 6498)):
 [KCrash Handler]
 #5  0x00007fd2c88e8fb5 in raise () from /lib/libc.so.6
 #6  0x00007fd2c88eabc3 in abort () from /lib/libc.so.6
 #7  0x00007fd2c9436885 in qt_message_output () from /usr/lib/libQtCore.so.4
 #8  0x00007fd2c94369cb in qFatal () from /usr/lib/libQtCore.so.4
 #9  0x00007fd2cb8813b8 in EngineController::slotAboutToFinish () from /usr/lib/libamaroklib.so.1
 #10 0x00007fd2cb884ce5 in EngineController::qt_metacall () from /usr/lib/libamaroklib.so.1
 #11 0x00007fd2c953d1f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
 #12 0x00007fd2c5815a60 in ?? () from /usr/lib/libphonon.so.4
 #13 0x00007fd2c58166d6 in Phonon::MediaObject::qt_metacall () from /usr/lib/libphonon.so.4
 #14 0x00007fd2c953d1f2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
 #15 0x00007fd2bb74127d in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
 #16 0x00007fd2bb743d45 in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
 #17 0x00007fd2c9537848 in QObject::event () from /usr/lib/libQtCore.so.4
 #18 0x00007fd2ca0d083d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #19 0x00007fd2ca0d8a2a in QApplication::notify () from /usr/lib/libQtGui.so.4
 #20 0x00007fd2cbe3326b in KApplication::notify () from /usr/lib/libkdeui.so.5
 #21 0x00007fd2c952775c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #22 0x00007fd2c95283ca in QCoreApplicationPrivate::sendPostedEvents () from /usr/lib/libQtCore.so.4
 #23 0x00007fd2c95511e3 in ?? () from /usr/lib/libQtCore.so.4
 #24 0x00007fd2c182720a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
 #25 0x00007fd2c182a8e0 in ?? () from /usr/lib/libglib-2.0.so.0
 #26 0x00007fd2c182aa7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
 #27 0x00007fd2c9550e6f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
 #28 0x00007fd2ca168c9f in ?? () from /usr/lib/libQtGui.so.4
 #29 0x00007fd2c9526002 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
 #30 0x00007fd2c95263cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
 #31 0x00007fd2c9528694 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
 #32 0x0000000000533127 in _start ()
 
 

When I run amarok from the commandline this is the output: 
amarok(6498) Phonon::KdePlatformPlugin::createBackend: using backend:  "Xine"
Object::connect: No such slot MainWindow::showStatistics() in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/MainWindow.cpp:692
Object::connect:  (receiver name: 'MainWindow')
QLayout: Attempting to add QLayout "" to MainWindow "MainWindow", which already has a layout
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
QWidget::insertAction: Attempt to insert null action
amarok(6498) Plasma::Applet::save: saving to "1"
amarok(6498) Context::ContextView::setContainment: "" Line:  599
amarok(6498) Plasma::ThemePrivate::config: using theme for app "amarok"
amarok(6498) Plasma::Applet::save: saving to "2"
amarok(6498) Plasma::Applet::save: saving to "3"
amarok(6498) Plasma::Applet::save: saving to "4"
amarok(6498) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6498) Context::ColumnContainment::insertInGrid: "" Line:  603
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
Object::connect: No such slot FileBrowser::Widget::setDir( const QString& ) in /build/buildd/amarok-2.0.2mysql5.1.30/amarok-2.0.2/src/browsers/filebrowser/FileBrowser.cpp:112
Object::connect:  (sender name:   'KBookmarkHandler')
Object::connect:  (receiver name: 'FileBrowser::Widget')
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
link XMLID_7_ hasn't been detected!
link XMLID_7_ hasn't been detected!
Couldn't resolve property: radialGradient3986
amarok(6498) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6498) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
amarok(6498) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x5200064
dinger@dingers-pc:~$ amarok(6498) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QPainter::begin: Cannot paint on a null pixmap
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
amarok(6498) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
QString::arg: Argument missing: Amarok - No track playing., 0:00
QString::arg: Argument missing: Amarok - No track playing., 0:00
amarok(6498) CurrentTrack::dataUpdated: CurrentTrack::dataUpdated
ASSERT: "d" in file /usr/include/ksharedptr.h, line 120
KCrash: Application 'amarok' crashing...
sock_file=/home/dinger/.kde/socket-dingers-pc/kdeinit4__0

---

### Post by allmyfingersandtoes on 2009-05-17
[http://osdir.com/ml/kde-bugs-dist/2009-04/msg10182.html](http://osdir.com/ml/kde-bugs-dist/2009-04/msg10182.html) says "the gstreamer backend is known to be buggy". Replace phonon-backend-gstreamer with phonon-backend-xine.

---

