---
title: "Network manager icon"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by ybbon1 on 2011-06-13
I have been using a Three [dongle]("http://en.wikipedia.org/wiki/Software_protection_dongle") for several months without a problem until the other day, there was no [network manager]("http://en.wikipedia.org/wiki/NetworkManager")  icon on the top task bar, so I re-booted and all was fine. After  booting up yesterday, again, it was missing, after several re-boots it  still remained missing, so I moved the [dongle]("http://en.wikipedia.org/wiki/Software_protection_dongle")  to another usb port and re-booted and I was connected, after booting up  today again it was missing, after several re-boots and moving the dongle it was still missing, going to control centre, start up applications, and clicking on [network manager]("http://en.wikipedia.org/wiki/NetworkManager"),edit,  the command line shows "nm-applet -sm-disable" I opened a terminal and  entered  nm-applet -sm-enable and the connection icon appeared and I was  connected this is what appeared in the command  line:-
ibloo@ibloo-U-100:~$ nm-applet sm-enable 
** (nm-applet:3354): DEBUG: old state indicates that this was not a disconnect 0 
** (nm-applet:3354): DEBUG: old state indicates that this was not a disconnect 0 
** (nm-applet:3354): DEBUG: foo_client_state_changed_cb 

** (nm-applet:3354): WARNING **: handle_property_changed: property  'ip-interface' changed but wasn't defined by object type NMGsmDevice. 
** (nm-applet:3354): DEBUG: foo_client_state_changed_cb 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 

(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 

(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 

(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 

(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 

(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 
(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 

(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

(nm-applet:3354): Gtk-CRITICAL **: IA__gtk_image_get_storage_type: assertion `GTK_IS_IMAGE (image)' failed 

(nm-applet:3354): GLib-GObject-WARNING **: invalid (NULL) pointer instance 

(nm-applet:3354): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed 

When I closed the [terminal window]("http://en.wikipedia.org/wiki/Terminal_emulator") the connection icon disappeared.
Can somebody tell me what to do to cure this bug.

I tried changing the command in the start up applications to read enable but it made no difference.

Many thanks.

---

