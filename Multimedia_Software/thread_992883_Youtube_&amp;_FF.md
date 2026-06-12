---
title: "Youtube &amp; FF"
date: 2008-11-25
forum: Multimedia Software
---

### Post by zkab on 2008-11-25
I have Ubuntu 8.10 amd64 and Firefox 3.04.
When watching video at youtube I receive following errors:


(npviewer.bin:9895): Gdk-WARNING **: GdkWindow 0x4c00021 unexpectedly destroyed

(npviewer.bin:9895): Gdk-WARNING **: GdkWindow 0x4c00020 unexpectedly destroyed

(npviewer.bin:9895): Gdk-WARNING **: GdkWindow 0x4c0001f unexpectedly destroyed

(npviewer.bin:9895): Gdk-WARNING **: GdkWindow 0x4c00003 unexpectedly destroyed

(npviewer.bin:9895): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 243 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() invoke: Connection closed

(firefox:9835): GLib-CRITICAL **: g_hash_table_remove_internal: assertion `hash_table != NULL' failed
*** NSPlugin Wrapper *** ERROR: NPObject 0x26330e0 is not valid!

(npviewer.bin:9911): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:9926): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:9926): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

What is wrong ???

---

### Post by djbushido on 2008-11-25
So this happened watching videos on youtube? did you try going fullscreen, and then this happened? can you watch other videos, like from google, non/fullscreen?

---

### Post by zkab on 2008-11-25
I have no problems watching videos at youtube - both normal size & fullscreen but the error indicates that something is wrong or ...

---

