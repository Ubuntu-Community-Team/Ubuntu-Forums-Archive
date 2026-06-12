---
title: "sound-juicer and grip freezing"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by brotell on 2007-05-08
I have been using soun-juicer as my rip and copy program but last week when i tried to use the program it froze my computer. I tried grip with the same results. The only clue i have is in the properties of the cd i get the permissions of "cdda" could not be determinded.
Any help would be appreciated.
My dvd player and recorder has not been affected.

Regards


Terry

---

### Post by aysiu on 2007-05-08
Open up [a terminal](http://www.psychocats.net/ubuntu/terminal) and type ```
grip
``` This will launch Grip but also give you error messages when Grip freezes. When it freezes, copy and paste those error messages back to this thread.

---

### Post by brotell on 2007-05-08
grip now works but no sound sound-juicer still freezes as soon as you try to play or extract. Cannot figure out why grip now works im confused.

---

### Post by brotell on 2007-05-08
I found this error report from the original freeze.
Memory status: size: 58421248 vsize: 0 resident: 58421248 share: 0 rss: 17592320 rss_rlim: 0
CPU usage: start_time: 1178367636 rtime: 0 utime: 53 stime: 0 cutime:50 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/grip'

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
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1228564816 (LWP 13857)]
[New Thread -1252910176 (LWP 13870)]
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
#1  0xb718534b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7b9b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb78e5ee5 in gtk_tree_model_get_valist ()
   from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb78e60dd in gtk_tree_model_get () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x08059cb2 in ?? ()
#7  0x080d34d0 in ?? ()
#8  0xbfd7ee48 in ?? ()
#9  0x00000002 in ?? ()
#10 0xbfd7ee58 in ?? ()
#11 0xffffffff in ?? ()
#12 0x084bd800 in ?? ()
#13 0x084bd9a8 in ?? ()
#14 0xb71781e4 in ?? () from /usr/lib/libglib-2.0.so.0
#15 0x084bd9a8 in ?? ()
#16 0xbfd7eecc in ?? ()
#17 0x00000000 in ?? ()

Thread 2 (Thread -1252910176 (LWP 13870)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6e3d803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb6fdc3ad in __res_queriesmatch () from /lib/tls/i686/cmov/libresolv.so.2
No symbol table info available.
#3  0xb6fdb153 in __libc_res_nquery () from /lib/tls/i686/cmov/libresolv.so.2
No symbol table info available.
#4  0xb6fdb3f0 in __libc_res_nquery () from /lib/tls/i686/cmov/libresolv.so.2
No symbol table info available.
#5  0xb6fdb63a in __libc_res_nsearch () from /lib/tls/i686/cmov/libresolv.so.2
No symbol table info available.
#6  0xb4d11976 in _nss_dns_gethostbyname3_r ()
   from /lib/tls/i686/cmov/libnss_dns.so.2
No symbol table info available.
#7  0xb4d11c4b in _nss_dns_gethostbyname2_r ()
   from /lib/tls/i686/cmov/libnss_dns.so.2
No symbol table info available.
#8  0xb6e2dac5 in freeaddrinfo () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#9  0xb6e2e716 in getaddrinfo () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#10 0xb70d31df in curl_share_strerror () from /usr/lib/libcurl-gnutls.so.3
No symbol table info available.
#11 0xb70b1d91 in ?? () from /usr/lib/libcurl-gnutls.so.3
No symbol table info available.
#12 0x08584ef8 in ?? ()
No symbol table info available.
#13 0x08585380 in ?? ()
No symbol table info available.
#14 0x00000050 in ?? ()
No symbol table info available.
#15 0xb551e4b4 in ?? ()
No symbol table info available.
#16 0x08584ef8 in ?? ()
No symbol table info available.
#17 0x08584a98 in ?? ()
No symbol table info available.
#18 0x0857c488 in ?? ()
No symbol table info available.
#19 0xb70d4c30 in curl_getdate () from /usr/lib/libcurl-gnutls.so.3
No symbol table info available.
#20 0xb70c1656 in curl_slist_free_all () from /usr/lib/libcurl-gnutls.so.3
No symbol table info available.
#21 0xb70ca348 in curl_mvsnprintf () from /usr/lib/libcurl-gnutls.so.3
No symbol table info available.
#22 0xb70cc89e in curl_mvsnprintf () from /usr/lib/libcurl-gnutls.so.3
No symbol table info available.
#23 0xb70cd063 in curl_easy_perform () from /usr/lib/libcurl-gnutls.so.3
No symbol table info available.
#24 0x0806520a in ?? ()
No symbol table info available.
#25 0x0857c488 in ?? ()
No symbol table info available.
#26 0x00002711 in ?? ()
No symbol table info available.
#27 0x08584c38 in ?? ()
No symbol table info available.
#28 0xb5521244 in ?? ()
No symbol table info available.
#29 0xb5521344 in ?? ()
No symbol table info available.
#30 0xb5521244 in ?? ()
No symbol table info available.
#31 0xb5521344 in ?? ()
No symbol table info available.
#32 0x00000006 in ?? ()
No symbol table info available.
#33 0xb5521244 in ?? ()
No symbol table info available.
#34 0xb6ae88f4 in ?? ()
No symbol table info available.
#35 0x08502410 in ?? ()
No symbol table info available.
#36 0xb6ea9ff4 in ?? () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#37 0x00000006 in ?? ()
No symbol table info available.
#38 0x085069c0 in ?? ()
No symbol table info available.
#39 0x00000000 in ?? ()
No symbol table info available.

Thread 1 (Thread -1228564816 (LWP 13857)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb718534b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7b9b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb78e5ee5 in gtk_tree_model_get_valist ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0xb78e60dd in gtk_tree_model_get () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0x08059cb2 in ?? ()
No symbol table info available.
#7  0x080d34d0 in ?? ()
No symbol table info available.
#8  0xbfd7ee48 in ?? ()
No symbol table info available.
#9  0x00000002 in ?? ()
No symbol table info available.
#10 0xbfd7ee58 in ?? ()
No symbol table info available.
#11 0xffffffff in ?? ()
No symbol table info available.
#12 0x084bd800 in ?? ()
No symbol table info available.
#13 0x084bd9a8 in ?? ()
No symbol table info available.
#14 0xb71781e4 in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0x084bd9a8 in ?? ()
No symbol table info available.
#16 0xbfd7eecc in ?? ()
No symbol table info available.
#17 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by aysiu on 2007-05-08
I [searched for your error message](http://www.google.com/search?hl=en&q=%22No+symbol+table+info+available.%22+grip&btnG=Google+Search) but couldn't find anything helpful.

The best thing at this point might be to file a bug report:
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

