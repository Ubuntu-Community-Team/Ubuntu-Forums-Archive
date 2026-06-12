---
title: "Banshee crashes during mp3 player sync."
date: 2009-11-08
forum: Multimedia Software
---

### Post by abrianb on 2009-11-08
After upgrading to Ubuntu 9.10 I lost the ability to sync my sanza 280. It crashes with a sigsegv error.
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.

The full debug is...

Native stacktrace:

    banshee-1 [0x80c8824]
    banshee-1 [0x80f4693]
    [0xd96410]
    /lib/tls/i686/cmov/libc.so.6(strlen+0x33) [0x184f43]
    /usr/lib/libmtp.so.8 [0x4b5bcf5]
    /usr/lib/libmtp.so.8(LIBMTP_Create_New_Album+0x7f) [0x4b5c8af]
    [0x310c05d]
    [0x310be54]
    [0x310bd42]
    [0x310bafa]
    [0x310bac4]
    [0x310b0d4]
    [0x310a781]
    [0x389484d]
    [0x3894482]
    [0x38941ef]
    [0x388c05f]
    [0x388bac9]
    [0x25c8b88]
    [0x25c8b2a]
    [0x388b989]
    [0x30d8c0b]
    [0x2f1086]
    banshee-1(mono_runtime_invoke_array+0x2fb) [0x8114f4b]
    banshee-1 [0x811512e]
    banshee-1 [0x81520a3]
    banshee-1 [0x8152577]
    banshee-1 [0x814f96c]
    banshee-1 [0x81bf9f2]
    banshee-1 [0x81de055]
    /lib/tls/i686/cmov/libpthread.so.0 [0x66480e]
    /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x1de7ee]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x3e7bb70 (LWP 3877)]
[New Thread 0x28d2b70 (LWP 3870)]
[New Thread 0x3873b70 (LWP 3869)]
[New Thread 0x2b20b70 (LWP 3867)]
[New Thread 0x3617b70 (LWP 3865)]
[New Thread 0x3516b70 (LWP 3864)]
[New Thread 0x3295b70 (LWP 3863)]
[New Thread 0x1a64b70 (LWP 3858)]
[New Thread 0x7f23b70 (LWP 3857)]
[New Thread 0x93ab70 (LWP 3856)]
0x00d96422 in __kernel_vsyscall ()
  11 Thread 0x93ab70 (LWP 3856)  0x00d96422 in __kernel_vsyscall ()
  10 Thread 0x7f23b70 (LWP 3857)  0x00d96422 in __kernel_vsyscall ()
  9 Thread 0x1a64b70 (LWP 3858)  0x00d96422 in __kernel_vsyscall ()
  8 Thread 0x3295b70 (LWP 3863)  0x00d96422 in __kernel_vsyscall ()
  7 Thread 0x3516b70 (LWP 3864)  0x00d96422 in __kernel_vsyscall ()
  6 Thread 0x3617b70 (LWP 3865)  0x00d96422 in __kernel_vsyscall ()
  5 Thread 0x2b20b70 (LWP 3867)  0x00d96422 in __kernel_vsyscall ()
  4 Thread 0x3873b70 (LWP 3869)  0x00d96422 in __kernel_vsyscall ()
  3 Thread 0x28d2b70 (LWP 3870)  0x00d96422 in __kernel_vsyscall ()
  2 Thread 0x3e7bb70 (LWP 3877)  0x00d96422 in __kernel_vsyscall ()
* 1 Thread 0xb966f0 (LWP 3854)  0x00d96422 in __kernel_vsyscall ()

Thread 11 (Thread 0x93ab70 (LWP 3856)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x0066c466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a3658 in ?? ()
#3  0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0x7f23b70 (LWP 3857)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x0066af75 in sem_wait@@GLIBC_2.1 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812bb29 in ?? ()
#3  0x0814f96c in ?? ()
#4  0x081bf9f2 in ?? ()
#5  0x081de055 in ?? ()
#6  0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0x1a64b70 (LWP 3858)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x00668e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814c923 in ?? ()
#6  0x00b5d315 in ?? ()
#7  0x00b5d12d in ?? ()
#8  0x00b594ea in ?? ()
#9  0x002f3df0 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0x3295b70 (LWP 3863)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x00668e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a8577 in ?? ()
#4  0x081c4403 in ?? ()
#5  0x0814e4a8 in ?? ()
#6  0x029872ad in ?? ()
#7  0x02986f89 in ?? ()
#8  0x02986b35 in ?? ()
#9  0x002f1086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0x3516b70 (LWP 3864)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x00668e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a8577 in ?? ()
#4  0x081c4403 in ?? ()
#5  0x0814e4a8 in ?? ()
#6  0x029872ad in ?? ()
#7  0x02986f89 in ?? ()
#8  0x02986b35 in ?? ()
#9  0x002f1086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0x3617b70 (LWP 3865)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x00668e15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a8577 in ?? ()
#4  0x081c4403 in ?? ()
#5  0x0814e4a8 in ?? ()
#6  0x029872ad in ?? ()
#7  0x02986f89 in ?? ()
#8  0x02986b35 in ?? ()
#9  0x002f1086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0x2b20b70 (LWP 3867)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x001d0ba6 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x0085153b in g_poll () from /lib/libglib-2.0.so.0
#3  0x0084455b in ?? () from /lib/libglib-2.0.so.0
#4  0x00844b8f in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x04d328c0 in ?? () from /usr/lib/libORBit-2.so.0
#6  0x0086b36f in ?? () from /lib/libglib-2.0.so.0
#7  0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0x3873b70 (LWP 3869)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x0066bc8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x00732482 in Mono_Posix_Syscall_read ()
   from /usr/lib/libMonoPosixHelper.so
#3  0x002fe66a in ?? ()
#4  0x00ca88e2 in ?? ()
#5  0x00ca8792 in ?? ()
#6  0x02a98002 in ?? ()
#7  0x02a9b245 in ?? ()
#8  0x02a8be20 in ?? ()
#9  0x002f1086 in ?? ()
#10 0x08114f4b in mono_runtime_invoke_array ()
#11 0x0811512e in ?? ()
#12 0x081520a3 in ?? ()
#13 0x08152577 in ?? ()
#14 0x0814f96c in ?? ()
#15 0x081bf9f2 in ?? ()
#16 0x081de055 in ?? ()
#17 0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0x28d2b70 (LWP 3870)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x0066be98 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081bc73e in ?? ()
#3  0x0815838b in ?? ()
#4  0x02b5fbad in ?? ()
#5  0x02b5f9f0 in ?? ()
#6  0x02b5f8f1 in ?? ()
#7  0x002f3df0 in ?? ()
#8  0x0810e6a4 in mono_runtime_delegate_invoke ()
#9  0x0814f9d7 in ?? ()
#10 0x081bf9f2 in ?? ()
#11 0x081de055 in ?? ()
#12 0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0x3e7bb70 (LWP 3877)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x0066bc8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()
#3  0x080f4693 in ?? ()
#4  <signal handler called>
#5  0x00184f43 in strlen () from /lib/tls/i686/cmov/libc.so.6
#6  0x04b5bcf5 in ?? () from /usr/lib/libmtp.so.8
#7  0x04b5c8af in LIBMTP_Create_New_Album () from /usr/lib/libmtp.so.8
#8  0x0310c05d in ?? ()
#9  0x0310be54 in ?? ()
#10 0x0310bd42 in ?? ()
#11 0x0310bafa in ?? ()
#12 0x0310bac4 in ?? ()
#13 0x0310b0d4 in ?? ()
#14 0x0310a781 in ?? ()
#15 0x0389484d in ?? ()
#16 0x03894482 in ?? ()
#17 0x038941ef in ?? ()
#18 0x0388c05f in ?? ()
#19 0x0388bac9 in ?? ()
#20 0x025c8b88 in ?? ()
#21 0x025c8b2a in ?? ()
#22 0x0388b989 in ?? ()
#23 0x030d8c0b in ?? ()
#24 0x002f1086 in ?? ()
#25 0x08114f4b in mono_runtime_invoke_array ()
#26 0x0811512e in ?? ()
#27 0x081520a3 in ?? ()
#28 0x08152577 in ?? ()
#29 0x0814f96c in ?? ()
#30 0x081bf9f2 in ?? ()
#31 0x081de055 in ?? ()
#32 0x0066480e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#33 0x001de7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb966f0 (LWP 3854)):
#0  0x00d96422 in __kernel_vsyscall ()
#1  0x001d0ba6 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x0085153b in g_poll () from /lib/libglib-2.0.so.0
#3  0x0084455b in ?? () from /lib/libglib-2.0.so.0
#4  0x00844b8f in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x012e9419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x058e09f0 in ?? ()
#7  0x058e0973 in ?? ()
#8  0x058e04dd in ?? ()
#9  0x005a54d5 in ?? ()
#10 0x005a5382 in ?? ()
#11 0x005a52b6 in ?? ()
#12 0x00547169 in ?? ()
#13 0x00544366 in ?? ()
#14 0x005442d3 in ?? ()
#15 0x081112ae in mono_runtime_exec_main ()
#16 0x00544253 in ?? ()
#17 0x0054413c in ?? ()
#18 0x00544016 in ?? ()
#19 0x00543fc0 in ?? ()
#20 0x00543f42 in ?? ()
#21 0x00543ef3 in ?? ()
#22 0x00543452 in ?? ()
#23 0x002f13f9 in ?? ()
#24 0x002f11fa in ?? ()
#25 0x081112ae in mono_runtime_exec_main ()
#26 0x081134da in mono_runtime_run_main ()
#27 0x080b19bd in mono_main ()
#28 0x0805aba5 in ?? ()
=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
 
Any help will be greatly appreciated.

---

### Post by abrianb on 2009-11-09
Any one got ideas?

---

### Post by directhex on 2009-11-09
Seems to be crashing in libmtp... Hard to be sure without the ddeb installed

---

