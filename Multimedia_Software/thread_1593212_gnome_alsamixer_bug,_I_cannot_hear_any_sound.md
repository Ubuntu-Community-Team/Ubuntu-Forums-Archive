---
title: "gnome alsamixer bug, I cannot hear any sound"
date: 2010-10-11
forum: Multimedia Software
---

### Post by hihihi100 on 2010-10-11
Hi there:

I have been dragging a sound problem for a month or so, this problem did not appear only after upgrading to 10.10 meerkat. Every time I try to open alsamixer, it shuts. Hopefuly, it gives me the option of getting a txt file with the bug information in it. Is it as follows:

```
System: Linux 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10900000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Ambiance
Icon Theme: ubuntu-mono-dark
GTK+ Modules: gnomesegvhandler, canberra-gtk-module

Memory status: size: 89907200 vsize: 89907200 resident: 14454784 share: 11456512 rss: 14454784 rss_rlim: 18446744073709551615
CPU usage: start_time: 1286804166 rtime: 21 utime: 18 stime: 3 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100



---- Critical and fatal warnings logged during execution ----

** GLib-GObject **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed 


----------- .xsession-errors ---------------------
(nautilus:1991): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gnome-alsamixer:4542): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (x-session-manager:1857): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
ptrace: Operation not permitted.
/home/hihihi100/4542: No such file or directory.
No stack.
--------------------------------------------------
```

any tips will be greatly appreciated

---

