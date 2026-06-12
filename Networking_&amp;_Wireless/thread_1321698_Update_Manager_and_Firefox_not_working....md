---
title: "Update Manager and Firefox not working..."
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by Radissthor on 2009-11-10
Hello everyone,

I had  aproblem with OOo and has to delete some packages. I fixed my problem but apparently Firefox was deleted. I realized I coudn't open the update manager. I tried installing firefox from terminal but I was only able to get SeaMonkey. I later downloaded firefox from the synapctic package manager and, apparently, it installed correctly.

But despite that, I'm still unable to run both the update manager and firefox. I was able to run updates and upgrades from the terminal, and I can open Firefox in safe mode from the terminal as well. What's surprizing is that after all the install, uninstall and install again processes, When openning firefox it still has my copnfiguration. It has my adds-on and all my tabs, organized as I had them. 

When trying to run forefoz from terminal, I get
```

hernan@Inspiron1525:~$ firefox

(process:2198): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.

(firefox:2198): Gdk-WARNING **: locale not supported by C library
terminate called after throwing an instance of 'std::runtime_error'
  what():  locale::facet::_S_create_c_locale name not valid
Aborted
hernan@Inspiron1525:~$ 

```

Any idea on what could be casuing the problem?

I'm running Ubuntu karmic Koala

---

### Post by Radissthor on 2009-11-11
It seems this is part of a Bug. When I run pppoeconf and then have to edit the file interfaces in /etc/network. I'm not abler to do this, since I get:

```
Gtk-WARNING **: Locale not supported by C library
         Using the fallback 'C' locale
```

So I cannot run 
```
gksudo gedit etc/network/interfaces 
```

and so I cannot restore wireless config. In another thread I was told to better do a fresh install. I looked for the bug in google andf I haven't found a fix yet... If anyone know a solution to thius, please comment.

---

