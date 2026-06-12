---
title: "skype segfaults while trying to enable webcam"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by theanswriz42 on 2011-04-03
Every time I open up skype, do the test for the webcam, the app segfaults. Is anyone experiencing similar issues?

---

### Post by cariboo on 2011-04-03
Can you provide us with some sort of log output?

---

### Post by theanswriz42 on 2011-04-03
The only output I'm really getting is 

```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3108): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3108): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3108): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3108): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:3108): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3108): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3108): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:3108): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:3108): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:3108): Gtk-WARNING **: Loading IM context type 'ibus' failed

``` 

When I run it from the command line, though I don't get any sort of message in /var/log/messages or dmesg specific to this issue.

```
ii  skype                                          2.1.0.81-1ubuntu5                                 VOIP and instant messaging client
```

---

### Post by rajeev1204 on 2011-04-04
Yes 64 bit ubuntu.

Try to start skype with the line LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype and your webcam should work now.

---

