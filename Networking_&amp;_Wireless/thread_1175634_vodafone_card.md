---
title: "vodafone card"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by maurox on 2009-06-01
hi all,
I've just installed ubuntu 9.04 on my mini-laptop and I'd like to use it with my vodafone ( usb)UMTS card.

I've installed usb-modeswitch_0.9.7_i386.deb and  vodafone-mobile-connect_2.00.00-1_all.deb, but this application doesn't work.
These are the errors :

$ vodafone-mobile-connect-card-driver-for-linux-debug 
Traceback (most recent call last):
  File "/usr/bin/upgrade-vmc-plugins", line 23, in <module>
    from vmc.common import plugin
ImportError: No module named vmc.common
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 694, in run
    runApp(config)
  File "/usr/lib/python2.6/dist-packages/twisted/scripts/twistd.py", line 23, in runApp
    _SomeApplicationRunner(config).run()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 411, in run
    self.application = self.createOrGetApplication()
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 494, in createOrGetApplication
    application = getApplication(self.config, passphrase)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/application/app.py", line 505, in getApplication
    application = service.loadApplication(filename, style, passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/application/service.py", line 390, in loadApplication
    application = sob.loadValueFromFile(filename, 'application', passphrase)
  File "/usr/lib/python2.6/dist-packages/twisted/persisted/sob.py", line 215, in loadValueFromFile
    exec fileObj in d, d
  File "/usr/share/vodafone-mobile-connect/gtk-tap.py", line 34, in <module>
    from vmc.common.startup import create_skeleton_and_do_initial_setup
exceptions.ImportError: No module named vmc.common.startup

Failed to load application: No module named vmc.common.startup

Strange errors :( ...any ideas ?
thanks in advance ,
Maurox

---

### Post by b-boy on 2009-06-03
I Had the same problem but I down loaded  this version [https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb](https://forge.betavine.net/frs/download.php/503/vodafone-mobile-connect_svn20090502_all.deb) and it worked like a charm

---

### Post by maurox on 2009-06-10
b-boy , 
I've tryed whit this sw version and now the errors are different:
 vodafone-mobile-connect-card-driver-for-linux-debug 
/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Removing stale pidfile /tmp/vmc.pid
/usr/share/vodafone-mobile-connect/vmc/contrib/epsilon/process.py:3: DeprecationWarning: the sets module is deprecated
  import os, sys, imp, sets
Efective user id: 0
2009-06-10 10:19:33+0200 [-] Log opened.
2009-06-10 10:19:33+0200 [-] twistd 8.2.0 (/usr/bin/python 2.6.2) starting up.
2009-06-10 10:19:33+0200 [-] reactor class: twisted.internet.gtk2reactor.Gtk2Reactor.
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Not running within active session)
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:59: gobject.Warning: invalid (NULL) pointer instance
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:59: gobject.Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:59: gtk.GtkWarning: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:59: gtk.GtkWarning: gdk_display_get_window_at_pointer: assertion `GDK_IS_DISPLAY (display)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:59: gtk.GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:59: gobject.Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:59: gobject.Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: gtk.GtkWarning: Screen for GtkWindow not set; you must always set
        a screen for a GtkWindow before using the window
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: gtk.GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_context_set_language: assertion `context != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_new: assertion `context != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_set_text: assertion `layout != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_set_attributes: assertion `layout != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_set_alignment: assertion `layout != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_set_width: assertion `layout != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: pango.PangoWarning: pango_layout_get_extents: assertion `layout != NULL' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: gtk.GtkWarning: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: gtk.GtkWarning: gdk_display_get_pointer: assertion `GDK_IS_DISPLAY (display)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: gtk.GtkWarning: gdk_screen_get_n_monitors: assertion `GDK_IS_SCREEN (screen)' failed
2009-06-10 10:19:33+0200 [-] /usr/share/vodafone-mobile-connect/vmc/contrib/gtkmvc/view.py:119: gtk.GtkWarning: get_monitor: assertion `GDK_IS_SCREEN (screen)' failed
/usr/bin/vodafone-mobile-connect-card-driver-for-linux-debug: line 4: 10419 Segmentation fault      twistd -r gtk2 --pidfile /tmp/vmc.pid -noy /usr/share/vodafone-mobile-connect/gtk-tap.py


:( :(

thanks ,
maurox

---

