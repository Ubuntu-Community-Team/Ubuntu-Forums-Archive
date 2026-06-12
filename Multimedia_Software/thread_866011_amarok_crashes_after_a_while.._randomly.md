---
title: "amarok crashes after a while.. randomly"
date: 2008-07-21
forum: Multimedia Software
---

### Post by ichbinesderelch on 2008-07-21
when i'm running amarok it just crashes after a while, sometimes a longer while, sometimes a shorter one, i ran it from konsole to get any output of the error, but the only thing that came out was:

david #  ~$  amarokapp
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8bc3c50 ): KAccel object alr              eady contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8bc3c50 ): KAccel object alr              eady contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow              /PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChang              ed(const QString&)
STARTUP
QColor::setRgb: RGB parameter(s) out of range
QWidget::setMinimumSize: The smallest allowed size is (0,0)
QComboBox::setCurrentItem: (speakerComboBox) Index 1 out of range

Beendet


means just nothing to me ;)
HELP!

edit:
*** glibc detected *** amarokapp: double free or corruption (!prev): 0x08dc7fc8 ***
======= Backtrace: =========
/lib/libc.so.6[0xb5aa5a44]
/lib/libc.so.6(cfree+0x9c)[0xb5aa73cc]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb5c697d1]
/opt/kde/lib/libkhtml.so.4[0xb76d8955]
/opt/kde/lib/libkhtml.so.4[0xb76d8df7]
/opt/kde/lib/libkhtml.so.4[0xb76d8f9f]
/opt/kde/lib/libkhtml.so.4[0xb769bbcf]
/opt/kde/lib/libkhtml.so.4[0xb76af35c]
/opt/kde/lib/libkhtml.so.4[0xb76bc346]
/opt/kde/lib/libkhtml.so.4[0xb762e334]
/opt/kde/lib/libkhtml.so.4[0xb762e708]
/opt/kde/lib/libkhtml.so.4[0xb762e708]
/opt/kde/lib/libkhtml.so.4[0xb7639d97]
/opt/kde/lib/libkhtml.so.4(_ZN9KHTMLPart5clearEv+0xaff)[0xb75e5955]
/opt/kde/lib/libkhtml.so.4(_ZN9KHTMLPart5beginERK4KURLii+0x36)[0xb7609a2a]
/opt/kde/lib/libamarok.so.0(_ZN8HTMLView3setERK7QString+0x4d)[0xb7bf32ad]
/opt/kde/lib/libamarok.so.0(_ZN15CurrentTrackJob11completeJobEv+0x2c9)[0xb7b9ed79]
/opt/kde/lib/libamarok.so.0(_ZN13ThreadManager5eventEP6QEvent+0x507)[0xb7da4807]
/opt/qt/lib/libqt-mt.so.3(_ZN12QApplication14internalNotifyEP7QObjectP6QEvent+0xcf)[0xb64f7723]
/opt/qt/lib/libqt-mt.so.3(_ZN12QApplication6notifyEP7QObjectP6QEvent+0xed)[0xb64f894f]
/opt/kde/lib/libkdecore.so.4(_ZN12KApplication6notifyEP7QObjectP6QEvent+0x92)[0xb6c11372]
/opt/qt/lib/libqt-mt.so.3(_ZN12QApplication16sendPostedEventsEP7QObjecti+0x15f)[0xb64f9519]
/opt/qt/lib/libqt-mt.so.3(_ZN12QApplication16sendPostedEventsEv+0x27)[0xb64f9663]
/opt/qt/lib/libqt-mt.so.3(_ZN10QEventLoop13processEventsEj+0x1f4)[0xb64a5f40]
/opt/qt/lib/libqt-mt.so.3(_ZN10QEventLoop9enterLoopEv+0x39)[0xb650ebc5]
/opt/qt/lib/libqt-mt.so.3(_ZN10QEventLoop4execEv+0x26)[0xb650ea9e]
/opt/qt/lib/libqt-mt.so.3(_ZN12QApplication4execEv+0x20)[0xb64f7cb6]
amarokapp[0x804c0f7]
/lib/libc.so.6(__libc_start_main+0xe5)[0xb5a505c5]
amarokapp(_ZN6QGListD0Ev+0x85)[0x804b6b1]
======= Memory map: ========
08048000-0806c000 r-xp 00000000 08:12 315616     /opt/kde/bin/amarokapp
0806c000-0806d000 rw-p 00024000 08:12 315616     /opt/kde/bin/amarokapp
0806d000-08077000 rw-p 0806d000 00:00 0
08213000-0910e000 rw-p 08213000 00:00 0          [heap]
b027f000-b0374000 rw-p b027f000 00:00 0
b0374000-b0400000 ---p b0374000 00:00 0
b0455000-b04d6000 rw-p b0455000 00:00 0
b04d6000-b04e6000 r--p 00000000 08:12 2265189    /usr/share/fonts/TTF/VeraIt.ttf
b04e6000-b04f6000 rw-s 00000000 00:08 10715138   /SYSV0056a4d6 (deleted)
b04f6000-b0506000 rw-s 00000000 00:0d 2107       /dev/snd/pcmC0D0p
b0506000-b0507000 ---p b0506000 00:00 0
b0507000-b0d07000 rwxp b0507000 00:00 0
b0d07000-b0d2d000 r-xp 00000000 08:12 2052850    /usr/lib/libwavpack.so.1.0.2
b0d2d000-b0d2e000 rw-p 00025000 08:12 2052850    /usr/lib/libwavpack.so.1.0.2
b0d39000-b0d4f000 r-xp 00000000 08:12 2136221    /usr/lib/xine/plugins/1.23/xineplug_decode_mad.so
b0d4f000-b0d50000 rw-p 00015000 08:12 2136221    /usr/lib/xine/plugins/1.23/xineplug_decode_mad.so
b0d50000-b0da2000 r-xp 00000000 08:12 2057521    /usr/lib/libFLAC.so.8.2.0
b0da2000-b0da3000 rw-p 00052000 08:12 2057521    /usr/lib/libFLAC.so.8.2.0
b0db1000-b0db5000 r-xp 00000000 08:12 2136200    /usr/lib/xine/plugins/1.23/xineplug_inp_rtp.so
b0db5000-b0db6000 rw-p 00003000 08:12 2136200    /usr/lib/xine/plugins/1.23/xineplug_inp_rtp.so
b0db6000-b0db7000 r-xp 00000000 08:12 2136180    /usr/lib/xine/plugins/1.23/xineplug_dmx_mpeg_elem.so
b0db7000-b0db8000 rw-p 00000000 08:12 2136180    /usr/lib/xine/plugins/1.23/xineplug_dmx_mpeg_elem.so
b0db8000-b0db9000 r-xp 00000000 08:12 2136208    /usr/lib/xine/plugins/1.23/xineplug_dmx_yuv_frames.so
b0db9000-b0dba000 rw-p 00000000 08:12 2136208    /usr/lib/xine/plugins/1.23/xineplug_dmx_yuv_frames.so
b0dba000-b0dbd000 r-xp 00000000 08:12 2136198    /usr/lib/xine/plugins/1.23/xineplug_wavpack.so
b0dbd000-b0dbe000 rw-p 00002000 08:12 2136198    /usr/lib/xine/plugins/1.23/xineplug_wavpack.so
b0dbe000-b0dc4000 r-xp 00000000 08:12 2136146    /usr/lib/xine/plugins/1.23/xineplug_dmx_sputext.so
b0dc4000-b0dc5000 rw-p 00005000 08:12 2136146    /usr/lib/xine/plugins/1.23/xineplug_dmx_sputex 

got more error output there!

---

