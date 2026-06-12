---
title: "External HDMI shows on login screen, but disappears after"
date: 2013-08-21
forum: Multimedia Software
---

### Post by MarshyTheKid on 2013-08-21
I tried resetting my xorg.conf by entering 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

On gnome-control-center under displays, when I try to enable the hdmi tv I get a popup saying
Failed to apply configuration: %s
GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SettingsDaemon was not provided by any .service files

Any help? Thanks!

---

### Post by MarshyTheKid on 2013-08-21
Based on somethings I just found, I tried removing gstreamer and running gnome-settings-daemon:

```
$ gnome-settings-daemon 
[1377143057,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application

(gnome-settings-daemon:14727): Gdk-ERROR **: The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 2382 error_code 8 request_code 131 minor_code 22)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap

```

---

### Post by MarshyTheKid on 2013-09-25
Any help?

---

