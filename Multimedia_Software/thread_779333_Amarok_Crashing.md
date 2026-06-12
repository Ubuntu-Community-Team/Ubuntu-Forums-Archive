---
title: "Amarok Crashing"
date: 2008-05-02
forum: Multimedia Software
---

### Post by thevjm on 2008-05-02
The last time I had Amarok open, I added some FLAC files.

I restarted Amarok, but now it wont open. It opens up Kmail and gives me this:

```
Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. Information describing the crash is below, so just click send, or if you have time, write a brief description of how the crash happened first.

Many thanks.







The information below is to help the developers identify the problem, please do not modify it.



======== DEBUG INFORMATION  =======
Version:    1.4.9.1
Engine:     xine-engine
Build date: Apr 23 2008
CC version: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
KDElibs:    3.5.9
Qt:         3.3.8b
TagLib:     1.4.0
CPU count:  2
NDEBUG:     true
==== file `which amarokapp` =======
/usr/bin/amarokapp: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped


==== (gdb) bt =====================
[Thread debugging using libthread_db enabled]
[New Thread 0x7f72acdd6750 (LWP 9165)]
[New Thread 0x43803950 (LWP 9203)]
[New Thread 0x43002950 (LWP 9202)]
[New Thread 0x42801950 (LWP 9201)]
[New Thread 0x40b43950 (LWP 9200)]
[New Thread 0x417ff950 (LWP 9199)]
0x00007f72b6b994df in waitpid () from /lib/libc.so.6
#0  0x00007f72b6b994df in waitpid () from /lib/libc.so.6
#1  0x0000000000405fd0 in Amarok::Crash::crashHandler ()
#2  <signal handler called>
#3  0x00007f72ba56a2b9 in CollectionView::renderTreeModeView ()
   from /usr/lib/libamarok.so.0
#4  0x00007f72ba56bcc3 in CollectionView::renderView ()
   from /usr/lib/libamarok.so.0
#5  0x00007f72ba57a74d in CollectionView::qt_invoke ()
   from /usr/lib/libamarok.so.0
#6  0x00007f72b62cffd0 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#7  0x00007f72b62d09a5 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#8  0x00007f72ba55b5c1 in BrowserBar::polish () from /usr/lib/libamarok.so.0
#9  0x00007f72b6306cc9 in QWidget::show () from /usr/lib/libqt-mt.so.3
#10 0x00007f72b6303973 in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
#11 0x00007f72b6306cd7 in QWidget::show () from /usr/lib/libqt-mt.so.3
#12 0x00007f72b92802bb in KSystemTray::minimizeRestore ()
   from /usr/lib/libkdeui.so.4
#13 0x00007f72b928bf16 in KSystemTray::activateOrHide ()
   from /usr/lib/libkdeui.so.4
#14 0x00007f72b92eeb16 in KSystemTray::mousePressEvent ()
   from /usr/lib/libkdeui.so.4
#15 0x00007f72b6304381 in QWidget::event () from /usr/lib/libqt-mt.so.3
#16 0x00007f72ba7abc5d in Amarok::TrayIcon::event ()
   from /usr/lib/libamarok.so.0
#17 0x00007f72b626833a in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#18 0x00007f72b626a410 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#19 0x00007f72b8de840d in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#20 0x00007f72b61f9280 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#21 0x00007f72b61f7e94 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#22 0x00007f72b61f6060 in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
#23 0x00007f72b620d106 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#24 0x00007f72b62825bf in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#25 0x00007f72b62822ab in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#26 0x00007f72b6269e00 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#27 0x0000000000404d01 in ?? ()
#28 0x00007f72b6b1a1c4 in __libc_start_main () from /lib/libc.so.6
#29 0x0000000000404599 in ?? ()
#30 0x00007fffc2d887e8 in ?? ()
#31 0x0000000000000000 in ?? ()
#0  0x00007f72b6b994df in waitpid () from /lib/libc.so.6
No symbol table info available.
#1  0x0000000000405fd0 in Amarok::Crash::crashHandler ()
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0x00007f72ba56a2b9 in CollectionView::renderTreeModeView ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#4  0x00007f72ba56bcc3 in CollectionView::renderView ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#5  0x00007f72ba57a74d in CollectionView::qt_invoke ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#6  0x00007f72b62cffd0 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#7  0x00007f72b62d09a5 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#8  0x00007f72ba55b5c1 in BrowserBar::polish () from /usr/lib/libamarok.so.0
No symbol table info available.
#9  0x00007f72b6306cc9 in QWidget::show () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#10 0x00007f72b6303973 in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#11 0x00007f72b6306cd7 in QWidget::show () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#12 0x00007f72b92802bb in KSystemTray::minimizeRestore ()
   from /usr/lib/libkdeui.so.4
No symbol table info available.
#13 0x00007f72b928bf16 in KSystemTray::activateOrHide ()
   from /usr/lib/libkdeui.so.4
No symbol table info available.
#14 0x00007f72b92eeb16 in KSystemTray::mousePressEvent ()
   from /usr/lib/libkdeui.so.4
No symbol table info available.
#15 0x00007f72b6304381 in QWidget::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#16 0x00007f72ba7abc5d in Amarok::TrayIcon::event ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#17 0x00007f72b626833a in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#18 0x00007f72b626a410 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#19 0x00007f72b8de840d in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
No symbol table info available.
#20 0x00007f72b61f9280 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#21 0x00007f72b61f7e94 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#22 0x00007f72b61f6060 in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#23 0x00007f72b620d106 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#24 0x00007f72b62825bf in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#25 0x00007f72b62822ab in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#26 0x00007f72b6269e00 in QApplication::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#27 0x0000000000404d01 in ?? ()
No symbol table info available.
#28 0x00007f72b6b1a1c4 in __libc_start_main () from /lib/libc.so.6
No symbol table info available.
#29 0x0000000000404599 in ?? ()
No symbol table info available.
#30 0x00007fffc2d887e8 in ?? ()
No symbol table info available.
#31 0x0000000000000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 6 (Thread 0x417ff950 (LWP 9199)):
#0  0x00007f72b257fe1d in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00007f72a95ff325 in ?? () from /usr/lib/libxine.so.1
#2  0x00007f72b257b3f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f72b6bd3b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()
Thread 5 (Thread 0x40b43950 (LWP 9200)):
#0  0x00007f72b6bcac76 in poll () from /lib/libc.so.6
#1  0x00007f72a461428d in ?? () from /usr/lib/libpulse.so.0
#2  0x00007f72a460925a in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#3  0x00007f72a460a598 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#4  0x00007f72a460a650 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#5  0x00007f72a46141ad in ?? () from /usr/lib/libpulse.so.0
#6  0x00007f72a462fd0d in ?? () from /usr/lib/libpulse.so.0
#7  0x00007f72b257b3f7 in start_thread () from /lib/libpthread.so.0
#8  0x00007f72b6bd3b2d in clone () from /lib/libc.so.6
#9  0x0000000000000000 in ?? ()
Thread 4 (Thread 0x42801950 (LWP 9201)):
#0  0x00007f72b257fb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00007f72a960e963 in ?? () from /usr/lib/libxine.so.1
#2  0x00007f72b257b3f7 in start_thread () from /lib/libpthread.so.0
#3  0x00007f72b6bd3b2d in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()
Thread 3 (Thread 0x43002950 (LWP 9202)):
#0  0x00007f72b257fb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00007f72a9602702 in ?? () from /usr/lib/libxine.so.1
#2  0x00007f72a96092be in ?? () from /usr/lib/libxine.so.1
#3  0x00007f72b257b3f7 in start_thread () from /lib/libpthread.so.0
#4  0x00007f72b6bd3b2d in clone () from /lib/libc.so.6
#5  0x0000000000000000 in ?? ()
Thread 2 (Thread 0x43803950 (LWP 9203)):
#0  0x00007f72b257fb99 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x00007f72a9611b8b in xine_event_wait () from /usr/lib/libxine.so.1
#2  0x00007f72a9611c09 in ?? () from /usr/lib/libxine.so.1
#3  0x00007f72b257b3f7 in start_thread () from /lib/libpthread.so.0
#4  0x00007f72b6bd3b2d in clone () from /lib/libc.so.6
#5  0x0000000000000000 in ?? ()
Thread 1 (Thread 0x7f72acdd6750 (LWP 9165)):
#0  0x00007f72b6b994df in waitpid () from /lib/libc.so.6
#1  0x0000000000405fd0 in Amarok::Crash::crashHandler ()
#2  <signal handler called>
#3  0x00007f72ba56a2b9 in CollectionView::renderTreeModeView ()
   from /usr/lib/libamarok.so.0
#4  0x00007f72ba56bcc3 in CollectionView::renderView ()
   from /usr/lib/libamarok.so.0
#5  0x00007f72ba57a74d in CollectionView::qt_invoke ()
   from /usr/lib/libamarok.so.0
#6  0x00007f72b62cffd0 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#7  0x00007f72b62d09a5 in QObject::activate_signal ()
   from /usr/lib/libqt-mt.so.3
#8  0x00007f72ba55b5c1 in BrowserBar::polish () from /usr/lib/libamarok.so.0
#9  0x00007f72b6306cc9 in QWidget::show () from /usr/lib/libqt-mt.so.3
#10 0x00007f72b6303973 in QWidget::showChildren () from /usr/lib/libqt-mt.so.3
#11 0x00007f72b6306cd7 in QWidget::show () from /usr/lib/libqt-mt.so.3
#12 0x00007f72b92802bb in KSystemTray::minimizeRestore ()
   from /usr/lib/libkdeui.so.4
#13 0x00007f72b928bf16 in KSystemTray::activateOrHide ()
   from /usr/lib/libkdeui.so.4
#14 0x00007f72b92eeb16 in KSystemTray::mousePressEvent ()
   from /usr/lib/libkdeui.so.4
#15 0x00007f72b6304381 in QWidget::event () from /usr/lib/libqt-mt.so.3
#16 0x00007f72ba7abc5d in Amarok::TrayIcon::event ()
   from /usr/lib/libamarok.so.0
#17 0x00007f72b626833a in QApplication::internalNotify ()
   from /usr/lib/libqt-mt.so.3
#18 0x00007f72b626a410 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#19 0x00007f72b8de840d in KApplication::notify ()
   from /usr/lib/libkdecore.so.4
#20 0x00007f72b61f9280 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#21 0x00007f72b61f7e94 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#22 0x00007f72b61f6060 in QApplication::x11ProcessEvent ()
   from /usr/lib/libqt-mt.so.3
#23 0x00007f72b620d106 in QEventLoop::processEvents ()
   from /usr/lib/libqt-mt.so.3
#24 0x00007f72b62825bf in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#25 0x00007f72b62822ab in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#26 0x00007f72b6269e00 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#27 0x0000000000404d01 in ?? ()
#28 0x00007f72b6b1a1c4 in __libc_start_main () from /lib/libc.so.6
#29 0x0000000000404599 in ?? ()
#30 0x00007fffc2d887e8 in ?? ()
#31 0x0000000000000000 in ?? ()
#0  0x00007f72b6b994df in waitpid () from /lib/libc.so.6


==== kdBacktrace() ================
```

---

### Post by benerivo on 2008-05-02
You could try deleting your user settings for amarok (ie. set it back to the default settings) by deleting...

/home/benerivo/.kde/share/apps/amarok/

---

### Post by thevjm on 2008-05-03
Worked great. Thanks.

---

