---
title: "Amarok not recognising IPOD"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by DOD1951 on 2006-10-07
Using Amarok 1.4.3. Trying to connect to IPOD using autodetect get this message: 
No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.
Tried to mount it manually and get this message:
Media Device: iPod mounted at /media/ipod already locked! If you are sure that this is an error, then remove the file /media/ipod/iPod_Control/iTunes/iTunesLock and try again.
Tried removing the iTunesLock file but as soon as started Amarok the file reappeared again. Have to assume that Amarok creates this file.
Anyone got any ideas or the same problem?

---

### Post by kkuzia on 2006-10-07
I have the first portion of your problem with the DBUS and HAL daemons error message and I have yet to figure out what to do.  I am following this thread right now:
[http://www.ubuntuforums.org/showthread.php?t=103071&highlight=ubuntu+ipod](http://www.ubuntuforums.org/showthread.php?t=103071&highlight=ubuntu+ipod)
in hopes of figuring how what is going wrong.  At one point my iPod was at least showing up on my desktop when I plugged it in, but not sure what the situation is now.

---

### Post by alecjw on 2006-10-07
My iPod video (5g) wasn't detected by amarok before. Now that i've installed the kubuntu-desktop package, it's detected by amarok, but not as an iPod. When i try to tell ti that it is an iPod, Kmail opens, showing this message:
> 
[noparse]
Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. Information 
describing the crash is below, so just click send, or if you have time, write 
a brief description of how the crash happened first.

Many thanks.






The information below is to help the developers identify the problem, please 
do not modify it.



======== DEBUG INFORMATION  =======
Version:    1.4.3
Engine:     xine-engine
Build date: Oct  1 2006
CC version: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu4)
KDElibs:    3.5.4
Qt:         3.3.6
TagLib:     1.4.0
CPU count:  2
NDEBUG:     true
==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: symbolic link to `/usr/bin/amarokapp'


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1256711952 (LWP 4864)]
[New Thread -1302479968 (LWP 4951)]
[New Thread -1294087264 (LWP 4950)]
[New Thread -1283806304 (LWP 4949)]
[New Thread -1260512352 (LWP 4948)]
[New Thread -1268905056 (LWP 4947)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d1734b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d191 in amaroK::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb6918c53 in strlen () from /lib/tls/i686/cmov/libc.so.6
#5  0xb12950ee in g_strdup () from /usr/lib/libglib-2.0.so.0
#6  0xb12f60de in itdb_device_list_devices () from /usr/lib/libgpod.so.0
#7  0xb12f6c39 in itdb_device_list_devices () from /usr/lib/libgpod.so.0
#8  0xb120de41 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#9  0xb120e7e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#10 0xb120e8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#11 0xb12f4f78 in itdb_device_new () from /usr/lib/libgpod.so.0
#12 0xb12e673c in itdb_set_mountpoint () from /usr/lib/libgpod.so.0
#13 0xb12edf78 in itdb_parse () from /usr/lib/libgpod.so.0
#14 0xb131070f in IpodMediaDevice::openDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#15 0xb7cd321c in MediaDevice::connectDevice () from /usr/lib/libamarok.so.0
#16 0xb7cd3994 in MediaBrowser::addDevice () from /usr/lib/libamarok.so.0
#17 0xb7cd6dd5 in MediaBrowser::mediumAdded () from /usr/lib/libamarok.so.0
#18 0xb7cd723f in MediaBrowser::pluginSelected () from /usr/lib/libamarok.so.0
#19 0xb7cd78b6 in MediaBrowser::qt_invoke () from /usr/lib/libamarok.so.0
#20 0xb63d179f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#21 0xb7ce73dd in MediumPluginManager::selectedPlugin ()
   from /usr/lib/libamarok.so.0
#22 0xb7ce7d40 in MediumPluginManager::finished ()
   from /usr/lib/libamarok.so.0
#23 0xb7c31a32 in AmarokConfigDialog::updateSettings ()
   from /usr/lib/libamarok.so.0
#24 0xb761575e in KConfigDialog::qt_invoke () from /usr/lib/libkdeui.so.4
#25 0xb7c2dcd3 in AmarokConfigDialog::qt_invoke ()
   from /usr/lib/libamarok.so.0
#26 0xb63d18cc in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0xb63d2244 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0xb752898c in KDialogBase::okClicked () from /usr/lib/libkdeui.so.4
#29 0xb75289c2 in KDialogBase::slotOk () from /usr/lib/libkdeui.so.4
#30 0xb76155d9 in KDialogBase::qt_invoke () from /usr/lib/libkdeui.so.4
#31 0xb7615743 in KConfigDialog::qt_invoke () from /usr/lib/libkdeui.so.4
#32 0xb7c2dcd3 in AmarokConfigDialog::qt_invoke ()
   from /usr/lib/libamarok.so.0
#33 0xb63d179f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#34 0xb63d2244 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#35 0xb6766da7 in QButton::clicked () from /usr/lib/libqt-mt.so.3
#36 0xb646fe30 in QButton::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#37 0xb6408571 in QWidget::event () from /usr/lib/libqt-mt.so.3
#38 0xb6368a98 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#39 0xb636ac56 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#40 0xb7374062 in KApplication::notify () from /usr/lib/libkdecore.so.4
#41 0xb62fb3fd in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#42 0xb62fa062 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#43 0xb62f814c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#44 0xb630f320 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#45 0xb638316e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#46 0xb6382f7e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#47 0xb636a641 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#48 0x0804bced in ?? ()
#49 0xbff338bc in ?? ()
#50 0xbff33a54 in ?? ()
#51 0x00000013 in ?? ()
#52 0x08067ae8 in _IO_stdin_used ()
#53 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6d1734b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0x0804d191 in amaroK::Crash::crashHandler ()
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb6918c53 in strlen () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb12950ee in g_strdup () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb12f60de in itdb_device_list_devices () from /usr/lib/libgpod.so.0
No symbol table info available.
#7  0xb12f6c39 in itdb_device_list_devices () from /usr/lib/libgpod.so.0
No symbol table info available.
#8  0xb120de41 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb120e7e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0xb120e8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#11 0xb12f4f78 in itdb_device_new () from /usr/lib/libgpod.so.0
No symbol table info available.
#12 0xb12e673c in itdb_set_mountpoint () from /usr/lib/libgpod.so.0
No symbol table info available.
#13 0xb12edf78 in itdb_parse () from /usr/lib/libgpod.so.0
No symbol table info available.
#14 0xb131070f in IpodMediaDevice::openDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
No symbol table info available.
#15 0xb7cd321c in MediaDevice::connectDevice () from /usr/lib/libamarok.so.0
No symbol table info available.
#16 0xb7cd3994 in MediaBrowser::addDevice () from /usr/lib/libamarok.so.0
No symbol table info available.
#17 0xb7cd6dd5 in MediaBrowser::mediumAdded () from /usr/lib/libamarok.so.0
No symbol table info available.
#18 0xb7cd723f in MediaBrowser::pluginSelected () from /usr/lib/libamarok.so.0
No symbol table info available.
#19 0xb7cd78b6 in MediaBrowser::qt_invoke () from /usr/lib/libamarok.so.0
No symbol table info available.
#20 0xb63d179f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#21 0xb7ce73dd in MediumPluginManager::selectedPlugin ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#22 0xb7ce7d40 in MediumPluginManager::finished ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#23 0xb7c31a32 in AmarokConfigDialog::updateSettings ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#24 0xb761575e in KConfigDialog::qt_invoke () from /usr/lib/libkdeui.so.4
No symbol table info available.
#25 0xb7c2dcd3 in AmarokConfigDialog::qt_invoke ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#26 0xb63d18cc in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#27 0xb63d2244 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#28 0xb752898c in KDialogBase::okClicked () from /usr/lib/libkdeui.so.4
No symbol table info available.
#29 0xb75289c2 in KDialogBase::slotOk () from /usr/lib/libkdeui.so.4
No symbol table info available.
#30 0xb76155d9 in KDialogBase::qt_invoke () from /usr/lib/libkdeui.so.4
No symbol table info available.
#31 0xb7615743 in KConfigDialog::qt_invoke () from /usr/lib/libkdeui.so.4
No symbol table info available.
#32 0xb7c2dcd3 in AmarokConfigDialog::qt_invoke ()
   from /usr/lib/libamarok.so.0
No symbol table info available.
#33 0xb63d179f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#34 0xb63d2244 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#35 0xb6766da7 in QButton::clicked () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#36 0xb646fe30 in QButton::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#37 0xb6408571 in QWidget::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#38 0xb6368a98 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#39 0xb636ac56 in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#40 0xb7374062 in KApplication::notify () from /usr/lib/libkdecore.so.4
No symbol table info available.
#41 0xb62fb3fd in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#42 0xb62fa062 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
No symbol table info available.
#43 0xb62f814c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#44 0xb630f320 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#45 0xb638316e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#46 0xb6382f7e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#47 0xb636a641 in QApplication::exec () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#48 0x0804bced in ?? ()
No symbol table info available.
#49 0xbff338bc in ?? ()
No symbol table info available.
#50 0xbff33a54 in ?? ()
No symbol table info available.
#51 0x00000013 in ?? ()
No symbol table info available.
#52 0x08067ae8 in _IO_stdin_used ()
No symbol table info available.
#53 0x00000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 6 (Thread -1268905056 (LWP 4947)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d13a8c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3abadff in _x_metronom_init () from /usr/lib/libxine.so.1
#3  0xb45e043c in ?? ()
#4  0xb45e0444 in ?? ()
#5  0x08643bb8 in ?? ()
#6  0xb45e043c in ?? ()
#7  0x00595bcd in ?? ()
#8  0x00000000 in ?? ()
Thread 5 (Thread -1260512352 (LWP 4948)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb696f803 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb37f219f in ?? ()
   from /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_alsa.so
#3  0xb4de1398 in ?? ()
#4  0x00000001 in ?? ()
#5  0x0000014d in ?? ()
#6  0x00000000 in ?? ()
Thread 4 (Thread -1283806304 (LWP 4949)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d13816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3ac91d2 in _x_ao_channels2mode () from /usr/lib/libxine.so.1
#3  0x0867ce5c in ?? ()
#4  0x0867ce44 in ?? ()
#5  0x00000000 in ?? ()
Thread 3 (Thread -1294087264 (LWP 4950)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d13816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3abe4cc in _x_dummy_fifo_buffer_new () from /usr/lib/libxine.so.1
#3  0x08789a24 in ?? ()
#4  0xb7f87d40 in _dl_make_stack_executable () from /lib/ld-linux.so.2
#5  0xb3ac4d65 in _x_audio_decoder_init () from /usr/lib/libxine.so.1
#6  0x0877e7b8 in ?? ()
Thread 2 (Thread -1302479968 (LWP 4951)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d13816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3ace16c in xine_event_wait () from /usr/lib/libxine.so.1
#3  0x08791d20 in ?? ()
Thread 1 (Thread -1256711952 (LWP 4864)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d1734b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d191 in amaroK::Crash::crashHandler ()
#3  <signal handler called>
#4  0xb6918c53 in strlen () from /lib/tls/i686/cmov/libc.so.6
#5  0xb12950ee in g_strdup () from /usr/lib/libglib-2.0.so.0
#6  0xb12f60de in itdb_device_list_devices () from /usr/lib/libgpod.so.0
#7  0xb12f6c39 in itdb_device_list_devices () from /usr/lib/libgpod.so.0
#8  0xb120de41 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#9  0xb120e7e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#10 0xb120e8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#11 0xb12f4f78 in itdb_device_new () from /usr/lib/libgpod.so.0
#12 0xb12e673c in itdb_set_mountpoint () from /usr/lib/libgpod.so.0
#13 0xb12edf78 in itdb_parse () from /usr/lib/libgpod.so.0
#14 0xb131070f in IpodMediaDevice::openDevice ()
   from /usr/lib/kde3/libamarok_ipod-mediadevice.so
#15 0xb7cd321c in MediaDevice::connectDevice () from /usr/lib/libamarok.so.0
#16 0xb7cd3994 in MediaBrowser::addDevice () from /usr/lib/libamarok.so.0
#17 0xb7cd6dd5 in MediaBrowser::mediumAdded () from /usr/lib/libamarok.so.0
#18 0xb7cd723f in MediaBrowser::pluginSelected () from /usr/lib/libamarok.so.0
#19 0xb7cd78b6 in MediaBrowser::qt_invoke () from /usr/lib/libamarok.so.0
#20 0xb63d179f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#21 0xb7ce73dd in MediumPluginManager::selectedPlugin ()
   from /usr/lib/libamarok.so.0
#22 0xb7ce7d40 in MediumPluginManager::finished ()
   from /usr/lib/libamarok.so.0
#23 0xb7c31a32 in AmarokConfigDialog::updateSettings ()
   from /usr/lib/libamarok.so.0
#24 0xb761575e in KConfigDialog::qt_invoke () from /usr/lib/libkdeui.so.4
#25 0xb7c2dcd3 in AmarokConfigDialog::qt_invoke ()
   from /usr/lib/libamarok.so.0
#26 0xb63d18cc in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#27 0xb63d2244 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#28 0xb752898c in KDialogBase::okClicked () from /usr/lib/libkdeui.so.4
#29 0xb75289c2 in KDialogBase::slotOk () from /usr/lib/libkdeui.so.4
#30 0xb76155d9 in KDialogBase::qt_invoke () from /usr/lib/libkdeui.so.4
#31 0xb7615743 in KConfigDialog::qt_invoke () from /usr/lib/libkdeui.so.4
#32 0xb7c2dcd3 in AmarokConfigDialog::qt_invoke ()
   from /usr/lib/libamarok.so.0
#33 0xb63d179f in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#34 0xb63d2244 in QObject::activate_signal () from /usr/lib/libqt-mt.so.3
#35 0xb6766da7 in QButton::clicked () from /usr/lib/libqt-mt.so.3
#36 0xb646fe30 in QButton::mouseReleaseEvent () from /usr/lib/libqt-mt.so.3
#37 0xb6408571 in QWidget::event () from /usr/lib/libqt-mt.so.3
#38 0xb6368a98 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
#39 0xb636ac56 in QApplication::notify () from /usr/lib/libqt-mt.so.3
#40 0xb7374062 in KApplication::notify () from /usr/lib/libkdecore.so.4
#41 0xb62fb3fd in QApplication::sendSpontaneousEvent ()
   from /usr/lib/libqt-mt.so.3
#42 0xb62fa062 in QETWidget::translateMouseEvent ()
   from /usr/lib/libqt-mt.so.3
#43 0xb62f814c in QApplication::x11ProcessEvent () from /usr/lib/libqt-mt.so.3
#44 0xb630f320 in QEventLoop::processEvents () from /usr/lib/libqt-mt.so.3
#45 0xb638316e in QEventLoop::enterLoop () from /usr/lib/libqt-mt.so.3
#46 0xb6382f7e in QEventLoop::exec () from /usr/lib/libqt-mt.so.3
#47 0xb636a641 in QApplication::exec () from /usr/lib/libqt-mt.so.3
#48 0x0804bced in ?? ()
#49 0xbff338bc in ?? ()
#50 0xbff33a54 in ?? ()
#51 0x00000013 in ?? ()
#52 0x08067ae8 in _IO_stdin_used ()
#53 0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


==== kdBacktrace() ================
[/noparse]

Which I sent, adding a few comments.

---

### Post by DOD1951 on 2006-10-18
Stll cannot get around this Ipod mounted at /media/ipod already locked issue in Amarok. Anyone been successful at getting Ipod to work with Amarok?

---

### Post by DOD1951 on 2006-11-02
bump

---

### Post by kaffekopp on 2006-12-13
I've got this same problem with a ipod video 80gb

The really annoying thing is that it worked perfectly until today. Then, all of a sudden I got the "Media Device: iPod mounted at /media/ipod already locked!" message... when I removed the lock file, it seemed to work, but I get a crash notification like the one posted above when I try to transfer files or disconnect the ipod. 

Before it went wrong, I was transferring some video files with gtkpod... but I don't think this could be the problem...? 

Help would be greatly appreciated!

---

### Post by meshica7 on 2006-12-13
I get the same message:

**Media Device: failed to create lockfile on iPod mounted at /media/ipod: Read-only file system**

 I am using Ubuntu 6.06 on a PowerMac G4.My i-Pod shows up on my desktop and Amarok lunches and then displays the aforementioned warning.
The fact that no-one has posted a solution to any of these concerns is a bit scary :neutral: .I would really like to get my 5 G Video i-Pod working with Linux.
I should mention that my i-Pod was oringinally configured for OS X.Perhaps this is the reason for the lockfile issue.

---

### Post by meshica7 on 2006-12-13
So,now I am mounting my i-Pod using gtkpod and playing its files using Amarok.Amarok even displays my album info from the i-Pod (artwork,tags,etc.).The weird thing is that when I try to mount my i-Pod within Amarok I still get the same lockfile message even though I am playing files right off my i-Pod :-k !I have also gotten XMMS to play files and display artwork using gtkpod.However,neither Amarok or XMMS will play Apple's own file format (whose name escapes me at the moment).
 I still have not tried to add/remove files using gtkpod.I am afraid of screwing up the content and losing data (over 2700 songs,podcasts,and videos).So,I'll start with creating a playlist and moving files into it and see how that goes.
Anyone else use gtkpod?What is your experience (good/bad) with this app?
I also tried Banshee and Listen but the do not recognize my i-Pod either.

[U]UPDATE: Cannot sync changes with any success (i.e. new playlists,add files,etc) with gtkpod. 
[/U]
[COLOR="RoyalBlue"]Error:

Error opening /media/ipod/iPod_Control/Artwork/F1028_1.ithmb: Read-only file system
Error opening /media/ipod/iPod_Control/Artwork/F1029_1.ithmb: Read-only file system
Failed to open /media/ipod/iPod_Control/Artwork/ArtworkDB: Read-only file system
Couldn't create /media/ipod/iPod_Control/Artwork/ArtworkDB
Opening of '/media/ipod/iPod_Control/iTunes/iTunesDB' for writing failed.
[/COLOR]

 It appears that,at least in my case,since my i-Pod was formated using OS X it will not allow for any alterations to the i-Pod files.Perhaps a new,clean i-Pod formated using a Linux machine wil have a better chance of syncing/mounting using Amarok or similiar apps.
Just a thought :)

---

### Post by kaffekopp on 2006-12-15
Thanks for your info, Meshica.

Hm, what really annoys me is that it WAS working. I swear! I'm using edgy, 6.10, and have never used my ipod on anything but edgy, so it can't be just the problem of formatting it on mac osx... 

I can transfer and sync files with gtkpod and gpixpod.

Anyone have any idea what the deal is with the ituneslock file? What does it do? How is it created, by what software? 

C'mon, we HAVE to figure this one out... :)

---

### Post by sygin on 2006-12-19
> **kaffekopp said:**
> Thanks for your info, Meshica.

Hm, what really annoys me is that it WAS working. I swear! I'm using edgy, 6.10, and have never used my ipod on anything but edgy, so it can't be just the problem of formatting it on mac osx... 

I can transfer and sync files with gtkpod and gpixpod.

C'mon, we HAVE to figure this one out... :)

Hi mate,

I too have had the same problem, Amarok worked well and then stopped working. It would crash when I disconnected. After thinking for a while, I remembered that I had put podcasts onto my IPOD Nano 4Gb with gtkpod which worked well. I used gtkpod because Amarok was giving me problems with podcasts.
 
I have just removed all my podcasts (and cleaned up orphaned files) and Amarok now works. Using gtkpod, I right-clicked on podcasts after connecting, and selected 'delete all podcasts'.

Try this 'fix,' and let us know.

PS: backup podcasts before deleting them.

Cheers
Sygin

---

### Post by Kingfield on 2006-12-20
try sudo amarok or make sure that ur ipod is mounted to media, not mnt.

---

### Post by kaffekopp on 2006-12-20
Sygin, I could kiss you! It worked like a charm :KS 

So, just to repeat the steps I did, so that hopefully as many as possible can benefit from this... (this is just a step-by-step reproduction of Sygin's instruction above)

(Back-up your podcasts first!)
1. Open gtkpod and click "Read"
2. Open the "Ipod" on the top of the left hand list
3. Right-click "Podcasts" under "Ipod" 
4. Select "Remove all podcasts from Ipod"
5. Click the "File" menu -> "Check iPod's Files". You will now get an "Orphaned". Right-click it, and choose something like "delete including files"
6. Click "sync" and exit gtkpod

Next time I tried to refuse the pod in Amarok, I got the same error as before, that the iPod was already locked. However, When I clicked "Remove", it worked without problems.

I guess this means that I'll have to stop transferring podcasts in gtkpod. As far as I remember, there were no problems transferring audio podcasts in Amarok, so it shouldn't be too much of a problem. 

When it comes to video podcasts, my Amarok doesn't handle it yet, so I guess what I'll have to do is to save video podcasts somewhere I can find them on my harddisk and transfer them manually ("add files") in gtkpod. 


> **sygin said:**
> Hi mate,

I too have had the same problem, Amarok worked well and then stopped working. It would crash when I disconnected. After thinking for a while, I remembered that I had put podcasts onto my IPOD Nano 4Gb with gtkpod which worked well. I used gtkpod because Amarok was giving me problems with podcasts.
 
I have just removed all my podcasts (and cleaned up orphaned files) and Amarok now works. Using gtkpod, I right-clicked on podcasts after connecting, and selected 'delete all podcasts'.

Try this 'fix,' and let us know.

PS: backup podcasts before deleting them.

Cheers
Sygin

---

### Post by datakid on 2007-01-30
Ok, I personally don't think that "deleting the podcasts" is a real solution to this problem (which I am also experiencing). 

I'm running 6.10 on dell dimension 9200. The iPod was initially used on an iBook. 

I don't want to use >1 music players either - I appreciate the range, but I've come to like amarok and want it to work - it's obvious that it did at some point - does anyone know if there was an upgrade immeditely before it stopped working? I've only just installed...

---

### Post by kaffekopp on 2007-01-30
Well, yes... and no...
While it's true that you delete the podcasts in gtkpod, there's nothing that stops you from putting them back in in Amarok - which I prefer to keep track of my podcasts anyway.

Of course, it would be brilliant if Amarok could cover all my ipod needs - but at the moment, I'm pretty happy with the following setup:
1. Amarok for music and audio podcasts
2. Gtkpod for transferring video files and video podcasts
3. Gtkpixpod for transferring photos

Anyone knows if the Amarok people will include support for video and photo transfer to the ipod in a future version?

---

