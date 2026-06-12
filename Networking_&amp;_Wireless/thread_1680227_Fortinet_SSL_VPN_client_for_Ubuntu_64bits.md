---
title: "Fortinet SSL VPN client for Ubuntu 64bits"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by java.artisan on 2011-02-02
Does anyone in here use the Fortinet SSL VPN client on 64 bits Ubuntu ?

A number of threads mention this client works, but I suspect it's only for 32 bits distro's. 

The 4.0.2010 release works on windows. The same release however doesn't work on my 64 bits Xubuntu 10.10 - Using the very same settings and certificate.

---

### Post by crabbyC on 2012-03-10
anyone have an answer on this?  There's another thread that points to the forticlient support website for a download, but I can't seem to navigate the site.

---

### Post by clemare on 2012-05-14
I have the same problem here. Ubuntu 12.04 64bits and when I try to start the application, it starts but can't stablish the tunnel.

The console shows this:

```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64
(forticlientsslvpn:4053): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64
(forticlientsslvpn:4053): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64
(forticlientsslvpn:4053): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so
```I don't know how to make the program to search for 32 bits version of libreries... or how to install them.

clemare

---

