---
title: "banshee crashes when I try to play any playlist."
date: 2010-07-08
forum: Multimedia Software
---

### Post by yonik on 2010-07-08
```
yonatan@yonatan-laptop:~$ banshee
[Info  21:51:42.086] Running Banshee 1.7.1: [Ubuntu 10.04 LTS 53f5b4c (linux-gnu, i486) @ 2010-06-21 16:16:42 UTC]
[Info  21:51:53.261] [Streamrecorder.Gst.Marshaller] gstreamer version found: GStreamer 0.10.28

** (Banshee:7662): WARNING **: Missing method Combine in assembly /usr/lib/banshee-1/Extensions/Banshee.Mirage.dll, type Banshee.Base.Paths

** (Banshee:7662): WARNING **: The class Banshee.Base.Paths could not be loaded, used in Banshee.Mirage
[Warn  21:51:53.317] Caught an exception - System.TypeLoadException: Could not load type 'Banshee.Base.Paths' from assembly 'Banshee.Mirage'. (in `Banshee.Mirage')
  at Banshee.Mirage.MiragePlugin.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  21:51:53.328] Extension `Banshee.Mirage.MiragePlugin' not started: Could not load type 'Banshee.Base.Paths' from assembly 'Banshee.Mirage'.

** (Banshee:7662): WARNING **: Missing method Combine in assembly /usr/lib/banshee-1/Extensions/Banshee.Mirage.dll, type Banshee.Base.Paths

** (Banshee:7662): WARNING **: The class Banshee.Base.Paths could not be loaded, used in Banshee.Mirage
[Warn  21:51:53.330] Caught an exception - System.TypeLoadException: Could not load type 'Banshee.Base.Paths' from assembly 'Banshee.Mirage'. (in `Banshee.Mirage')
  at Banshee.Mirage.MiragePlugin.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] 
[Warn  21:51:53.330] Extension `Banshee.Mirage.MiragePlugin' not started: Could not load type 'Banshee.Base.Paths' from assembly 'Banshee.Mirage'.
[Info  21:51:53.333] All services are started 10.051315
[Info  21:51:56.685] nereid Client Started
[Warn  21:51:58.462] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
Marshaling row_activated signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.ArgumentException: MIRAGE_DISTANCE
Parameter name: HYENA_BINARY_FUNCTION name (arg 0)
at Hyena.Data.Sqlite.BinaryFunction.Invoke (object[]) <0x000e5>
at Mono.Data.Sqlite.SqliteFunction.ScalarCallback (intptr,int,intptr) <0x00028>
at (wrapper native-to-managed) Mono.Data.Sqlite.SqliteFunction.ScalarCallback (intptr,int,intptr) <0x0004b>
at (wrapper managed-to-native) Mono.Data.Sqlite.UnsafeNativeMethods.sqlite3_step (intptr) <0x00004>
at Mono.Data.Sqlite.Sqlite3.Step (Mono.Data.Sqlite.SqliteStatement) <0x00033>
at Mono.Data.Sqlite.SqliteDataReader.NextResult () <0x003e6>
at Mono.Data.Sqlite.SqliteDataReader..ctor (Mono.Data.Sqlite.SqliteCommand,System.Data.CommandBehavior) <0x00050>
at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteDataReader..ctor (Mono.Data.Sqlite.SqliteCommand,System.Data.CommandBehavior) <0x00037>
at Mono.Data.Sqlite.SqliteCommand.ExecuteReader (System.Data.CommandBehavior) <0x00037>
at Mono.Data.Sqlite.SqliteCommand.ExecuteReader () <0x00012>
at (wrapper remoting-invoke-with-check) Mono.Data.Sqlite.SqliteCommand.ExecuteReader () <0x00053>
at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection,Mono.Data.Sqlite.SqliteConnection) <0x00118>

  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
   at Gtk.Widget.gtksharp_widget_base_button_press_event(IntPtr , IntPtr )
   at Gtk.Widget.OnButtonPressEvent(Gdk.EventButton evnt)
   at Banshee.Sources.Gui.SourceView.OnButtonPressEvent(Gdk.EventButton press)
   at Gtk.Widget.buttonpressevent_cb(IntPtr widget, IntPtr evnt)
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()
libmirageaudio: destroy.

** (Banshee:7662): WARNING **: Shutting down finalizer thread timed out.

```

How can I solve this problem?

---

