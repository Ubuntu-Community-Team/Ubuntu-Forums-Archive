---
title: "F-Spot doesn't start"
date: 2008-05-22
forum: Multimedia Software
---

### Post by framirez on 2008-05-22
Hi

I am running Ubunty 8.04 and I can't get F-Spot running.  It seems to be something with SQL....  

When I run  dbus-launch F-Spot this is what I get



framirez@ubuntu-laptop:~$ dbus-launch f-spot
Unable to create /home/framirez/.dbus/session-bus
Starting new FSpot server

Unhandled Exception: System.Exception: Unsupported SQLite database version
  at Banshee.Database.QueuedSqliteDatabase.ProcessQueue () [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()
framirez@ubuntu-laptop:~$ sudo dbus-launch f-spot
[sudo] password for framirez: 

(/usr/lib/f-spot/f-spot.exe:13674): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.16.3/gobject/gtype.c:2248: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/f-spot/f-spot.exe:13674): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/f-spot/f-spot.exe:13674): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0xffffffff>
  at GConf.Client..ctor () <0x0003b>
  at FSpot.GConfPreferenceBackend.get_Client () <0x0001f>
  at FSpot.GConfPreferenceBackend.AddNotify (string,FSpot.NotifyChangedHandler) <0x00033>
  at FSpot.Preferences.get_Backend () <0x0007c>
  at FSpot.Preferences.Get (string) <0x00074>
  at FSpot.Driver.Main (string[]) <0x00112>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x816b1fa]
	f-spot [0x807de81]
	[0xb7f49440]
	/usr/lib/libgconf-2.so.4(gconf_client_get_default+0xa9) [0xb6c6b9f9]
	[0xb77d4a68]
	[0xb77d4504]
	[0xb77d44a0]
	[0xb77d43ec]
	[0xb77d42c5]
	[0xb77d3e7d]
	[0xb77d090b]
	[0xb77d01c4]
	f-spot(mono_runtime_exec_main+0x10e) [0x809c68e]
	f-spot(mono_runtime_run_main+0x173) [0x809c933]
	f-spot(mono_main+0x6a9) [0x805acd9]
	f-spot [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cfd450]
	f-spot [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7ca5940 (LWP 13674)]
[New Thread 0xb724ab90 (LWP 13680)]
[New Thread 0xb726eb90 (LWP 13679)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f49410 in __kernel_vsyscall ()
  3 Thread 0xb726eb90 (LWP 13679)  0xb7f49410 in __kernel_vsyscall ()
  2 Thread 0xb724ab90 (LWP 13680)  0xb7f49410 in __kernel_vsyscall ()
  1 Thread 0xb7ca5940 (LWP 13674)  0xb7f49410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb726eb90 (LWP 13679)):
#0  0xb7f49410 in __kernel_vsyscall ()
#1  0xb7e68196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb726e344 in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread 0xb724ab90 (LWP 13680)):
#0  0xb7f49410 in __kernel_vsyscall ()
#1  0xb7e64aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0xb77481dc in ?? ()
#4  0xb77481c4 in ?? ()
#5  0x00000001 in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread 0xb7ca5940 (LWP 13674)):
#0  0xb7f49410 in __kernel_vsyscall ()
#1  0xb7db6881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ee4e14 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7ee51dc in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  0xb7b73848 in ?? ()
#6  0xb7b73844 in ?? ()
#7  0xb7b73840 in ?? ()
#8  0xb7b7383c in ?? ()
#9  0x00000000 in ?? ()
#0  0xb7f49410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
framirez@ubuntu-laptop:~$ clear

framirez@ubuntu-laptop:~$ sudo dbus-launch f-spot

(/usr/lib/f-spot/f-spot.exe:14135): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.16.3/gobject/gtype.c:2248: initialization assertion failed, use IA__g_type_init() prior to this function

(/usr/lib/f-spot/f-spot.exe:14135): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(/usr/lib/f-spot/f-spot.exe:14135): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Stacktrace:

  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0x00004>
  at (wrapper managed-to-native) GConf.Client.gconf_client_get_default () <0xffffffff>
  at GConf.Client..ctor () <0x0003b>
  at FSpot.GConfPreferenceBackend.get_Client () <0x0001f>
  at FSpot.GConfPreferenceBackend.AddNotify (string,FSpot.NotifyChangedHandler) <0x00033>
  at FSpot.Preferences.get_Backend () <0x0007c>
  at FSpot.Preferences.Get (string) <0x00074>
  at FSpot.Driver.Main (string[]) <0x00112>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        f-spot [0x816b1fa]
        f-spot [0x807de81]
        [0xb7f7a440]
        /usr/lib/libgconf-2.so.4(gconf_client_get_default+0xa9) [0xb6c9c9f9]
        [0xb7805a68]
        [0xb7805504]
        [0xb78054a0]
        [0xb78053ec]
        [0xb78052c5]
	[0xb7804e7d]
	[0xb780190b]
	[0xb78011c4]
	f-spot(mono_runtime_exec_main+0x10e) [0x809c68e]
	f-spot(mono_runtime_run_main+0x173) [0x809c933]
	f-spot(mono_main+0x6a9) [0x805acd9]
	f-spot [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d2e450]
	f-spot [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7cd6940 (LWP 14135)]
[New Thread 0xb727bb90 (LWP 14141)]
[New Thread 0xb729fb90 (LWP 14140)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f7a410 in __kernel_vsyscall ()
  3 Thread 0xb729fb90 (LWP 14140)  0xb7f7a410 in __kernel_vsyscall ()
  2 Thread 0xb727bb90 (LWP 14141)  0xb7f7a410 in __kernel_vsyscall ()
  1 Thread 0xb7cd6940 (LWP 14135)  0xb7f7a410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb729fb90 (LWP 14140)):
#0  0xb7f7a410 in __kernel_vsyscall ()
#1  0xb7e99196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb729f344 in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread 0xb727bb90 (LWP 14141)):
#0  0xb7f7a410 in __kernel_vsyscall ()
#1  0xb7e95aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0xb77791dc in ?? ()
#4  0xb77791c4 in ?? ()
#5  0x00000001 in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread 0xb7cd6940 (LWP 14135)):
#0  0xb7f7a410 in __kernel_vsyscall ()
#1  0xb7dadd89 in fork () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e9b034 in fork () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7f150f9 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7d85341 in ?? () from /lib/tls/i686/cmov/libc.so.6
#5  0x08329df2 in ?? ()
#6  0x00000028 in ?? ()
#7  0x00000010 in ?? ()
#8  0x00000010 in ?? ()
#9  0xb7e62ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#10 0x08285100 in ?? ()
#11 0x08330140 in ?? ()
#12 0xb7e644d0 in ?? () from /lib/tls/i686/cmov/libc.so.6
#13 0xb7e62ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
#14 0x00000010 in ?? ()
#15 0x00000010 in ?? ()
#16 0x00000010 in ?? ()
#17 0xb7d8775b in realloc () from /lib/tls/i686/cmov/libc.so.6
#18 0xb7f15d1d in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#19 0xb7f161dc in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#20 0x0816b295 in ?? ()
#21 0xb7ba4848 in ?? ()
#22 0xb7ba4844 in ?? ()
#23 0xb7ba4840 in ?? ()
#24 0xb7ba483c in ?? ()
#25 0x00000000 in ?? ()
#0  0xb7f7a410 in __kernel_vsyscall ()


What can I do?

---

### Post by Fergus_McSnort on 2008-06-09
Similar problem.  I'm trying to copy pictures from a Canon SD750 camera.  The camera is detected, and f-spot starts to launch then hangs.

With or without a camera in the USB slot, f-spot always hangs on launch.  Starting it from a command line:
$ f-spot

returns:

Starting new FSpot server

then it just hangs.  Nothing else happens.  It used to work fine, but two things have happened since the last time I used it - 1. new motherboard and video card (Radeon 3450); and 2. upgrade to Hardy Heron.

I tried re-installing.  Same thing.

Also, how can I have the camera's flash memory appear as a regular USB storage device?  That would be easier than working through f-spot anyway.

---

### Post by xc3RnbFO8P on 2008-06-09
> I am running Ubunty 8.04 and I can't get F-Spot running. It seems to be something with SQL.... 
[https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/81905/comments/13]("https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/81905/comments/13")

Fergus_McSnort, try KPhotoalbum in Add/Remove (all available application)

---

### Post by Fergus_McSnort on 2008-06-09
> **Ringi said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/81905/comments/13]("https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/81905/comments/13")

Fergus_McSnort, try KPhotoalbum in Add/Remove (all available application)

Thanks Ringi, but I'm gettin' no love from KPhoto.  It loads just fine, but seems unaware of the camera, and I cannot seem to get its plugins installed.

---

### Post by xc3RnbFO8P on 2008-06-10
You mean this doesnt work?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73539&d=1213097849[/IMG]

---

### Post by Fergus_McSnort on 2008-06-10
> **Ringi said:**
> You mean this doesnt work?


I can't find the dialog windows you have pictured.  I cannot find a way to configure or select a camera.

---

### Post by xc3RnbFO8P on 2008-06-10
Plugins> Import> Digital Camera> Setup> Add (or Auto-Detect)> find camera, check usb

---

### Post by Fergus_McSnort on 2008-06-10
> **Ringi said:**
> Plugins> Import> Digital Camera> Setup> Add (or Auto-Detect)> find camera, check usb

Thank-you Ringi, I appreciate the time you're spending on this. 

There are no plugins available under Plugins.  I've read through the KPhotoAlbum documentation, found the name of some of the plugins, and tried to install them using Add/Remove Programs, but still nothing appears.  I cannot find where in KPhotoAlbum to point to the location of plugin files.

Here's a picture of what my KPhotoAlbum screen looks like:
[IMG]http://tampacycling.com/Screenshot-KPhotoAlbum.png[/IMG]

---

### Post by xc3RnbFO8P on 2008-06-10
Check in Synaptic Package Manager if you got (and install if you haven't)
**kdebase-bin**,  **kdebase-bin-kde3**,  **kdelibs4c2a**,
**kdelibs-data**,   **kipi-plugins**

Restart the computer

Reinstall KPhotoalbum from Synaptic Package Manager.

---

### Post by Fergus_McSnort on 2008-06-10
> **Ringi said:**
> Check in Synaptic Package Manager if you got (and install if you haven't)
**kdebase-bin**,  **kdebase-bin-kde3**,  **kdelibs4c2a**,
**kdelibs-data**,   **kipi-plugins**

Restart the computer

Reinstall KPhotoalbum from Synaptic Package Manager.

That did it!  A thousand thanks.

---

### Post by Creap on 2008-06-26
> **Ringi said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/81905/comments/13]("https://bugs.edge.launchpad.net/ubuntu/+source/f-spot/+bug/81905/comments/13")
My F-spot won't start either, giving me hundreds of "open("/usr/lib/i686/cmov/libgtk-x11-2.0.so.0.so", O_RDONLY) = -1 ENOENT (No such file or directory)" errors with all kinds of different files. I tried ```
$ sqlite ~/.gnome2/f-spot/photos.db
Unable to open database "/home/jacob/.gnome2/f-spot/photos.db": file is encrypted or is not a database
```

And it worked fine yesterday...

---

### Post by Creap on 2008-06-27
I also tried removing (renaming) the entire ~/.gnome2/f-spot directory, but that didn't change anything.

---

