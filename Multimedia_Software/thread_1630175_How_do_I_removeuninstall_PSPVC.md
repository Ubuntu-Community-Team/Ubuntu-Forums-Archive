---
title: "How do I remove/uninstall PSPVC?"
date: 2010-11-24
forum: Multimedia Software
---

### Post by searchesend on 2010-11-24
I can't seem to uninstall PSPVC. I can run the program by typing 'pspvc' into the terminal but typing 'sudo apt-get remove pspvc' yields unknown package?

```
matt@searchesend:~$ pspvc
http://pspvc.sourceforge.net

(pspvc:14723): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(pspvc:14723): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
matt@searchesend:~$ sudo apt-get remove pspvc
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package pspvc
matt@searchesend:~$
```

---

### Post by CajunPirate on 2011-04-01
Open Terminal and navigate to the directory it is installed in.
```
mark@Jeeves:~$ cd /usr/local/bin
mark@Jeeves:~$ sudo rm pspvc
```
Voila!

---

