---
title: "banshee wont start :("
date: 2008-07-04
forum: Multimedia Software
---

### Post by mrsudo on 2008-07-04
banshee has been acting up on me again .... as with all of my other music players as a matter of fact

but banshee is my favorite!  

i run 'banshee' from the terminal and get 

> ** (/usr/lib/banshee/banshee.exe:19514): CRITICAL **: _wapi_shm_file_open: shared file [/home/kevin/.wapi/shared_data-a1600n-Linux-i686-312-11-0] write error: No space left on device

** (/usr/lib/banshee/banshee.exe:19514): CRITICAL **: _wapi_shm_attach: shared file [/home/kevin/.wapi/shared_data-a1600n-Linux-i686-312-11-0] open error
**
** ERROR:(shared.c:346):shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/banshee/banshee.exe:19514): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/banshee/banshee.exe:19514): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/banshee/banshee.exe:19514): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	banshee [0x816b1fa]
	[0xb7fd0440]
	/lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7d97a01]
	/usr/lib/libglib-2.0.so.0(g_assertion_message+0x121) [0xb7f573e1]
	/usr/lib/libglib-2.0.so.0 [0xb7f5793d]
	banshee [0x811703e]
	banshee [0x8109342]
	banshee(mono_once+0x96) [0x8112726]
	banshee [0x810907c]
	banshee [0x8115f6e]
	banshee [0x8116364]
	banshee [0x80d1877]
	banshee(mono_runtime_init+0x26) [0x80d8836]
	banshee [0x8134535]
	banshee(mono_main+0x3aa) [0x805a9da]
	banshee [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d81450]
	banshee [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d29940 (LWP 19514)]
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
0xb7fd0410 in __kernel_vsyscall ()
  1 Thread 0xb7d29940 (LWP 19514)  0xb7fd0410 in __kernel_vsyscall ()

Thread 1 (Thread 0xb7d29940 (LWP 19514)):
#0  0xb7fd0410 in __kernel_vsyscall ()
#1  0xb7e3a84d in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f68e14 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f691dc in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  <signal handler called>
#6  0xb7fd0410 in __kernel_vsyscall ()
#7  0xb7d96085 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7d97a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7f573e1 in g_assertion_message () from /usr/lib/libglib-2.0.so.0
#10 0xb7f5793d in g_assertion_message_expr () from /usr/lib/libglib-2.0.so.0
#11 0x0811703e in ?? ()
#12 0x08109342 in ?? ()
#13 0x08112726 in mono_once ()
#14 0x0810907c in ?? ()
#15 0x08115f6e in ?? ()
#16 0x08116364 in ?? ()
#17 0x080d1877 in ?? ()
#18 0x080d8836 in mono_runtime_init ()
#19 0x08134535 in ?? ()
#20 0x0805a9da in mono_main ()
#21 0x0805a122 in ?? ()
#22 0xb7d81450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#23 0x0805a091 in ?? ()
#0  0xb7fd0410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted


i wouldnt even know how to begin troubleshooting this..
any help would be much appreciated!

---

### Post by mrsudo on 2008-07-05
a couple reboots later and banshee is up and running.

no clue what was wrong .... and sorry for any people looking for a solution to a similiar problem.

---

