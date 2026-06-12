---
title: "Installing Ardour2"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by Rocket Boy on 2006-12-05
I tried my best to follow the directions at [www.ardour.org/building](www.ardour.org/building)... but I obviously don't understand something because this is what I get:

scons: Reading SConscript files ...
Package lrdf was not found in the pkg-config search path.
Perhaps you should add the directory containing `lrdf.pc'
to the PKG_CONFIG_PATH environment variable
No package 'lrdf' found
Package samplerate was not found in the pkg-config search path.
Perhaps you should add the directory containing `samplerate.pc'
to the PKG_CONFIG_PATH environment variable
No package 'samplerate' found
Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found
Package gobject-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gobject-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gobject-2.0' found
Package gmodule-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gmodule-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gmodule-2.0' found
Package gthread-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gthread-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gthread-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package pango was not found in the pkg-config search path.
Perhaps you should add the directory containing `pango.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pango' found
Package libgnomecanvas-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libgnomecanvas-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libgnomecanvas-2.0' found
Checking for usb_interrupt_write() in C library usb... no
Checking for FLAC__stream_decoder_new() in C++ library FLAC... no
Checking for C++ header file boost/shared_ptr.hpp... yes
Checking for lo_server_new() in C library lo... no
liblo does not appear to be installed.

---

### Post by Rocket Boy on 2006-12-06
bump

---

### Post by [S|G] on 2006-12-13
>  liblo does not appear to be installed.

Seems you're missing a dependency...  you could try to install liblo0-dev

---

