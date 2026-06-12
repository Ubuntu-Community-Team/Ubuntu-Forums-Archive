---
title: "[SOLVED] Banshee won't start - SIGSEGV"
date: 2008-01-04
forum: Multimedia &amp; Video
---

### Post by itsjustarumour on 2008-01-04
Hi All,

Banshee has been working just fine for me since I installed Gutsy, but I tried it today and nothing happens.  I tried reinstalling it from the Gutsy repos, but no joy.

Running Banshee in the terminal gives:

> ******@COOLERMASTER:~$ banshee

** (/usr/lib/banshee/banshee.exe:6056): WARNING **: The following assembly referenced from /usr/lib/mono/gac/NDesk.DBus.GLib/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.GLib.dll could not be loaded:
     Assembly:   NDesk.DBus    (assemblyref_index=1)
     Version:    1.0.0.0
     Public Key: f6716e4f9b2ed099
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/mono/gac/NDesk.DBus.GLib/1.0.0.0__f6716e4f9b2ed099).


** (/usr/lib/banshee/banshee.exe:6056): WARNING **: Could not load file or assembly 'NDesk.DBus, Version=1.0.0.0, Culture=neutral, PublicKeyToken=f6716e4f9b2ed099' or one of its dependencies.

** (/usr/lib/banshee/banshee.exe:6056): WARNING **: Missing method get_System in assembly /usr/lib/mono/gac/NDesk.DBus.GLib/1.0.0.0__f6716e4f9b2ed099/NDesk.DBus.GLib.dll, type NDesk.DBus.Bus
Stacktrace:

  at Banshee.BansheeEntry.Startup (string[]) <0xffffffff>
  at Banshee.BansheeEntry.Startup (string[]) <0x0006b>
  at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_string[] (string[]) <0xffffffff>
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.CleanRoomStartup/StartupInvocationHandler,string[]) <0x000ae>
  at Banshee.BansheeEntry.Main (string[]) <0x00038>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

        banshee [0x8194ca6]
        banshee [0x81770ed]
        [0xffffe440]
        banshee(mono_object_new+0x18) [0x80b596a]
        banshee(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        banshee(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        banshee [0x810f9a7]
        banshee [0x811a390]
        banshee(mono_class_vtable+0x181) [0x80b29b3]
        banshee(mono_object_new+0x18) [0x80b596a]
        banshee(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        banshee(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        banshee [0x810f9a7]
        banshee [0x8176370]
        banshee [0x817699e]
        banshee [0x8176a98]
        banshee(mono_compile_method+0x3b) [0x80b13bd]
        banshee [0x808fe5a]
        [0xb7be9032]
        [0xb73a808e]
        [0xb73a7f3f]
        [0xb73a7261]
        [0xb73a7075]
        banshee [0x8176f50]
        banshee(mono_runtime_invoke+0x27) [0x80b0b2f]
        banshee(mono_runtime_exec_main+0x142) [0x80b5383]
        banshee(mono_runtime_run_main+0x27e) [0x80b5631]
        banshee(mono_jit_exec+0xbd) [0x805a4cb]
        banshee [0x805a5a8]
        banshee(mono_main+0x1683) [0x805bdc9]
        banshee [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d40050]
        banshee [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210939696 (LWP 6056)]
[New Thread -1220916336 (LWP 6058)]
[New Thread -1220834416 (LWP 6057)]
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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
  3 Thread -1220834416 (LWP 6057)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220916336 (LWP 6058)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210939696 (LWP 6056)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1220834416 (LWP 6057)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ea59f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb73b83ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220916336 (LWP 6058)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ea2676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb78921dc in ?? ()
#4  0xb78921c4 in ?? ()
#5  0xb7ea0541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb78921dc in ?? ()
#8  0xb78921c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210939696 (LWP 6056)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7df62a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f15780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f15b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7be8844 in ?? ()
#6  0xb7be882c in ?? ()
#7  0xb7be8828 in ?? ()
#8  0xb7be8824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
******@COOLERMASTER:~$ 


Anyone got any ideas on how I go about fixing this one?  I can't think of any changes I've made to my system that would have caused this...

Best Regards,

itsjustarumour

---

### Post by itsjustarumour on 2008-01-04
Ah, nuts - DOH!!!  ](*,)

I think I know what caused this - I tried - and failed - to install the latest Beagle 3.0 yesterday - of course, thats another Mono app!  So I must have broken this myself somehow :oops:

I've tried reinstalling everything relating to Mono, libraries etc but still same problem....

---

### Post by itsjustarumour on 2008-01-04
OK, all sorted!  :-)

Re-installing mono-runtime did the trick.

:popcorn:

---

