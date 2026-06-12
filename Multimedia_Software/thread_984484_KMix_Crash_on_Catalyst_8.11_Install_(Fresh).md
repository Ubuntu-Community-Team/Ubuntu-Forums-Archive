---
title: "KMix Crash on Catalyst 8.11 Install (Fresh)"
date: 2008-11-16
forum: Multimedia Software
---

### Post by jpichie on 2008-11-16
I am on Kubuntu Intrepid 8.10, I followed the following guide:
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")

I am using an 2x ATI Radeon 3870 (crossfire configuration).
If I have to, I will try it with a single card to see if it makes any difference.

I am then receiving the following error at the end of the installs.
```
Application: KMix (kmix), signal SIGABRT
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread 0x7f0a1694a6f0 (LWP 5871)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#5  0x00007f0a161b7fd5 in raise () from /lib/libc.so.6
#6  0x00007f0a161b9b43 in abort () from /lib/libc.so.6
#7  0x00007f0a14e886b5 in qt_message_output () from /usr/lib/libQtCore.so.4
#8  0x00007f0a14e887fd in qFatal () from /usr/lib/libQtCore.so.4
#9  0x00007f0a156e1493 in ?? () from /usr/lib/libsolid.so.4
#10 0x00007f0a156e17a7 in ?? () from /usr/lib/libsolid.so.4
#11 0x00007f0a14f8d134 in QMetaObject::activate ()
   from /usr/lib/libQtCore.so.4
#12 0x00007f0a156f0e32 in ?? () from /usr/lib/libsolid.so.4
#13 0x00007f0a157139dc in ?? () from /usr/lib/libsolid.so.4
#14 0x00007f0a14bd8ea3 in ?? () from /usr/lib/libQtDBus.so.4
#15 0x00007f0a14bdfeef in ?? () from /usr/lib/libQtDBus.so.4
#16 0x00007f0a14f87da5 in QObject::event () from /usr/lib/libQtCore.so.4
#17 0x00007f0a13fe3c3d in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#18 0x00007f0a13feb9ea in QApplication::notify () from /usr/lib/libQtGui.so.4
#19 0x00007f0a15dacb8b in KApplication::notify () from /usr/lib/libkdeui.so.5
#20 0x00007f0a14f78d61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#21 0x00007f0a14f799fa in QCoreApplicationPrivate::sendPostedEvents ()
   from /usr/lib/libQtCore.so.4
#22 0x00007f0a14fa14d3 in ?? () from /usr/lib/libQtCore.so.4
#23 0x00007f0a1163fd3b in g_main_context_dispatch ()
   from /usr/lib/libglib-2.0.so.0
#24 0x00007f0a1164350d in ?? () from /usr/lib/libglib-2.0.so.0
#25 0x00007f0a116436cb in g_main_context_iteration ()
   from /usr/lib/libglib-2.0.so.0
#26 0x00007f0a14fa115f in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#27 0x00007f0a14075a9f in ?? () from /usr/lib/libQtGui.so.4
#28 0x00007f0a14f77682 in QEventLoop::processEvents ()
   from /usr/lib/libQtCore.so.4
#29 0x00007f0a14f7780d in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#30 0x00007f0a14f79cbd in QCoreApplication::exec ()
   from /usr/lib/libQtCore.so.4
#31 0x00007f0a1651352a in kdemain () from /usr/lib/libkdeinit4_kmix.so
#32 0x00007f0a161a3466 in __libc_start_main () from /lib/libc.so.6
#33 0x0000000000400659 in _start ()
#0  0x00007f0a1622d5f0 in nanosleep () from /lib/libc.so.6

```

Could anyone please shed some light on what is going on? I am new to the whole sound and video on Linux (never really used one as a Desktop).

---

### Post by jpichie on 2008-11-17
**UPDATE**

I was able to get everything to install (kernel source, drivers and amdccc).
Once I have aticonfig create the new xorg.conf file, and reboot, I cannot boot into X. It is giving me an ABI mismatch as well as "failed to load module DRI" error...

Any help is extremely appreciated.

---

### Post by jpichie on 2008-11-17
**UPDATE**
I tried a new install of Intrepid, but only had one ATI Radeon 3870 installed (not 2 in CF mode).

I installed from the ubuntu repos, worked fine.
If I try to boot with the fglrx driver, it will not boot into X.

If I change the same config driver from "fglrx" to "radeon" it boots...

I would really like to have 3D working.

---

