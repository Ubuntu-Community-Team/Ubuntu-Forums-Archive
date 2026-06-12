---
title: "Conky from source with xmms2"
date: 2010-06-17
forum: Multimedia Software
---

### Post by greggc2006 on 2010-06-17
I have been having a play with conky and have hit another hurdle I can't jump. I would like to monitor xmms2 with it and decided un-install the package in synaptic and follow the guide here:-

[http://ubuntuforums.org/showthread.php?t=706736](http://ubuntuforums.org/showthread.php?t=706736)

All went well until I ran '$ make' , I got:-
```
gregg@burt:~/conky-1.4.9$ make
Making all in src
make[1]: Entering directory `/home/gregg/conky-1.4.9/src'
make  all-am
make[2]: Entering directory `/home/gregg/conky-1.4.9/src'
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT common.o -MD -MP -MF .deps/common.Tpo -c -o common.o common.c
mv -f .deps/common.Tpo .deps/common.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT conky.o -MD -MP -MF .deps/conky.Tpo -c -o conky.o conky.c
mv -f .deps/conky.Tpo .deps/conky.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT fs.o -MD -MP -MF .deps/fs.Tpo -c -o fs.o fs.c
mv -f .deps/fs.Tpo .deps/fs.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT hddtemp.o -MD -MP -MF .deps/hddtemp.Tpo -c -o hddtemp.o hddtemp.c
mv -f .deps/hddtemp.Tpo .deps/hddtemp.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT linux.o -MD -MP -MF .deps/linux.Tpo -c -o linux.o linux.c
mv -f .deps/linux.Tpo .deps/linux.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT top.o -MD -MP -MF .deps/top.Tpo -c -o top.o top.c
mv -f .deps/top.Tpo .deps/top.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT mail.o -MD -MP -MF .deps/mail.Tpo -c -o mail.o mail.c
mv -f .deps/mail.Tpo .deps/mail.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT mixer.o -MD -MP -MF .deps/mixer.Tpo -c -o mixer.o mixer.c
mv -f .deps/mixer.Tpo .deps/mixer.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT libtcp-portmon.o -MD -MP -MF .deps/libtcp-portmon.Tpo -c -o libtcp-portmon.o libtcp-portmon.c
mv -f .deps/libtcp-portmon.Tpo .deps/libtcp-portmon.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT timed_thread.o -MD -MP -MF .deps/timed_thread.Tpo -c -o timed_thread.o timed_thread.c
mv -f .deps/timed_thread.Tpo .deps/timed_thread.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT mboxscan.o -MD -MP -MF .deps/mboxscan.Tpo -c -o mboxscan.o mboxscan.c
mv -f .deps/mboxscan.Tpo .deps/mboxscan.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT x11.o -MD -MP -MF .deps/x11.Tpo -c -o x11.o x11.c
mv -f .deps/x11.Tpo .deps/x11.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/local/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT xmms2.o -MD -MP -MF .deps/xmms2.Tpo -c -o xmms2.o xmms2.c
xmms2.c: In function ‘handle_curent_id’:
xmms2.c:127: warning: implicit declaration of function ‘xmmsc_result_get_uint’
xmms2.c:138: warning: implicit declaration of function ‘xmmsc_result_get_dict_entry_string’
xmms2.c:211: warning: implicit declaration of function ‘xmmsc_result_get_dict_entry_int’
xmms2.c: In function ‘handle_playtime’:
xmms2.c:238: warning: implicit declaration of function ‘xmmsc_result_restart’
xmms2.c:238: warning: assignment makes pointer from integer without a cast
xmms2.c: In function ‘update_xmms2’:
xmms2.c:319: warning: passing argument 2 of ‘xmmsc_result_notifier_set_full’ from incompatible pointer type
/usr/include/xmms2/xmmsclient/xmmsclient.h:348: note: expected ‘xmmsc_result_notifier_t’ but argument is of type ‘void (*)(struct xmmsc_result_t *, void *)’
xmms2.c:320: warning: passing argument 2 of ‘xmmsc_result_notifier_set_full’ from incompatible pointer type
/usr/include/xmms2/xmmsclient/xmmsclient.h:348: note: expected ‘xmmsc_result_notifier_t’ but argument is of type ‘void (*)(struct xmmsc_result_t *, void *)’
xmms2.c:321: warning: passing argument 2 of ‘xmmsc_result_notifier_set_full’ from incompatible pointer type
/usr/include/xmms2/xmmsclient/xmmsclient.h:348: note: expected ‘xmmsc_result_notifier_t’ but argument is of type ‘void (*)(struct xmmsc_result_t *, void *)’
xmms2.c:322: warning: passing argument 2 of ‘xmmsc_result_notifier_set_full’ from incompatible pointer type
/usr/include/xmms2/xmmsclient/xmmsclient.h:348: note: expected ‘xmmsc_result_notifier_t’ but argument is of type ‘void (*)(struct xmmsc_result_t *, void *)’
mv -f .deps/xmms2.Tpo .deps/xmms2.Po
/bin/bash ../libtool --tag=CC   --mode=link gcc  -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -lpthread -lm -Wl,-O1 -o conky   common.o conky.o  fs.o hddtemp.o linux.o top.o mail.o mixer.o   libtcp-portmon.o  timed_thread.o mboxscan.o x11.o xmms2.o  -lrt  -lxmmsclient    -lX11   -lXext   -lXdamage -lXfixes   -lXft   -lglib-2.0  
mkdir .libs
gcc -I/usr/include/xmms2 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -W -Wl,-O1 -o conky common.o conky.o fs.o hddtemp.o linux.o top.o mail.o mixer.o libtcp-portmon.o timed_thread.o mboxscan.o x11.o xmms2.o  -lpthread -lm -lrt -lxmmsclient -lX11 -lXext -lXdamage -lXfixes -lXft /usr/lib/libglib-2.0.so  
xmms2.o: In function `handle_curent_id':
xmms2.c:(.text+0x310): undefined reference to `xmmsc_result_get_uint'
xmms2.c:(.text+0x371): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x3d8): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x43f): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x4a6): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x50d): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.o:xmms2.c:(.text+0x574): more undefined references to `xmmsc_result_get_dict_entry_string' follow
xmms2.o: In function `handle_curent_id':
xmms2.c:(.text+0x710): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.c:(.text+0x736): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.c:(.text+0x75c): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.c:(.text+0x795): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.o: In function `handle_playtime':
xmms2.c:(.text+0x7f1): undefined reference to `xmmsc_result_get_uint'
xmms2.c:(.text+0x800): undefined reference to `xmmsc_result_restart'
xmms2.o: In function `handle_playback_state_change':
xmms2.c:(.text+0x88f): undefined reference to `xmmsc_result_get_uint'
xmms2.o: In function `update_xmms2':
xmms2.c:(.text+0xc22): undefined reference to `xmmsc_result_get_uint'
collect2: ld returned 1 exit status
make[2]: *** [conky] Error 1
make[2]: Leaving directory `/home/gregg/conky-1.4.9/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/gregg/conky-1.4.9/src'
make: *** [all-recursive] Error 1
gregg@burt:~/conky-1.4.9$ make install
Making install in src
make[1]: Entering directory `/home/gregg/conky-1.4.9/src'
/bin/bash ../libtool --tag=CC   --mode=link gcc  -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -lpthread -lm -Wl,-O1 -o conky   common.o conky.o  fs.o hddtemp.o linux.o top.o mail.o mixer.o   libtcp-portmon.o  timed_thread.o mboxscan.o x11.o xmms2.o  -lrt  -lxmmsclient    -lX11   -lXext   -lXdamage -lXfixes   -lXft   -lglib-2.0  
gcc -I/usr/include/xmms2 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -Wall -W -Wl,-O1 -o conky common.o conky.o fs.o hddtemp.o linux.o top.o mail.o mixer.o libtcp-portmon.o timed_thread.o mboxscan.o x11.o xmms2.o  -lpthread -lm -lrt -lxmmsclient -lX11 -lXext -lXdamage -lXfixes -lXft /usr/lib/libglib-2.0.so  
xmms2.o: In function `handle_curent_id':
xmms2.c:(.text+0x310): undefined reference to `xmmsc_result_get_uint'
xmms2.c:(.text+0x371): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x3d8): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x43f): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x4a6): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.c:(.text+0x50d): undefined reference to `xmmsc_result_get_dict_entry_string'
xmms2.o:xmms2.c:(.text+0x574): more undefined references to `xmmsc_result_get_dict_entry_string' follow
xmms2.o: In function `handle_curent_id':
xmms2.c:(.text+0x710): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.c:(.text+0x736): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.c:(.text+0x75c): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.c:(.text+0x795): undefined reference to `xmmsc_result_get_dict_entry_int'
xmms2.o: In function `handle_playtime':
xmms2.c:(.text+0x7f1): undefined reference to `xmmsc_result_get_uint'
xmms2.c:(.text+0x800): undefined reference to `xmmsc_result_restart'
xmms2.o: In function `handle_playback_state_change':
xmms2.c:(.text+0x88f): undefined reference to `xmmsc_result_get_uint'
xmms2.o: In function `update_xmms2':
xmms2.c:(.text+0xc22): undefined reference to `xmmsc_result_get_uint'
collect2: ld returned 1 exit status
make[1]: *** [conky] Error 1
make[1]: Leaving directory `/home/gregg/conky-1.4.9/src'
make: *** [install-recursive] Error 1
gregg@burt:~/conky-1.4.9$ conky
bash: /usr/bin/conky: No such file or directory

```

---

### Post by greggc2006 on 2010-06-19
Bump

Anyone got any ideas?? Is there a .deb out there with xmms2 enabled????

---

### Post by greggc2006 on 2010-06-23
Anyone???

---

### Post by greggc2006 on 2010-06-29
Did I ask a bad question?

---

