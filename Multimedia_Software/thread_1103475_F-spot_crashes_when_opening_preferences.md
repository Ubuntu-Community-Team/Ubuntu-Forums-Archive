---
title: "F-spot crashes when opening preferences"
date: 2009-03-22
forum: Multimedia Software
---

### Post by bruno9779 on 2009-03-22
F-spot crashes when opening preferences with the following terminal output:

f-spot
[Info  23:20:46.507] Initializing DBus
[Info  23:20:46.630] Initializing Mono.Addins
[Info  23:20:46.819] Starting new FSpot server

(f-spot:6327): Gtk-CRITICAL **: gtk_window_resize: assertion `width > 0' failed
[Info  23:20:47.885] Starting DBusService
[Info  23:20:47.892] Starting BeagleService
[Info  23:20:47.892] Hack for gnome-settings-daemon engaged

(f-spot:6327): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at FSpot.UI.Dialog.PreferenceDialog.LoadPreference (System.String key) [0x00000] 
  at FSpot.UI.Dialog.PreferenceDialog..ctor () [0x00000] 
  at FSpot.UI.Dialog.PreferenceDialog.Show () [0x00000] 
  at MainWindow.HandlePreferences (System.Object sender, System.EventArgs args) [0x00000] 
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Signal.voidObjectCallback(IntPtr handle, IntPtr data)
   at GLib.Signal.voidObjectCallback(IntPtr , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)


I have recently deleted the favorite tag, that was being used for the screensaver.

PLZ help

---

### Post by bruno9779 on 2009-03-24
bump

---

### Post by directhex on 2009-03-24
You might be better off filing a bug upstream, or checking whether they have an IRC channel

---

### Post by bruno9779 on 2009-03-24
right.

I am going to completely remove F-spot from synaptic and reinstall.

let's see if it helps

---

### Post by directhex on 2009-03-24
You're likely to have MUCH more luck erasing your user's settings and photo DB (~/.gnome2/f-spot/)

---

