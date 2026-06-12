---
title: "Skype crashes in Ubuntu 10.10"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by gruenkohl on 2010-09-24
Hi there,

for several reasons I yesterday installed the ubuntu 10.10 beta on my lenovo x201. but now i cannot get skype (from their website: skype-ubuntu-intrepid_2.1.0.81-1_amd64) to work. When I try to send a chat message I get the last of the following terminal messages and skype crashes. I haven't found any information on the web yet. So does anyone know how to deal with this?


(<unknown>:6624): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6624): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6624): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6624): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6624): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6624): Gtk-WARNING **: Loading IM context type 'ibus' failed
me@x201:~$ skype

(<unknown>:6643): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6643): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6643): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6643): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6643): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6643): Gtk-WARNING **: Loading IM context type 'ibus' failed
Inconsistency detected by ld.so: dl-open.c: 612: _dl_open: Assertion `_dl_debug_initialize (0, args.nsid)->r_state == RT_CONSISTENT' failed!

---

### Post by Otto Nascarella on 2010-09-24
Got the same thing.

Interesting is that it was working before on maverick.
I cannot detect what it was, but I guess the last update...

---

### Post by gruenkohl on 2010-09-24
[https://bugs.launchpad.net/ubuntu/+source/skype/+bug/646862](https://bugs.launchpad.net/ubuntu/+source/skype/+bug/646862)

---

### Post by wykedengel on 2010-09-25
I am having the same problem myself. Will check out the launchpad report. Strange it worked yesterday and it started crashing after the most recent update. I am sure the situation will get straightened out. Just something a little unexpected.

---

### Post by HeatherR on 2010-09-25
After this mornings updates with 10.10 I haven't even been able to get the skype log in screen. So you got further than I did, before the updates it was working just fine.

---

### Post by Meizirkki on 2010-09-26
I'm having the same problem, and as I use skype quite a lot..

Is there any alternative clients?

---

### Post by ostlund on 2010-09-26
Seems to work after this morning packages update.

---

### Post by Elfy on 2010-09-26
moved to maverick

---

### Post by mörgæs on 2010-09-26
For those of you who still have the problem after updating the system: Did you try the solution posted in Launchpad?

---

### Post by CoolJohnB on 2010-09-26
I haven't had any problems with Skype but I installed it from synaptic rather than the Skype webpage my version is: 2.1.0.81

---

### Post by mythmgn on 2010-09-28
It happened to me as well this morning. I cannot get it started at all. It will disappear the sec I click on the icon.

---

### Post by macrules on 2010-09-28
i ran all updates about 12 hours ago, it works for me, just took a long time to login.
Maybe that helps someone.

---

