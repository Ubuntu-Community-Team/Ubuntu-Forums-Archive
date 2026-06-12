---
title: "Nero Linux"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by loyal one on 2007-02-15
Why are we prevented from downloading Nero Linux in the USA ? Is there a work around for this problem ? Thanks to all for your help.
Loyal01:guitar:

---

### Post by Belyel on 2007-02-15
I definitely am able to download nero linux in the US from the nero website.  It's a debian package, easy to install in Ubuntu.  It's probably not in the repositories because it's not free or open.  It costs $19.99 for a license if you wish to buy it from Nero.

---

### Post by r4ik on 2007-02-15
Why not use K3b it is in Synaptic.
Does the same maybe more..

Good luck !

---

### Post by loyal one on 2007-02-16
Thanks for the responses. I forgot about K3B, I will install it again as I like it. As for the Nero download, when I try to purchase ( is that a dirty word ? ) it, I am directed to a page that requires me to indicate my country for d/l. When I enter USA, then go to purchase, a pop up informs me that the software cannot be ported to the good 'ol yooessay. This happens no matter where I go to get the software --  I am directed to a Nero page that prevents a download. 
Loyal:( :( :( :guitar:

---

### Post by taurus on 2007-02-16
I didn't have problem trying to purchase it (download it)!  Went through all the way up to step where it asked me for a credit card number.

---

### Post by yabbadabbadont on 2007-02-16
Just as an FYI, if you already have a Windows license key for Nero, you can use it with NeroLinux too.

---

### Post by Shay Stephens on 2007-02-16
I was using nerolinux for a while.  I switched to K3b and have never been sorry about it.  It takes a little bit of getting used to, but I get all the functionality I need out of it including data verification (which can't be said for gnomebaker currently).

Plus nerolinux looks horrible (GTK1?)

---

### Post by yabbadabbadont on 2007-02-16
I use nero because it always works while cdrecord, which is used as a backend by almost all of the OSS graphical burn programs, fails between 40 to 60 percent of the time.  (depending on which of my two burners I use)  As long as it works, I don't care what it looks like.  (nero does burn verification too)

---

### Post by Shay Stephens on 2007-02-16
> **yabbadabbadont said:**
> I use nero because it always works while cdrecord, which is used as a backend by almost all of the OSS graphical burn programs, fails between 40 to 60 percent of the time.  (depending on which of my two burners I use)  As long as it works, I don't care what it looks like.  (nero does burn verification too)

I wonder if the failures could be hardware related?  I have been having better success with K3b than I did with nerolinux.  Hmm, something to ponder.  I do know if K3b were to stop working for me, my fall back program would be nerolinux.  Until gnomebaker decides to grace us with data verification (how hard could it be?), I can't use it (but I wish I could).

---

### Post by yabbadabbadont on 2007-02-16
> **Shay Stephens said:**
> I wonder if the failures could be hardware related?  I have been having better success with K3b than I did with nerolinux.  Hmm, something to ponder.  I do know if K3b were to stop working for me, my fall back program would be nerolinux.  Until gnomebaker decides to grace us with data verification (how hard could it be?), I can't use it (but I wish I could).

It's not the hardware.  (at least it isn't in my case)  It's the newer versions of cdrecord.  Older versions of cdrecord used to work fine and growisofs still works fine for burning dvds.

---

### Post by dasunst3r on 2007-02-16
I'd say that you just shouldn't even waste your time and money.  K3b gets the job done.

So go forth, pocket your $19.99, and spend it on something else (or donate it to Ubuntu development)

---

### Post by F-3582 on 2007-02-17
I just installed NeroLinux. Works pretty well, from what I can say. The only problem is - it totally wrecked apt and my Gnome Main Menu. Apt can't find its data no more:

```
E: The package nerolinux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

This disables me from doing anything with it.

The Gnome Menu crashes everytime I click it:

```
Memory status: size: 61173760 vsize: 0 resident: 61173760 share: 0 rss: 17199104 rss_rlim: 0
CPU usage: start_time: 1171700954 rtime: 0 utime: 339 stime: 0 cutime:300 cstime: 0 timeout: 39 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

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
[Thread debugging using libthread_db enabled]
[New Thread -1225619792 (LWP 5465)]
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
#1  0xb75df323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ed71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74c7770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74c8ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76e3122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76e3159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76e31d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b32d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b32dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b2e591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb76d8aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76da802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76dd7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76ddb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7adc574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225619792 (LWP 5465)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75df323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ed71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74c7770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74c8ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76e3122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76e3159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76e31d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b32d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b32dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b2e591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb76d8aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76da802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76dd7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76ddb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7adc574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

It all started with a Postinst error during Nerolinux installation... First, I thought that it hadn't installed at all and tried to remove it. After this failed, I did the fatal thing: I flushed the cache. That's where I'm standing, now.

Any suggestions?

---

### Post by CodyJarrett on 2007-02-17
This command finally got rid of the cursed thing for me:
```
sudo dpkg --remove --force-depends --force-remove-reinstreq nerolinux
```

you might need to remove all files beginning with nerolinux from the /var/lib/dpkg/info/ folder.

Hope this helps.

---

### Post by F-3582 on 2007-02-17
Didn't work. However, I tried to get an older package (2.1.0.3) and it magically repaired everything. Thanks anyway.

---

### Post by loyal one on 2007-02-17
[QUOTE=yabbadabbadont;2168075]Just as an FYI, if you already have a Windows license key for Nero, you can use it with NeroLinux too.

Thanks for this hint, I do have this app in windows, but I still have the download matter to overcome. I really don't have a clue what is going on with this issue, I have never encountered it before. I suspect that it has something to do with a DRM agreement -- or ???

I would like to try Nero Linux, but I am no great fan of Nero in general. In fact, I am well on the way to dumping windows for good. I have been trying various Linux distros for several years, and since discovering Ubuntu, I have found a new operating system. This forum has been invaluable to me as I work with Ubuntu: I have crashed and re-installed it at least 6 times. This incarnation seems to be right and stable.

I installed K3B, and it seemed to work as planned: the only missing program was audio normalizer, which I don't use very much anyway. This is a great forum.
Loyal

---

### Post by yabbadabbadont on 2007-02-17
I'm not sure if you mean that you can't download the software or that the website won't let you purchase a license...  Anyway, there appears to be a new version out.  2.1.0.4 was released on the 15th.  You can get the deb file here: [http://ftp5.use.nero.com/software/NeroLINUX/nerolinux-2.1.0.4-x86.deb](http://ftp5.use.nero.com/software/NeroLINUX/nerolinux-2.1.0.4-x86.deb)

---

### Post by Shay Stephens on 2007-02-17
> I installed K3B, and it seemed to work as planned: the only missing program was audio normalizer, which I don't use very much anyway. This is a great forum.
Loyal

Install audacity.  It has a normalize filter.  I use audacity for all my audio editing needs.

---

### Post by yabbadabbadont on 2007-02-17
> **Shay Stephens said:**
> Install audacity.  It has a normalize filter.  I use audacity for all my audio editing needs.

You need to edit your quote.  It was "loyal one" who made the comment you quoted, not me.  :D  (He had a broken quote of something I said in his post)

---

