---
title: "Segfault when starting mythfrontend"
date: 2009-04-07
forum: Mythbuntu
---

### Post by jyavenard on 2009-04-07
Hi

Starting from a clean install of Ubuntu 9.04

I installed the mythtv-frontend package, which installed libmyth-0.21 and mythtv-common

starting mythfrontend would properly creates the mythtv group and add the running account.

But then will segfault
2009-04-08 01:27:06.969 Using runtime prefix = /usr
2009-04-08 01:27:06.998 XScreenSaver support enabled
2009-04-08 01:27:07.002 DPMS is disabled.
2009-04-08 01:27:07.003 Empty LocalHostName.
2009-04-08 01:27:07.003 Using localhost value of ubuntu
2009-04-08 01:27:07.010 New DB connection, total: 1
2009-04-08 01:27:07.010 Unable to connect to database!
2009-04-08 01:27:07.010 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-04-08 01:27:07.061 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2009-04-08 01:27:09.192 UPnPautoconf() - No UPnP backends found
2009-04-08 01:27:09.192 No UPnP backends found
2009-04-08 01:27:09.197 Primary screen 0.
2009-04-08 01:27:09.197 Using screen 0, 1280x729 at 0,0
2009-04-08 01:27:09.197 No theme dir: /home/avenardj/.mythtv/themes/blue
2009-04-08 01:27:09.198 Switching to square mode (blue)
2009-04-08 01:27:09.226 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-04-08 01:27:09.227 lirc_init failed for mythtv, see preceding messages
2009-04-08 01:27:09.227 JoystickMenuClient Error: Joystick disabled - Failed to read /home/avenardj/.mythtv/joystickmenurc
Segmentation fault (core dumped)

this is normally where the screen telling me that no backend could be contacted and where you enter the mysql details.

Using the weekly build yield the same error...

Sounds to me like a Qt library crashing ...

Jean-Yves

---

### Post by jyavenard on 2009-04-08
I've recompiled the mythbuntu weekly 20300 packages with debugging on.

The only packages installed are libmyth-0.21 mythtv-common and mythtv-frontend.

the problem occur when /etc/mythtv contains an incorrect mysql configuration (not set up yet) and ~/.mythtv isn't set properly either

avenardj@ubuntu:~/Work/mythtv/ubuntu/fixes/release-0.21-fixes$ gdb mythfrontend.real -x ~/gdbcommands 
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
Function "qFatal" not defined.
Breakpoint 1 (qFatal) pending.
[Thread debugging using libthread_db enabled]
2009-04-08 16:43:47.998 Using runtime prefix = /usr
[New Thread 0x7f0ba4528760 (LWP 25177)]
[New Thread 0x7f0b9922e950 (LWP 25181)]
[New Thread 0x7f0b98a2d950 (LWP 25182)]
[New Thread 0x7f0b9822c950 (LWP 25183)]
2009-04-08 16:43:48.301 XScreenSaver support enabled
2009-04-08 16:43:48.301 DPMS is active.
2009-04-08 16:43:48.335 Empty LocalHostName.
2009-04-08 16:43:48.336 Using localhost value of ubuntu
2009-04-08 16:43:49.008 New DB connection, total: 1
2009-04-08 16:43:49.008 Unable to connect to database!
2009-04-08 16:43:49.008 Driver error was [1/2002]:
QMYSQL3: Unable to connect
Database error was:
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2009-04-08 16:43:49.059 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
................................................................................
2009-04-08 16:43:51.202 UPnPautoconf() - No UPnP backends found
2009-04-08 16:43:51.202 No UPnP backends found
2009-04-08 16:43:51.256 Primary screen 0.
2009-04-08 16:43:51.257 Using screen 0, 1280x720 at 0,0
2009-04-08 16:43:51.257 No theme dir: /home/avenardj/.mythtv/themes/blue
2009-04-08 16:43:51.274 Switching to square mode (blue)
2009-04-08 16:43:52.521 Using the Qt painter
[New Thread 0x7f0b9669a950 (LWP 25189)]
mythtv: could not connect to socket
[New Thread 0x7f0b95e99950 (LWP 25190)]
mythtv: No such file or directory
2009-04-08 16:43:52.544 lirc_init failed for mythtv, see preceding messages
[Thread 0x7f0b9669a950 (LWP 25189) exited]
2009-04-08 16:43:52.558 JoystickMenuClient Error: Joystick disabled - Failed to read /home/avenardj/.mythtv/joystickmenurc
[Thread 0x7f0b95e99950 (LWP 25190) exited]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7f0ba4528760 (LWP 25177)]
0x00007f0b9e4e77cf in glXWaitX () from /usr/lib/libGL.so.1

Thread 4 (Thread 0x7f0b9822c950 (LWP 25183)):
#0  0x00007f0b9d136742 in select () from /lib/libc.so.6
No symbol table info available.
#1  0x00007f0ba244bd3d in SSDP::run (this=0x1d803e0) at ssdp.cpp:207
	nMaxSocket = 14
	read_set = {fds_bits = {28672, 0 <repeats 15 times>}}
	timeout = {tv_sec = 0, tv_usec = 239841}
#2  0x00007f0b9ecc6aeb in QThreadInstance::start () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#3  0x00007f0b9db7b3ba in start_thread () from /lib/libpthread.so.0
No symbol table info available.
#4  0x00007f0b9d13dfcd in clone () from /lib/libc.so.6
No symbol table info available.
#5  0x0000000000000000 in ?? ()
No symbol table info available.

Thread 3 (Thread 0x7f0b98a2d950 (LWP 25182)):
#0  0x00007f0b9db7f56d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
No symbol table info available.
#1  0x00007f0b9ecc61f5 in ?? () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#2  0x00007f0b9ecc635e in QThread::msleep () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#3  0x00007f0ba245001b in TaskQueue::run (this=0x1d7f0c0) at taskqueue.cpp:114
	ttNow = {tv_sec = 1239173033, tv_usec = 330574}
	pTask = (Task *) 0x0
#4  0x00007f0b9ecc6aeb in QThreadInstance::start () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#5  0x00007f0b9db7b3ba in start_thread () from /lib/libpthread.so.0
No symbol table info available.
#6  0x00007f0b9d13dfcd in clone () from /lib/libc.so.6
No symbol table info available.
#7  0x0000000000000000 in ?? ()
No symbol table info available.

Thread 2 (Thread 0x7f0b9922e950 (LWP 25181)):
#0  0x00007f0b9db7f56d in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
No symbol table info available.
#1  0x00007f0b9efa6e59 in QWaitCondition::wait () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#2  0x00007f0ba246081b in CEvent::WaitForEvent (this=0x1d7e7b0, time=500) at threadpool.cpp:96
	ret = false
#3  0x00007f0ba246090a in WorkerThread::run (this=0x1d7e790) at threadpool.cpp:202
	timer = {m_timer = {ds = 60228052}}
#4  0x00007f0b9ecc6aeb in QThreadInstance::start () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#5  0x00007f0b9db7b3ba in start_thread () from /lib/libpthread.so.0
No symbol table info available.
#6  0x00007f0b9d13dfcd in clone () from /lib/libc.so.6
No symbol table info available.
#7  0x0000000000000000 in ?? ()
No symbol table info available.

Thread 1 (Thread 0x7f0ba4528760 (LWP 25177)):
#0  0x00007f0b9e4e77cf in glXWaitX () from /usr/lib/libGL.so.1
No symbol table info available.
#1  0x00007f0b9ef5f80a in QGLWidget::resizeEvent () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#2  0x00007f0b9ed5e869 in QWidget::event () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#3  0x00007f0b9eccc4a5 in QApplication::internalNotify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#4  0x00007f0b9eccd27a in QApplication::notify () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#5  0x00007f0b9ecce2c9 in QApplication::sendPostedEvents () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#6  0x00007f0b9ed5d7ea in QWidget::show () from /usr/lib/libqt-mt.so.3
No symbol table info available.
#7  0x00007f0ba186d95c in MythMainWindow::Show (this=0x1d9b9a0) at mythmainwindow.cpp:605
No locals.
#8  0x00007f0ba186de61 in MythMainWindow::Init (this=0x1d9b9a0) at mythmainwindow.cpp:595
	hideCursor = true
	flags = 8396816
#9  0x00007f0ba1cabb60 in MythContextPrivate::TempMainWindow (this=0x1d7afc0, languagePrompt=true) at mythcontext.cpp:423
	mainWindow = (class MythMainWindow *) 0x1d9b9a0
#10 0x00007f0ba1caea0e in MythContextPrivate::PromptForDatabaseParams (this=0x1d7afc0, error=@0x7fffac65a7d0) at mythcontext.cpp:1024
	settings = {<ConfigurationWizard> = {<ConfigurationDialog> = {<Storage> = {_vptr.Storage = 0x8}, cfgChildren = {<std::_Vector_base<Configurable*, std::allocator<Configurable*> >> = {_M_impl = {<std::allocator<Configurable*>> = {<__gnu_cxx::new_allocator<Configurable*>> = {<No data fields>}, <No data fields>}, _M_start = 0x44, _M_finish = 0xa45cbd1f, _M_end_of_storage = 0x7f0ba44480f0}}, <No data fields>}, childwidget = {<std::_Vector_base<QWidget*, std::allocator<QWidget*> >> = {_M_impl = {<std::allocator<QWidget*>> = {<__gnu_cxx::new_allocator<QWidget*>> = {<No data fields>}, <No data fields>}, _M_start = 0x7f0ba1b0e1f0, _M_finish = 0x20000001f, _M_end_of_storage = 0x29172f4}}, <No data fields>}, dialog = 0x7fffac65a260, cfgGrp = 0x7fffac65a408}, <No data fields>}, <No data fields>}
	accepted = false
#11 0x00007f0ba1cb5f69 in MythContextPrivate::FindDatabase (this=0x1d7afc0, prompt=false, noPrompt=false) at mythcontext.cpp:667
	manualSelect = false
	autoSelect = true
	failure = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x1d84680, static shared_null = 0x1c0ee20}
#12 0x00007f0ba1cb643e in MythContextPrivate::Init (this=0x1d7afc0, gui=true, UPnPclient=0x1d7a1c0, promptForBackend=false, noPrompt=false) at mythcontext.cpp:554
No locals.
#13 0x00007f0ba1cb6f81 in MythContext::Init (this=0x1d7bba0, gui=true, UPnPclient=0x1d7a1c0, promptForBackend=false, disableAutoDiscovery=false) at mythcontext.cpp:1571
No locals.
#14 0x0000000000439ce8 in main (argc=5, argv=0x7fffac65ba68) at main.cpp:1164
	bPromptForBackend = false
	bBypassAutoDiscovery = false
	upgradeAllowed = false
	geometry = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x1c0ee20, static shared_null = 0x1c0ee20}
	display = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x1c0ee20, static shared_null = 0x1c0ee20}
	a = <incomplete type>
	pluginname = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x1d49a00, static shared_null = 0x1c0ee20}
	settingsOverride = {sh = 0x1d759c0}
	finfo = {fn = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x1d77210, static shared_null = 0x1c0ee20}, fic = 0x0, cache = true, symLink = false}
	binname = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x1d79390, static shared_null = 0x1c0ee20}
	ResetSettings = false
	fileprefix = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x40, static shared_null = 0x1c0ee20}
	dir = <incomplete type>
	priv_thread = 139687867403752
	priv_thread_created = false
	status = -1660520848
	themename = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x7fffac65b470, static shared_null = 0x1c0ee20}
	randomtheme = 67
	themedir = {static null = {static null = <same as static member of an already seen type>, d = 0x1c0ee20, static shared_null = 0x1c0ee20}, d = 0x1, static shared_null = 0x1c0ee20}
	mainWindow = (class MythMainWindow *) 0x1d306d0
	pmanager = (MythPluginManager *) 0x7f0b9d3c5a00
	mon = (class MediaMonitor *) 0x7fffac65b950
	networkControl = (class NetworkControl *) 0x7fffac65b450
	exitstatus = 5603029
(gdb) 


I can't debug it ; it segfault when opening the new window in
libs/libmythui/mythmainwindow.cpp
void MythMainWindow::Show(void)
{
    show();    <-- Segfault here

---

### Post by sxa on 2009-04-18
I had the same problem on my AMD Geode system. It doesn't occur if I use a non-local DISPLAY (i.e. log in from somewhere else, but the front end still running on the Geode).

So it seems like an X issue. Hopefully it'll work in final 9.04.

---

### Post by MountainX on 2009-11-07
I just installed Mythbuntu 9.10 i386

```
[  151.826967] mythfrontend.re[2048]: segfault at ffffffe8 ip 010a988d sp bfeb9a30 error 4 in libmythtv-0.22.so.0.22.0[bce000+a6c000]
```

Not sure what to do next...

---

### Post by matt06 on 2010-01-18
> **MountainX said:**
> I just installed Mythbuntu 9.10 i386

```
[  151.826967] mythfrontend.re[2048]: segfault at ffffffe8 ip 010a988d sp bfeb9a30 error 4 in libmythtv-0.22.so.0.22.0[bce000+a6c000]
```

Not sure what to do next...

Hi MountainX, did you find a resolution for this?  I'm getting this on a combined fe/be system while the frontend is sitting idle (not always, but usually when the backend is recording/flagging at the same time) on a new 9.10 install.  I've been digging and fixing things one at a time and this is a new one to me.

---

### Post by MountainX on 2010-01-18
> **matt06 said:**
> Hi MountainX, did you find a resolution for this? 

I had to sit MythTV aside for now. I did not resolve my issues and I decided to spend my time on other things. I'll come back to MythTV at some point in the future because it is the most feature-rich product in this class. For now, gotta work on other stuff :)

---

### Post by matt06 on 2010-01-18
Understood.  This problem is on a new build for me, but my other mythbuntu systems have been unbelievably reliable.  I don't want to hijack this thread so I'll post my own when I have enough info about my problem.

---

