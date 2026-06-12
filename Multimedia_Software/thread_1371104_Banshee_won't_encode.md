---
title: "Banshee won't encode"
date: 2010-01-03
forum: Multimedia Software
---

### Post by Da CalebMan on 2010-01-03
banshee won't encode to mp3 when importing to my ipod shuffle 1st gen. My music collection is all ogg, and wma. Do I need to install an extra plugin? Please help.

---

### Post by Yellow Pasque on 2010-01-03
Banshee uses gstreamer for its backend. Make sure you have the gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-bad, gstreamer0.10-ffmpeg packages installed.

EDIT: You can also try the soundconverter package/program

---

### Post by Da CalebMan on 2010-01-03
Thanks for replying, 
I also have problems with banshee not playing video it simply crashes. I installed all the codecs.:(

---

### Post by Yellow Pasque on 2010-01-03
Can you start banshee from a terminal and see if it gives error output?

---

### Post by Da CalebMan on 2010-01-03
The whole thing is quite long, but it's at the bottom where the error is.

```
$ banshee
[Info  07:54:12.099] Running Banshee 1.5.1: [Ubuntu karmic (development branch) (linux-gnu, i486) @ 2009-10-19 14:46:07 UTC]

(/usr/lib/banshee-1/Banshee.exe:1753): GLib-WARNING **: g_set_prgname() called multiple times

(/usr/lib/banshee-1/Banshee.exe:1753): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'

(/usr/lib/banshee-1/Banshee.exe:1753): Gtk-CRITICAL **: gtk_container_child_set_property: assertion `child->parent == GTK_WIDGET (container)' failed
[Info  07:54:18.722] All services are started 5.524986s
[Info  07:54:22.518] nereid Client Started

Native stacktrace:

	banshee-1 [0x80c8824]
	banshee-1 [0x805d448]
	[0x64d410]
	/usr/lib/libGL.so.1 [0x51e5326]
	/usr/lib/libgobject-2.0.so.0(g_type_create_instance+0x13f) [0x76799f]
	/usr/lib/libgobject-2.0.so.0 [0x74c748]
	/usr/lib/libgobject-2.0.so.0(g_object_newv+0x552) [0x74db62]
	/usr/lib/libgobject-2.0.so.0(g_object_new_valist+0x2ba) [0x74e58a]
	/usr/lib/libgobject-2.0.so.0(g_object_new+0x6e) [0x74e70e]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_factory_create+0x90) [0x76b8190]
	/usr/lib/gstreamer-0.10/libgstautodetect.so [0x3147d43]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x76b3005]
	/usr/lib/libgstreamer-0.10.so.0 [0x76b6614]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x76b2260]
	/usr/lib/libgstreamer-0.10.so.0 [0x76a1477]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x76b3005]
	/usr/lib/libgstreamer-0.10.so.0 [0x76b6614]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x76b2260]
	/usr/lib/libgstreamer-0.10.so.0 [0x76a1477]
	/usr/lib/gstreamer-0.10/libgstgconfelements.so [0x2b1aa06]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x76b3005]
	/usr/lib/libgstreamer-0.10.so.0 [0x76b6614]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x76b2260]
	/usr/lib/libgstreamer-0.10.so.0 [0x76a1477]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_change_state+0x35) [0x76b3005]
	/usr/lib/libgstreamer-0.10.so.0 [0x76b6614]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_set_state+0x90) [0x76b2260]
	/usr/lib/gstreamer-0.10/libgstplaybin.so [0x2aeb23b]
	/usr/lib/gstreamer-0.10/libgstplaybin.so [0x2aec58e]
	/usr/lib/gstreamer-0.10/libgstplaybin.so [0x2b01334]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x7549fc]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x747072]
	/usr/lib/libgobject-2.0.so.0 [0x75c7a8]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x75db2d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x75dfb6]
	/usr/lib/libgstreamer-0.10.so.0(gst_element_no_more_pads+0x8a) [0x76b49da]
	/usr/lib/gstreamer-0.10/libgstdecodebin.so [0x7b8775e]
	/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__PARAM+0x88) [0x754118]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x747072]
	/usr/lib/libgobject-2.0.so.0 [0x75c7a8]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x75db2d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x75dfb6]
	/usr/lib/libgobject-2.0.so.0 [0x74b3e1]
	/usr/lib/libgstreamer-0.10.so.0 [0x76996c1]
	/usr/lib/libgobject-2.0.so.0 [0x747daf]
	/usr/lib/libgobject-2.0.so.0(g_object_notify+0x2a3) [0x74cec3]
	/usr/lib/libgstreamer-0.10.so.0(gst_pad_set_caps+0x1cf) [0x76ccb4f]
	/usr/lib/gstreamer-0.10/libgstmpegaudioparse.so [0x32d0729]
	/usr/lib/libgstreamer-0.10.so.0 [0x76d3a95]
	/usr/lib/libgstreamer-0.10.so.0 [0x76d4600]
	/usr/lib/gstreamer-0.10/libgstcoreelements.so [0x2f824cd]
	/usr/lib/libgstreamer-0.10.so.0 [0x76f3895]
	/usr/lib/libgstreamer-0.10.so.0 [0x76f51a7]
	/lib/libglib-2.0.so.0 [0x8da9af]
	/lib/libglib-2.0.so.0 [0x8d937f]
	/lib/tls/i686/cmov/libpthread.so.0 [0x7da80e]
	/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x51e7ee]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0xabcc0b70 (LWP 1776)]
[New Thread 0xac4c1b70 (LWP 1775)]
[New Thread 0xaccc2b70 (LWP 1774)]
[New Thread 0xb14c4b70 (LWP 1773)]
[New Thread 0xb1cc5b70 (LWP 1772)]
[New Thread 0xb24c6b70 (LWP 1771)]
[New Thread 0xb34ffb70 (LWP 1770)]
[New Thread 0x3b4eb70 (LWP 1769)]
[New Thread 0x34f2b70 (LWP 1768)]
[New Thread 0x5903b70 (LWP 1764)]
[New Thread 0x4fefb70 (LWP 1763)]
[New Thread 0x35f3b70 (LWP 1762)]
[New Thread 0x1e9bb70 (LWP 1760)]
[New Thread 0x169ab70 (LWP 1757)]
[New Thread 0xa2db70 (LWP 1756)]
[New Thread 0xc5eb70 (LWP 1755)]
0x0064d422 in __kernel_vsyscall ()
  17 Thread 0xc5eb70 (LWP 1755)  0x0064d422 in __kernel_vsyscall ()
  16 Thread 0xa2db70 (LWP 1756)  0x0064d422 in __kernel_vsyscall ()
  15 Thread 0x169ab70 (LWP 1757)  0x0064d422 in __kernel_vsyscall ()
  14 Thread 0x1e9bb70 (LWP 1760)  0x0064d422 in __kernel_vsyscall ()
  13 Thread 0x35f3b70 (LWP 1762)  0x0064d422 in __kernel_vsyscall ()
  12 Thread 0x4fefb70 (LWP 1763)  0x0064d422 in __kernel_vsyscall ()
  11 Thread 0x5903b70 (LWP 1764)  0x0064d422 in __kernel_vsyscall ()
  10 Thread 0x34f2b70 (LWP 1768)  0x0064d422 in __kernel_vsyscall ()
  9 Thread 0x3b4eb70 (LWP 1769)  0x0064d422 in __kernel_vsyscall ()
  8 Thread 0xb34ffb70 (LWP 1770)  0x0064d422 in __kernel_vsyscall ()
  7 Thread 0xb24c6b70 (LWP 1771)  0x0064d422 in __kernel_vsyscall ()
  6 Thread 0xb1cc5b70 (LWP 1772)  0x0064d422 in __kernel_vsyscall ()
  5 Thread 0xb14c4b70 (LWP 1773)  0x0064d422 in __kernel_vsyscall ()
  4 Thread 0xaccc2b70 (LWP 1774)  0x0064d422 in __kernel_vsyscall ()
  3 Thread 0xac4c1b70 (LWP 1775)  0x0064d422 in __kernel_vsyscall ()
  2 Thread 0xabcc0b70 (LWP 1776)  0x0064d422 in __kernel_vsyscall ()
* 1 Thread 0xef36f0 (LWP 1753)  0x0064d422 in __kernel_vsyscall ()

Thread 17 (Thread 0xc5eb70 (LWP 1755)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007e2466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a3658 in ?? ()
#3  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 16 (Thread 0xa2db70 (LWP 1756)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007e0f75 in sem_wait@@GLIBC_2.1 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812bb29 in ?? ()
#3  0x0814f96c in ?? ()
#4  0x081bf9f2 in ?? ()
#5  0x081de055 in ?? ()
#6  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 15 (Thread 0x169ab70 (LWP 1757)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814c923 in ?? ()
#6  0x00c09e65 in ?? ()
#7  0x00c09c7d in ?? ()
#8  0x00c09242 in ?? ()
#9  0x00708df0 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 14 (Thread 0x1e9bb70 (LWP 1760)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x00510ba6 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x065a8cc2 in ?? () from /usr/lib/libpulse.so.0
#3  0x06595e09 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0x06597c23 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0x06597cf4 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0x065a8bc3 in ?? () from /usr/lib/libpulse.so.0
#7  0x02accac2 in ?? () from /usr/lib/libpulsecommon-0.9.19.so
#8  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 13 (Thread 0x35f3b70 (LWP 1762)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a8577 in ?? ()
#4  0x081c4403 in ?? ()
#5  0x0814e4a8 in ?? ()
#6  0x032f4cc5 in ?? ()
#7  0x032f4a79 in ?? ()
#8  0x032f474d in ?? ()
#9  0x00706086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0x4fefb70 (LWP 1763)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a8577 in ?? ()
#4  0x081c4403 in ?? ()
#5  0x0814e4a8 in ?? ()
#6  0x032f4cc5 in ?? ()
#7  0x032f4a79 in ?? ()
#8  0x032f474d in ?? ()
#9  0x00706086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0x5903b70 (LWP 1764)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a8577 in ?? ()
#4  0x081c4403 in ?? ()
#5  0x0814e4a8 in ?? ()
#6  0x032f4cc5 in ?? ()
#7  0x032f4a79 in ?? ()
#8  0x032f474d in ?? ()
#9  0x00706086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0x34f2b70 (LWP 1768)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007e1c8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x005b4482 in Mono_Posix_Syscall_read ()
   from /usr/lib/libMonoPosixHelper.so
#3  0x0071364a in ?? ()
#4  0x002cf8e2 in ?? ()
#5  0x002cf792 in ?? ()
#6  0x0685d072 in ?? ()
#7  0x068602b5 in ?? ()
#8  0x06855078 in ?? ()
#9  0x00706086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0x3b4eb70 (LWP 1769)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007e1e98 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081bc73e in ?? ()
#3  0x0815838b in ?? ()
#4  0x03016b35 in ?? ()
#5  0x03016978 in ?? ()
#6  0x03016879 in ?? ()
#7  0x00708df0 in ?? ()
#8  0x0810e6a4 in mono_runtime_delegate_invoke ()
#9  0x0814f9d7 in ?? ()
#10 0x081bf9f2 in ?? ()
#11 0x081de055 in ?? ()
#12 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb34ffb70 (LWP 1770)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x02f84084 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x076d3a95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x076d4600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x030e2bc8 in ?? () from /usr/lib/gstreamer-0.10/libgstavi.so
#6  0x030ec043 in ?? () from /usr/lib/gstreamer-0.10/libgstavi.so
#7  0x076f3895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#8  0x076f51a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#9  0x008da9af in ?? () from /lib/libglib-2.0.so.0
#10 0x008d937f in ?? () from /lib/libglib-2.0.so.0
#11 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb24c6b70 (LWP 1771)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x02f81d71 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x076f3895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x076f51a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x008da9af in ?? () from /lib/libglib-2.0.so.0
#6  0x008d937f in ?? () from /lib/libglib-2.0.so.0
#7  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb1cc5b70 (LWP 1772)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007e1c8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()
#3  0x0805d448 in ?? ()
#4  <signal handler called>
#5  0x051e5326 in glGetString () from /usr/lib/libGL.so.1
#6  0x00d68e1b in ?? () from /usr/lib/banshee-1/libbanshee.so
#7  0x0076799f in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#8  0x0074c748 in ?? () from /usr/lib/libgobject-2.0.so.0
#9  0x0074db62 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#10 0x0074e58a in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#11 0x0074e70e in g_object_new () from /usr/lib/libgobject-2.0.so.0
#12 0x076b8190 in gst_element_factory_create ()
   from /usr/lib/libgstreamer-0.10.so.0
#13 0x03147d43 in ?? () from /usr/lib/gstreamer-0.10/libgstautodetect.so
#14 0x076b3005 in gst_element_change_state ()
   from /usr/lib/libgstreamer-0.10.so.0
#15 0x076b6614 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#16 0x076b2260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#17 0x076a1477 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x076b3005 in gst_element_change_state ()
   from /usr/lib/libgstreamer-0.10.so.0
#19 0x076b6614 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#20 0x076b2260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#21 0x076a1477 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#22 0x02b1aa06 in ?? () from /usr/lib/gstreamer-0.10/libgstgconfelements.so
#23 0x076b3005 in gst_element_change_state ()
   from /usr/lib/libgstreamer-0.10.so.0
#24 0x076b6614 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#25 0x076b2260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#26 0x076a1477 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#27 0x076b3005 in gst_element_change_state ()
   from /usr/lib/libgstreamer-0.10.so.0
#28 0x076b6614 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#29 0x076b2260 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#30 0x02aeb23b in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#31 0x02aec58e in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#32 0x02b01334 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#33 0x007549fc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#34 0x00747072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#35 0x0075c7a8 in ?? () from /usr/lib/libgobject-2.0.so.0
#36 0x0075db2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#37 0x0075dfb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#38 0x076b49da in gst_element_no_more_pads ()
   from /usr/lib/libgstreamer-0.10.so.0
#39 0x07b8775e in ?? () from /usr/lib/gstreamer-0.10/libgstdecodebin.so
#40 0x00754118 in g_cclosure_marshal_VOID__PARAM ()
   from /usr/lib/libgobject-2.0.so.0
#41 0x00747072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#42 0x0075c7a8 in ?? () from /usr/lib/libgobject-2.0.so.0
#43 0x0075db2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#44 0x0075dfb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#45 0x0074b3e1 in ?? () from /usr/lib/libgobject-2.0.so.0
#46 0x076996c1 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#47 0x00747daf in ?? () from /usr/lib/libgobject-2.0.so.0
#48 0x0074cec3 in g_object_notify () from /usr/lib/libgobject-2.0.so.0
#49 0x076ccb4f in gst_pad_set_caps () from /usr/lib/libgstreamer-0.10.so.0
#50 0x032d0729 in ?? () from /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
#51 0x076d3a95 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#52 0x076d4600 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#53 0x02f824cd in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#54 0x076f3895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#55 0x076f51a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#56 0x008da9af in ?? () from /lib/libglib-2.0.so.0
#57 0x008d937f in ?? () from /lib/libglib-2.0.so.0
#58 0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#59 0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb14c4b70 (LWP 1773)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x00510ba6 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x065a8cc2 in ?? () from /usr/lib/libpulse.so.0
#3  0x06595e09 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0x06597c23 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0x06597cf4 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0x065a8bc3 in ?? () from /usr/lib/libpulse.so.0
#7  0x02accac2 in ?? () from /usr/lib/libpulsecommon-0.9.19.so
#8  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xaccc2b70 (LWP 1774)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x02f81d71 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x076f3895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x076f51a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x008da9af in ?? () from /lib/libglib-2.0.so.0
#6  0x008d937f in ?? () from /lib/libglib-2.0.so.0
#7  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xac4c1b70 (LWP 1775)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x02f81d71 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x076f3895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x076f51a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x008da9af in ?? () from /lib/libglib-2.0.so.0
#6  0x008d937f in ?? () from /lib/libglib-2.0.so.0
#7  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xabcc0b70 (LWP 1776)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x007dee15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x02f81d71 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#3  0x076f3895 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#4  0x076f51a7 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#5  0x008da9af in ?? () from /lib/libglib-2.0.so.0
#6  0x008d937f in ?? () from /lib/libglib-2.0.so.0
#7  0x007da80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x0051e7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xef36f0 (LWP 1753)):
#0  0x0064d422 in __kernel_vsyscall ()
#1  0x00510ba6 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x008bf54b in g_poll () from /lib/libglib-2.0.so.0
#3  0x008b256b in ?? () from /lib/libglib-2.0.so.0
#4  0x008b2b9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x07007419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x07791e28 in ?? ()
#7  0x07791deb in ?? ()
#8  0x07791b7d in ?? ()
#9  0x00433195 in ?? ()
#10 0x00433042 in ?? ()
#11 0x00432f76 in ?? ()
#12 0x00c7f169 in ?? ()
#13 0x00c7c366 in ?? ()
#14 0x00c7c2d3 in ?? ()
#15 0x081112ae in mono_runtime_exec_main ()
#16 0x00c7c253 in ?? ()
#17 0x00c7c13c in ?? ()
#18 0x00c7c016 in ?? ()
#19 0x00c7bfc0 in ?? ()
#20 0x00c7bf42 in ?? ()
#21 0x00c7bef3 in ?? ()
#22 0x00c7b452 in ?? ()
#23 0x007063f9 in ?? ()
#24 0x007061fa in ?? ()
#25 0x081112ae in mono_runtime_exec_main ()
#26 0x081134da in mono_runtime_run_main ()
#27 0x080b19bd in mono_main ()
#28 0x0805aba5 in ?? ()
#29 0x00468b56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#30 0x0805aae1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
```

---

### Post by Yellow Pasque on 2010-01-03
```
gstreamer-properties
```
Under the video tab, does the test work?

---

### Post by Da CalebMan on 2010-01-05
Neither VFL, nor VFL2 work. These are the errors:

```
"Video for Linux (v4l): Device "/dev/video0" does not exist"
``` 

"```
Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'."
```

I haven't tried custom yet...

---

### Post by Yellow Pasque on 2010-01-05
I was asking about the 'Default Output' video test..

---

### Post by Da CalebMan on 2010-01-06
Sorry! It's set to autodetect, and the test seems to wrok fine.

~Caleb

---

### Post by John Peschken on 2010-09-05
> **Da CalebMan said:**
> banshee won't encode to mp3 when importing to my ipod shuffle 1st gen. My music collection is all ogg, and wma. Do I need to install an extra plugin? Please help.
I have a similar problem.  My music is in Vorbis FLAC format on my hard drive.  I have the device properties for my Sansa e260 set as "Encode to OGG Vorbis", but the files end up on the player still  in FLAC format.  

The Sansa shows up as "Rockbox device" since I have Rockbox installed on it,  I am sending them to the player by drag and dropping them onto the Rockbox device.

Rockbox reports that it is "Adding 1 of 1 to Rockbox Device".  It happens too fast for any conversion to be going on. Shouldn't Banshee be converting to the "Encode To" format when I do this?

---

