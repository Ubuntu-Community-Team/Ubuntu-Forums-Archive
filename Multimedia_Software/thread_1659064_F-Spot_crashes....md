---
title: "F-Spot crashes..."
date: 2011-01-03
forum: Multimedia Software
---

### Post by Howy on 2011-01-03
So, I was just importing some images to F-Spot, when it suddenly crashed. 
Now, when I try starting it, it flashes with some error that I can't read. It appears and disappears very quickly.
Here's the output from the terminal:
```
[Info  21:02:15.757] Initializing Mono.Addins
`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:20563): Gtk-WARNING **: Failed to load type module: (null)

Value is greater than Int32.MaxValue or less than Int32.MinValue
System.OverflowException: Value is greater than Int32.MaxValue or less than Int32.MinValue
  at System.Convert.ToInt32 (Int64 value) [0x00000] in <filename unknown>:0 
  at System.Int64.System.IConvertible.ToInt32 (IFormatProvider provider) [0x00000] in <filename unknown>:0 
  at System.Convert.ToType (System.Object value, System.Type conversionType, IFormatProvider provider, Boolean try_target_to_type) [0x00000] in <filename unknown>:0 
  at System.Convert.ChangeType (System.Object value, System.Type conversionType, IFormatProvider provider) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.Sqlite3.GetValue (Mono.Data.Sqlite.SqliteStatement stmt, Int32 index, Mono.Data.Sqlite.SqliteType typ) [0x00000] in <filename unknown>:0 
  at Mono.Data.Sqlite.SqliteDataReader.GetValue (Int32 i) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteArrayDataReader.ReadAllRows (Mono.Data.Sqlite.SqliteDataReader reader) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteArrayDataReader..ctor (Mono.Data.Sqlite.SqliteDataReader reader) [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Hyena.Data.Sqlite.HyenaSqliteArrayDataReader:.ctor (Mono.Data.Sqlite.SqliteDataReader)
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.Sqlite.SqliteConnection connection) [0x00000] in <filename unknown>:0 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: Argument is out of range.
Parameter name: Parameters describe an unrepresentable DateTime.
  at System.DateTime..ctor (Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond) [0x00000] in <filename unknown>:0 
  at System.DateTime..ctor (Int32 year, Int32 month, Int32 day) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndexAscending (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndex (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.TickLabel (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.GroupSelector.HandleAdaptorChanged (FSpot.GroupAdaptor adaptor) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) FSpot.GroupAdaptor/ChangedHandler:invoke_void__this___GroupAdaptor (FSpot.GroupAdaptor)
  at FSpot.TimeAdaptor+<DoReload>c__AnonStorey19.<>m__6B () [0x00000] in <filename unknown>:0 
  at FSpot.Driver+<RunIdle>c__AnonStorey11.<>m__50 () [0x00000] in <filename unknown>:0 
  at GLib.Idle+IdleProxy.Handler () [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Dialog.gtk_dialog_run(IntPtr )
   at Gtk.Dialog.Run()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at FSpot.Driver.Main(System.String[] args)

```
Is F-Spot screwed forever, or is it possible to save it from replacement? (I like the GUI...)
Oh, and, don't worry about menu_proxy_module_load, it appears for many apps when I start them in terminal.

---

### Post by no2498 on 2011-01-03
did you do a upgrade
not a clean install
if yes the repositories is not set rite
so it can not get updates for the ubuntu you use now

---

### Post by Howy on 2011-01-03
Ok, so i added the PPA for F-Spot, and well... not much of a change.
This is the terminal output:
```
[Info  22:31:59.028] Initializing Mono.Addins
`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': f-spot: undefined symbol: menu_proxy_module_load

(f-spot:7969): Gtk-WARNING **: Failed to load type module: (null)


(f-spot:7969): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentOutOfRangeException: Argument is out of range.
Parameter name: Parameters describe an unrepresentable DateTime.
  at System.DateTime..ctor (Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond) [0x00000] in <filename unknown>:0 
  at System.DateTime..ctor (Int32 year, Int32 month, Int32 day) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndexAscending (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.DateFromIndex (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.TimeAdaptor.TickLabel (Int32 item) [0x00000] in <filename unknown>:0 
  at FSpot.GroupSelector.HandleAdaptorChanged (FSpot.GroupAdaptor adaptor) [0x00000] in <filename unknown>:0 
  at (wrapper delegate-invoke) FSpot.GroupAdaptor/ChangedHandler:invoke_void__this___GroupAdaptor (FSpot.GroupAdaptor)
  at FSpot.TimeAdaptor+<DoReload>c__AnonStorey19.<>m__6B () [0x00000] in <filename unknown>:0 
  at FSpot.Driver+<RunIdle>c__AnonStorey11.<>m__50 () [0x00000] in <filename unknown>:0 
  at GLib.Idle+IdleProxy.Handler () [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at FSpot.Driver.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at FSpot.Driver.Main(System.String[] args)
```

---

