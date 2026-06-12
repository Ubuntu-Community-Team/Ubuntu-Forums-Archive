---
title: "Banshee Crashing in Jaunty - Stack Overflow"
date: 2009-09-01
forum: Multimedia Software
---

### Post by Mad-Halfling on 2009-09-01
I recently upgraded to 9.04, also getting mono updates and now banshee crashes when I go to play a song.  It will load and play the first couple of notes, but then it bombs out.  I didn't try it between the 9.04 upgrade and the mono update, as as it uses mono I was wondering if that might be the problem.  I have tried uninstalling it and then reinstalling it, removing all the directories with banshee in the name in between, and also doing the same adding in "http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main" to my software sources, but it still doesn't work.  I've also tried reinstalling all the installed mono(2) packages in synaptic (due to the "possible corruption" error listed).

Is this a known issue?

the output after the error occurs is

```
Stack overflow: IP: 0xb7de5a95, fault addr: 0xaa5fedf4
At Unmanaged
Stacktrace:


Native stacktrace:

	mono [0x806d944]
	[0xb7fa4410]
	/lib/tls/i686/cmov/libc.so.6(abort+0x188) [0xb7d4b098]
	mono [0x818685e]
	[0xb7fa4410]

Debug info from gdb:

(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7cea6e0 (LWP 6163)]
[New Thread 0xaa6ffb90 (LWP 6245)]
[New Thread 0xaabfdb90 (LWP 6244)]
[New Thread 0xabbffb90 (LWP 6241)]
[New Thread 0xac522b90 (LWP 6240)]
[New Thread 0xacd23b90 (LWP 6239)]
[New Thread 0xad524b90 (LWP 6238)]
[New Thread 0xb5da6b90 (LWP 6237)]
[New Thread 0xb26afb90 (LWP 6201)]
[New Thread 0xb27ffb90 (LWP 6200)]
[New Thread 0xb296ab90 (LWP 6198)]
[New Thread 0xb2f36b90 (LWP 6195)]
[New Thread 0xb303bb90 (LWP 6194)]
[New Thread 0xb3150b90 (LWP 6193)]
[New Thread 0xb5effb90 (LWP 6190)]
[New Thread 0xb752bb90 (LWP 6166)]
[New Thread 0xb7ed2b90 (LWP 6165)]
0xb7fa4430 in __kernel_vsyscall ()
  17 Thread 0xb7ed2b90 (LWP 6165)  0xb7fa4430 in __kernel_vsyscall ()
  16 Thread 0xb752bb90 (LWP 6166)  0xb7fa4430 in __kernel_vsyscall ()
  15 Thread 0xb5effb90 (LWP 6190)  0xb7fa4430 in __kernel_vsyscall ()
  14 Thread 0xb3150b90 (LWP 6193)  0xb7fa4430 in __kernel_vsyscall ()
  13 Thread 0xb303bb90 (LWP 6194)  0xb7fa4430 in __kernel_vsyscall ()
  12 Thread 0xb2f36b90 (LWP 6195)  0xb7fa4430 in __kernel_vsyscall ()
  11 Thread 0xb296ab90 (LWP 6198)  0xb7fa4430 in __kernel_vsyscall ()
  10 Thread 0xb27ffb90 (LWP 6200)  0xb7fa4430 in __kernel_vsyscall ()
  9 Thread 0xb26afb90 (LWP 6201)  0xb7fa4430 in __kernel_vsyscall ()
  8 Thread 0xb5da6b90 (LWP 6237)  0xb7fa4430 in __kernel_vsyscall ()
  7 Thread 0xad524b90 (LWP 6238)  0xb7fa4430 in __kernel_vsyscall ()
  6 Thread 0xacd23b90 (LWP 6239)  0xb7fa4430 in __kernel_vsyscall ()
  5 Thread 0xac522b90 (LWP 6240)  0xb7fa4430 in __kernel_vsyscall ()
  4 Thread 0xabbffb90 (LWP 6241)  0xb7fa4430 in __kernel_vsyscall ()
  3 Thread 0xaabfdb90 (LWP 6244)  0xb7fa4430 in __kernel_vsyscall ()
  2 Thread 0xaa6ffb90 (LWP 6245)  0xb7fa4430 in __kernel_vsyscall ()
  1 Thread 0xb7cea6e0 (LWP 6163)  0xb7fa4430 in __kernel_vsyscall ()

Thread 17 (Thread 0xb7ed2b90 (LWP 6165)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb48f6 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081492e8 in ?? ()
#3  0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 16 (Thread 0xb752bb90 (LWP 6166)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb10e5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c607 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x0814f25c in ?? ()
#5  0x08169b02 in ?? ()
#6  0x080d565a in ?? ()
#7  0x080f7639 in ?? ()
#8  0x081653b6 in ?? ()
#9  0x08183355 in ?? ()
#10 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 15 (Thread 0xb5effb90 (LWP 6190)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb1412 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5b8 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x0814f25c in ?? ()
#5  0x08169b02 in ?? ()
#6  0x080f45e3 in ?? ()
#7  0xb632b79a in ?? ()
#8  0xb632b5db in ?? ()
#9  0xb6329a50 in ?? ()
#10 0xb7926859 in ?? ()
#11 0x080b8974 in mono_runtime_delegate_invoke ()
#12 0x080f76bf in ?? ()
#13 0x081653b6 in ?? ()
#14 0x08183355 in ?? ()
#15 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 14 (Thread 0xb3150b90 (LWP 6193)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb1412 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5b8 in ?? ()
#3  0x0814c682 in ?? ()
#4  0x0816a055 in ?? ()
#5  0x080f6159 in ?? ()
#6  0xb379ee9f in ?? ()
#7  0xb379ec7e in ?? ()
#8  0xb379ea8f in ?? ()
#9  0xb379e97e in ?? ()
#10 0x080bd00a in mono_runtime_invoke_array ()
#11 0x080bd214 in ?? ()
#12 0x080fa933 in ?? ()
#13 0x080fad50 in ?? ()
#14 0x080f7639 in ?? ()
#15 0x081653b6 in ?? ()
#16 0x08183355 in ?? ()
#17 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 13 (Thread 0xb303bb90 (LWP 6194)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb1412 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5b8 in ?? ()
#3  0x0814c682 in ?? ()
#4  0x0816a055 in ?? ()
#5  0x080f6159 in ?? ()
#6  0xb379ee9f in ?? ()
#7  0xb379ec7e in ?? ()
#8  0xb379ea8f in ?? ()
#9  0xb379e97e in ?? ()
#10 0x080bd00a in mono_runtime_invoke_array ()
#11 0x080bd214 in ?? ()
#12 0x080fa933 in ?? ()
#13 0x080fad50 in ?? ()
#14 0x080f7639 in ?? ()
#15 0x081653b6 in ?? ()
#16 0x08183355 in ?? ()
#17 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0xb2f36b90 (LWP 6195)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb1412 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5b8 in ?? ()
#3  0x0814c682 in ?? ()
#4  0x0816a055 in ?? ()
#5  0x080f6159 in ?? ()
#6  0xb379ee9f in ?? ()
#7  0xb379ec7e in ?? ()
#8  0xb379ea8f in ?? ()
#9  0xb379e97e in ?? ()
#10 0x080bd00a in mono_runtime_invoke_array ()
#11 0x080bd214 in ?? ()
#12 0x080fa933 in ?? ()
#13 0x080fad50 in ?? ()
#14 0x080f7639 in ?? ()
#15 0x081653b6 in ?? ()
#16 0x08183355 in ?? ()
#17 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0xb296ab90 (LWP 6198)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7df7ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f2e74b in IA__g_poll (fds=0x8e1fbe8, nfds=5, timeout=-1)
    at /build/buildd/glib2.0-2.20.1/glib/gpoll.c:127
#3  0xb7f20f82 in g_main_context_iterate (context=0x8e21370, block=1, 
    dispatch=1, self=0x8e22d70)
    at /build/buildd/glib2.0-2.20.1/glib/gmain.c:2761
#4  0xb7f215ba in IA__g_main_loop_run (loop=0x8e1f940)
    at /build/buildd/glib2.0-2.20.1/glib/gmain.c:2656
#5  0xb55388c0 in ?? () from /usr/lib/libORBit-2.so.0
#6  0xb7f487bf in g_thread_create_proxy (data=0x8e22d70)
    at /build/buildd/glib2.0-2.20.1/glib/gthread.c:635
#7  0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xb27ffb90 (LWP 6200)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7df7ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb29819d9 in ?? ()
#3  0xb2981985 in ?? ()
#4  0xb714d650 in ?? ()
#5  0xb26f9a5d in avahi_simple_poll_run () from /usr/lib/libavahi-common.so.3
#6  0xb26fa330 in avahi_simple_poll_iterate ()
   from /usr/lib/libavahi-common.so.3
#7  0xb26fa380 in avahi_simple_poll_loop () from /usr/lib/libavahi-common.so.3
#8  0xb2981943 in ?? ()
#9  0xb298187a in ?? ()
#10 0xb7926859 in ?? ()
#11 0x080b8974 in mono_runtime_delegate_invoke ()
#12 0x080f76bf in ?? ()
#13 0x081653b6 in ?? ()
#14 0x08183355 in ?? ()
#15 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xb26afb90 (LWP 6201)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb4318 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08162529 in ?? ()
#3  0x080ff74b in ?? ()
#4  0xb26b7cea in ?? ()
#5  0xb26b7b0e in ?? ()
#6  0xb26b79fe in ?? ()
#7  0xb7926859 in ?? ()
#8  0x080b8974 in mono_runtime_delegate_invoke ()
#9  0x080f76bf in ?? ()
#10 0x081653b6 in ?? ()
#11 0x08183355 in ?? ()
#12 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb5da6b90 (LWP 6237)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb10e5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3234754 in gst_queue_chain (pad=0xb2884598, buffer=0x8d62a30)
    at gstqueue.c:934
#3  0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb2884598, buffer=0x8d62a30)
    at gstpad.c:3890
#4  0xb4e9aeba in gst_pad_push (pad=0xb28844d8, buffer=0x8d62a30)
    at gstpad.c:4057
#5  0xb31d6618 in gst_selector_pad_chain (pad=0xb28a6558, buf=0x8d62a30)
    at gststreamselector.c:424
#6  0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb28a6558, buffer=0x8d62a30)
    at gstpad.c:3890
#7  0xb4e9aeba in gst_pad_push (pad=0xb4f29e20, buffer=0x8d62a30)
    at gstpad.c:4057
#8  0xb4e8a31d in gst_proxy_pad_do_chain (pad=0xb389d5b8, buffer=0x8d62a30)
    at gstghostpad.c:191
#9  0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb389d5b8, buffer=0x8d62a30)
    at gstpad.c:3890
#10 0xb4e9aeba in gst_pad_push (pad=0xb2884418, buffer=0x8d62a30)
    at gstpad.c:4057
#11 0xb17dc576 in gst_mad_chain (pad=0xb2884358, buffer=0x8da0800)
    at gstmad.c:1671
#12 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb2884358, buffer=0x8da0800)
    at gstpad.c:3890
#13 0xb4e9aeba in gst_pad_push (pad=0xb2884298, buffer=0x8da0800)
    at gstpad.c:4057
#14 0xb39050e1 in gst_mp3parse_emit_frame (mp3parse=0xb28a8980, size=418, 
    mode=1, crc=1) at gstmpegaudioparse.c:832
#15 0xb3906b98 in gst_mp3parse_chain (pad=0xb28841d8, buf=0xb28be730)
    at gstmpegaudioparse.c:1344
#16 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb28841d8, buffer=0xb28be730)
    at gstpad.c:3890
#17 0xb4e9aeba in gst_pad_push (pad=0xb2884118, buffer=0xb28be730)
    at gstpad.c:4057
#18 0xb50604a0 in gst_tag_demux_chain (pad=0xb2884058, buf=0xb28be730)
    at gsttagdemux.c:694
#19 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb2884058, buffer=0xb28be730)
    at gstpad.c:3890
#20 0xb4e9aeba in gst_pad_push (pad=0xb38be630, buffer=0xb28be730)
    at gstpad.c:4057
#21 0xb323887a in gst_type_find_element_chain (pad=0xb38be570, 
    buffer=0xb28be730) at gsttypefindelement.c:623
#22 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb38be570, buffer=0xb28be730)
    at gstpad.c:3890
#23 0xb4e9aeba in gst_pad_push (pad=0xb389d278, buffer=0xb28be730)
    at gstpad.c:4057
#24 0xb4e8a31d in gst_proxy_pad_do_chain (pad=0xb4f29d40, buffer=0xb28be730)
    at gstghostpad.c:191
#25 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb4f29d40, buffer=0xb28be730)
    at gstpad.c:3890
#26 0xb4e9aeba in gst_pad_push (pad=0xb38be4b0, buffer=0xb28be730)
    at gstpad.c:4057
#27 0xb524ac81 in gst_base_src_loop (pad=0xb38be4b0) at gstbasesrc.c:2275
#28 0xb4ebc593 in gst_task_func (task=0xb2a17560, tclass=0xb626c648)
    at gsttask.c:192
#29 0xb7f49e26 in g_thread_pool_thread_proxy (data=0xb626c6d8)
    at /build/buildd/glib2.0-2.20.1/glib/gthreadpool.c:265
#30 0xb7f487bf in g_thread_create_proxy (data=0xb28a8fc8)
    at /build/buildd/glib2.0-2.20.1/glib/gthread.c:635
#31 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#32 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xad524b90 (LWP 6238)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7df7ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb1762912 in ?? () from /usr/lib/libpulse.so.0
#3  0xb17523c0 in pa_mainloop_poll () from /usr/lib/libpulse.so.0
#4  0xb1753d43 in pa_mainloop_iterate () from /usr/lib/libpulse.so.0
#5  0xb1753e14 in pa_mainloop_run () from /usr/lib/libpulse.so.0
#6  0xb17626c3 in ?? () from /usr/lib/libpulse.so.0
#7  0xb178cef2 in ?? () from /usr/lib/libpulse.so.0
#8  0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#9  0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xacd23b90 (LWP 6239)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb10e5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3775db6 in wait_segment (buf=0xb28ca1f0) at gstringbuffer.c:1406
#3  0xb37763a9 in gst_ring_buffer_commit_full (buf=0xb28ca1f0, 
    sample=0xacd227f8, 
    data=0x8e7ce10 "\214\177g&#65533;\r&#65533;[\001L&#65533;o&#65533;-&#65533;\\\001\230&#65533;\202&#65533;y'g\0018&#65533;\216&#65533;\215_i\001&#65533;)\223&#65533;m\032d\001&#65533;C\235&#65533;\006&#65533;d\001rD&#65533;&#65533;&#1655;l\001\205A&#65533;&#65533;3\207o\001&#65533;&#65533;&#65533;&#65533;fzl\001&#65533;\027&#65533;&#65533;&#65533;&#65533;p\001\222&#65533;&#65533;&#65533;3&#65533;~\001\037&#65533;&#65533;&#65533;&#65533;F\212\001\214>\016&#65533;\223&#65533;\223\001\037&#65533;)&#65533;&#65533;\006&#65533;\001\237\216G&#65533; :&#65533;\001\037<U&#65533;&#65533;&#65533;&#65533;\001r0[&#65533;\223&#65533;&#65533;\001&#65533;&#65533;s&#65533;3\030&#65533;\001\206\230\225&#65533;S-&#65533;\001&#65533;&#65533;\223&#65533;M\211&#65533;\001&#65533;$h&#65533;&#65533;&#65533;&#65533;\001&#65533;&#65533;H&#65533;&#428;\210\001&#65533;|]&#65533;&#65533;\023\232\001&#65533;&#65533;\213&#65533;", 
    in_samples=694, out_samples=1152, accum=0xacd22814) at gstringbuffer.c:1644
#4  0xb376ac2b in gst_base_audio_sink_render (bsink=0xb28da040, buf=0xb28be780)
    at gstbaseaudiosink.c:1481
#5  0xb523ea20 in gst_base_sink_render_object (basesink=0xb28da040, 
    pad=0xb28c5be0, obj=0xb28be780) at gstbasesink.c:2359
#6  0xb523faa8 in gst_base_sink_queue_object_unlocked (basesink=0xb28da040, 
    pad=0xb28c5be0, obj=0xb28be780, prerollable=1) at gstbasesink.c:2566
#7  0xb524020d in gst_base_sink_chain_unlocked (basesink=0xb28da040, 
    pad=0xb28c5be0, buf=0xb28be780) at gstbasesink.c:2923
#8  0xb5240725 in gst_base_sink_chain (pad=0xb28c5be0, buf=0xb28be780)
    at gstbasesink.c:2964
#9  0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb28c5be0, buffer=0xb28be780)
    at gstpad.c:3890
#10 0xb4e9aeba in gst_pad_push (pad=0xb28c9040, buffer=0xb28be780)
    at gstpad.c:4057
#11 0xb4e8a31d in gst_proxy_pad_do_chain (pad=0xb28c8800, buffer=0xb28be780)
    at gstghostpad.c:191
#12 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb28c8800, buffer=0xb28be780)
    at gstpad.c:3890
#13 0xb4e9aeba in gst_pad_push (pad=0xb389d008, buffer=0xb28be780)
    at gstpad.c:4057
#14 0xb4e8a31d in gst_proxy_pad_do_chain (pad=0xb4f299c0, buffer=0xb28be780)
    at gstghostpad.c:191
#15 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb4f299c0, buffer=0xb28be780)
    at gstpad.c:3890
#16 0xb4e9aeba in gst_pad_push (pad=0xb38be030, buffer=0xb28be780)
    at gstpad.c:4057
#17 0xb5253caf in gst_base_transform_chain (pad=0xb38484c0, buffer=0xb28be9a8)
    at gstbasetransform.c:2030
#18 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb38484c0, buffer=0xb28be9a8)
    at gstpad.c:3890
#19 0xb4e9aeba in gst_pad_push (pad=0xb3848340, buffer=0xb28be9a8)
    at gstpad.c:4057
#20 0xb5253caf in gst_base_transform_chain (pad=0xb3848280, buffer=0xb28be9a8)
    at gstbasetransform.c:2030
#21 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb3848280, buffer=0xb28be9a8)
    at gstpad.c:3890
#22 0xb4e9aeba in gst_pad_push (pad=0xb38be1b0, buffer=0xb28be9a8)
    at gstpad.c:4057
#23 0xb5253caf in gst_base_transform_chain (pad=0xb38be0f0, buffer=0xb28be9a8)
    at gstbasetransform.c:2030
#24 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb38be0f0, buffer=0xb28be9a8)
    at gstpad.c:3890
#25 0xb4e9aeba in gst_pad_push (pad=0xb3848640, buffer=0xb28be9a8)
    at gstpad.c:4057
#26 0xb5253caf in gst_base_transform_chain (pad=0xb3848400, buffer=0xb165cb78)
    at gstbasetransform.c:2030
#27 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb3848400, buffer=0xb165cb78)
    at gstpad.c:3890
#28 0xb4e9aeba in gst_pad_push (pad=0xb38481c0, buffer=0xb165cb78)
    at gstpad.c:4057
#29 0xb32321a2 in gst_queue_loop (pad=0xb38481c0) at gstqueue.c:1047
#30 0xb4ebc593 in gst_task_func (task=0xb28be460, tclass=0xb626c648)
    at gsttask.c:192
#31 0xb7f49e26 in g_thread_pool_thread_proxy (data=0xb626c6d8)
    at /build/buildd/glib2.0-2.20.1/glib/gthreadpool.c:265
#32 0xb7f487bf in g_thread_create_proxy (data=0xb28e5948)
    at /build/buildd/glib2.0-2.20.1/glib/gthread.c:635
#33 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#34 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xac522b90 (LWP 6240)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb10e5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb3234754 in gst_queue_chain (pad=0xb3848100, buffer=0xb165d380)
    at gstqueue.c:934
#3  0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb3848100, buffer=0xb165d380)
    at gstpad.c:3890
#4  0xb4e9aeba in gst_pad_push (pad=0xb38be270, buffer=0xb165d380)
    at gstpad.c:4057
#5  0xb3235964 in gst_tee_handle_buffer (tee=0xb38f5000, buffer=0xb165d380)
    at gsttee.c:522
#6  0xb3235c75 in gst_tee_chain (pad=0xb3848580, buffer=0xb165d380)
    at gsttee.c:646
#7  0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb3848580, buffer=0xb165d380)
    at gstpad.c:3890
#8  0xb4e9aeba in gst_pad_push (pad=0xb389d0d8, buffer=0xb165d380)
    at gstpad.c:4057
#9  0xb4e8a31d in gst_proxy_pad_do_chain (pad=0xb4f29aa0, buffer=0xb165d380)
    at gstghostpad.c:191
#10 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb4f29aa0, buffer=0xb165d380)
    at gstpad.c:3890
#11 0xb4e9aeba in gst_pad_push (pad=0xb28c5b20, buffer=0xb165d380)
    at gstpad.c:4057
#12 0xb5253caf in gst_base_transform_chain (pad=0xb28c5a60, buffer=0xb165d380)
    at gstbasetransform.c:2030
#13 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb28c5a60, buffer=0xb165d380)
    at gstpad.c:3890
#14 0xb4e9aeba in gst_pad_push (pad=0xb28c59a0, buffer=0xb165d380)
    at gstpad.c:4057
#15 0xb5253caf in gst_base_transform_chain (pad=0xb28c58e0, buffer=0xb165d380)
    at gstbasetransform.c:2030
#16 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb28c58e0, buffer=0xb165d380)
    at gstpad.c:3890
#17 0xb4e9aeba in gst_pad_push (pad=0xb28c5820, buffer=0xb165d380)
    at gstpad.c:4057
#18 0xb5253caf in gst_base_transform_chain (pad=0xb2884718, buffer=0xb165d380)
    at gstbasetransform.c:2030
#19 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb2884718, buffer=0xb165d380)
    at gstpad.c:3890
#20 0xb4e9aeba in gst_pad_push (pad=0xb389d688, buffer=0xb165d380)
    at gstpad.c:4057
#21 0xb4e8a31d in gst_proxy_pad_do_chain (pad=0xb4f29f00, buffer=0xb165d380)
    at gstghostpad.c:191
#22 0xb4e99ac5 in gst_pad_chain_unchecked (pad=0xb4f29f00, buffer=0xb165d380)
    at gstpad.c:3890
#23 0xb4e9aeba in gst_pad_push (pad=0xb2884658, buffer=0xb165d380)
    at gstpad.c:4057
#24 0xb32321a2 in gst_queue_loop (pad=0xb2884658) at gstqueue.c:1047
#25 0xb4ebc593 in gst_task_func (task=0xb28be4b0, tclass=0xb626c648)
    at gsttask.c:192
#26 0xb7f49e26 in g_thread_pool_thread_proxy (data=0xb626c6d8)
    at /build/buildd/glib2.0-2.20.1/glib/gthreadpool.c:265
#27 0xb7f487bf in g_thread_create_proxy (data=0xb1658688)
    at /build/buildd/glib2.0-2.20.1/glib/gthread.c:635
#28 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#29 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xabbffb90 (LWP 6241)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7df7ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb1582f4d in ?? () from /usr/lib/libasound.so.2
#3  0xb15830c4 in snd_pcm_wait () from /usr/lib/libasound.so.2
#4  0xb17ae1f9 in gst_alsasink_write (asink=0xb28da040, data=0x8e5ea20, 
    length=3528) at gstalsasink.c:882
#5  0xb376710c in audioringbuffer_thread_func (buf=0xb28ca1f0)
    at gstaudiosink.c:236
#6  0xb7f487bf in g_thread_create_proxy (data=0x8d6b300)
    at /build/buildd/glib2.0-2.20.1/glib/gthread.c:635
#7  0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xaabfdb90 (LWP 6244)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb1412 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5b8 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x081699dc in ?? ()
#5  0x080f45e3 in ?? ()
#6  0xb632b79a in ?? ()
#7  0xb1714e0c in ?? ()
#8  0xb1714cc5 in ?? ()
#9  0xb1714b4a in ?? ()
#10 0xb17112d8 in ?? ()
#11 0xb170b1d5 in ?? ()
#12 0xb170ad43 in ?? ()
#13 0xb1709644 in ?? ()
#14 0xb1709383 in ?? ()
#15 0xb1709333 in ?? ()
#16 0xb1709290 in ?? ()
#17 0xb1709268 in ?? ()
#18 0xb170903b in ?? ()
#19 0xb26bfeff in ?? ()
#20 0xb297a574 in ?? ()
#21 0xb297a287 in ?? ()
#22 0xb7926859 in ?? ()
#23 0x080b8974 in mono_runtime_delegate_invoke ()
#24 0x080f76bf in ?? ()
#25 0x081653b6 in ?? ()
#26 0x08183355 in ?? ()
#27 0xb7ead4ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#28 0xb7e0249e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xaa6ffb90 (LWP 6245)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7eb40fb in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0806da5e in ?? ()
#3  <signal handler called>
#4  0xb7fa4430 in __kernel_vsyscall ()
#5  0xb7d496d0 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7d4b098 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0x0818685e in ?? ()
#8  <signal handler called>
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 1 (Thread 0xb7cea6e0 (LWP 6163)):
#0  0xb7fa4430 in __kernel_vsyscall ()
#1  0xb7df7ae7 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f2e74b in IA__g_poll (fds=0xb2abad68, nfds=6, timeout=12)
    at /build/buildd/glib2.0-2.20.1/glib/gpoll.c:127
#3  0xb7f20f82 in g_main_context_iterate (context=0xb6288880, block=1, 
    dispatch=1, self=0x8bb8d40)
    at /build/buildd/glib2.0-2.20.1/glib/gmain.c:2761
#4  0xb7f215ba in IA__g_main_loop_run (loop=0xb2ab8138)
    at /build/buildd/glib2.0-2.20.1/glib/gmain.c:2656
#5  0xb6aac7d9 in IA__gtk_main ()
    at /build/buildd/gtk+2.0-2.16.1/gtk/gtkmain.c:1205
#6  0xb2d0616e in ?? ()
#7  0xb2d06138 in ?? ()
#8  0xb2d05f16 in ?? ()
#9  0xb71491b2 in ?? ()
#10 0xb714909b in ?? ()
#11 0xb7148fb9 in ?? ()
#12 0xb7141412 in ?? ()
#13 0xb713d5c3 in ?? ()
#14 0xb713d553 in ?? ()
#15 0x080bad75 in mono_runtime_exec_main ()
#16 0xb713d4fd in ?? ()
#17 0xb713d421 in ?? ()
#18 0xb713d31a in ?? ()
#19 0xb713d2c6 in ?? ()
#20 0xb713d23d in ?? ()
#21 0xb713d1fa in ?? ()
#22 0xb713c33e in ?? ()
#23 0xb79243a9 in ?? ()
#24 0xb79241ae in ?? ()
#25 0x080bad75 in mono_runtime_exec_main ()
#26 0x080bb4eb in mono_runtime_run_main ()
#27 0x0805c917 in mono_main ()
#28 0x0805ac62 in ?? ()
#29 0xb7d34775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#30 0x0805aba1 in ?? ()
#0  0xb7fa4430 in __kernel_vsyscall ()

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
```

---

