---
title: "Samba will not load"
date: 2012-01-09
forum: Networking &amp; Wireless
---

### Post by Robert Finley on 2012-01-09
Ubuntu 11.10

I just installed Samba (system-config-samba).  When I go to the Unity menu and select "samba" I get prompted for a password.  After I enter the password, nothing...  I tried rebooting the machine and it had no effect.

I also tried entering sudo system-config-samba in a treminal and got:

(system-config-samba:3663): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(system-config-samba:3663): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(system-config-samba:3663): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(system-config-samba:3663): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 44, in <module>
    import mainWindow
  File "/usr/share/system-config-samba/mainWindow.py", line 30, in <module>
    import gtk.glade
ImportError: No module named glade


This is all greek to me.  Can somebody help me get samba going please?
Thank you for your time.

---

### Post by Robert Finley on 2012-01-09
Went to Software Center, found "[COLOR=red]glade[/COLOR]" & "[COLOR=red]python-glade[/COLOR]" and installed both of them.

Samba fired right up.

---

