---
title: "problems  with  brasero"
date: 2008-11-25
forum: Multimedia Software
---

### Post by balki2005 on 2008-11-25
Hello,

I have  allways problem  to  use  brasero,  when  I start it, and  select  a  directory it desapear.this is the  error:

```
jonay@thunderdragon:~$ brasero 

(brasero:8561): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GstElement'

(brasero:8561): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(brasero:8561): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(brasero:8561): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(brasero:8561): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Segmentation fault
jonay@thunderdragon:~$ 

```

can somebody  help me, i even reinstall ubuntu  and  without success :(

some system  info:
ubuntu 8.10
2GB RAM
3.2 MHz HT
256Mb RAM Videocard


thanks in advance,

Balki2005

---

### Post by djbushido on 2008-11-25
Stupid question, but what is the directory name? I.e., it might contain an invalid character. Also, try using another utility like k3b to see if the same problem occurs.

---

### Post by balki2005 on 2008-11-25
hello,

thanks  for the  answer  but that is  not the  problem I think. because I have also  a laptop  with  the  same version of  ubuntu 8.10. and there I can burn  my cd  without  problem ?

greets,

Balki2005

---

