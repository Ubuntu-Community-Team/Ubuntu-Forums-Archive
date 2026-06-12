---
title: "f-spot crashes on attempting to print"
date: 2010-07-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-07-25
Like the title suggests, if I try to print a photo it instantly crashes f-spot without bringing up any kind of print dialogue.

Printing is working fine in other apps.

Filed a bug >[HERE]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/609713")< but posting here to see if anyone else is suffering the problem and if there are any know workarounds at this stage?

This is the terminal output leading up to the crash: ```
(f-spot:2851): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.EntryPointNotFoundException: f_pixbuf_from_cairo_surface
  at (wrapper managed-to-native) FSpot.PrintOperation:f_pixbuf_from_cairo_surface (intptr)
  at FSpot.PrintOperation.CreatePixbuf (Cairo.Surface s) [0x00000] in <filename unknown>:0
  at FSpot.PrintOperation.OnCustomWidgetChanged (Gtk.Widget widget) [0x00000] in <filename unknown>:0
  at FSpot.PrintOperation.OnCreateCustomWidget () [0x00000] in <filename unknown>:0
  at Gtk.PrintOperation.createcustomwidget_cb (IntPtr operation) [0x00000] in <filename unknown>:0
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.PrintOperation.createcustomwidget_cb(IntPtr operation)
   at Gtk.PrintOperation.gtk_print_operation_run(IntPtr , Int32 , IntPtr , IntPtr ByRef )
   at Gtk.PrintOperation.Run(PrintOperationAction action, Gtk.Window parent)
   at FSpot.MainWindow.HandlePrintCommand(System.Object sender, System.EventArgs e)
   at System.Reflection.MonoMethod.InternalInvoke(System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MethodBase.Invoke(System.Object obj, System.Object[] parameters)
   at System.Delegate.DynamicInvokeImpl(System.Object[] args)
   at System.MulticastDelegate.DynamicInvokeImpl(System.Object[] args)
   at System.Delegate.DynamicInvoke(System.Object[] args)
   at GLib.Signal.ClosureInvokedCB(System.Object o, GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.Invoke(GLib.ClosureInvokedArgs args)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure,  IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr  invocation_hint, IntPtr marshal_data)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at FSpot.Driver.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at FSpot.Driver.Main(System.String[] args)
```

---

