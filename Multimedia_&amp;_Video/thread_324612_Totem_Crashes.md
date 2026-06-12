---
title: "Totem Crashes"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by rykel on 2006-12-24
Hi,

Totem keeps crashing on me a while ago. (It had been working perfectly fine for a long time.)

The error message that pops up is a Bugzilla report dialog (see screenshot) and the following words:

[INDENT][B]Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 57155584 vsize: 0 resident: 57155584 share: 0 rss: 16121856 rss_rlim: 0
CPU usage: start_time: 1166943176 rtime: 0 utime: 52 stime: 0 cutime:50 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/totem'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[Thread debugging using libthread_db enabled]
[New Thread -1225881936 (LWP 5154)]
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
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb730a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ebc1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7075c53 in strlen () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7075975 in strdup () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74b11e1 in xine_new_framegrab_audio_port () from /usr/lib/libxine.so.1
#7  0x00000001 in ?? ()
#8  0xb74db898 in ?? () from /usr/lib/libxine.so.1
#9  0x083c5928 in ?? ()
#10 0xb74dba38 in ?? () from /usr/lib/libxine.so.1
#11 0x00000014 in ?? ()
#12 0xb74b1aec in _x_free_demux_plugin () from /usr/lib/libxine.so.1
#13 0x083e9960 in ?? ()
#14 0x083f3800 in ?? ()
#15 0xbfd49580 in ?? ()
#16 0x083eb690 in ?? ()
#17 0xb74d8cfc in ?? () from /usr/lib/libxine.so.1
#18 0xb713a120 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#19 0x00000000 in ?? ()

Thread 1 (Thread -1225881936 (LWP 5154)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb730a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ebc1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7075c53 in strlen () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb7075975 in strdup () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74b11e1 in xine_new_framegrab_audio_port () from /usr/lib/libxine.so.1
No symbol table info available.
#7  0x00000001 in ?? ()
No symbol table info available.
#8  0xb74db898 in ?? () from /usr/lib/libxine.so.1
No symbol table info available.
#9  0x083c5928 in ?? ()
No symbol table info available.
#10 0xb74dba38 in ?? () from /usr/lib/libxine.so.1
No symbol table info available.
#11 0x00000014 in ?? ()
No symbol table info available.
#12 0xb74b1aec in _x_free_demux_plugin () from /usr/lib/libxine.so.1
No symbol table info available.
#13 0x083e9960 in ?? ()
No symbol table info available.
#14 0x083f3800 in ?? ()
No symbol table info available.
#15 0xbfd49580 in ?? ()
No symbol table info available.
#16 0x083eb690 in ?? ()
No symbol table info available.
#17 0xb74d8cfc in ?? () from /usr/lib/libxine.so.1
No symbol table info available.
#18 0xb713a120 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#19 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
[/B][/INDENT]

I have Removed Completely Totem, Totem-xine, Totem-mozilla, rebooted and reinstalled them but still, the crash persists.

Can you help me please?

---

### Post by RagingOcelot on 2006-12-27
same problem here...

---

### Post by rykel on 2007-01-10
Although I am now using Totem from Edgy_Proposed repository, and have forced the officially latest version as well, Totem seems to have died completely, crashing EVERYTIME I load a video or song.

Is there anyone out there who knows if this is a universal problem now, or is it just me?

If it is just me, do you know how to solve the matter? Thanks!!!

---

### Post by epruesse on 2007-02-22
This sounds very much like what I just experienced. Try removing the contents of the folder "~/.xine". The file catalog.cache is apparently used to cache plugin meta information. On loading the library (startup of totem, xine, amarok, ...) the file is read. It is assumed to be well-formed. If that is not the case, the app depending on libxine will crash.

---

