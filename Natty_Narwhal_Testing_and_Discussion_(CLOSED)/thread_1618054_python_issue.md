---
title: "python issue"
date: 2010-11-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-11-10
cant load some apps today, seem to be due to gtk2, even ubuntu-bug fail to run:

/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Gtk2/Gtk2.so: undefined symbol: gtk_private_flags_get_type

bug-report 673432

---

### Post by afv on 2010-11-10
Trying to run terminator gives me this:

$ terminator 
You need to install the python bindings for gobject, gtk and pango to run Terminator.

---

### Post by dino99 on 2010-11-10
> **afv said:**
> Trying to run terminator gives me this:

$ terminator 
You need to install the python bindings for gobject, gtk and pango to run Terminator.

dont spam this thread, open yours

---

### Post by afv on 2010-11-10
> **dino99 said:**
> dont spam this thread, open yours

Hum? The thread's title was "python issues" and you wrote about python (you changed it later to gtk), that's why I posted here.

---

### Post by nperry on 2010-11-10
> **dino99 said:**
> cant load some apps today, seem to be due to gtk2, even ubuntu-bug fail to run:

/usr/bin/perl: symbol lookup error: /usr/lib/perl5/auto/Gtk2/Gtk2.so: undefined symbol: gtk_private_flags_get_type

bug-report 673432
Same seem to be having a lot of Segmentation faults.

---

### Post by dino99 on 2010-11-10
> **nperry said:**
> Same seem to be having a lot of Segmentation faults.

has been fixed (revert back) yet, waiting it in the repo to upgrade

---

### Post by colorprint on 2010-11-10
[https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/673432](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/673432)

---

