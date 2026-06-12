---
title: "My kaffeine player does not start"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by Squirrel- on 2006-11-18
I've got KDE and have proglem with kaffeine. 

I watch last sunday tv at klock 9 pm and it works. But after 11.30pm player did not work anymore. 

When I klick kaffeine, kaffeine's logo blink littlebit but then disappears. /var/log/syslog shows nothing. But if I make systest user and start kaffeine, kaffeine work's fine until I start watch tv (channel's search does working) and give KDE crash raport.

Crash raport:
```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found) <-- (=repeat 43 times)
[Thread debugging using libthread_db enabled]
[New Thread -1237813584 (LWP 5994)]
[New Thread -1374319712 (LWP 6248)]
[New Thread -1253655648 (LWP 6247)]
[New Thread -1363154016 (LWP 6245)]
[New Thread -1354761312 (LWP 6244)]
[New Thread -1345029216 (LWP 6243)]
[New Thread -1334748256 (LWP 6242)]
[New Thread -1322255456 (LWP 6241)]
[New Thread -1308623968 (LWP 6240)]
[New Thread -1290437728 (LWP 6239)]
[New Thread -1262048352 (LWP 6238)]
[New Thread -1241617504 (LWP 5998)]
(no debugging symbols found) (repeat 179 times)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb662d3fb in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb712c97e in _kde_IceTransGetConnectionNumber ()
   from /usr/lib/libDCOP.so.4
#3  0xb712c62f in _kde_IceTransRead () from /usr/lib/libDCOP.so.4
#4  0xb71264af in _kde_IceRead () from /usr/lib/libDCOP.so.4
#5  0xb712ac9f in KDE_IceProcessMessages () from /usr/lib/libDCOP.so.4
#6  0xb71163f9 in DCOPClient::callInternal () from /usr/lib/libDCOP.so.4
#7  0xb71166dd in DCOPClient::callInternal () from /usr/lib/libDCOP.so.4
#8  0xb711b127 in DCOPClient::call () from /usr/lib/libDCOP.so.4
#9  0xb711b187 in DCOPClient::call () from /usr/lib/libDCOP.so.4
#10 0xb711b388 in DCOPClient::disconnectDCOPSignal ()
   from /usr/lib/libDCOP.so.4
#11 0xb711bcf9 in DCOPObject::~DCOPObject () from /usr/lib/libDCOP.so.4
#12 0xb782a38a in KDirListerCache::~KDirListerCache ()
   from /usr/lib/libkio.so.4
#13 0xb781e2f4 in KServiceTypeProfile::clear () from /usr/lib/libkio.so.4
#14 0xb63e354f in __cxa_finalize () from /lib/tls/i686/cmov/libc.so.6
#15 0xb7763d03 in ?? () from /usr/lib/libkio.so.4
#16 0xb79ad120 in ?? () from /usr/lib/libkio.so.4
#17 0xb79a81fc in ?? () from /usr/lib/libkio.so.4
#18 0xbfefa268 in ?? ()
#19 0xb796b30c in _fini () from /usr/lib/libkio.so.4
#20 0xb796b30c in _fini () from /usr/lib/libkio.so.4
#21 0xb7fb14ce in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#22 0xb63e3299 in exit () from /lib/tls/i686/cmov/libc.so.6
#23 0xb6abd142 in QApplication::x11_initialize_style ()
   from /usr/lib/libqt-mt.so.3
#24 0xb72019cd in KApplication::xioErrhandler () from /usr/lib/libkdecore.so.4
#25 0xb7201a19 in KApplication::xioErrhandler () from /usr/lib/libkdecore.so.4
#26 0xb6691f4d in _XIOError () from /usr/lib/libX11.so.6
#27 0xb6693817 in _XSend () from /usr/lib/libX11.so.6
#28 0xb66947b0 in _XEventsQueued () from /usr/lib/libX11.so.6
#29 0xb6680262 in XPending () from /usr/lib/libX11.so.6
#30 0xb6add360 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#31 0xb6b5125e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#32 0xb6b5106e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#33 0xb6b38731 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#34 0x08072a05 in ?? ()
#35 0xb63cc8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#36 0x080725f1 in ?? ()

```

How I can repair my kaffeine player?

---

### Post by Squirrel- on 2006-11-19
I've thinking, that I need to reinstall my Kubuntu. Nowhere I can find solution to have my player to working.

---

### Post by corstar on 2006-12-12
Maybe it's too late for this advise, but after my kaffeine stopped working, I just entered "killall kaffeine" in a console. Problem solved.

It stopped working after I installed dvb drivers.

---

