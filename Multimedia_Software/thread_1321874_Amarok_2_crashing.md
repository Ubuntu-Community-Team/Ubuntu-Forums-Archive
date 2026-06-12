---
title: "Amarok 2 crashing"
date: 2009-11-10
forum: Multimedia Software
---

### Post by jms1989 on 2009-11-10
I tried looking for solution through google but nothing recent enough to help. Problem is, amarok wont start. The problem started after I installed ubuntu 9.10 on another partition but opted to use my existing home partition.

Here is my crash report;

```

Application: Amarok (amarok), signal SIGABRT
[Current thread is 0 (LWP 11219)]

Thread 5 (Thread 0xaff30b90 (LWP 11220)):
#0  0xb7f7e424 in __kernel_vsyscall ()
#1  0xb77ef412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0d77ae3 in ?? () from /usr/lib/libxine.so.1

Thread 4 (Thread 0xaf663b90 (LWP 11221)):
#0  0xb7f7e424 in __kernel_vsyscall ()
#1  0xb670aae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb443874b in g_poll () from /usr/lib/libglib-2.0.so.0
#3  0xb442af82 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb442b268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#5  0xb6a2f457 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
#6  0xb6a0206a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#7  0xb6a024aa in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#8  0xb690c639 in QThread::exec () from /usr/lib/libQtCore.so.4
#9  0xb0dc520a in ?? () from /usr/lib/kde4/plugins/phonon_backend/phonon_xine.so
#10 0xb690f96e in ?? () from /usr/lib/libQtCore.so.4
#11 0xb77eb4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb671549e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xaee62b90 (LWP 11222)):
#0  0xb7f7e424 in __kernel_vsyscall ()
#1  0xb670aae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xaf6d4912 in ?? () from /usr/lib/libpulse.so.0
#3  0xaf6c43c0 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0xaf6c5d43 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0xaf6c5e14 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0xaf6d46c3 in ?? () from /usr/lib/libpulse.so.0
#7  0xaf6feef2 in ?? () from /usr/lib/libpulse.so.0
#8  0xb77eb4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb671549e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xaa660b90 (LWP 11223)):
#0  0xb7f7e424 in __kernel_vsyscall ()
#1  0xb77ef0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0d88d8e in ?? () from /usr/lib/libxine.so.1
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 1 (Thread 0xb2f8c950 (LWP 11219)):
[KCrash Handler]
#6  0xb7f7e424 in __kernel_vsyscall ()
#7  0xb665c6d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb665e098 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb6907595 in qt_message_output () from /usr/lib/libQtCore.so.4
#10 0xb6907681 in qFatal () from /usr/lib/libQtCore.so.4
#11 0xb690772c in qt_assert_x () from /usr/lib/libQtCore.so.4
#12 0xb7a611f9 in ?? () from /usr/lib/libamaroklib.so.1
#13 0xb7ab3009 in MainWindow::init () from /usr/lib/libamaroklib.so.1
#14 0xb7a9bff2 in App::continueInit () from /usr/lib/libamaroklib.so.1
#15 0xb7aa0ca2 in App::App () from /usr/lib/libamaroklib.so.1
#16 0x0814c4a3 in _start ()


```

One page on the web suggested a gstreamer swf package maybe the culprit but I can't find it in synaptic. Oh, I did a reinstall of amarok and removed it's config data but no dice.

Ideas?

---

### Post by The Chef on 2009-11-15
From my experience Amarok 2.2.0 is simply not compatible with Ubuntu 9.10.  I have installed it on 2 fresh Ubuntu installations with no success and one near disaster.  The two platforms could not be less similar: one is a solid state drive, Intel Atom, EeePC 901 notebook, the other is a dual boot XP Dell 8250 Pentium 4 machine.  Both have the same symptom.

<Gratuitous_Rant> The first time the application boots the splash screen obscures a setup wizard for a KDE wallet thingy that will protect your last.fm password with 256bit encryption or some nonsense.  Once you realize that the setup window is where you can't see it - and that Amarok hasn't crashed- you can cancel it.  Then you're treated to a new Amarok interface which is really clunky and spends forever trying to access a wikipedia page based on your first music track title. </Gratuitous_Rant>

When you press the play button it changes to pause bars, the track name appears in a translucent window and a message appears for a split second in the bottom window frame saying that the track is playing.  The button then immediately changes back from pause bars to the play arrow.  No sound.  No error message.  Nothing. Testing the output devices through the Amarok configuration produces perfect tones, and reordering their priority does nothing.  The tracks I am trying to play, play fine under Totem Movie Player, so I have the codex etc.

Here is what not to do: go into Synaptic and install recommended packages for Amarok.  I did this and got several error messages including buffer overflow something-or-other.  The next time I booted up Ubuntu, I got a login screen with low resolution graphics and it crashed when I logged in with an error message that said the power management system had been installed incorrectly.  In other words, the Amarok install had smoked by PC.  I recovered from the error, using the recovery mode boot and freeing up disk space from the diagnostic menu this produces, but only after I searched the internet for 45 minutes trying to find the new Grub 2 keystroke to get to the boot menu (which, by the way, is holding down the shift key, not the ESC key as before, one of the many fantastic labour saving improvements I am sure.)

So, what is the best media player to use now?

---

### Post by themusicalduck on 2009-11-15
EDIT: I just re-read your post and I missed that you'd already tried this. :/ oh well.

Amarok is working pretty much fine for me in Karmic.

One thing you could try to stop it crashing is to delete the folder in /home/username/.kde/share/apps named amarok. (Note this'll reset configuration, your playlist and you'll need to rescan your library)

Or just rename it to something else if you like, then you can just name it back if you want to and use the same config file again.

---

### Post by jms1989 on 2009-11-16
> **themusicalduck said:**
> EDIT: I just re-read your post and I missed that you'd already tried this. :/ oh well.

Amarok is working pretty much fine for me in Karmic.

One thing you could try to stop it crashing is to delete the folder in /home/username/.kde/share/apps named amarok. (Note this'll reset configuration, your playlist and you'll need to rescan your library)

Or just rename it to something else if you like, then you can just name it back if you want to and use the same config file again.

I already did that (Note the last paragraph). I always delete or rename the config folder if a program crashes on me for some reason. It didn't work. I'm using the latest version Karmic had installed from its release cd.

After some more thinking, I did have some issue where my on-board sound device wasn't supported. That could be why it didn't work but normally it should allow the program to start but produce errors about it not finding a suitable audio device.

Edit: Also after installing 9.10 on another partition and reusing my home partition with it, amarok also refused to start when running my older 9.04 install. It would just crash and spit out that error message. Deleting it config directory didn't help.

---

