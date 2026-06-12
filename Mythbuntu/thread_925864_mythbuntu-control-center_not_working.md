---
title: "mythbuntu-control-center not working"
date: 2008-09-21
forum: Mythbuntu
---

### Post by TheConsultant on 2008-09-21
Hi.

My mythbuntu-control-centre is not working. I have applied the latest bug fixes from the weekly builds.

I have tested the command with:
[FONT="Times New Roman"]sudo /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre[/FONT]

The output is as follows:

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut
Reading state information... Fertig
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

What is going wrong?

Regards

Martin

---

