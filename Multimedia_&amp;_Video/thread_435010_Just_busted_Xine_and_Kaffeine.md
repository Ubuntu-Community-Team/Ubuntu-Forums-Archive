---
title: "Just busted Xine and Kaffeine"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by rp2615 on 2007-05-06
Hello!

I've just updated to feisty and I noticed that both versions of xinelib and kaffeine in the official repositories are somewhat outdated, so I deleted the original packages for kaffeine and xinelib and I decided to try and build the latest stable versions of both.

I downloaded the sources for xinelib 1.1.6 and kaffeine 0.8.4 and everything seemed to work fine (with simple "./configure", "make" and "sudo make install" commands).
The problem is that now kaffeine will crash every time I try to open a video file or watch a dvb channel.

It crashes with this output:
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
0
kaffeine: Found DVB device.
/dev/dvb/0/frontend0 : opened ( ST STV0299 DVB-S )
/dev/dvb/0/frontend1 : : No such file or directory
DVB plugin loaded
.QLayout "unnamed" added to QWidget "unnamed", which already has a layout
kaffeine: PLAYLIST
kaffeine: PlayList: add 1 items to playlist
kaffeine: PlayList: Check for kaffeine/noatun/m3u/pls/asx playlist
kaffeine: PlayList: Try loading kaffeine playlist
kaffeine: PlaylistImport: kaffeine: /home/rp2615/.kde/share/apps/kaffeine/playlists/NEW.kaffeine
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kaffeine: Window manager: not KWin - using save fullscreen mode
kaffeine: Kaffeine:: Try to load service: xine_part
kaffeine: This is a KaffeinePart...
kaffeine: XinePart: Creating new XinePart...
kaffeine: XinePart: Using xine-config file: /home/rp2615/.kde/share/apps/kaffeine/xine-config
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
rp2615@experience-linux:~/Desktop/kaffeine-0.8.4$ kaffeine: KXineWidget: Display aspect ratio (v/h): 1.0887
kaffeine: KXineWidget: Using xine version 1.1.6
kaffeine: KXineWidget: Post-init xine engine
kaffeine: KXineWidget: Use audio driver auto
kaffeine: KXineWidget: Use video driver xvmc
kaffeine: KXineWidget: Init video driver
KCrash: Application 'kaffeine' crashing...

```


Here is the KDE crash handler backtrace:
```
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1238853936 (LWP 20998)]
[New Thread -1257649264 (LWP 21006)]
[New Thread -1245013104 (LWP 21000)]
[KCrash handler]
#6  0xb53c978f in KXineWidget::getXineLog () from /usr/lib/kde3/libxinepart.so
#7  0xb53c2ae1 in XinePart::slotError () from /usr/lib/kde3/libxinepart.so
#8  0xb53c30e5 in XinePart::qt_invoke () from /usr/lib/kde3/libxinepart.so
#9  0xb6b2488b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#10 0xb6b24dc0 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#11 0xb53c9c53 in KXineWidget::signalXineError ()
   from /usr/lib/kde3/libxinepart.so
#12 0xb53da7a4 in KXineWidget::initXine () from /usr/lib/kde3/libxinepart.so
#13 0xb53b0fe1 in XinePart::slotConfigXine ()
   from /usr/lib/kde3/libxinepart.so
#14 0xb53c30c7 in XinePart::qt_invoke () from /usr/lib/kde3/libxinepart.so
#15 0xb6b2488b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#16 0xb6b25330 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#17 0xb74824c9 in KAction::activated () from /usr/lib/libkdeui.so.4
#18 0xb74bacc2 in KAction::slotActivated () from /usr/lib/libkdeui.so.4
#19 0xb758806d in KAction::slotPopupActivated () from /usr/lib/libkdeui.so.4
#20 0xb7588331 in KAction::qt_invoke () from /usr/lib/libkdeui.so.4
#21 0xb6b2488b in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#22 0xb6eb0ae0 in QSignal::signal () from /usr/lib/libqt-mt.so.3
#23 0xb6b4481e in QSignal::activate () from /usr/lib/libqt-mt.so.3
#24 0xb6c4af1b in QPopupMenu::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#25 0xb748934e in KPopupMenu::mouseReleaseEvent () from /usr/lib/libkdeui.so.4
#26 0xb6b5b65d in QWidget::event () from /usr/lib/libqt-mt.so.3
#27 0xb6abba60 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#28 0xb6abdc1e in QApplication::notify () from /usr/lib/libqt-mt.so.3
#29 0xb7292ce2 in KApplication::notify () from /usr/lib/libkdecore.so.4
#30 0xb6a4e25d in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#31 0xb6a4cb9f in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#32 0xb6a4afac in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#33 0xb6a62180 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#34 0xb6ad6136 in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#35 0xb6ad5f46 in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#36 0xb6abd609 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#37 0x080758d5 in main ()

```

Does anyone have any idea of what is causing this? It even crashes when I try to go into the "xine engine parameters" dialog...

Thanks for the help!

---

