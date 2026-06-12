---
title: "kaffeine crashes every time"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by noahsark1126 on 2007-10-20
I'm running Kubuntu Gutsy (x86), ATI X1400 video card with fglrx installed and working.  Every time I try to play a file (of any kind) in Kaffiene, it crashes.  I get the same result by opening up Kaffeine and going to "xine Engine Parameters."  I've tried reinstalling kaffeine and the xine plugins, with no luck.  Any way to fix this? 

Here's the backtrace of the crash:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1239472448 (LWP 11356)]
[New Thread -1254769776 (LWP 11364)]
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
#6  0xb4b5620c in ?? ()
   from /usr/lib/xine/plugins/1.1.7/xineplug_vo_out_xcbxv.so
#7  0x08432020 in ?? ()
#8  0x00000024 in ?? ()
#9  0x00000000 in ?? ()

---

### Post by bsimpson63 on 2007-10-23
I've got the same problem, let me know if you figure it out.

---

### Post by h@l0 on 2007-10-27
Same problem here exactly.  Same details and backtrace.

Can anyone help us out?

---

### Post by Gruelius on 2007-10-27
Yep, ive got the same problem too.

ATI X1950pro with FGLRX driver. Im guessing the card has a part to do with this error.

VLC player was quite jerky with the wrong colours, but sometimes it will work. Other times the whole screen will go black for a bit when it tries to play a video :S

---

### Post by Gruelius on 2007-10-28
I found some interesting stuff 

[http://ubuntuforums.org/showthread.php?p=3600210](http://ubuntuforums.org/showthread.php?p=3600210)

Have a look at the line:
# Driver Video da usare (predefinito auto)
# { auto  dxr3  aadxr3  xv  XDirectFB  SyncFB  opengl  xshm  xxmc  none  sdl  fb  xvmc }, default: 0
video.driver:xshm

Try setting it to xv , opengl and then maybe auto. From what ive heard Xv should be first preference, then opengl and if they both dont work auto.

Something to do with the ATI drivers being shitty is the problem :p

---

### Post by h@l0 on 2007-10-30
I didn't seem to have a xine-config in ~/.kde/share/apps/kaffeine/ .  Only in ~/.kde/share/apps/amarok/ and ~/.kde/share/apps/kplayer/ .  On the chance that that was my problem, I created it with the settings from the post referenced by Gruelius. 

Setting "video.driver:xv"  and "video.driver:auto" still crashed with the same backtrace as before.  Setting to "opengl" gave me a "xine error" message saying " Can't init Video Driver 'opengl' - trying 'auto'..." - then it crashed after clicking OK.

Many thanks to Gruelius for the help.  No dice yet, though.

---

### Post by Gruelius on 2007-10-30
Hey all, good news!

To fix just update to the latest fglrx driver with envy or by some other method. That fixed it for me.

---

### Post by wavesound on 2007-11-03
Hi All
 I have found that kaffeine is the only player that will play with my RME digi card.

It's only crashed once and here is the backtrace if it helps anyone on here.

********************************************************************

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[Thread debugging using libthread_db enabled]
[New Thread -1232673088 (LWP 7711)]
[New Thread -1334412368 (LWP 7741)]
[New Thread -1326019664 (LWP 7740)]
[New Thread -1317426256 (LWP 7739)]
[New Thread -1307145296 (LWP 7738)]
[New Thread -1294652496 (LWP 7737)]
[New Thread -1285952592 (LWP 7731)]
[New Thread -1264313424 (LWP 7730)]
[New Thread -1244210256 (LWP 7729)]
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
#6  0xaf928758 in KMpegPlugin::parse_audio () from /usr/lib/kde3/kfile_mpeg.so
#7  0xaf928a6d in KMpegPlugin::read_mpeg () from /usr/lib/kde3/kfile_mpeg.so
#8  0xaf92977e in KMpegPlugin::readInfo () from /usr/lib/kde3/kfile_mpeg.so
#9  0xb7d4953d in KFileMetaInfo::init () from /usr/lib/libkio.so.4
#10 0xb7d4b02c in KFileMetaInfo::KFileMetaInfo () from /usr/lib/libkio.so.4
#11 0x0808635c in ?? ()
#12 0x08093b1e in ?? ()
#13 0x0809a55b in ?? ()
#14 0x0809a733 in ?? ()
#15 0x0809ae65 in ?? ()
#16 0xb7090051 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb7090aec in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#18 0xb79a08a7 in KAction::activated () from /usr/lib/libkdeui.so.4
#19 0xb79d6674 in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#20 0xb79d661e in KAction::slotButtonClicked () from /usr/lib/libkdeui.so.4
#21 0xb79f2070 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#22 0xb7090051 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#23 0xb79dd4bd in KToolBarButton::buttonClicked () from /usr/lib/libkdeui.so.4
#24 0xb79dd679 in KToolBarButton::mouseReleaseEvent ()
   from /usr/lib/libkdeui.so.4
#25 0xb70ca825 in QWidget::event () from /usr/lib/libqt-mt.so.3
#26 0xb7a33add in KToolBarButton::event () from /usr/lib/libkdeui.so.4
#27 0xb7025f3e in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#28 0xb70264c8 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#29 0xb77aad8d in KApplication::notify () from /usr/lib/libkdecore.so.4
#30 0xb6fb71c5 in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#31 0xb6fb2873 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#32 0xb6fb0d59 in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#33 0xb6fca4db in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#34 0xb703ea2f in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#35 0xb703e952 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#36 0xb7024a4d in QApplication::exec () from /usr/lib/libqt-mt.so.3
#37 0x0806cbc3 in ?? ()
#38 0xb68acea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#39 0x08069511 in ?? ()



************************************************************************************

Also I don't get sound if I play a DV file.

Cheers
Bob

---

