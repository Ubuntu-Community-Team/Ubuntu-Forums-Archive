---
title: "install myth after installer"
date: 2008-12-18
forum: Mythbuntu
---

### Post by bartvh on 2008-12-18
I installed MythBuntu using the Alternate Install CD (because I needed software RAID). Unfortunately, I didn't select a frontend and backend when it asked me which software to install (I did install OpenSSH and Samba).

Now all I have is a text terminal. How do I "finish" the installation process? I want to run both the front- and back-end on the same server.

Thanks

---

### Post by clw3388 on 2008-12-18
Not a big mythbuntu user but try 
sudo apt-get install mythbuntu-desktop
assuming you have a proper sources list and an internet connection?

---

### Post by clw3388 on 2008-12-18
or you can try to do a contro alt f7..
or sudo startx... as gui may be there but not started...

---

### Post by bartvh on 2008-12-18
I've installed mythbuntu-control-centre (boy did it get a looot of packages) and rebooted, but I still get text.
I've tried startx (after installing initx) but that tells me that X11 was not found.

Ctrl-Alt-F7 does nothing. What's it supposed to do?

Oh yeah, if I run mythbuntu-control-centre (both through ssh and on the actual machine) I get:
```
mythbuntu-control-centre
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Reading package lists... Done
Building dependency tree
Reading state information... Done
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:175: Warning: invalid (NULL) pointer instance
  self.glade = gtk.glade.XML(GLADEDIR + '/' + 'mythbuntu_control_centre.glade')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:175: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  self.glade = gtk.glade.XML(GLADEDIR + '/' + 'mythbuntu_control_centre.glade')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:175: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.glade = gtk.glade.XML(GLADEDIR + '/' + 'mythbuntu_control_centre.glade')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:175: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  self.glade = gtk.glade.XML(GLADEDIR + '/' + 'mythbuntu_control_centre.glade')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:175: Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
  self.glade = gtk.glade.XML(GLADEDIR + '/' + 'mythbuntu_control_centre.glade')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: Warning: invalid (NULL) pointer instance
  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: GtkWarning: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: GtkWarning: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:110: GtkWarning: Invalid icon size 1

  gladexml = gtk.glade.XML(gladefile, name, 'mythbuntu-control-centre')
Segmentation fault

```
A segfault must mean something is wrong.

Would it be easier to just rerun the installer?

---

