---
title: "mythfrontend crashes in mytharchive"
date: 2008-02-07
forum: Mythbuntu
---

### Post by rhp on 2008-02-07
Hi all, when using mytharchive mythfrontend crashes when I select the step "Create DVD".
I tried the same on another machine (installing mytharchive freshly) with the same result.
Running in gdb gives me the following stack trace:

#0  0xb6bf4fd6 in UIListBtnType::Reset () from /usr/lib/libmyth-0.20.2.so.0
#1  0xb49388b6 in MythburnWizard::updateArchiveList () from /usr/lib/mythtv/plugins/libmytharchive.so
#2  0xb4938c1c in MythburnWizard::setCategory () from /usr/lib/mythtv/plugins/libmytharchive.so
#3  0xb4938f56 in MythburnWizard::getArchiveList () from /usr/lib/mythtv/plugins/libmytharchive.so
#4  0xb493ddf2 in MythburnWizard::wireUpTheme () from /usr/lib/mythtv/plugins/libmytharchive.so
#5  0xb493ff8d in MythburnWizard::MythburnWizard () from /usr/lib/mythtv/plugins/libmytharchive.so
#6  0xb491018d in runCreateDVD () from /usr/lib/mythtv/plugins/libmytharchive.so
#7  0xb49105b3 in FormatCallback () from /usr/lib/mythtv/plugins/libmytharchive.so
#8  0xb6a4a36e in MythThemedMenuPrivate::handleAction () from /usr/lib/libmythui-0.20.2.so.0
#9  0xb6a4af35 in MythThemedMenuPrivate::keyHandler () from /usr/lib/libmythui-0.20.2.so.0
#10 0xb6a4bcae in MythThemedMenuPrivate::keyPressHandler () from /usr/lib/libmythui-0.20.2.so.0
#11 0xb6a4bea4 in MythThemedMenu::keyPressEvent () from /usr/lib/libmythui-0.20.2.so.0
#12 0xb6a01d86 in MythMainWindow::eventFilter () from /usr/lib/libmythui-0.20.2.so.0
#13 0xb6217e40 in QObject::activate_filters () from /usr/lib/libqt-mt.so.3
#14 0xb6217ebe in QObject::event () from /usr/lib/libqt-mt.so.3
#15 0xb624f5b3 in QWidget::event () from /usr/lib/libqt-mt.so.3
#16 0xb61afaf0 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#17 0xb61b1ac0 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#18 0xb614227d in QApplication::sendSpontaneousEvent () from /usr/lib/libqt-mt.so.3
#19 0xb6132c69 in QETWidget::translateKeyEvent () from /usr/lib/libqt-mt.so.3
#20 0xb613f04f in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#21 0xb61561a4 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#22 0xb61ca1ce in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#23 0xb61c9fde in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#24 0xb61b1699 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#25 0x0806fb3e in ?? ()
#26 0xb5a79050 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#27 0x08065f61 in ?? ()

So, what is the problem here? And how can I fix it?

Ronald

---

### Post by rhp on 2008-02-14
Turns out the MePo theme was causing problems.
Using another theme it runs fine.

---

