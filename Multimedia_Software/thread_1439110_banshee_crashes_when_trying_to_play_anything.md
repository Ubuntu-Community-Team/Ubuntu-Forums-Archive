---
title: "banshee crashes when trying to play anything"
date: 2010-03-25
forum: Multimedia Software
---

### Post by evanct on 2010-03-25
Banshee starts normally, but as soon as I try to play anything - audio or video - it instantly crashes with the error:

```
=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```

The full output:

```
Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0xae2ffb70 (LWP 3625)]
[New Thread 0x3561b70 (LWP 3624)]
[New Thread 0x3924b70 (LWP 3623)]
[New Thread 0x1fbab70 (LWP 3620)]
[New Thread 0x3287b70 (LWP 3618)]
[New Thread 0x21feb70 (LWP 3617)]
[New Thread 0x20fdb70 (LWP 3616)]
[New Thread 0xaf2b1b70 (LWP 3614)]
[New Thread 0x3108b70 (LWP 3613)]
[New Thread 0x12b3b70 (LWP 3611)]
[New Thread 0x9f0b70 (LWP 3610)]
[New Thread 0x237b70 (LWP 3609)]
0x008b607e in ?? () from /usr/lib/libfontconfig.so.1
  13 Thread 0x237b70 (LWP 3609)  0x00b5f422 in __kernel_vsyscall ()
  12 Thread 0x9f0b70 (LWP 3610)  0x00b5f422 in __kernel_vsyscall ()
  11 Thread 0x12b3b70 (LWP 3611)  0x00b5f422 in __kernel_vsyscall ()
  10 Thread 0x3108b70 (LWP 3613)  0x00b5f422 in __kernel_vsyscall ()
  9 Thread 0xaf2b1b70 (LWP 3614)  0x00b5f422 in __kernel_vsyscall ()
  8 Thread 0x20fdb70 (LWP 3616)  0x00b5f422 in __kernel_vsyscall ()
  7 Thread 0x21feb70 (LWP 3617)  0x00b5f422 in __kernel_vsyscall ()
  6 Thread 0x3287b70 (LWP 3618)  0x00b5f422 in __kernel_vsyscall ()
  5 Thread 0x1fbab70 (LWP 3620)  0x00b5f422 in __kernel_vsyscall ()
  4 Thread 0x3924b70 (LWP 3623)  0x00b5f422 in __kernel_vsyscall ()
  3 Thread 0x3561b70 (LWP 3624)  0x00b5f422 in __kernel_vsyscall ()
  2 Thread 0xae2ffb70 (LWP 3625)  0x00b5f422 in __kernel_vsyscall ()
* 1 Thread 0xc4a6f0 (LWP 3607)  0x008b607e in ?? () from /usr/lib/libfontconfig.so.1

Thread 13 (Thread 0x237b70 (LWP 3609)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070d736 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a5988 in ?? ()
#3  0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0x9f0b70 (LWP 3610)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070c245 in sem_wait@@GLIBC_2.1 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812d1c9 in ?? ()
#3  0x0815176a in ?? ()
#4  0x081c1e72 in ?? ()
#5  0x081e06a5 in ?? ()
#6  0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0x12b3b70 (LWP 3611)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070a015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ab711 in ?? ()
#3  0x081ab784 in ?? ()
#4  0x081c624f in ?? ()
#5  0x0814e6e3 in ?? ()
#6  0x00de8315 in ?? ()
#7  0x00de812c in ?? ()
#8  0x00de7672 in ?? ()
#9  0x005bba01 in ?? ()
#10 0x0810ff34 in mono_runtime_delegate_invoke ()
#11 0x081517db in ?? ()
#12 0x081c1e72 in ?? ()
#13 0x081e06a5 in ?? ()
#14 0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0x3108b70 (LWP 3613)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070a015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0b83177 in ?? () from /usr/lib/libwebkit-1.0.so.2
#3  0xb0b831b1 in ?? () from /usr/lib/libwebkit-1.0.so.2
#4  0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xaf2b1b70 (LWP 3614)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070a015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb0abee84 in ?? () from /usr/lib/libwebkit-1.0.so.2
#3  0xb085200f in ?? () from /usr/lib/libwebkit-1.0.so.2
#4  0xb08520e4 in ?? () from /usr/lib/libwebkit-1.0.so.2
#5  0xb0abedef in ?? () from /usr/lib/libwebkit-1.0.so.2
#6  0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0x20fdb70 (LWP 3616)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070a015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ab711 in ?? ()
#3  0x081ab807 in ?? ()
#4  0x081c6883 in ?? ()
#5  0x08150278 in ?? ()
#6  0x06a2cc65 in ?? ()
#7  0x06a2ca19 in ?? ()
#8  0x06a2c6ed in ?? ()
#9  0x005b5087 in ?? ()
#10 0x08114daf in mono_runtime_invoke_array ()
#11 0x08114ffe in ?? ()
#12 0x08153fb3 in ?? ()
#13 0x08154487 in ?? ()
#14 0x0815176a in ?? ()
#15 0x081c1e72 in ?? ()
#16 0x081e06a5 in ?? ()
#17 0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0x21feb70 (LWP 3617)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070a015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ab711 in ?? ()
#3  0x081ab807 in ?? ()
#4  0x081c6883 in ?? ()
#5  0x08150278 in ?? ()
#6  0x06a2cc65 in ?? ()
#7  0x06a2ca19 in ?? ()
#8  0x06a2c6ed in ?? ()
#9  0x005b5087 in ?? ()
#10 0x08114daf in mono_runtime_invoke_array ()
#11 0x08114ffe in ?? ()
#12 0x08153fb3 in ?? ()
#13 0x08154487 in ?? ()
#14 0x0815176a in ?? ()
#15 0x081c1e72 in ?? ()
#16 0x081e06a5 in ?? ()
#17 0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0x3287b70 (LWP 3618)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070a015 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081ab711 in ?? ()
#3  0x081ab807 in ?? ()
#4  0x081c6883 in ?? ()
#5  0x08150278 in ?? ()
#6  0x06a2cc65 in ?? ()
#7  0x06a2ca19 in ?? ()
#8  0x06a2c6ed in ?? ()
#9  0x005b5087 in ?? ()
#10 0x08114daf in mono_runtime_invoke_array ()
#11 0x08114ffe in ?? ()
#12 0x08153fb3 in ?? ()
#13 0x08154487 in ?? ()
#14 0x0815176a in ?? ()
#15 0x081c1e72 in ?? ()
#16 0x081e06a5 in ?? ()
#17 0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0x1fbab70 (LWP 3620)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x003f9b56 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x0015c5fb in IA__g_poll (fds=0x8ce82b8, nfds=5, timeout=-1) at /build/buildd/glib2.0-2.23.6/glib/gpoll.c:127
#3  0x0014f10c in g_main_context_poll (context=0x8ce4780, block=<value optimized out>, dispatch=1, self=0x8c944d0)
    at /build/buildd/glib2.0-2.23.6/glib/gmain.c:2904
#4  g_main_context_iterate (context=0x8ce4780, block=<value optimized out>, dispatch=1, self=0x8c944d0)
    at /build/buildd/glib2.0-2.23.6/glib/gmain.c:2586
#5  0x0014f877 in IA__g_main_loop_run (loop=0x8ce4530) at /build/buildd/glib2.0-2.23.6/glib/gmain.c:2799
#6  0x06c19160 in ?? () from /usr/lib/libORBit-2.so.0
#7  0x0017612f in g_thread_create_proxy (data=0x8c944d0) at /build/buildd/glib2.0-2.23.6/glib/gthread.c:1893
#8  0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0x3924b70 (LWP 3623)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070cf5b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0030d452 in Mono_Posix_Syscall_read () from /usr/lib/libMonoPosixHelper.so
#3  0x005c34aa in ?? ()
#4  0x0031944a in ?? ()
#5  0x003192fa in ?? ()
#6  0x025e3282 in ?? ()
#7  0x025e65f5 in ?? ()
#8  0x025db1c7 in ?? ()
#9  0x005b5087 in ?? ()
#10 0x08114daf in mono_runtime_invoke_array ()
#11 0x08114ffe in ?? ()
#12 0x08153fb3 in ?? ()
#13 0x08154487 in ?? ()
#14 0x0815176a in ?? ()
#15 0x081c1e72 in ?? ()
#16 0x081e06a5 in ?? ()
#17 0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0x3561b70 (LWP 3624)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070d168 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081be9de in ?? ()
#3  0x0815a29b in ?? ()
#4  0x0275d8dd in ?? ()
#5  0x0275d708 in ?? ()
#6  0x02730981 in ?? ()
#7  0x005bba01 in ?? ()
#8  0x0810ff34 in mono_runtime_delegate_invoke ()
#9  0x081517db in ?? ()
#10 0x081c1e72 in ?? ()
#11 0x081e06a5 in ?? ()
#12 0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xae2ffb70 (LWP 3625)):
#0  0x00b5f422 in __kernel_vsyscall ()
#1  0x0070cf5b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c99ce in ?? ()
#3  0x0805d548 in ?? ()
#4  <signal handler called>
#5  0x05a7db5b in ?? () from /usr/lib/gstreamer-0.10/libgstbluetooth.so
#6  0x05a7ec01 in ?? () from /usr/lib/gstreamer-0.10/libgstbluetooth.so
#7  0x052858af in ?? () from /usr/lib/libgstbase-0.10.so.0
#8  0x084ef435 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#9  0x084f2928 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#10 0x084ee7f0 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#11 0x05a7f63c in ?? () from /usr/lib/gstreamer-0.10/libgstbluetooth.so
#12 0x084ef435 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#13 0x084f2928 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#14 0x084ee7f0 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#15 0x084de827 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#16 0x084ef435 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#17 0x084f2928 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#18 0x084ee7f0 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#19 0x01e5793e in ?? () from /usr/lib/gstreamer-0.10/libgstgconfelements.so
#20 0x01e54c27 in ?? () from /usr/lib/gstreamer-0.10/libgstgconfelements.so
#21 0x01e54f7d in ?? () from /usr/lib/gstreamer-0.10/libgstgconfelements.so
#22 0x084ef435 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#23 0x084f2928 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#24 0x084ee7f0 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#25 0x084de827 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#26 0x084ef435 in gst_element_change_state () from /usr/lib/libgstreamer-0.10.so.0
#27 0x084f2928 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#28 0x084ee7f0 in gst_element_set_state () from /usr/lib/libgstreamer-0.10.so.0
#29 0x02213a92 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#30 0x02215e8c in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#31 0x0221857f in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#32 0x0220cb5b in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#33 0x006b143c in IA__g_cclosure_marshal_VOID__VOID (closure=0xae455a50, return_value=0x0, n_param_values=1, param_values=0xae5cb230, 
    invocation_hint=0xae2fe200, marshal_data=0x0) at /build/buildd/glib2.0-2.23.6/gobject/gmarshal.c:77
#34 0x006a3252 in IA__g_closure_invoke (closure=0xae41ecd0, return_value=0x0, n_param_values=1, param_values=0xae5cb230, 
    invocation_hint=0xae2fe200) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#35 0x006ba97d in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb737e270, 
    emission_return=0x0, instance_and_params=0xae5cb230) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3248
#36 0x006bbfe4 in IA__g_signal_emit_valist (instance=0xb737e270, signal_id=344, detail=0, 
    var_args=0xae2fe3bc "\364ox\002\364ox\002p\342\067\267\030\344/\256I\320w\002p\342\067\267\362Ax\002")
    at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2981
#37 0x006bc746 in IA__g_signal_emit (instance=0xb737e270, signal_id=344, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#38 0x084f0d3a in gst_element_no_more_pads () from /usr/lib/libgstreamer-0.10.so.0
#39 0x0277d049 in ?? () from /usr/lib/gstreamer-0.10/libgstdecodebin2.so
#40 0x006b143c in IA__g_cclosure_marshal_VOID__VOID (closure=0x828ef70, return_value=0x0, n_param_values=1, param_values=0xae5cb218, 
    invocation_hint=0xae2fe570, marshal_data=0xb737e270) at /build/buildd/glib2.0-2.23.6/gobject/gmarshal.c:77
#41 0x006a3252 in IA__g_closure_invoke (closure=0xae425ca0, return_value=0x0, n_param_values=1, param_values=0xae5cb218, 
    invocation_hint=0xae2fe570) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#42 0x006ba97d in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xae427028, 
    emission_return=0x0, instance_and_params=0xae5cb218) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3248
#43 0x006bbfe4 in IA__g_signal_emit_valist (instance=0xae427028, signal_id=344, detail=0, 
    var_args=0xae2fe72c "\364ox\002\364ox\002(pB\256\310\347/\256\230;w\002(pB\256") at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2981
#44 0x006bc746 in IA__g_signal_emit (instance=0xae427028, signal_id=344, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#45 0x084f0d3a in gst_element_no_more_pads () from /usr/lib/libgstreamer-0.10.so.0
#46 0x02773b98 in ?? () from /usr/lib/gstreamer-0.10/libgstdecodebin2.so
#47 0x027750bf in ?? () from /usr/lib/gstreamer-0.10/libgstdecodebin2.so
#48 0x08504fd1 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#49 0x085077a7 in gst_pad_push_event () from /usr/lib/libgstreamer-0.10.so.0
#50 0x0279f494 in ?? () from /usr/lib/gstreamer-0.10/libgstmad.so
#51 0x085070c3 in gst_pad_send_event () from /usr/lib/libgstreamer-0.10.so.0
#52 0x0850763a in gst_pad_push_event () from /usr/lib/libgstreamer-0.10.so.0
#53 0x05f45b5e in ?? () from /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
#54 0x05f471fc in ?? () from /usr/lib/gstreamer-0.10/libgstmpegaudioparse.so
#55 0x08509e05 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#56 0x0850a864 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#57 0x033d262f in ?? () from /usr/lib/libgsttag-0.10.so.0
#58 0x08509e05 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#59 0x0850a864 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#60 0x05e0d426 in ?? () from /usr/lib/gstreamer-0.10/libgstcoreelements.so
#61 0x08509e05 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#62 0x0850a864 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#63 0x084f8d7d in ?? () from /usr/lib/libgstreamer-0.10.so.0
#64 0x08509e05 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#65 0x0850a864 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#66 0x0528e45a in ?? () from /usr/lib/libgstbase-0.10.so.0
#67 0x08535d6b in ?? () from /usr/lib/libgstreamer-0.10.so.0
#68 0x08537377 in ?? () from /usr/lib/libgstreamer-0.10.so.0
#69 0x0017804c in g_thread_pool_thread_proxy (data=0xb70208b8) at /build/buildd/glib2.0-2.23.6/glib/gthreadpool.c:315
#70 0x0017612f in g_thread_create_proxy (data=0xae5cac88) at /build/buildd/glib2.0-2.23.6/glib/gthread.c:1893
#71 0x0070596e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#72 0x004079de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xc4a6f0 (LWP 3607)):
#0  0x008b607e in ?? () from /usr/lib/libfontconfig.so.1
#1  0x008b7200 in FcValueSave () from /usr/lib/libfontconfig.so.1
#2  0x008a4cfb in ?? () from /usr/lib/libfontconfig.so.1
#3  0x008a5541 in ?? () from /usr/lib/libfontconfig.so.1
#4  0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#5  0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#6  0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#7  0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#8  0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#9  0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#10 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#11 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#12 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#13 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#14 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#15 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#16 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#17 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#18 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#19 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#20 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#21 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#22 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#23 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#24 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#25 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#26 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#27 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#28 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#29 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#30 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#31 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#32 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#33 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#34 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#35 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#36 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#37 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#38 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#39 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#40 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#41 0x008a556a in ?? () from /usr/lib/libfontconfig.so.1
#42 0x008a5926 in FcConfigSubstituteWithPat () from /usr/lib/libfontconfig.so.1
#43 0x008a5e37 in FcConfigSubstitute () from /usr/lib/libfontconfig.so.1
#44 0x002b1b48 in ?? () from /usr/lib/libpangocairo-1.0.so.0
#45 0x00a39848 in ?? () from /usr/lib/libpangoft2-1.0.so.0
#46 0x00a3cb55 in ?? () from /usr/lib/libpangoft2-1.0.so.0
#47 0x0084fe16 in pango_font_map_load_fontset () from /usr/lib/libpango-1.0.so.0
#48 0x00a3ce55 in ?? () from /usr/lib/libpangoft2-1.0.so.0
#49 0x0084fedf in pango_font_map_load_font () from /usr/lib/libpango-1.0.so.0
#50 0x0084d3d3 in ?? () from /usr/lib/libpango-1.0.so.0
#51 0x0084d84e in ?? () from /usr/lib/libpango-1.0.so.0
#52 0x0084dea7 in pango_itemize_with_base_dir () from /usr/lib/libpango-1.0.so.0
#53 0x0084dfc3 in pango_itemize () from /usr/lib/libpango-1.0.so.0
#54 0x00843f82 in ?? () from /usr/lib/libpango-1.0.so.0
#55 0x0084412b in ?? () from /usr/lib/libpango-1.0.so.0
#56 0x00844820 in ?? () from /usr/lib/libpango-1.0.so.0
#57 0x00857255 in ?? () from /usr/lib/libpango-1.0.so.0
#58 0x008582b4 in ?? () from /usr/lib/libpango-1.0.so.0
#59 0x00859edb in pango_layout_get_pixel_extents () from /usr/lib/libpango-1.0.so.0
#60 0x00859f3a in pango_layout_get_pixel_size () from /usr/lib/libpango-1.0.so.0
#61 0x016a8732 in ?? ()
#62 0x016a86ed in ?? ()
#63 0x01e4bfa5 in ?? ()
#64 0x01d17e58 in ?? ()
#65 0x01e4b971 in ?? ()
#66 0x01e4a8d0 in ?? ()
#67 0x01e4a17a in ?? ()
#68 0x01e48408 in ?? ()
#69 0x01e4121a in ?? ()
#70 0x013ff3af in ?? ()
#71 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#72 0x006a18b9 in g_type_class_meta_marshal (closure=0xb76ed3b0, return_value=0xbfa55864, n_param_values=2, param_values=0x864a4f, 
    invocation_hint=0xbfa55850, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#73 0x006a3178 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa55864, n_param_values=2, param_values=0x8fb0200, 
    invocation_hint=0xbfa55850) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#74 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb7031510, 
    emission_return=0xbfa559ac, instance_and_params=0x8fb0200) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#75 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb7031510, signal_id=41, detail=0, 
    var_args=0xbfa55a10 "<Z\245\277`\302F\267XZ\245\277\252`\016\a\364\317$\a\020\025\003\267XZ\245\277\020\025\003\267\020\025\003\267`\302F\267\"\002") at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#76 0x006bc746 in IA__g_signal_emit (instance=0xb7031510, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#77 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#78 0x06f279c3 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#79 0x06f279f1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#80 0x06eefadd in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#81 0x0701f40d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#82 0x06f28554 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#83 0x06f29ca7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#84 0x07020d59 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#85 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#86 0x006a18b9 in g_type_class_meta_marshal (closure=0x6f279d0, return_value=0xbfa55da4, n_param_values=2, param_values=0xb70d0ea8, 
    invocation_hint=0xbfa55d90, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#87 0x006a3178 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa55da4, n_param_values=2, param_values=0x8fafe50, 
    invocation_hint=0xbfa55d90) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#88 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb70d0ea8, 
    emission_return=0xbfa55eec, instance_and_params=0x8fafe50) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#89 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb70d0ea8, signal_id=41, detail=0, 
    var_args=0xbfa55f50 "|_\245\277`\302F\267\230_\245\277\252`\016\a\364\317$\a\250\016\r\267\230_\245\277\250\016\r\267\250\016\r\267`\302F\267\062\002") at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#90 0x006bc746 in IA__g_signal_emit (instance=0xb70d0ea8, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#91 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#92 0x06f279c3 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#93 0x06f279f1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#94 0x06fe208d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#95 0x06f28554 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#96 0x06f29ca7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#97 0x06fe4e0c in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#98 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#99 0x006a18b9 in g_type_class_meta_marshal (closure=0xb749f5e8, return_value=0xbfa56284, n_param_values=2, param_values=0x6f279d0, 
    invocation_hint=0xbfa56270, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#100 0x006a3178 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa56284, n_param_values=2, param_values=0x8fb0000, 
    invocation_hint=0xbfa56270) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#101 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb749f5e8, 
    emission_return=0xbfa563cc, instance_and_params=0x8fb0000) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#102 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb749f5e8, signal_id=41, detail=0, 
    var_args=0xbfa56430 "\\d\245\277`\302F\267xd\245\277\252`\016\a\364\317$\a\350\365I\267xd\245\277\350\365I\267\350\365I\267`\302F\267K\003") at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#103 0x006bc746 in IA__g_signal_emit (instance=0xb749f5e8, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#104 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#105 0x06f279c3 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#106 0x06f279f1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#107 0x06ef3c75 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#108 0x06f28554 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#109 0x06f29ca7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#110 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#111 0x006a18b9 in g_type_class_meta_marshal (closure=0xbfa56568, return_value=0xbfa56724, n_param_values=2, param_values=0x6f279d0, 
    invocation_hint=0xbfa56710, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#112 0x006a3178 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa56724, n_param_values=2, param_values=0x8fb0078, 
    invocation_hint=0xbfa56710) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#113 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb73f8718, 
    emission_return=0xbfa5686c, instance_and_params=0x8fb0078) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#114 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb73f8718, signal_id=41, detail=0, 
    var_args=0xbfa568d0 "\374h\245\277`\302F\267\030i\245\277\252`\016\a\364\317$\a\030\207?\267\030i\245\277\030\207?\267\030\207?\267`\302F\267K\003") at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#115 0x006bc746 in IA__g_signal_emit (instance=0xb73f8718, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#116 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#117 0x06f279c3 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#118 0x06f279f1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#119 0x06ef3c75 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#120 0x06f28554 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#121 0x06f29ca7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#122 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#123 0x006a18b9 in g_type_class_meta_marshal (closure=0xbfa56a08, return_value=0xbfa56bc4, n_param_values=2, param_values=0x6f279d0, 
    invocation_hint=0xbfa56bb0, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#124 0x006a3178 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa56bc4, n_param_values=2, param_values=0x8fafc78, 
    invocation_hint=0xbfa56bb0) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#125 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb72a0dd0, 
    emission_return=0xbfa56d0c, instance_and_params=0x8fafc78) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#126 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb72a0dd0, signal_id=41, detail=0, 
    var_args=0xbfa56d70 "\234m\245\277`\302F\267\270m\245\277\252`\016\a\364\317$\a\320\r*\267\270m\245\277\320\r*\267\320\r*\267`\302F\267K\003") at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#127 0x006bc746 in IA__g_signal_emit (instance=0xb72a0dd0, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#128 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#129 0x06f279c3 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#130 0x06f279f1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#131 0x06fe208d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#132 0x06f28554 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#133 0x06f29ca7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#134 0x06fe4e0c in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#135 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#136 0x006a18b9 in g_type_class_meta_marshal (closure=0xb749f048, return_value=0xbfa570a4, n_param_values=2, param_values=0x6f279d0, 
    invocation_hint=0xbfa57090, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#137 0x006a3178 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa570a4, n_param_values=2, param_values=0x8fb0028, 
    invocation_hint=0xbfa57090) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#138 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb749f048, 
    emission_return=0xbfa571ec, instance_and_params=0x8fb0028) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#139 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb749f048, signal_id=41, detail=0, 
    var_args=0xbfa57250 "|r\245\277`\302F\267\230r\245\277\252`\016\a\364\317$\aH\360I\267\230r\245\277H\360I\267H\360I\267`\302F\267")
    at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#140 0x006bc746 in IA__g_signal_emit (instance=0xb749f048, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#141 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#142 0x06f279c3 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#143 0x06f279f1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#144 0x06ef3c75 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#145 0x06f28554 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#146 0x06f29ca7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#147 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#148 0x006a18b9 in g_type_class_meta_marshal (closure=0xbfa57388, return_value=0xbfa57544, n_param_values=2, param_values=0x6f279d0, 
    invocation_hint=0xbfa57530, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#149 0x006a3178 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa57544, n_param_values=2, param_values=0x8fafe28, 
    invocation_hint=0xbfa57530) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#150 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb72a0970, 
    emission_return=0xbfa5768c, instance_and_params=0x8fafe28) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#151 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb72a0970, signal_id=41, detail=0, 
    var_args=0xbfa576f0 "\034w\245\277`\302F\267\070w\245\277\252`\016\a\364\317$\ap\t*\267\070w\245\277p\t*\267p\t*\267`\302F\267")
    at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#152 0x006bc746 in IA__g_signal_emit (instance=0xb72a0970, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#153 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#154 0x06f279c3 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#155 0x06f279f1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#156 0x06eefadd in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#157 0x06f28554 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#158 0x06f29ca7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#159 0x070fe8a7 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#160 0x06fb92f4 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#161 0x006a18b9 in g_type_class_meta_marshal (closure=0xb72e4358, return_value=0xbfa57a14, n_param_values=2, param_values=0xb72ed040, 
    invocation_hint=0xbfa57a00, marshal_data=0xc8) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:878
#162 0x006a3252 in IA__g_closure_invoke (closure=0xb74672e0, return_value=0xbfa57a14, n_param_values=2, param_values=0x8fafdb8, 
    invocation_hint=0xbfa57a00) at /build/buildd/glib2.0-2.23.6/gobject/gclosure.c:767
#163 0x006ba5c6 in signal_emit_unlocked_R (node=<value optimized out>, detail=<value optimized out>, instance=0xb72ed040, 
    emission_return=0xbfa57b5c, instance_and_params=0x8fafdb8) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3286
#164 0x006bbe63 in IA__g_signal_emit_valist (instance=0xb72ed040, signal_id=41, detail=0, 
    var_args=0xbfa57bc0 "\354{\245\277`\302F\267@\373\372\b\252`\016\a\364\317$\a@\320.\267\b|\245\277@\320.\267@\320.\267`\302F\267(\002")
    at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:2991
#165 0x006bc746 in IA__g_signal_emit (instance=0xb72ed040, signal_id=41, detail=0) at /build/buildd/glib2.0-2.23.6/gobject/gsignal.c:3038
#166 0x070e6306 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#167 0x06fb2feb in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#168 0x00ab882b in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#169 0x00ae1984 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#170 0x00ab4f83 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#171 0x00ab6f9f in gdk_window_process_all_updates () from /usr/lib/libgdk-x11-2.0.so.0
#172 0x06f286df in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#173 0x00a93318 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#174 0x001496c1 in g_idle_dispatch (source=0xb74d01c0, callback=0x37a21, user_data=0xae6c7c00)
    at /build/buildd/glib2.0-2.23.6/glib/gmain.c:4065
#175 0x0014b645 in g_main_dispatch (context=0xb74652a0) at /build/buildd/glib2.0-2.23.6/glib/gmain.c:1960
#176 IA__g_main_context_dispatch (context=0xb74652a0) at /build/buildd/glib2.0-2.23.6/glib/gmain.c:2513
#177 0x0014f338 in g_main_context_iterate (context=0xb74652a0, block=<value optimized out>, dispatch=1, self=0x8998d40)
    at /build/buildd/glib2.0-2.23.6/glib/gmain.c:2591
#178 0x0014f877 in IA__g_main_loop_run (loop=0xb7427308) at /build/buildd/glib2.0-2.23.6/glib/gmain.c:2799
#179 0x06fb3299 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#180 0x01e3e520 in ?? ()
#181 0x01e3e4e3 in ?? ()
#182 0x01e3e275 in ?? ()
#183 0x00bfb0fd in ?? ()
#184 0x00bfafa2 in ?? ()
#185 0x00bfaed6 in ?? ()
#186 0x00bf4041 in ?? ()
#187 0x00bf11be in ?? ()
#188 0x00bf112c in ?? ()
#189 0x08112b6e in mono_runtime_exec_main ()
#190 0x00bf10ab in ?? ()
#191 0x00bf0f94 in ?? ()
#192 0x00bf0e6e in ?? ()
#193 0x00bf0e18 in ?? ()
#194 0x00bf0d9a in ?? ()
#195 0x00bf0d4b in ?? ()
#196 0x00bf02aa in ?? ()
#197 0x005b53f7 in ?? ()
#198 0x005b51fb in ?? ()
#199 0x08112b6e in mono_runtime_exec_main ()
#200 0x081132ea in mono_runtime_run_main ()
#201 0x080b28cd in mono_main ()
#202 0x0805ac85 in ?? ()
#203 0x00350bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#204 0x0805abc1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

```

This is 10.04 beta, but it happened with 9.10 also.

---

### Post by hatapota on 2010-03-26
I'm using Banshee too and yesterday it kept crashing while opening. It eventually "opened" but it just showed a white screen. I'm not sure how to find out what's wrong with it - how do you get an output showing what's going on?
 
I'm getting a bit sick of Banshee now :(

---

### Post by Dportner on 2010-03-28
same thing is happening to me.
i open banshee, press play, music plays for 1 second then it crashes

i dont get any error message tho

anybody know why this is happening?


EDIT:  well i found out the reason for me. i uncheckd the clutter flow extension and it seemd to fix things up :/

---

