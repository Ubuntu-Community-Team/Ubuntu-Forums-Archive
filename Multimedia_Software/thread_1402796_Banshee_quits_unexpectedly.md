---
title: "Banshee quits unexpectedly"
date: 2010-02-09
forum: Multimedia Software
---

### Post by afrodeity on 2010-02-09
Banshee quits about 3seconds into song. This is the error I got running it from the terminal:

```
Running Banshee 1.5.3: [Ubuntu 9.10 (linux-gnu, i486) @ 2010-01-28 17:30:51 UTC]

(/usr/lib/banshee-1/Banshee.exe:27712): GLib-WARNING **: g_set_prgname() called multiple times
```

followed by some [mono code]("http://paste.ubuntu.com/372695/") and:

[COLOR="Red"]Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.[/COLOR]

Following this thread [http://ubuntuforums.org/showthread.php?t=1312590&page=2](http://ubuntuforums.org/showthread.php?t=1312590&page=2)

Which recommended I do this:

```
mv ~/.config/banshee-1 ~/.config/banshee-1.bak
```

and if that didn't work to try deleting .wapi

However after doing this I still have the problem but slightly different terminal output. 

```

(/usr/lib/banshee-1/Banshee.exe:27712): Clutter-CRITICAL **: clutter_timeline_set_duration: assertion `CLUTTER_IS_TIMELINE (timeline)' failed

(/usr/lib/banshee-1/Banshee.exe:27712): Clutter-CRITICAL **: clutter_timeline_rewind: assertion `CLUTTER_IS_TIMELINE (timeline)' failed

(/usr/lib/banshee-1/Banshee.exe:27712): Clutter-CRITICAL **: clutter_timeline_start: assertion `CLUTTER_IS_TIMELINE (timeline)' failed

(/usr/lib/banshee-1/Banshee.exe:27712): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at GLib.GType.GetQualifiedName (System.String cname) [0x00000] 
  at GLib.GType.LookupType (IntPtr typeid) [0x00000] 
  at GLib.ObjectManager.GetTypeOrParent (IntPtr obj) [0x00000] 
  at GLib.ObjectManager.CreateObject (IntPtr raw) [0x00000] 
  at GLib.Object.GetObject (IntPtr o, Boolean owned_ref) [0x00000] 
  at GLib.Object.GetObject (IntPtr o) [0x00000] 
  at Clutter.Animation.get_Timeline () [0x00000] 
  at ClutterFlow.Captions.Caption.FadeIn () [0x00000] 
  at ClutterFlow.Captions.CoverCaption.HandleNewCurrentCover (ClutterFlow.ClutterFlowActor cover, System.EventArgs e) [0x00000] 
  at ClutterFlow.CoverManager.InvokeNewCurrentCover (ClutterFlow.ClutterFlowActor cover) [0x00000] 
  at ClutterFlow.CoverManager.set_CurrentCover (ClutterFlow.ClutterFlowActor value) [0x00000] 
  at ClutterFlow.CoverManager.HandleTargetMarkerReached (System.Object sender, ClutterFlow.TargetReachedEventArgs args) [0x00000] 
  at ClutterFlow.ThrottledTimeline.InvokeTargetReached () [0x00000] 
  at ClutterFlow.ThrottledTimeline.set_Progress (Double value) [0x00000] 
  at ClutterFlow.ThrottledTimeline.RepaintFunc () [0x00000] 
  at GLibSharp.GSourceFuncWrapper.NativeCallback (IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLibSharp.GSourceFuncWrapper.NativeCallback(IntPtr data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()

** (/usr/lib/banshee-1/Banshee.exe:27712): WARNING **: Shutting down finalizer thread timed out.

```

---

### Post by tgalati4 on 2010-02-09
Do you get any extra information running banshee --debug in a terminal?

Looks like a clutterflow problem.

---

### Post by afrodeity on 2010-02-10
```

Native stacktrace:

	banshee-1 [0x80c8824]
	banshee-1 [0x80f4693]
	[0xe62410]
	/usr/lib/libGL.so.1 [0x35bdad2]
	/usr/lib/libclutter-glx-1.0.so.0(cogl_texture_get_data+0x2e9) [0x83c9699]
	/usr/lib/libclutter-glx-1.0.so.0 [0x83a7b5c]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0xcb79fc]
	/usr/lib/libgobject-2.0.so.0 [0xca86f9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xca9f98]
	/usr/lib/libgobject-2.0.so.0 [0xcbf49e]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0xcc0b2d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xcc0fb6]
	/usr/lib/libclutter-glx-1.0.so.0 [0x8365aa2]
	/usr/lib/libclutter-glx-1.0.so.0 [0x83881e4]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_container_foreach_with_internals+0xc3) [0x8384ad3]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_actor_real_unrealize+0xa2) [0x8366202]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0xcb79fc]
	/usr/lib/libgobject-2.0.so.0 [0xca86f9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0xcaa072]
	/usr/lib/libgobject-2.0.so.0 [0xcbf49e]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0xcc0b2d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xcc0fb6]
	/usr/lib/libclutter-glx-1.0.so.0 [0x8365aa2]
	/usr/lib/libclutter-glx-1.0.so.0 [0x836ed62]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_actor_unparent+0x97) [0x836f767]
	/usr/lib/libclutter-glx-1.0.so.0 [0x838883c]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_container_remove_actor+0x155) [0x8384f45]
	[0x4a7170f]
	[0x4a716c4]
	[0x480f437]
	[0x61515bd]
	[0x615155f]
	[0x5108f0]
	banshee-1 [0x812ba39]
	banshee-1 [0x812bbeb]
	banshee-1 [0x814f96c]
	banshee-1 [0x81bf9f2]
	banshee-1 [0x81de055]
	/lib/tls/i686/cmov/libpthread.so.0 [0xfc380e]
	/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x1e28de]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x2408b70 (LWP 7894)]
[New Thread 0xafdfbb70 (LWP 7892)]
[New Thread 0xb05fcb70 (LWP 7891)]
[New Thread 0xb0dfdb70 (LWP 7890)]
[New Thread 0xb55ffb70 (LWP 7889)]
[New Thread 0x1fc7b70 (LWP 7888)]
[New Thread 0x42d3b70 (LWP 7887)]
[New Thread 0x2f01b70 (LWP 7883)]
[New Thread 0x2449b70 (LWP 7881)]
[New Thread 0x2b74b70 (LWP 7879)]
[New Thread 0x2a73b70 (LWP 7878)]
[New Thread 0x2972b70 (LWP 7877)]
[New Thread 0x166eb70 (LWP 7873)]
[New Thread 0x88fb70 (LWP 7869)]
[New Thread 0x645b70 (LWP 7868)]
0x00e62422 in __kernel_vsyscall ()
  16 Thread 0x645b70 (LWP 7868)  0x00e62422 in __kernel_vsyscall ()
  15 Thread 0x88fb70 (LWP 7869)  0x00e62422 in __kernel_vsyscall ()
  14 Thread 0x166eb70 (LWP 7873)  0x00e62422 in __kernel_vsyscall ()
  13 Thread 0x2972b70 (LWP 7877)  0x00e62422 in __kernel_vsyscall ()
  12 Thread 0x2a73b70 (LWP 7878)  0x00e62422 in __kernel_vsyscall ()
  11 Thread 0x2b74b70 (LWP 7879)  0x00e62422 in __kernel_vsyscall ()
  10 Thread 0x2449b70 (LWP 7881)  0x00e62422 in __kernel_vsyscall ()
  9 Thread 0x2f01b70 (LWP 7883)  0x00e62422 in __kernel_vsyscall ()
  8 Thread 0x42d3b70 (LWP 7887)  0x00e62422 in __kernel_vsyscall ()
  7 Thread 0x1fc7b70 (LWP 7888)  0x00e62422 in __kernel_vsyscall ()
  6 Thread 0xb55ffb70 (LWP 7889)  0x00e62422 in __kernel_vsyscall ()
  5 Thread 0xb0dfdb70 (LWP 7890)  0x00e62422 in __kernel_vsyscall ()
  4 Thread 0xb05fcb70 (LWP 7891)  0x00e62422 in __kernel_vsyscall ()
  3 Thread 0xafdfbb70 (LWP 7892)  0x00e62422 in __kernel_vsyscall ()
  2 Thread 0x2408b70 (LWP 7894)  0x00e62422 in __kernel_vsyscall ()
* 1 Thread 0x4d46f0 (LWP 7866)  0x00e62422 in __kernel_vsyscall ()

Thread 16 (Thread 0x645b70 (LWP 7868)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a3658 in ?? ()
#3  0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 15 (Thread 0x88fb70 (LWP 7869)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcac8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()
#3  0x080f4693 in ?? ()
#4  <signal handler called>
#5  0x035bdad2 in glPixelStorei () from /usr/lib/libGL.so.1
#6  0x083c9309 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#7  0x083c9699 in cogl_texture_get_data ()
   from /usr/lib/libclutter-glx-1.0.so.0
#8  0x083a7b5c in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#9  0x00cb79fc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#10 0x00ca86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#11 0x00ca9f98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#12 0x00cbf49e in ?? () from /usr/lib/libgobject-2.0.so.0
#13 0x00cc0b2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#14 0x00cc0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#15 0x08365aa2 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#16 0x083881e4 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#17 0x08384ad3 in clutter_container_foreach_with_internals ()
   from /usr/lib/libclutter-glx-1.0.so.0
#18 0x08366202 in clutter_actor_real_unrealize ()
   from /usr/lib/libclutter-glx-1.0.so.0
#19 0x00cb79fc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#20 0x00ca86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#21 0x00caa072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#22 0x00cbf49e in ?? () from /usr/lib/libgobject-2.0.so.0
#23 0x00cc0b2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#24 0x00cc0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#25 0x08365aa2 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#26 0x0836ed62 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#27 0x0836f767 in clutter_actor_unparent ()
   from /usr/lib/libclutter-glx-1.0.so.0
#28 0x0838883c in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#29 0x08384f45 in clutter_container_remove_actor ()
   from /usr/lib/libclutter-glx-1.0.so.0
#30 0x04a7170f in ?? ()
#31 0x04a716c4 in ?? ()
#32 0x0480f437 in ?? ()
#33 0x061515bd in ?? ()
#34 0x0615155f in ?? ()
#35 0x005108f0 in ?? ()
#36 0x0812ba39 in ?? ()
#37 0x0812bbeb in ?? ()
#38 0x0814f96c in ?? ()
#39 0x081bf9f2 in ?? ()
#40 0x081de055 in ?? ()
#41 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#42 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 14 (Thread 0x166eb70 (LWP 7873)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x00ecbbbd in ?? ()
#8  0x00eca62a in ?? ()
#9  0x00483df0 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 13 (Thread 0x2972b70 (LWP 7877)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x061514b3 in ?? ()
#7  0x02246bf5 in ?? ()
#8  0x022468b9 in ?? ()
#9  0x0224658d in ?? ()
#10 0x00481086 in ?? ()
#11 0x08114f4b in mono_runtime_invoke_array ()
#12 0x0811512e in ?? ()
#13 0x081520a3 in ?? ()
#14 0x08152577 in ?? ()
#15 0x0814f96c in ?? ()
#16 0x081bf9f2 in ?? ()
#17 0x081de055 in ?? ()
#18 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#19 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0x2a73b70 (LWP 7878)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x061514b3 in ?? ()
#7  0x02246bf5 in ?? ()
#8  0x022468b9 in ?? ()
#9  0x0224658d in ?? ()
#10 0x00481086 in ?? ()
#11 0x08114f4b in mono_runtime_invoke_array ()
#12 0x0811512e in ?? ()
#13 0x081520a3 in ?? ()
#14 0x08152577 in ?? ()
#15 0x0814f96c in ?? ()
#16 0x081bf9f2 in ?? ()
#17 0x081de055 in ?? ()
#18 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#19 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0x2b74b70 (LWP 7879)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x022468b9 in ?? ()
#8  0x0224658d in ?? ()
#9  0x00481086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0x2449b70 (LWP 7881)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x001d4c96 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x006c054b in g_poll () from /lib/libglib-2.0.so.0
#3  0x006b356b in ?? () from /lib/libglib-2.0.so.0
#4  0x006b3b9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x084d98c0 in ?? () from /usr/lib/libORBit-2.so.0
#6  0x006da37f in ?? () from /lib/libglib-2.0.so.0
#7  0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0x2f01b70 (LWP 7883)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x00b05ee8 in ?? ()
#8  0x00b0b19a in ?? ()
#9  0x00b0b04a in ?? ()
#10 0x0527bbe2 in ?? ()
#11 0x0527ee25 in ?? ()
#12 0x02263050 in ?? ()
#13 0x00481086 in ?? ()
#14 0x08114f4b in mono_runtime_invoke_array ()
#15 0x0811512e in ?? ()
#16 0x081520a3 in ?? ()
#17 0x08152577 in ?? ()
#18 0x0814f96c in ?? ()
#19 0x081bf9f2 in ?? ()
#20 0x081de055 in ?? ()
#21 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#22 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0x42d3b70 (LWP 7887)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x036c7a78 in ?? ()
#8  0x03f9c849 in ?? ()
#9  0x00483df0 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0x1fc7b70 (LWP 7888)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x036fb084 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x03285ef5 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#6  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#7  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#8  0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#10 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#11 0x03e08c75 in ?? () from /usr/lib/gstreamer-0.10/libgstflump3dec.so
#12 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#13 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x0371460e in ?? () from /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
#15 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#16 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x04631fff in ?? () from /usr/lib/libgsttag-0.10.so.0
#18 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#19 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x036ff5d7 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#21 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#23 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#25 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#26 0x016c063e in ?? () from /usr/lib/libgstbase-0.10.so.0
#27 0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#28 0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#29 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#30 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#31 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#32 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb55ffb70 (LWP 7889)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x001d4c96 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x03e659e2 in ?? () from /usr/lib/libpulse.so.0
#3  0x03e52a79 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0x03e54893 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0x03e54964 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0x03e658e3 in ?? () from /usr/lib/libpulse.so.0
#7  0x03f792f2 in ?? () from /usr/lib/libpulsecommon-0.9.21.so
#8  0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb0dfdb70 (LWP 7890)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x03f77fac in pa_cond_wait () from /usr/lib/libpulsecommon-0.9.21.so
#3  0x03e65cc0 in pa_threaded_mainloop_wait () from /usr/lib/libpulse.so.0
#4  0x064ee8fa in ?? () from /usr/lib/gstreamer-0.10/libgstpulse.so
#5  0x03733a4d in gst_ring_buffer_commit_full ()
   from /usr/lib/libgstaudio-0.10.so.0
#6  0x0373bd8a in ?? () from /usr/lib/libgstaudio-0.10.so.0
#7  0x016b0ef8 in ?? () from /usr/lib/libgstbase-0.10.so.0
#8  0x016b26b7 in ?? () from /usr/lib/libgstbase-0.10.so.0
#9  0x016b4759 in ?? () from /usr/lib/libgstbase-0.10.so.0
#10 0x016b4d0d in ?? () from /usr/lib/libgstbase-0.10.so.0
#11 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#12 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#13 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#15 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#16 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#19 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#21 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#23 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#25 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#26 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#27 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#28 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#29 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#30 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#31 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#32 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#33 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#34 0x036f94cd in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#35 0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#36 0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#37 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#38 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#39 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#40 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb05fcb70 (LWP 7891)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x02c906e6 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#3  0x02c9c6c7 in gst_pad_push_event () from /usr/lib/libgstreamer-0.10.so.0
#4  0x016c7182 in ?? () from /usr/lib/libgstbase-0.10.so.0
#5  0x02c9bdde in gst_pad_send_event () from /usr/lib/libgstreamer-0.10.so.0
#6  0x02c9c5bb in gst_pad_push_event () from /usr/lib/libgstreamer-0.10.so.0
#7  0x036f9933 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#8  0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#10 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#11 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#12 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xafdfbb70 (LWP 7892)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x036fb084 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x036fc32d in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#6  0x036fc82d in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#7  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#8  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#10 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#11 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#12 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#13 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#15 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#16 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#19 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#21 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#23 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x036f94cd in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#25 0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#26 0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#27 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#28 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#29 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#30 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0x2408b70 (LWP 7894)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x0614fb4e in ?? ()
#8  0x0614efa2 in ?? ()
#9  0x0614eecc in ?? ()
#10 0x0614ee7b in ?? ()
#11 0x0614e1b3 in ?? ()
#12 0x0614da8a in ?? ()
#13 0x0614d904 in ?? ()
#14 0x0614d478 in ?? ()
#15 0x04f5d792 in ?? ()
#16 0x04f5d3c6 in ?? ()
#17 0x04f5cf36 in ?? ()
#18 0x04f5c449 in ?? ()
#19 0x06142a4d in ?? ()
#20 0x022612a2 in ?? ()
#21 0x00483df0 in ?? ()
#22 0x0810e6a4 in mono_runtime_delegate_invoke ()
#23 0x0814f9d7 in ?? ()
#24 0x081bf9f2 in ?? ()
#25 0x081de055 in ?? ()
#26 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#27 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0x4d46f0 (LWP 7866)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc8142 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a83c4 in ?? ()
#3  0x081c3c28 in ?? ()
#4  0x0812c7e5 in mono_domain_finalize ()
#5  0x0805b4e0 in ?? ()
#6  0x08159a03 in mono_runtime_quit ()
#7  0x0812095a in ?? ()
#8  0x06151454 in ?? ()
#9  0x0614f6ac in ?? ()
#10 0x03d5b87e in ?? ()
#11 0x00966201 in ?? ()
#12 0x0838df4d in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#13 0x083b1b83 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#14 0x0838813e in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#15 0x006afe88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#16 0x006b3730 in ?? () from /lib/libglib-2.0.so.0
#17 0x006b3b9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#18 0x0669b419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x03257740 in ?? ()
#20 0x03257703 in ?? ()
#21 0x03257495 in ?? ()
#22 0x00f98765 in ?? ()
#23 0x00f98612 in ?? ()
#24 0x00f98546 in ?? ()
#25 0x00576811 in ?? ()
#26 0x00573a3e in ?? ()
#27 0x005739ab in ?? ()
#28 0x081112ae in mono_runtime_exec_main ()
#29 0x0057392b in ?? ()
#30 0x00573814 in ?? ()
#31 0x005736ee in ?? ()
#32 0x00573698 in ?? ()
#33 0x0057361a in ?? ()
#34 0x005735cb in ?? ()
#35 0x00572b2a in ?? ()
#36 0x004813f9 in ?? ()
#37 0x004811fa in ?? ()
#38 0x081112ae in mono_runtime_exec_main ()
#39 0x081134da in mono_runtime_run_main ()
#40 0x080b19bd in mono_main ()
#41 0x0805aba5 in ?? ()
#42 0x0012cb56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#43 0x0805aae1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by afrodeity on 2010-02-10
```

Native stacktrace:

	banshee-1 [0x80c8824]
	banshee-1 [0x80f4693]
	[0xe62410]
	/usr/lib/libGL.so.1 [0x35bdad2]
	/usr/lib/libclutter-glx-1.0.so.0(cogl_texture_get_data+0x2e9) [0x83c9699]
	/usr/lib/libclutter-glx-1.0.so.0 [0x83a7b5c]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0xcb79fc]
	/usr/lib/libgobject-2.0.so.0 [0xca86f9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xca9f98]
	/usr/lib/libgobject-2.0.so.0 [0xcbf49e]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0xcc0b2d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xcc0fb6]
	/usr/lib/libclutter-glx-1.0.so.0 [0x8365aa2]
	/usr/lib/libclutter-glx-1.0.so.0 [0x83881e4]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_container_foreach_with_internals+0xc3) [0x8384ad3]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_actor_real_unrealize+0xa2) [0x8366202]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0xcb79fc]
	/usr/lib/libgobject-2.0.so.0 [0xca86f9]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0xcaa072]
	/usr/lib/libgobject-2.0.so.0 [0xcbf49e]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0xcc0b2d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xcc0fb6]
	/usr/lib/libclutter-glx-1.0.so.0 [0x8365aa2]
	/usr/lib/libclutter-glx-1.0.so.0 [0x836ed62]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_actor_unparent+0x97) [0x836f767]
	/usr/lib/libclutter-glx-1.0.so.0 [0x838883c]
	/usr/lib/libclutter-glx-1.0.so.0(clutter_container_remove_actor+0x155) [0x8384f45]
	[0x4a7170f]
	[0x4a716c4]
	[0x480f437]
	[0x61515bd]
	[0x615155f]
	[0x5108f0]
	banshee-1 [0x812ba39]
	banshee-1 [0x812bbeb]
	banshee-1 [0x814f96c]
	banshee-1 [0x81bf9f2]
	banshee-1 [0x81de055]
	/lib/tls/i686/cmov/libpthread.so.0 [0xfc380e]
	/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x1e28de]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x2408b70 (LWP 7894)]
[New Thread 0xafdfbb70 (LWP 7892)]
[New Thread 0xb05fcb70 (LWP 7891)]
[New Thread 0xb0dfdb70 (LWP 7890)]
[New Thread 0xb55ffb70 (LWP 7889)]
[New Thread 0x1fc7b70 (LWP 7888)]
[New Thread 0x42d3b70 (LWP 7887)]
[New Thread 0x2f01b70 (LWP 7883)]
[New Thread 0x2449b70 (LWP 7881)]
[New Thread 0x2b74b70 (LWP 7879)]
[New Thread 0x2a73b70 (LWP 7878)]
[New Thread 0x2972b70 (LWP 7877)]
[New Thread 0x166eb70 (LWP 7873)]
[New Thread 0x88fb70 (LWP 7869)]
[New Thread 0x645b70 (LWP 7868)]
0x00e62422 in __kernel_vsyscall ()
  16 Thread 0x645b70 (LWP 7868)  0x00e62422 in __kernel_vsyscall ()
  15 Thread 0x88fb70 (LWP 7869)  0x00e62422 in __kernel_vsyscall ()
  14 Thread 0x166eb70 (LWP 7873)  0x00e62422 in __kernel_vsyscall ()
  13 Thread 0x2972b70 (LWP 7877)  0x00e62422 in __kernel_vsyscall ()
  12 Thread 0x2a73b70 (LWP 7878)  0x00e62422 in __kernel_vsyscall ()
  11 Thread 0x2b74b70 (LWP 7879)  0x00e62422 in __kernel_vsyscall ()
  10 Thread 0x2449b70 (LWP 7881)  0x00e62422 in __kernel_vsyscall ()
  9 Thread 0x2f01b70 (LWP 7883)  0x00e62422 in __kernel_vsyscall ()
  8 Thread 0x42d3b70 (LWP 7887)  0x00e62422 in __kernel_vsyscall ()
  7 Thread 0x1fc7b70 (LWP 7888)  0x00e62422 in __kernel_vsyscall ()
  6 Thread 0xb55ffb70 (LWP 7889)  0x00e62422 in __kernel_vsyscall ()
  5 Thread 0xb0dfdb70 (LWP 7890)  0x00e62422 in __kernel_vsyscall ()
  4 Thread 0xb05fcb70 (LWP 7891)  0x00e62422 in __kernel_vsyscall ()
  3 Thread 0xafdfbb70 (LWP 7892)  0x00e62422 in __kernel_vsyscall ()
  2 Thread 0x2408b70 (LWP 7894)  0x00e62422 in __kernel_vsyscall ()
* 1 Thread 0x4d46f0 (LWP 7866)  0x00e62422 in __kernel_vsyscall ()

Thread 16 (Thread 0x645b70 (LWP 7868)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a3658 in ?? ()
#3  0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 15 (Thread 0x88fb70 (LWP 7869)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcac8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()
#3  0x080f4693 in ?? ()
#4  <signal handler called>
#5  0x035bdad2 in glPixelStorei () from /usr/lib/libGL.so.1
#6  0x083c9309 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#7  0x083c9699 in cogl_texture_get_data ()
   from /usr/lib/libclutter-glx-1.0.so.0
#8  0x083a7b5c in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#9  0x00cb79fc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#10 0x00ca86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#11 0x00ca9f98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#12 0x00cbf49e in ?? () from /usr/lib/libgobject-2.0.so.0
#13 0x00cc0b2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#14 0x00cc0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#15 0x08365aa2 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#16 0x083881e4 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#17 0x08384ad3 in clutter_container_foreach_with_internals ()
   from /usr/lib/libclutter-glx-1.0.so.0
#18 0x08366202 in clutter_actor_real_unrealize ()
   from /usr/lib/libclutter-glx-1.0.so.0
#19 0x00cb79fc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#20 0x00ca86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#21 0x00caa072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#22 0x00cbf49e in ?? () from /usr/lib/libgobject-2.0.so.0
#23 0x00cc0b2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#24 0x00cc0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#25 0x08365aa2 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#26 0x0836ed62 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#27 0x0836f767 in clutter_actor_unparent ()
   from /usr/lib/libclutter-glx-1.0.so.0
#28 0x0838883c in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#29 0x08384f45 in clutter_container_remove_actor ()
   from /usr/lib/libclutter-glx-1.0.so.0
#30 0x04a7170f in ?? ()
#31 0x04a716c4 in ?? ()
#32 0x0480f437 in ?? ()
#33 0x061515bd in ?? ()
#34 0x0615155f in ?? ()
#35 0x005108f0 in ?? ()
#36 0x0812ba39 in ?? ()
#37 0x0812bbeb in ?? ()
#38 0x0814f96c in ?? ()
#39 0x081bf9f2 in ?? ()
#40 0x081de055 in ?? ()
#41 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#42 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 14 (Thread 0x166eb70 (LWP 7873)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x00ecbbbd in ?? ()
#8  0x00eca62a in ?? ()
#9  0x00483df0 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 13 (Thread 0x2972b70 (LWP 7877)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x061514b3 in ?? ()
#7  0x02246bf5 in ?? ()
#8  0x022468b9 in ?? ()
#9  0x0224658d in ?? ()
#10 0x00481086 in ?? ()
#11 0x08114f4b in mono_runtime_invoke_array ()
#12 0x0811512e in ?? ()
#13 0x081520a3 in ?? ()
#14 0x08152577 in ?? ()
#15 0x0814f96c in ?? ()
#16 0x081bf9f2 in ?? ()
#17 0x081de055 in ?? ()
#18 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#19 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0x2a73b70 (LWP 7878)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x061514b3 in ?? ()
#7  0x02246bf5 in ?? ()
#8  0x022468b9 in ?? ()
#9  0x0224658d in ?? ()
#10 0x00481086 in ?? ()
#11 0x08114f4b in mono_runtime_invoke_array ()
#12 0x0811512e in ?? ()
#13 0x081520a3 in ?? ()
#14 0x08152577 in ?? ()
#15 0x0814f96c in ?? ()
#16 0x081bf9f2 in ?? ()
#17 0x081de055 in ?? ()
#18 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#19 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0x2b74b70 (LWP 7879)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x022468b9 in ?? ()
#8  0x0224658d in ?? ()
#9  0x00481086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0x2449b70 (LWP 7881)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x001d4c96 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x006c054b in g_poll () from /lib/libglib-2.0.so.0
#3  0x006b356b in ?? () from /lib/libglib-2.0.so.0
#4  0x006b3b9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x084d98c0 in ?? () from /usr/lib/libORBit-2.so.0
#6  0x006da37f in ?? () from /lib/libglib-2.0.so.0
#7  0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0x2f01b70 (LWP 7883)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x00b05ee8 in ?? ()
#8  0x00b0b19a in ?? ()
#9  0x00b0b04a in ?? ()
#10 0x0527bbe2 in ?? ()
#11 0x0527ee25 in ?? ()
#12 0x02263050 in ?? ()
#13 0x00481086 in ?? ()
#14 0x08114f4b in mono_runtime_invoke_array ()
#15 0x0811512e in ?? ()
#16 0x081520a3 in ?? ()
#17 0x08152577 in ?? ()
#18 0x0814f96c in ?? ()
#19 0x081bf9f2 in ?? ()
#20 0x081de055 in ?? ()
#21 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#22 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0x42d3b70 (LWP 7887)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x036c7a78 in ?? ()
#8  0x03f9c849 in ?? ()
#9  0x00483df0 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0x1fc7b70 (LWP 7888)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x036fb084 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x03285ef5 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#6  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#7  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#8  0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#10 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#11 0x03e08c75 in ?? () from /usr/lib/gstreamer-0.10/libgstflump3dec.so
#12 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#13 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x0371460e in ?? () from /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
#15 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#16 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x04631fff in ?? () from /usr/lib/libgsttag-0.10.so.0
#18 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#19 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x036ff5d7 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#21 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#23 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#25 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#26 0x016c063e in ?? () from /usr/lib/libgstbase-0.10.so.0
#27 0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#28 0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#29 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#30 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#31 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#32 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb55ffb70 (LWP 7889)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x001d4c96 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x03e659e2 in ?? () from /usr/lib/libpulse.so.0
#3  0x03e52a79 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0x03e54893 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0x03e54964 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0x03e658e3 in ?? () from /usr/lib/libpulse.so.0
#7  0x03f792f2 in ?? () from /usr/lib/libpulsecommon-0.9.21.so
#8  0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb0dfdb70 (LWP 7890)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x03f77fac in pa_cond_wait () from /usr/lib/libpulsecommon-0.9.21.so
#3  0x03e65cc0 in pa_threaded_mainloop_wait () from /usr/lib/libpulse.so.0
#4  0x064ee8fa in ?? () from /usr/lib/gstreamer-0.10/libgstpulse.so
#5  0x03733a4d in gst_ring_buffer_commit_full ()
   from /usr/lib/libgstaudio-0.10.so.0
#6  0x0373bd8a in ?? () from /usr/lib/libgstaudio-0.10.so.0
#7  0x016b0ef8 in ?? () from /usr/lib/libgstbase-0.10.so.0
#8  0x016b26b7 in ?? () from /usr/lib/libgstbase-0.10.so.0
#9  0x016b4759 in ?? () from /usr/lib/libgstbase-0.10.so.0
#10 0x016b4d0d in ?? () from /usr/lib/libgstbase-0.10.so.0
#11 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#12 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#13 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#15 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#16 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#19 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#21 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#23 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#25 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#26 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#27 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#28 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#29 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#30 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#31 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#32 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#33 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#34 0x036f94cd in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#35 0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#36 0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#37 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#38 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#39 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#40 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb05fcb70 (LWP 7891)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x02c906e6 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#3  0x02c9c6c7 in gst_pad_push_event () from /usr/lib/libgstreamer-0.10.so.0
#4  0x016c7182 in ?? () from /usr/lib/libgstbase-0.10.so.0
#5  0x02c9bdde in gst_pad_send_event () from /usr/lib/libgstreamer-0.10.so.0
#6  0x02c9c5bb in gst_pad_push_event () from /usr/lib/libgstreamer-0.10.so.0
#7  0x036f9933 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#8  0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#10 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#11 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#12 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xafdfbb70 (LWP 7892)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc7e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x036fb084 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x036fc32d in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#6  0x036fc82d in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#7  0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#8  0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#10 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#11 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#12 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#13 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#15 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#16 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#17 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x016c9868 in ?? () from /usr/lib/libgstbase-0.10.so.0
#19 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#21 0x02c83f2d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x02c9aa95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#23 0x02c9b600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x036f94cd in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#25 0x02cba895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#26 0x02cbc1a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#27 0x006db9af in ?? () from /lib/libglib-2.0.so.0
#28 0x006da37f in ?? () from /lib/libglib-2.0.so.0
#29 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#30 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0x2408b70 (LWP 7894)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fcb466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be7f0 in ?? ()
#3  0x081be8b5 in ?? ()
#4  0x0814fbec in ?? ()
#5  0x0814fef0 in ?? ()
#6  0x00ab506f in ?? ()
#7  0x0614fb4e in ?? ()
#8  0x0614efa2 in ?? ()
#9  0x0614eecc in ?? ()
#10 0x0614ee7b in ?? ()
#11 0x0614e1b3 in ?? ()
#12 0x0614da8a in ?? ()
#13 0x0614d904 in ?? ()
#14 0x0614d478 in ?? ()
#15 0x04f5d792 in ?? ()
#16 0x04f5d3c6 in ?? ()
#17 0x04f5cf36 in ?? ()
#18 0x04f5c449 in ?? ()
#19 0x06142a4d in ?? ()
#20 0x022612a2 in ?? ()
#21 0x00483df0 in ?? ()
#22 0x0810e6a4 in mono_runtime_delegate_invoke ()
#23 0x0814f9d7 in ?? ()
#24 0x081bf9f2 in ?? ()
#25 0x081de055 in ?? ()
#26 0x00fc380e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#27 0x001e28de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0x4d46f0 (LWP 7866)):
#0  0x00e62422 in __kernel_vsyscall ()
#1  0x00fc8142 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a83c4 in ?? ()
#3  0x081c3c28 in ?? ()
#4  0x0812c7e5 in mono_domain_finalize ()
#5  0x0805b4e0 in ?? ()
#6  0x08159a03 in mono_runtime_quit ()
#7  0x0812095a in ?? ()
#8  0x06151454 in ?? ()
#9  0x0614f6ac in ?? ()
#10 0x03d5b87e in ?? ()
#11 0x00966201 in ?? ()
#12 0x0838df4d in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#13 0x083b1b83 in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#14 0x0838813e in ?? () from /usr/lib/libclutter-glx-1.0.so.0
#15 0x006afe88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#16 0x006b3730 in ?? () from /lib/libglib-2.0.so.0
#17 0x006b3b9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#18 0x0669b419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#19 0x03257740 in ?? ()
#20 0x03257703 in ?? ()
#21 0x03257495 in ?? ()
#22 0x00f98765 in ?? ()
#23 0x00f98612 in ?? ()
#24 0x00f98546 in ?? ()
#25 0x00576811 in ?? ()
#26 0x00573a3e in ?? ()
#27 0x005739ab in ?? ()
#28 0x081112ae in mono_runtime_exec_main ()
#29 0x0057392b in ?? ()
#30 0x00573814 in ?? ()
#31 0x005736ee in ?? ()
#32 0x00573698 in ?? ()
#33 0x0057361a in ?? ()
#34 0x005735cb in ?? ()
#35 0x00572b2a in ?? ()
#36 0x004813f9 in ?? ()
#37 0x004811fa in ?? ()
#38 0x081112ae in mono_runtime_exec_main ()
#39 0x081134da in mono_runtime_run_main ()
#40 0x080b19bd in mono_main ()
#41 0x0805aba5 in ?? ()
#42 0x0012cb56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#43 0x0805aae1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by tgalati4 on 2010-02-10
Can you turn off the clutterflow display and see if Banshee runs longer than 3 seconds?  Also if you have compiz, try turning it off:

metacity --replace &

Then run banshee.

compiz --replace &

To turn compiz back on when you are finished.

---

### Post by afrodeity on 2010-02-11
clutterflow was on, now its off. I tried turning off compiz. Same problem. Quits when I play anything. Maybe I should remove clutterflow completely from the system or reinstall?

---

### Post by afrodeity on 2010-02-11
Well its working fine now after I removed banshee-clutterflow-plugin in synaptic. So you right, sigh. Maybe I'm missing something. Should I try compiling it?

---

### Post by tgalati4 on 2010-02-11
File a bug with both mono and banshee and reference this thread.  You can try compiling from scratch, but I would be 90% confident that you will simply recreate the bug.  I'm running Jaunty, so I don't have access to the banshee clutterflow plug-in.  And I don't feel like breaking my current, working banshee install by playing with it.

You will have to file some bug reports and see if there is a quick fix.

---

