---
title: "Can't start Amarok or Banshee"
date: 2008-07-17
forum: Multimedia Software
---

### Post by snkngshps on 2008-07-17
I just got a new laptop and for some reason I can't start Banshee or Amarok. If I try to start Banshee a window for it is shown in the tray but eventually disappears and nothing happens. When I try to start Amarok I get these 2 errors:

"There was an error setting up inter-process communications for KDE. The message returned by the system was:

Could not read the network connection list.
/home/joshua/.DCOPserver_SNKNGSHPS_0

Please check that the "dcopserver" program is running!"

When I hit OK I get this one:

"Could not set application as the default: Failed to close file '/home/joshua/.local/share/applications/mimeapps.list.5BE3DU': fclose() failed: Success"


I've been able to run these programs fine on past computers. MP3s will play in Totem but nothing else. Any ideas?

---

### Post by tuxxy on 2008-07-17
Another reason I dont even install KDE apps, they can effect my GNOME it seems :(

---

### Post by nikgare on 2008-07-18
What errors do you get when you start Banshee in a terminal windows?

---

### Post by snkngshps on 2008-07-18
> **nikgare said:**
> What errors do you get when you start Banshee in a terminal windows?

Here's the full response:

joshua@SNKNGSHPS:~$ banshee start

** (/usr/lib/banshee/banshee.exe:5845): CRITICAL **: _wapi_shm_file_open: shared file [/home/joshua/.wapi/shared_data-SNKNGSHPS-Linux-i686-312-11-0] open error: No such file or directory

** (/usr/lib/banshee/banshee.exe:5845): CRITICAL **: _wapi_shm_attach: shared file [/home/joshua/.wapi/shared_data-SNKNGSHPS-Linux-i686-312-11-0] open error
**
** ERROR:(shared.c:346):shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/banshee/banshee.exe:5845): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/banshee/banshee.exe:5845): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/banshee/banshee.exe:5845): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	banshee [0x816b1fa]
	[0xb7f07440]
	/lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7cd0a01]
	/usr/lib/libglib-2.0.so.0(g_assertion_message+0x121) [0xb7e903e1]
	/usr/lib/libglib-2.0.so.0 [0xb7e9093d]
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
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cba450]
	banshee [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c62940 (LWP 5845)]
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
0xb7f07410 in __kernel_vsyscall ()
  1 Thread 0xb7c62940 (LWP 5845)  0xb7f07410 in __kernel_vsyscall ()

Thread 1 (Thread 0xb7c62940 (LWP 5845)):
#0  0xb7f07410 in __kernel_vsyscall ()
#1  0xb7d7384d in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ea1e14 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7ea21dc in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  <signal handler called>
#6  0xb7f07410 in __kernel_vsyscall ()
#7  0xb7ccf085 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7cd0a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7e903e1 in g_assertion_message () from /usr/lib/libglib-2.0.so.0
#10 0xb7e9093d in g_assertion_message_expr () from /usr/lib/libglib-2.0.so.0
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
#22 0xb7cba450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#23 0x0805a091 in ?? ()
#0  0xb7f07410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by snkngshps on 2008-07-19
Does anyone know how I can fix these :-/

---

### Post by nikgare on 2008-07-19
> Does anyone know how I can fix these :-/

Not really, apart from the usual aptitude remove -purge and deleteing/moving the config directories

---

