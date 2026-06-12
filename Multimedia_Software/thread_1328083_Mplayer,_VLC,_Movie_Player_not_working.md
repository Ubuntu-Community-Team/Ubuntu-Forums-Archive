---
title: "Mplayer, VLC, Movie Player not working"
date: 2009-11-16
forum: Multimedia Software
---

### Post by nonicutie on 2009-11-16
Hi,

I had a problem with all my player to run any dvds. MPlayer. VLC. and Movie player all stuck. Said 'seek-failed'. which is weird. I have used it yesterday running fine. 

Is there solution for this? Thanks

---

### Post by bernardfrancois on 2009-11-16
Maybe there's something wrong with the DVD disc you're trying to play? You could try if an other DVD works; if it does it's probably the DVD that is scratched or corrupt...

The 'seek-failed' error looks like those programs can't read from that specific DVD disc.

---

### Post by nonicutie on 2009-11-16
all dvds i have tried not working on. :( all of them seek-failed. it wasnt like that yesterday.

---

### Post by bernardfrancois on 2009-11-16
Is there anything that changed since yesterday? Did you install something specific? Did you do something that could have damaged your dvd player?

---

### Post by nonicutie on 2009-11-16
I run sudo apt-get update today morning and i installed 60MB files from Update Manager. Its an usual update from Ubuntu. Does it sound causing problem? 

I installed Mplayer just today evening to back up VLC or movie player. But, all of them stop. :(

---

### Post by bernardfrancois on 2009-11-16
Maybe installing mplayer broke it? Did you install it in synaptic or manually?

You could try uninstalling mplayer, and then try again...

How exactly do you get the 'seek-failed' error in these programs? Could you post a screenshot of VLC showing this error?

---

### Post by nonicutie on 2009-11-16
Hereis the message.

[COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]

I installed using repository. Il try to uninstall and reinstall tomorrow. I can watch those dvds using PS2, its working well.

---

### Post by andrew.46 on 2009-11-17
Hi nonicutie,

> **nonicutie said:**
> I installed Mplayer just today evening to back up VLC or movie player. But, all of them stop. :(

Can you run a dvd from the commandline with MPlayer as follows:

```
mplayer -v dvd://
```

and post the full commandline and terminal output here? This will give some information about the version of MPlayer you are using and also some indication why MPlayer is failing.

All the best,

Andrew

---

### Post by robertmbowes on 2009-11-17
I tried that and got the following:

robert@rbowes-l-it-d:~$ mplayer -v dvd://
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
CPU vendor name: AuthenticAMD  max cpuid level: 1
CPU: AMD Athlon(tm) 64 Processor 3500+ (Family: 15, Model: 79, Stepping: 2)
extended cpuid-level: 24
extended cache-info: 33587520
Detected cache-line size is 64 bytes
Testing OS support for SSE... yes.
Tests of OS support for SSE passed.
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNowExt: 1 SSE: 1 SSE2: 1 SSSE3: 0
Compiled with runtime CPU detection.
get_path('codecs.conf') -> '/home/robert/.mplayer/codecs.conf'
Reading /home/robert/.mplayer/codecs.conf: Can't open '/home/robert/.mplayer/codecs.conf': No such file or directory
Reading /etc/mplayer/codecs.conf: Can't open '/etc/mplayer/codecs.conf': No such file or directory
Using built-in default codecs.conf.
Configuration: --prefix=/usr --confdir=/etc/mplayer --datadir=/usr/share/mplayer --codecsdir=/usr/lib/codecs --enable-xvmc --enable-vdpau --enable-sdl --enable-ossaudio --enable-lirc --enable-freetype --enable-menu --enable-largefiles --extra-cflags=-I/build/buildd/mplayer-1.0~rc3+svn20090426/debian/include --disable-bitmap-font --disable-ggi --language=all --disable-xmms --disable-arts --disable-aa --disable-mad --disable-musepack --disable-libdv --disable-libavutil_a --disable-libavcodec_a --disable-libavformat_a --disable-libpostproc_a --disable-libswscale_a --enable-mp3lame --enable-faac-lavc --enable-x264-lavc --enable-mp3lame-lavc --enable-libdirac-lavc --enable-libschroedinger-lavc --target=i586-linux --enable-win32dll --enable-real --enable-xanim --enable-runtime-cpudetection --enable-vdpau --disable-libdvdcss-internal --enable-dvdread --enable-debug --enable-tv-v4l2 --enable-xmga --enable-mga --enable-3dfx --enable-tdfxfb --enable-fbdev --disable-gui
CommandLine: '-v' 'dvd://'
init_freetype
Using MMX (with tiny bit MMX2) Optimized OnScreenDisplay
get_path('fonts') -> '/home/robert/.mplayer/fonts'
Using nanosleep() timing
get_path('input.conf') -> '/home/robert/.mplayer/input.conf'
Can't open input config file /home/robert/.mplayer/input.conf: No such file or directory
Parsing input config file /etc/mplayer/input.conf
Input config file /etc/mplayer/input.conf parsed: 89 binds
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
get_path('.conf') -> '/home/robert/.mplayer/.conf'

Playing dvd://.
get_path('sub/') -> '/home/robert/.mplayer/sub/'
URL: dvd://
libdvdread: Encrypted DVD support unavailable.
Reading disc structure, please wait...
libdvdread: Invalid IFO for VMGM (VIDEO_TS.IFO).
Can't open VMG info!
No stream found to handle url dvd://

vo: x11 uninit called but X11 not initialized..

Exiting... (End of file)


I installed all of the codecs I could find in the Ubuntu software center. I installed VLC from there as well.
Robert

---

### Post by andrew.46 on 2009-11-17
Hi robert,

> **robertmbowes said:**
> 
```
libdvdread: Encrypted DVD support unavailable.
```


Looks like you don't have libdvdcss2 installed. There are several ways to install it, and perhaps the easiest is to make sure you have enabled the Medibuntu repository:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

and then install libdvdcss2:

```
sudo apt-get install libdvdcss2
```

and with any luck this is all you will need :).

Andrew

---

### Post by naldin on 2009-11-18
I have a similar problem, but the Totem, VLC, Kaffeine, Miro don´t run any movie(divx, mp4, wmv...). I tried reinstall the codecs(Gstreamer), install de Midibunt and not solved.

I´m using Ubuntu 9.10 32bits.

Error´s:

**Totem**:
Gstreamer encountered a stream error
Internal Data Stream Error:

**VLC**:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.
But the audio run.
[B]
Miro[/B]:
Always crash

**Kaffeine**:
Run the audio sometimes or the crash below:
```

Application: Kaffeine (kaffeine), signal: Segmentation fault
[Current thread is 1 (Thread 0xb573e700 (LWP 5386))]

Thread 10 (Thread 0xb226ab70 (LWP 5387)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5c02142 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5f287e4 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb33fd9ff in ?? () from /usr/lib/libxine.so.1
#4  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xb1905b70 (LWP 5388)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5c02142 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5f287e4 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb33fa51e in xine_play () from /usr/lib/libxine.so.1
#4  0xb3469ab2 in ?? () from /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
#5  0xb346abc8 in ?? () from /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
#6  0xb66d8f54 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#7  0xb66e067c in QApplication::notify(QObject*, QEvent*) () from /usr/lib/libQtGui.so.4
#8  0xb717bbfa in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#9  0xb62096cb in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/libQtCore.so.4
#10 0xb620a2b2 in QCoreApplicationPrivate::sendPostedEvents(QObject*, int, QThreadData*) () from /usr/lib/libQtCore.so.4
#11 0xb620a47d in QCoreApplication::sendPostedEvents(QObject*, int) () from /usr/lib/libQtCore.so.4
#12 0xb62343ff in ?? () from /usr/lib/libQtCore.so.4
#13 0xb5a3ee78 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#14 0xb5a42720 in ?? () from /lib/libglib-2.0.so.0
#15 0xb5a42853 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#16 0xb623402c in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#17 0xb6207c79 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#18 0xb62080ca in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#19 0xb6115b73 in QThread::exec() () from /usr/lib/libQtCore.so.4
#20 0xb345d20a in ?? () from /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
#21 0xb6118e32 in ?? () from /usr/lib/libQtCore.so.4
#22 0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#23 0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xad103b70 (LWP 5398)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5f0dba6 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb1a64c3b in ?? () from /usr/lib/xine/plugins/1.26/xineplug_ao_out_alsa.so
#3  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb10feb70 (LWP 5399)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5c01e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5f2878d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb340e5ee in ?? () from /usr/lib/libxine.so.1
#4  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb04ffb70 (LWP 5400)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5f14981 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb3426be0 in xine_usec_sleep () from /usr/lib/libxine.so.1
#3  0xb340b011 in ?? () from /usr/lib/libxine.so.1
#4  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xaf4feb70 (LWP 5402)):
[KCrash Handler]
#6  0xb32994cd in ?? () from /usr/lib/xine/plugins/1.26/xineplug_decode_ff.so
#7  0xb3406fea in ?? () from /usr/lib/libxine.so.1
#8  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xaeb30b70 (LWP 5403)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5c01e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5f2878d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb33fdd3c in ?? () from /usr/lib/libxine.so.1
#4  0xb3407ce4 in ?? () from /usr/lib/libxine.so.1
#5  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xae32fb70 (LWP 5404)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5c01e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5f2878d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb341151a in xine_event_wait () from /usr/lib/libxine.so.1
#4  0xb34115a2 in ?? () from /usr/lib/libxine.so.1
#5  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xada6db70 (LWP 5406)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5f14981 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb3426be0 in xine_usec_sleep () from /usr/lib/libxine.so.1
#3  0xb34166e0 in ?? () from /usr/lib/libxine.so.1
#4  0xb5bfd80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb5f1b7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb573e700 (LWP 5386)):
#0  0xb780f430 in __kernel_vsyscall ()
#1  0xb5c01e15 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb5f2878d in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb6119e67 in QWaitCondition::wait(QMutex*, unsigned long) () from /usr/lib/libQtCore.so.4
#4  0xb3462352 in ?? () from /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
#5  0xb3477f72 in ?? () from /usr/lib/qt4/plugins/phonon_backend/phonon_xine.so
#6  0xb74b0cec in Phonon::MediaNodePrivate::deleteBackendObject() () from /usr/lib/libphonon.so.4
#7  0xb74c0147 in ?? () from /usr/lib/libphonon.so.4
#8  0xb74beda5 in ?? () from /usr/lib/libphonon.so.4
#9  0xb74bc47b in ?? () from /usr/lib/libphonon.so.4
#10 0xb5e7e05f in ?? () from /lib/tls/i686/cmov/libc.so.6
#11 0xb5e7e0cf in exit () from /lib/tls/i686/cmov/libc.so.6
#12 0xb4f48610 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#13 0xb717b54a in KApplication::xioErrhandler(_XDisplay*) () from /usr/lib/libkdeui.so.5
#14 0xb717b586 in ?? () from /usr/lib/libkdeui.so.5
#15 0xb5c582e6 in _XIOError () from /usr/lib/libX11.so.6
#16 0xb5c5ff8a in ?? () from /usr/lib/libX11.so.6
#17 0xb5c608c6 in _XEventsQueued () from /usr/lib/libX11.so.6
#18 0xb5c495ff in XEventsQueued () from /usr/lib/libX11.so.6
#19 0xb6779db5 in ?? () from /usr/lib/libQtGui.so.4
#20 0xb5a41cc1 in g_main_context_check () from /lib/libglib-2.0.so.0
#21 0xb5a4246c in ?? () from /lib/libglib-2.0.so.0
#22 0xb5a42853 in g_main_context_iteration () from /lib/libglib-2.0.so.0
#23 0xb623402c in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#24 0xb6779be5 in ?? () from /usr/lib/libQtGui.so.4
#25 0xb6207c79 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#26 0xb62080ca in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#27 0xb620a53f in QCoreApplication::exec() () from /usr/lib/libQtCore.so.4
#28 0xb66d8dd7 in QApplication::exec() () from /usr/lib/libQtGui.so.4
#29 0x080c045d in _start ()

```

---

### Post by naldin on 2009-11-18
My problem was solved. I removed the libavcodec52 / libavcodec-extra-52 and this removed all video app related with then. Next I removed the Gstreamer and I deleted all "deb" in the cache(/var/cache/apt/archives/), I reinstalled GStreamer and all were ok.

---

### Post by syn4k on 2009-11-22
Thanks Andrew! Your install script saved me a LOT of headache!:P

---

### Post by andrew.46 on 2009-11-23
Hi syn4k,

> **syn4k said:**
> Thanks Andrew! Your install script saved me a LOT of headache!:P

If you mean the couple of lines that load the Medibuntu Repository I cannot claim any credit as I lifted it straight from:

Medibuntu - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

All the best,

Andrew

---

