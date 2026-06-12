---
title: "k9copy crashes making mpeg-4's but not iso's"
date: 2008-09-01
forum: Multimedia Software
---

### Post by tnunamak on 2008-09-01
For some reason, I can rip ISO files perfectly with k9copy, but when I use the mpeg-4 option, I always get an immediate crash and the following backtrace with no other information:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb66cd6c0 (LWP 14638)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x0810e0e7 in ?? ()
#7  0x0810ec8c in ?? ()
#8  0x0807305e in ?? ()
#9  0x080aa069 in ?? ()
#10 0xb6f93704 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb6f941e9 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#12 0xb78c3b19 in KAction::activated () from /usr/lib/libkdeui.so.4
#13 0xb7904452 in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#14 0xb79043ec in KAction::slotButtonClicked () from /usr/lib/libkdeui.so.4
#15 0xb79efa78 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#16 0xb6f93704 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb78fb584 in KToolBarButton::buttonClicked () from /usr/lib/libkdeui.so.4
#18 0xb78fb853 in KToolBarButton::mouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#19 0xb6fc9e33 in QWidget::event () from /usr/lib/libqt-mt.so.3
#20 0xb7972061 in KToolBarButton::event () from /usr/lib/libkdeui.so.4
#21 0xb6f27c36 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#22 0xb6f29de5 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#23 0xb76e8672 in KApplication::notify () from /usr/lib/libkdecore.so.4
#24 0xb6eb8301 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#25 0xb6eb6f8d in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#26 0xb6eb512f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#27 0xb6ecc943 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#28 0xb6f42f90 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#29 0xb6f42c8e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#30 0xb6f297df in QApplication::exec () from /usr/lib/libqt-mt.so.3
#31 0x0809104e in ?? ()
#32 0xb6730450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#33 0x08068311 in ?? ()

Any ideas? I've been searching for solutions but haven't found any.

---

### Post by tnunamak on 2008-09-02
bump

---

### Post by thikrat on 2008-09-04
Same thing happening with me, any luck?  amd64, hardy

---

