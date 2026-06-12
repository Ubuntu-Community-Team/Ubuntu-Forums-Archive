---
title: "banshee does not startup on ubuntu8.10"
date: 2009-01-29
forum: Multimedia Software
---

### Post by genryu on 2009-01-29
hi , im having problem with my banshee 1.4.2(which is the newest i think).
Banshee does not even run when i click it the taskbar at that btm shows starting banshee media player for around 5seconds after that it fades and banshee is not started. Any solutions for this?

---

### Post by AndThenWhat on 2009-01-29
can you run "banshee" in a terminal window and post the output please?

---

### Post by genryu on 2009-01-29
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x002be>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x00072>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Banshee.Base.XdgBaseDirectorySpec.GetUserDirectory (string,string) <0x000b2>
  at Banshee.Base.Paths..cctor () <0x00054>
  at (wrapper runtime-invoke) Banshee.Base.ApplicationContext.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0x00009>
  at (wrapper runtime-invoke) Banshee.Gui.GtkBaseClient.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Nereid.Client.Main (string[]) <0xffffffff>
  at Nereid.Client.Main (string[]) <0x0000b>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00055>
  at Booter.Booter.Main () <0x00188>
  at (wrapper runtime-invoke) Booter.Booter.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817b4ae]
	banshee-1 [0x807f78b]
	[0xb7f1a410]
	banshee-1 [0x811b52b]
	banshee-1 [0x811b80d]
	banshee-1 [0x80dae6e]
	[0xb6f5229e]
	[0xb6f515c7]
	[0xb6f512f0]
	[0xb6f512ac]
	[0xb6f51242]
	[0xb6f510e3]
	[0xb6f51057]
	[0xb6f5100a]
	[0xb6f4f4fb]
	[0xb6f4f03d]
	[0xb789e546]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b25066]
	[0xb6f4ef46]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b25066]
	[0xb6f4ee9b]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	[0xb6f4ee45]
	[0xb6f4ed51]
	[0xb6f4ec4a]
	[0xb6f4ebf6]
	[0xb6f4eb6d]
	[0xb6f4eb2a]
	[0xb6f4db9e]
	[0xb789e3b9]
	[0xb789e1be]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	banshee-1(mono_runtime_run_main+0x16b) [0x809d19b]
	banshee-1(mono_main+0x60e) [0x805af2e]
	banshee-1 [0x805a432]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c97685]
	banshee-1 [0x805a371]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c556d0 (LWP 6539)]
[New Thread 0xb7314b90 (LWP 6541)]
[New Thread 0xb7ee6b90 (LWP 6540)]
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
0xb7f1a430 in __kernel_vsyscall ()
  3 Thread 0xb7ee6b90 (LWP 6540)  0xb7f1a430 in __kernel_vsyscall ()
  2 Thread 0xb7314b90 (LWP 6541)  0xb7f1a430 in __kernel_vsyscall ()
  1 Thread 0xb7c556d0 (LWP 6539)  0xb7f1a430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7ee6b90 (LWP 6540)):
#0  0xb7f1a430 in __kernel_vsyscall ()
#1  0xb7e12906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7e0b50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d627ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb7314b90 (LWP 6541)):
#0  0xb7f1a430 in __kernel_vsyscall ()
#1  0xb7e0f075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7e0b50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d627ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c556d0 (LWP 6539)):
#0  0xb7f1a430 in __kernel_vsyscall ()
#1  0xb7e1210b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e939fe in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7e93ee2 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7e9487b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7e94d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0817b565 in ?? ()
#7  0x0807f78b in ?? ()
#8  <signal handler called>
#9  0x08114bd3 in ?? ()
#10 0x0811b52b in ?? ()
#11 0x0811b80d in ?? ()
#12 0x080dae6e in ?? ()
#13 0xb6f5229e in ?? ()
#14 0xb6f515c7 in ?? ()
#15 0xb6f512f0 in ?? ()
#16 0xb6f512ac in ?? ()
#17 0xb6f51242 in ?? ()
#18 0xb6f510e3 in ?? ()
#19 0xb6f51057 in ?? ()
#20 0xb6f5100a in ?? ()
#21 0xb6f4f4fb in ?? ()
#22 0xb6f4f03d in ?? ()
#23 0xb789e546 in ?? ()
#24 0x080a02f1 in mono_runtime_class_init ()
#25 0x08159420 in ?? ()
#26 0x08164d3d in ?? ()
#27 0x08166624 in ?? ()
#28 0x081815d6 in ?? ()
#29 0xb7b25066 in ?? ()
#30 0xb6f4ef46 in ?? ()
#31 0x080a02f1 in mono_runtime_class_init ()
#32 0x08159420 in ?? ()
#33 0x08164d3d in ?? ()
#34 0x08166624 in ?? ()
#35 0x081815d6 in ?? ()
#36 0xb7b25066 in ?? ()
#37 0xb6f4ee9b in ?? ()
#38 0x0809cb76 in mono_runtime_exec_main ()
#39 0xb6f4ee45 in ?? ()
#40 0xb6f4ed51 in ?? ()
#41 0xb6f4ec4a in ?? ()
#42 0xb6f4ebf6 in ?? ()
#43 0xb6f4eb6d in ?? ()
#44 0xb6f4eb2a in ?? ()
#45 0xb6f4db9e in ?? ()
#46 0xb789e3b9 in ?? ()
#47 0xb789e1be in ?? ()
#48 0x0809cb76 in mono_runtime_exec_main ()
#49 0x0809d19b in mono_runtime_run_main ()
#50 0x0805af2e in mono_main ()
#51 0x0805a432 in ?? ()
#52 0xb7c97685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#53 0x0805a371 in ?? ()
#0  0xb7f1a430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by NewJack on 2009-01-29
How did you install Banshee?  Just curious, because I added the Banshee PPA to my sources.list and it installed.  No problems at all so far.  If you didn't use the PPA, you may want to remove the current Banshee that you have installed and reinstall from the PPA.  I know that it installed Mono with it, so that may fix the issue you are having.

PPA:
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) intrepid main

Good Luck!

---

### Post by genryu on 2009-01-29
whats a ppa? care to explain please?

---

### Post by NewJack on 2009-01-29
A PPA is a "**P**ersonal **P**ackage **A**rchive".  It is used by developers to help users have access to the most recent stable release of their apps or the app's development branch (For those who need to be on the bleeding edge).  Some non-devs even host .deb packages that they have compiled of various programs to make apps available to fellow users.  

Anyway, if you go to the Banshee link I posted it will explain how to add the PPA to your Software Sources and then install Banshee on your system.  The instructions are very straight forward.  

** Make sure you uninstall the Banshee you already have before reinstalling**

Good Luck!

---

### Post by genryu on 2009-01-30
erm , is it posible to explain to me step by step im still getting the same error over and over i been trying this for at lease 5times ==

---

### Post by mozychan on 2009-01-30
After you have uninstalled banshee.  The instructions are [here]("https://edge.launchpad.net/~banshee-team/+archive/ppa").  For your convenience:

```
This PPA contains the latest debs of Banshee for Ubuntu Gutsy and Hardy. To install Banshee, you must first enable the PPA on your system:
1. Open Software Sources (System->Administration->Software Sources)
2. Navigate to the "Third Party Sources" tab.
3. Click "Add"
4. Enter the APT line below that corresponds to your Ubuntu version that starts with "deb".
5. Click "Add Source"
6. Click "Close"
7. It will prompt you to reload your software cache. Click "Reload".
8. Now install the package "banshee" from Synaptic, or using the command below:
sudo apt-get install banshee
```

-moose

---

### Post by mozychan on 2009-01-30
For step 4, input:

```
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu intrepid main
```

-moose

---

### Post by genryu on 2009-01-30
did everything still getting the same output

Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x002be>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x00072>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Banshee.Base.XdgBaseDirectorySpec.GetUserDirectory (string,string) <0x000b2>
  at Banshee.Base.Paths..cctor () <0x00054>
  at (wrapper runtime-invoke) Banshee.Base.ApplicationContext.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0x00009>
  at (wrapper runtime-invoke) Banshee.Gui.GtkBaseClient.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Nereid.Client.Main (string[]) <0xffffffff>
  at Nereid.Client.Main (string[]) <0x0000b>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00055>
  at Booter.Booter.Main () <0x00188>
  at (wrapper runtime-invoke) Booter.Booter.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817b4ae]
	banshee-1 [0x807f78b]
	[0xb7f4c410]
	banshee-1 [0x811b52b]
	banshee-1 [0x811b80d]
	banshee-1 [0x80dae6e]
	[0xb6f8429e]
	[0xb6f835c7]
	[0xb6f832f0]
	[0xb6f832ac]
	[0xb6f83242]
	[0xb6f830e3]
	[0xb6f83057]
	[0xb6f8300a]
	[0xb6f814fb]
	[0xb6f8103d]
	[0xb78d0546]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b57066]
	[0xb6f80f46]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b57066]
	[0xb6f80e9b]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	[0xb6f80e45]
	[0xb6f80d51]
	[0xb6f80c4a]
	[0xb6f80bf6]
	[0xb6f80b6d]
	[0xb6f80b2a]
	[0xb6f7fb9e]
	[0xb78d03b9]
	[0xb78d01be]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	banshee-1(mono_runtime_run_main+0x16b) [0x809d19b]
	banshee-1(mono_main+0x60e) [0x805af2e]
	banshee-1 [0x805a432]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7cc9685]
	banshee-1 [0x805a371]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c876d0 (LWP 8083)]
[New Thread 0xb7346b90 (LWP 8085)]
[New Thread 0xb7f18b90 (LWP 8084)]
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
0xb7f4c430 in __kernel_vsyscall ()
  3 Thread 0xb7f18b90 (LWP 8084)  0xb7f4c430 in __kernel_vsyscall ()
  2 Thread 0xb7346b90 (LWP 8085)  0xb7f4c430 in __kernel_vsyscall ()
  1 Thread 0xb7c876d0 (LWP 8083)  0xb7f4c430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7f18b90 (LWP 8084)):
#0  0xb7f4c430 in __kernel_vsyscall ()
#1  0xb7e44906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7e3d50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d947ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb7346b90 (LWP 8085)):
#0  0xb7f4c430 in __kernel_vsyscall ()
#1  0xb7e41075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7e3d50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d947ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c876d0 (LWP 8083)):
#0  0xb7f4c430 in __kernel_vsyscall ()
#1  0xb7e4410b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ec59fe in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7ec5ee2 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7ec687b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7ec6d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0817b565 in ?? ()
#7  0x0807f78b in ?? ()
#8  <signal handler called>
#9  0x08114bd3 in ?? ()
#10 0x0811b52b in ?? ()
#11 0x0811b80d in ?? ()
#12 0x080dae6e in ?? ()
#13 0xb6f8429e in ?? ()
#14 0xb6f835c7 in ?? ()
#15 0xb6f832f0 in ?? ()
#16 0xb6f832ac in ?? ()
#17 0xb6f83242 in ?? ()
#18 0xb6f830e3 in ?? ()
#19 0xb6f83057 in ?? ()
#20 0xb6f8300a in ?? ()
#21 0xb6f814fb in ?? ()
#22 0xb6f8103d in ?? ()
#23 0xb78d0546 in ?? ()
#24 0x080a02f1 in mono_runtime_class_init ()
#25 0x08159420 in ?? ()
#26 0x08164d3d in ?? ()
#27 0x08166624 in ?? ()
#28 0x081815d6 in ?? ()
#29 0xb7b57066 in ?? ()
#30 0xb6f80f46 in ?? ()
#31 0x080a02f1 in mono_runtime_class_init ()
#32 0x08159420 in ?? ()
#33 0x08164d3d in ?? ()
#34 0x08166624 in ?? ()
#35 0x081815d6 in ?? ()
#36 0xb7b57066 in ?? ()
#37 0xb6f80e9b in ?? ()
#38 0x0809cb76 in mono_runtime_exec_main ()
#39 0xb6f80e45 in ?? ()
#40 0xb6f80d51 in ?? ()
#41 0xb6f80c4a in ?? ()
#42 0xb6f80bf6 in ?? ()
#43 0xb6f80b6d in ?? ()
#44 0xb6f80b2a in ?? ()
#45 0xb6f7fb9e in ?? ()
#46 0xb78d03b9 in ?? ()
#47 0xb78d01be in ?? ()
#48 0x0809cb76 in mono_runtime_exec_main ()
#49 0x0809d19b in mono_runtime_run_main ()
#50 0x0805af2e in mono_main ()
#51 0x0805a432 in ?? ()
#52 0xb7cc9685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#53 0x0805a371 in ?? ()
#0  0xb7f4c430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by directhex on 2009-01-30
A native stacktrace is a funny thing to see.

What is the FULL output in the terminal if you run "banshee-1 --debug"? The stack trace on its own doesn't help as it doesn't reveal at which point it's crashing

---

### Post by genryu on 2009-01-30
genryu@ubuntu:~$ banshee-1 --debug
** Running Mono with --debug   **
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMod
e,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoI
OError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMod
e,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoI
OError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,
System.IO.FileShare,int,bool,System.IO.FileOptions) <0x002be>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,
System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,Sys
tem.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x0007
2>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) 
<0xffffffff>
  at Banshee.Base.XdgBaseDirectorySpec.GetUserDirectory (string,string) [0x00042
] in /build/buildd/banshee-1.4.2/src/Core/Banshee.Core/Banshee.Base/XdgBaseDirec
torySpec.cs:53
  at Banshee.Base.Paths..cctor () <0x00054>
  at (wrapper runtime-invoke) Banshee.Base.ApplicationContext.runtime_invoke_voi
d (object,intptr,intptr,intptr) <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0x00009>
  at (wrapper runtime-invoke) Banshee.Gui.GtkBaseClient.runtime_invoke_void (obj
ect,intptr,intptr,intptr) <0xffffffff>
  at Nereid.Client.Main (string[]) [0x00006] in /build/buildd/banshee-1.4.2/src/
Clients/Nereid/Nereid/Client.cs:49
  at Nereid.Client.Main (string[]) [0x00000] in /build/buildd/banshee-1.4.2/src/
Clients/Nereid/Nereid/Client.cs:48
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object
,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflec
tion.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflec
tion.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string
[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,st
ring[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (stri
ng,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (stri
ng) <0xffffffff>
  at Booter.Booter.BootClient (string) [0x00000] in /build/buildd/banshee-1.4.2/
src/Clients/Booter/Booter/Entry.cs:106
  at Booter.Booter.Main () [0x000d3] in /build/buildd/banshee-1.4.2/src/Clients/
Booter/Booter/Entry.cs:100
  at (wrapper runtime-invoke) Booter.Booter.runtime_invoke_void (object,intptr,i
ntptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817b4ae]
	banshee-1 [0x807f78b]
	[0xb7fa6410]
	banshee-1 [0x811b52b]
	banshee-1 [0x811b80d]
	banshee-1 [0x80dae6e]
	[0xb6f52706]
	[0xb6f51a2f]
	[0xb6f51758]
	[0xb6f51714]
	[0xb6f516aa]
	[0xb6f5154b]
	[0xb6f514bf]
	[0xb6f51472]
	[0xb6f4f963]
	[0xb6f4f4a5]
	[0xb792a546]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7bb1066]
	[0xb6f4f3ae]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7bb1066]
	[0xb6f4f303]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	[0xb6f4f2ad]
	[0xb6f4f1b9]
	[0xb6f4f0b2]
	[0xb6f4f05e]
	[0xb6f4efd5]
	[0xb6f4ef92]
	[0xb6f4e166]
	[0xb792a3b9]
	[0xb792a1be]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	banshee-1(mono_runtime_run_main+0x16b) [0x809d19b]
	banshee-1(mono_main+0x60e) [0x805af2e]
	banshee-1 [0x805a432]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d23685]
	banshee-1 [0x805a371]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7ce16d0 (LWP 9227)]
[New Thread 0xb73a0b90 (LWP 9229)]
[New Thread 0xb7f72b90 (LWP 9228)]
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
0xb7fa6430 in __kernel_vsyscall ()
  3 Thread 0xb7f72b90 (LWP 9228)  0xb7fa6430 in __kernel_vsyscall ()
  2 Thread 0xb73a0b90 (LWP 9229)  0xb7fa6430 in __kernel_vsyscall ()
  1 Thread 0xb7ce16d0 (LWP 9227)  0xb7fa6430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7f72b90 (LWP 9228)):
#0  0xb7fa6430 in __kernel_vsyscall ()
#1  0xb7e9e906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7e9750f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7dee7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb73a0b90 (LWP 9229)):
#0  0xb7fa6430 in __kernel_vsyscall ()
#1  0xb7e9b075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7e9750f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7dee7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7ce16d0 (LWP 9227)):
#0  0xb7fa6430 in __kernel_vsyscall ()
#1  0xb7e9e10b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f1f9fe in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7f1fee2 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7f2087b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7f20d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0817b565 in ?? ()
#7  0x0807f78b in ?? ()
#8  <signal handler called>
#9  0x08114bd3 in ?? ()
#10 0x0811b52b in ?? ()
#11 0x0811b80d in ?? ()
#12 0x080dae6e in ?? ()
#13 0xb6f52706 in ?? ()
#14 0xb6f51a2f in ?? ()
#15 0xb6f51758 in ?? ()
#16 0xb6f51714 in ?? ()
#17 0xb6f516aa in ?? ()
#18 0xb6f5154b in ?? ()
#19 0xb6f514bf in ?? ()
#20 0xb6f51472 in ?? ()
#21 0xb6f4f963 in ?? ()
#22 0xb6f4f4a5 in ?? ()
#23 0xb792a546 in ?? ()
#24 0x080a02f1 in mono_runtime_class_init ()
#25 0x08159420 in ?? ()
#26 0x08164d3d in ?? ()
#27 0x08166624 in ?? ()
#28 0x081815d6 in ?? ()
#29 0xb7bb1066 in ?? ()
#30 0xb6f4f3ae in ?? ()
#31 0x080a02f1 in mono_runtime_class_init ()
#32 0x08159420 in ?? ()
#33 0x08164d3d in ?? ()
#34 0x08166624 in ?? ()
#35 0x081815d6 in ?? ()
#36 0xb7bb1066 in ?? ()
#37 0xb6f4f303 in ?? ()
#38 0x0809cb76 in mono_runtime_exec_main ()
#39 0xb6f4f2ad in ?? ()
#40 0xb6f4f1b9 in ?? ()
#41 0xb6f4f0b2 in ?? ()
#42 0xb6f4f05e in ?? ()
#43 0xb6f4efd5 in ?? ()
#44 0xb6f4ef92 in ?? ()
#45 0xb6f4e166 in ?? ()
#46 0xb792a3b9 in ?? ()
#47 0xb792a1be in ?? ()
#48 0x0809cb76 in mono_runtime_exec_main ()
#49 0x0809d19b in mono_runtime_run_main ()
#50 0x0805af2e in mono_main ()
#51 0x0805a432 in ?? ()
#52 0xb7d23685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#53 0x0805a371 in ?? ()
#0  0xb7fa6430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by directhex on 2009-01-30
Can you install the mono-dbg package then try again?

---

### Post by genryu on 2009-01-30
edit i installed it but still get this 

** Running Mono with --debug   **
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) [0x00222] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/FileStream.cs:279
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/FileStream.cs:135
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/File.cs:384
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) [0x00077] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/StreamReader.cs:167
  at System.IO.StreamReader..ctor (string) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/StreamReader.cs:143
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Banshee.Base.XdgBaseDirectorySpec.GetUserDirectory (string,string) [0x00042] in /build/buildd/banshee-1.4.2/src/Core/Banshee.Core/Banshee.Base/XdgBaseDirectorySpec.cs:53
  at Banshee.Base.Paths..cctor () <0x00054>
  at (wrapper runtime-invoke) Banshee.Base.ApplicationContext.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0x00009>
  at (wrapper runtime-invoke) Banshee.Gui.GtkBaseClient.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Nereid.Client.Main (string[]) [0x00006] in /build/buildd/banshee-1.4.2/src/Clients/Nereid/Nereid/Client.cs:49
  at Nereid.Client.Main (string[]) [0x00000] in /build/buildd/banshee-1.4.2/src/Clients/Nereid/Nereid/Client.cs:48
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) [0x00026] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/AppDomain.cs:527
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) [0x00008] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/AppDomain.cs:510
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/AppDomain.cs:499
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) [0x00000] in /build/buildd/banshee-1.4.2/src/Clients/Booter/Booter/Entry.cs:106
  at Booter.Booter.Main () [0x000d3] in /build/buildd/banshee-1.4.2/src/Clients/Booter/Booter/Entry.cs:100
  at (wrapper runtime-invoke) Booter.Booter.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817b4ae]
	banshee-1 [0x807f78b]
	[0xb7f08410]
	banshee-1 [0x811b52b]
	banshee-1 [0x811b80d]
	banshee-1 [0x80dae6e]
	[0xb6aff706]
	[0xb6afea2f]
	[0xb6afe758]
	[0xb6afe714]
	[0xb6afe6aa]
	[0xb6afe54b]
	[0xb6afe4bf]
	[0xb6afe472]
	[0xb6afc963]
	[0xb6afc4a5]
	[0xb765b546]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b13066]
	[0xb6afc3ae]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b13066]
	[0xb6afc303]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	[0xb6afc2ad]
	[0xb6afc1b9]
	[0xb6afc0b2]
	[0xb6afc05e]
	[0xb6afbfd5]
	[0xb6afbf92]
	[0xb6afb166]
	[0xb765b3b9]
	[0xb765b1be]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	banshee-1(mono_runtime_run_main+0x16b) [0x809d19b]
	banshee-1(mono_main+0x60e) [0x805af2e]
	banshee-1 [0x805a432]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c85685]
	banshee-1 [0x805a371]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c436d0 (LWP 6763)]
[New Thread 0xb70d1b90 (LWP 6765)]
[New Thread 0xb7ed4b90 (LWP 6764)]
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
0xb7f08430 in __kernel_vsyscall ()
  3 Thread 0xb7ed4b90 (LWP 6764)  0xb7f08430 in __kernel_vsyscall ()
  2 Thread 0xb70d1b90 (LWP 6765)  0xb7f08430 in __kernel_vsyscall ()
  1 Thread 0xb7c436d0 (LWP 6763)  0xb7f08430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7ed4b90 (LWP 6764)):
#0  0xb7f08430 in __kernel_vsyscall ()
#1  0xb7e00906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7df950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d507ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb70d1b90 (LWP 6765)):
#0  0xb7f08430 in __kernel_vsyscall ()
#1  0xb7dfd075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7df950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d507ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c436d0 (LWP 6763)):
#0  0xb7f08430 in __kernel_vsyscall ()
#1  0xb7e0010b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e819fe in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7e81ee2 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7e8287b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7e82d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0817b565 in ?? ()
#7  0x0807f78b in ?? ()
#8  <signal handler called>
#9  0x08114bd3 in ?? ()
#10 0x0811b52b in ?? ()
#11 0x0811b80d in ?? ()
#12 0x080dae6e in ?? ()
#13 0xb6aff706 in ?? ()
#14 0xb6afea2f in ?? ()
#15 0xb6afe758 in ?? ()
#16 0xb6afe714 in ?? ()
#17 0xb6afe6aa in ?? ()
#18 0xb6afe54b in ?? ()
#19 0xb6afe4bf in ?? ()
#20 0xb6afe472 in ?? ()
#21 0xb6afc963 in ?? ()
#22 0xb6afc4a5 in ?? ()
#23 0xb765b546 in ?? ()
#24 0x080a02f1 in mono_runtime_class_init ()
#25 0x08159420 in ?? ()
#26 0x08164d3d in ?? ()
#27 0x08166624 in ?? ()
#28 0x081815d6 in ?? ()
#29 0xb7b13066 in ?? ()
#30 0xb6afc3ae in ?? ()
#31 0x080a02f1 in mono_runtime_class_init ()
#32 0x08159420 in ?? ()
#33 0x08164d3d in ?? ()
#34 0x08166624 in ?? ()
#35 0x081815d6 in ?? ()
#36 0xb7b13066 in ?? ()
#37 0xb6afc303 in ?? ()
#38 0x0809cb76 in mono_runtime_exec_main ()
#39 0xb6afc2ad in ?? ()
#40 0xb6afc1b9 in ?? ()
#41 0xb6afc0b2 in ?? ()
#42 0xb6afc05e in ?? ()
#43 0xb6afbfd5 in ?? ()
#44 0xb6afbf92 in ?? ()
#45 0xb6afb166 in ?? ()
#46 0xb765b3b9 in ?? ()
#47 0xb765b1be in ?? ()
#48 0x0809cb76 in mono_runtime_exec_main ()
#49 0x0809d19b in mono_runtime_run_main ()
#50 0x0805af2e in mono_main ()
#51 0x0805a432 in ?? ()
#52 0xb7c85685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#53 0x0805a371 in ?? ()
#0  0xb7f08430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by directhex on 2009-01-30
> **genryu said:**
> edit i installed it but still get this

But now I get line numbers in the Mono source code to see where it's going wrong. Is this the standard Mono included in Ubuntu 8.10 (1.9.1+dfsg-4ubuntu2) or from somewhere else?

---

### Post by directhex on 2009-01-30
Can you add libmono0-dbg and mono-jit-dbg, then re-run? Hopefully that'll tell me more about the MonoIO native calls

---

### Post by genryu on 2009-01-30
heres the next output :

** Running Mono with --debug   **
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) [0x00222] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/FileStream.cs:279
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/FileStream.cs:135
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/File.cs:384
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) [0x00077] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/StreamReader.cs:167
  at System.IO.StreamReader..ctor (string) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System.IO/StreamReader.cs:143
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Banshee.Base.XdgBaseDirectorySpec.GetUserDirectory (string,string) [0x00042] in /build/buildd/banshee-1.4.2/src/Core/Banshee.Core/Banshee.Base/XdgBaseDirectorySpec.cs:53
  at Banshee.Base.Paths..cctor () <0x00054>
  at (wrapper runtime-invoke) Banshee.Base.ApplicationContext.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0xffffffff>
  at Banshee.Gui.GtkBaseClient..cctor () <0x00009>
  at (wrapper runtime-invoke) Banshee.Gui.GtkBaseClient.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Nereid.Client.Main (string[]) [0x00006] in /build/buildd/banshee-1.4.2/src/Clients/Nereid/Nereid/Client.cs:49
  at Nereid.Client.Main (string[]) [0x00000] in /build/buildd/banshee-1.4.2/src/Clients/Nereid/Nereid/Client.cs:48
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) [0x00026] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/AppDomain.cs:527
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) [0x00008] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/AppDomain.cs:510
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) [0x00000] in /build/buildd/mono-1.9.1+dfsg/mcs/class/corlib/System/AppDomain.cs:499
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) [0x00000] in /build/buildd/banshee-1.4.2/src/Clients/Booter/Booter/Entry.cs:106
  at Booter.Booter.Main () [0x000d3] in /build/buildd/banshee-1.4.2/src/Clients/Booter/Booter/Entry.cs:100
  at (wrapper runtime-invoke) Booter.Booter.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x817b4ae]
	banshee-1 [0x807f78b]
	[0xb7f32410]
	banshee-1 [0x811b52b]
	banshee-1 [0x811b80d]
	banshee-1 [0x80dae6e]
	[0xb6b29706]
	[0xb6b28a2f]
	[0xb6b28758]
	[0xb6b28714]
	[0xb6b286aa]
	[0xb6b2854b]
	[0xb6b284bf]
	[0xb6b28472]
	[0xb6b26963]
	[0xb6b264a5]
	[0xb7685546]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b3d066]
	[0xb6b263ae]
	banshee-1(mono_runtime_class_init+0x241) [0x80a02f1]
	banshee-1 [0x8159420]
	banshee-1 [0x8164d3d]
	banshee-1 [0x8166624]
	banshee-1 [0x81815d6]
	[0xb7b3d066]
	[0xb6b26303]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	[0xb6b262ad]
	[0xb6b261b9]
	[0xb6b260b2]
	[0xb6b2605e]
	[0xb6b25fd5]
	[0xb6b25f92]
	[0xb6b25166]
	[0xb76853b9]
	[0xb76851be]
	banshee-1(mono_runtime_exec_main+0xb6) [0x809cb76]
	banshee-1(mono_runtime_run_main+0x16b) [0x809d19b]
	banshee-1(mono_main+0x60e) [0x805af2e]
	banshee-1 [0x805a432]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7caf685]
	banshee-1 [0x805a371]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c6d6d0 (LWP 6591)]
[New Thread 0xb70fbb90 (LWP 6593)]
[New Thread 0xb7efeb90 (LWP 6592)]
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
0xb7f32430 in __kernel_vsyscall ()
  3 Thread 0xb7efeb90 (LWP 6592)  0xb7f32430 in __kernel_vsyscall ()
  2 Thread 0xb70fbb90 (LWP 6593)  0xb7f32430 in __kernel_vsyscall ()
  1 Thread 0xb7c6d6d0 (LWP 6591)  0xb7f32430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7efeb90 (LWP 6592)):
#0  0xb7f32430 in __kernel_vsyscall ()
#1  0xb7e2a906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7e2350f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d7a7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb70fbb90 (LWP 6593)):
#0  0xb7f32430 in __kernel_vsyscall ()
#1  0xb7e27075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7e2350f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d7a7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c6d6d0 (LWP 6591)):
#0  0xb7f32430 in __kernel_vsyscall ()
#1  0xb7d35ed5 in fork () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7e2c834 in fork () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7eabd25 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7eac87b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7eacd3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0817b565 in ?? ()
#7  0x0807f78b in ?? ()
#8  <signal handler called>
#9  0x08114bd3 in ?? ()
#10 0x0811b52b in ?? ()
#11 0x0811b80d in ?? ()
#12 0x080dae6e in ?? ()
#13 0xb6b29706 in ?? ()
#14 0xb6b28a2f in ?? ()
#15 0xb6b28758 in ?? ()
#16 0xb6b28714 in ?? ()
#17 0xb6b286aa in ?? ()
#18 0xb6b2854b in ?? ()
#19 0xb6b284bf in ?? ()
#20 0xb6b28472 in ?? ()
#21 0xb6b26963 in ?? ()
#22 0xb6b264a5 in ?? ()
#23 0xb7685546 in ?? ()
#24 0x080a02f1 in mono_runtime_class_init ()
#25 0x08159420 in ?? ()
#26 0x08164d3d in ?? ()
#27 0x08166624 in ?? ()
#28 0x081815d6 in ?? ()
#29 0xb7b3d066 in ?? ()
#30 0xb6b263ae in ?? ()
#31 0x080a02f1 in mono_runtime_class_init ()
#32 0x08159420 in ?? ()
#33 0x08164d3d in ?? ()
#34 0x08166624 in ?? ()
#35 0x081815d6 in ?? ()
#36 0xb7b3d066 in ?? ()
#37 0xb6b26303 in ?? ()
#38 0x0809cb76 in mono_runtime_exec_main ()
#39 0xb6b262ad in ?? ()
#40 0xb6b261b9 in ?? ()
#41 0xb6b260b2 in ?? ()
#42 0xb6b2605e in ?? ()
#43 0xb6b25fd5 in ?? ()
#44 0xb6b25f92 in ?? ()
#45 0xb6b25166 in ?? ()
#46 0xb76853b9 in ?? ()
#47 0xb76851be in ?? ()
#48 0x0809cb76 in mono_runtime_exec_main ()
#49 0x0809d19b in mono_runtime_run_main ()
#50 0x0805af2e in mono_main ()
#51 0x0805a432 in ?? ()
#52 0xb7caf685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#53 0x0805a371 in ?? ()
#0  0xb7f32430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by directhex on 2009-01-30
Does F-Spot or Tomboy run?

Can you try moving your Banshee database out of the way (mv ~/.config/banshee-1 ~/.config/banshee-bak)?

---

### Post by genryu on 2009-01-30
i do not have fspot and tomboy and i do not understand what do u mean by moving banshee =.= care to explain?

---

### Post by NewJack on 2009-01-30
Unless you uninstalled them, you should have F-Spot and Tomboy by default.

Also, as far as moving your Banshee database, use the command line input that directhex gave you.  It will move the Banshee database file from ~/.config/banshee-1 to ~/.config/banshee-bak.  This way if there is a conflict with Mono and the Banshee DB this should resolve it.

---

### Post by genryu on 2009-01-30
do i have to reinstall tomboy and f-spot? and btw banshee still does not run after that comand ==


edit: f-spot and tomboy does not run and same case as banshee which is taskbar pops up starting (tomboy / f-spot) then terminates later on

---

### Post by genryu on 2009-02-01
is there other solution like reinstalling ubuntu or repairing with the disc or anything ?

---

