---
title: "Can't use my Syntek webcam"
date: 2012-12-16
forum: Multimedia Software
---

### Post by Exhack on 2012-12-16
Hi,
I recently installed Ubuntu 12.04 onmy Asus A7C laptop. I tried to Hangout with my son on Google+ but there were no pix. Seems my Syntek webcam isn't recognised. After reading a few posts, I ran the lsusb and gstreamer-properties commands in my Terminal and this is what I got:


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 002 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
david@david-A7C:~$ gstreamer-properties

(gstreamer-properties:8238): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:8238): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

(gstreamer-properties:8238): GLib-GObject-WARNING **: invalid cast from `GtkBuilder' to `GtkWidget'

(gstreamer-properties:8238): Gtk-CRITICAL **: gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

I also installed Cheese. But it does not seem to like my setup.

How should I proceed from here?

---

