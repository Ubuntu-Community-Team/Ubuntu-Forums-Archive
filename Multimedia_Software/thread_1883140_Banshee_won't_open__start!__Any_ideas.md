---
title: "Banshee won't open / start!  Any ideas?"
date: 2011-11-18
forum: Multimedia Software
---

### Post by wildwildebeest on 2011-11-18
All of a sudden, Banshee stopped opening, via any means.

Actually, typing 'sudo banshee' into a terminal does open the program, but it shuts as soon as you click on anything.

Any ideas would be much appreciated as I use it so often!


I'm running Ubuntu 11.10.

When I run just 'banshee' in a terminal I get:

[Info  18:25:33.839] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-09-23 04:47:58 UTC]
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.ArgumentException: Value does not fall within the expected range.
  at Hyena.Gui.Canvas.Rect.set_Width (Double value) [0x00000] in <filename unknown>:0 
  at Hyena.Gui.Canvas.Rect.op_Explicit (Rectangle rect) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Gui.ListView`1[Banshee.Collection.AlbumInfo].OnSizeAllocated (Rectangle allocation) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.sizeallocated_cb (IntPtr widget, IntPtr allocation) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.sizeallocated_cb(IntPtr widget, IntPtr allocation)
   at Gtk.Widget.gtksharp_widget_base_show(IntPtr )
   at Gtk.Widget.OnShown()
   at Nereid.PlayerInterface.OnShown()
   at Gtk.Widget.shown_cb(IntPtr widget)
   at Gtk.Widget.gtk_widget_show(IntPtr )
   at Gtk.Widget.Show()
   at Banshee.Gui.BaseClientWindow.InitialShowPresent()
   at Nereid.PlayerInterface.Initialize()
   at Banshee.Gui.BaseClientWindow.InitializeWindow()
   at Banshee.Gui.BaseClientWindow..ctor(System.String title, System.String configNameSpace, Int32 defaultWidth, Int32 defaultHeight)
   at Nereid.PlayerInterface..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.ServiceStack.ServiceManager.RegisterService(System.Type type)
   at Banshee.ServiceStack.ServiceManager.Run()
   at Banshee.ServiceStack.Application.Run()
   at Banshee.Gui.GtkBaseClient.Initialize(Boolean registerCommonServices)
   at Banshee.Gui.GtkBaseClient..ctor(Boolean initializeDefault, System.String defaultIconName)
   at Banshee.Gui.GtkBaseClient..ctor()
   at Nereid.Client..ctor()
   at System.Reflection.MonoCMethod.InternalInvoke(System.Reflection.MonoCMethod , System.Object , System.Object[] , System.Exception ByRef )
   at System.Reflection.MonoCMethod.Invoke(System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.MonoCMethod.Invoke(BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
   at System.Reflection.ConstructorInfo.Invoke(System.Object[] parameters)
   at System.Activator.CreateInstance(System.Type type, Boolean nonPublic)
   at System.Activator.CreateInstance(System.Type type)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Startup()
   at Banshee.Gui.GtkBaseClient.Startup(System.String[] args)
   at Nereid.Client.Main(System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.AppDomain , System.Reflection.Assembly , System.String[] )
   at System.AppDomain.ExecuteAssemblyInternal(System.Reflection.Assembly a, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile, System.Security.Policy.Evidence assemblySecurity, System.String[] args)
   at System.AppDomain.ExecuteAssembly(System.String assemblyFile)
   at Booter.Booter.BootClient(System.String clientName)
   at Booter.Booter.Main()







and when I run 'sudo banshee' I get:

[Info  18:26:48.302] Running Banshee 2.2.0: [Ubuntu oneiric (development branch) (linux-gnu, x86_64) @ 2011-09-23 04:47:58 UTC]
[Warn  18:26:49.386] DBus support could not be started. Disabling for this session. - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
System.Exception: Unable to open the session message bus. (in `dbus-sharp')
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
  at DBus.BusG.Init () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.DBusConnection.Connect (System.String serviceName, Boolean init) [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.DBusConnection.Connect (System.String serviceName) [0x00000] in <filename unknown>:0 
[Info  18:26:50.227] Updating web proxy from GConf
[Warn  18:26:51.700] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  18:26:51.701] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Warn  18:26:51.716] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  18:26:51.716] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.

(Banshee:2270): Gtk-WARNING **: Refusing to add non-unique action 'CloseAction' to action group 'Global'
[Warn  18:26:51.822] Caught an exception - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `dbus-sharp')
  at DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
[Warn  18:26:51.822] Extension `Banshee.SoundMenu.SoundMenuService' not started: Unable to open the session message bus.
[Warn  18:26:51.822] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  18:26:51.823] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  18:26:51.824] All services are started 2.436102
[Info  18:26:52.421] AmazonMP3 store redirect URL: [https://one.ubuntu.com/music/store/amz/](https://one.ubuntu.com/music/store/amz/)
[Info  18:26:52.797] nereid Client Started
[Info  18:26:52.920] GStreamer version 0.10.35.0, gapless: True, replaygain: False
Stacktrace:

  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000b>
  at Banshee.Gui.GtkBaseClient.Run () <0x0005f>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00049>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x0008e>
  at Banshee.Gui.GtkBaseClient.Startup<T> () <0x0006b>
  at Banshee.Gui.GtkBaseClient.Startup<T> (string[]) <0x000ff>
  at Nereid.Client.Main (string[]) <0x00017>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.AppDomain,System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00047>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00037>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x0006b>
[Warn  18:27:02.994]  at Booter.Booter.Main () <0x001db>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

 Could no read GConf key sources.MusicLibrarySource-Library.current_filters - GLib.GException: Configuration server couldn't be contacted: D-BUS error: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. (in `gconf-sharp')
  at GConf.Client.Get (System.String key) [0x00000] in <filename unknown>:0 
  at Banshee.GnomeBackend.GConfConfigurationClient.TryGet[String[]] (System.String namespace, System.String key, System.String[]& result) [0x00000] in <filename unknown>:0

---

### Post by jerrrys on 2011-11-20
go to your home folder/.config/xbanshee-1 and rename the xbanshee-1 file (in case you want to restore it) and then open banshee.  this file will regenerate and may solve your problem.

---

### Post by wildwildebeest on 2011-11-20
Thanks for replying!

That helped a bit - I was able to click on a few things in Banshee (I tried to 'rescan music library') - but it wasn't long before it crashed again.

And still nothing from the usual banshee icons.

Any further suggestions very welcome.


EXTRA INFO, PROBABLY IRRELEVANT:
The terminal output was a bit different: the final 2 paragraphs (title 'native stacktrace:' and 'stacktrace:') were blank.

Finally, the 'banshee-1' folder that regenerated is a bit different, missing a few files ('get_accel_map', 'log', 'ossifer-browser-cookies.sqlite'), and the subfolder 'addin-db-001' is also missing 'config.xml'.



Cheers!

---

