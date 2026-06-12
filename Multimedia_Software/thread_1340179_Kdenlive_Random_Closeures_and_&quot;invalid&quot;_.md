---
title: "Kdenlive Random Closeures and &quot;invalid&quot; files"
date: 2009-11-28
forum: Multimedia Software
---

### Post by caffeinatedcupcake on 2009-11-28
okee so me and my friends use kedenlive for every video we edit and we constantly have to redo our videos due  to a basically unstable kdenlive sos obviously we need to get the fixed. Once kdenlive closed unexpectidley because it encountered an error... and this is what it said:

p, li { white-space: pre-wrap; }  Application: Kdenlive (kdenlive), signal SIGSEGV
 0x00007f1b3b4f5d21 in nanosleep () from /lib/libc.so.6
 [Current thread is 0 (LWP 3293)]
 
 Thread 4 (Thread 0x7f1b1e655950 (LWP 3431)):
 #0  0x00007f1b3b52c742 in select () from /lib/libc.so.6
 #1  0x00007f1b3ccdbf06 in ?? () from /usr/lib/libQtCore.so.4
 #2  0x00007f1b3cc14952 in ?? () from /usr/lib/libQtCore.so.4
 #3  0x00007f1b3b0353ba in start_thread () from /lib/libpthread.so.0
 #4  0x00007f1b3b533fcd in clone () from /lib/libc.so.6
 #5  0x0000000000000000 in ?? ()
 
 Thread 3 (Thread 0x7f1b1fef5950 (LWP 3449)):
 #0  0x00007f1b3b52c742 in select () from /lib/libc.so.6
 #1  0x00007f1b365831ae in ?? () from /usr/lib/libxcb.so.1
 #2  0x00007f1b36584cac in xcb_wait_for_reply () from /usr/lib/libxcb.so.1
 #3  0x00007f1b3a015fbc in _XReply () from /usr/lib/libX11.so.6
 #4  0x00007f1b3a009e13 in XSync () from /usr/lib/libX11.so.6
 #5  0x00007f1b2938aadd in ?? () from /usr/lib/libSDL-1.2.so.0
 #6  0x00007f1b2938acdb in ?? () from /usr/lib/libSDL-1.2.so.0
 #7  0x00007f1b2938f64a in ?? () from /usr/lib/libSDL-1.2.so.0
 #8  0x00007f1b2937fd4d in SDL_SetVideoMode () from /usr/lib/libSDL-1.2.so.0
 #9  0x00007f1b295ed9e2 in ?? () from /usr/lib/mlt/libmltsdl.so
 #10 0x00007f1b3b0353ba in start_thread () from /lib/libpthread.so.0
 #11 0x00007f1b3b533fcd in clone () from /lib/libc.so.6
 #12 0x0000000000000000 in ?? ()
 
 Thread 2 (Thread 0x7f1b206f6950 (LWP 3450)):
 #0  0x00007f1b3b0392e9 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
 #1  0x00007f1b295ecedb in ?? () from /usr/lib/mlt/libmltsdl.so
 #2  0x00007f1b3b0353ba in start_thread () from /lib/libpthread.so.0
 #3  0x00007f1b3b533fcd in clone () from /lib/libc.so.6
 #4  0x0000000000000000 in ?? ()
 
 Thread 1 (Thread 0x7f1b3f655750 (LWP 3293)):
 [KCrash Handler]
 #5  0x0000000000491a4c in QBasicAtomicInt::ref ()
 #6  0x000000000049507f in QList<CommentedTime>::QList ()
 #7  0x000000000054d7c2 in DocClipBase::commentedSnapMarkers ()
 #8  0x00000000005baf99 in ClipItem::paint ()
 #9  0x00007f1b3c729408 in ?? () from /usr/lib/libQtGui.so.4
 #10 0x00007f1b3c72b51e in QGraphicsScene::drawItems () from /usr/lib/libQtGui.so.4
 #11 0x00007f1b3c74d260 in QGraphicsView::paintEvent () from /usr/lib/libQtGui.so.4
 #12 0x00007f1b3c1916e6 in QWidget::event () from /usr/lib/libQtGui.so.4
 #13 0x00007f1b3c52b40b in QFrame::event () from /usr/lib/libQtGui.so.4
 #14 0x00007f1b3c747d1b in QGraphicsView::viewportEvent () from /usr/lib/libQtGui.so.4
 #15 0x00007f1b3ccfca68 in QCoreApplicationPrivate::sendThroughObjectEventFilters () from /usr/lib/libQtCore.so.4
 #16 0x00007f1b3c14075c in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #17 0x00007f1b3c14897a in QApplication::notify () from /usr/lib/libQtGui.so.4
 #18 0x00007f1b3e9cc26b in KApplication::notify () from /usr/lib/libkdeui.so.5
 #19 0x00007f1b3ccfd75c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #20 0x00007f1b3c1989a5 in QWidgetPrivate::drawWidget () from /usr/lib/libQtGui.so.4
 #21 0x00007f1b3c33c2fe in ?? () from /usr/lib/libQtGui.so.4
 #22 0x00007f1b3c18a050 in QWidgetPrivate::syncBackingStore () from /usr/lib/libQtGui.so.4
 #23 0x00007f1b3c19157d in QWidget::event () from /usr/lib/libQtGui.so.4
 #24 0x00007f1b3c545d9b in QMainWindow::event () from /usr/lib/libQtGui.so.4
 #25 0x00007f1b3ead7838 in KXmlGuiWindow::event () from /usr/lib/libkdeui.so.5
 #26 0x00007f1b3c14078d in QApplicationPrivate::notify_helper () from /usr/lib/libQtGui.so.4
 #27 0x00007f1b3c14897a in QApplication::notify () from /usr/lib/libQtGui.so.4
 #28 0x00007f1b3e9cc26b in KApplication::notify () from /usr/lib/libkdeui.so.5
 #29 0x00007f1b3ccfd75c in QCoreApplication::notifyInternal () from /usr/lib/libQtCore.so.4
 #30 0x00007f1b3ccfe3ca in QCoreApplicationPrivate::sendPostedEvents () from /usr/lib/libQtCore.so.4
 #31 0x00007f1b3cd271e3 in ?? () from /usr/lib/libQtCore.so.4
 #32 0x00007f1b3751320a in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
 #33 0x00007f1b375168e0 in ?? () from /usr/lib/libglib-2.0.so.0
 #34 0x00007f1b37516a7c in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
 #35 0x00007f1b3cd26e6f in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
 #36 0x00007f1b3c1d8bef in ?? () from /usr/lib/libQtGui.so.4
 #37 0x00007f1b3ccfc002 in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
 #38 0x00007f1b3ccfc3cd in QEventLoop::exec () from /usr/lib/libQtCore.so.4
 #39 0x00007f1b3ccfe694 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
 #40 0x000000000049813b in main ()






we will be greatful if you help us with this delema. :D
weird...smileys in the code? O_O

---

