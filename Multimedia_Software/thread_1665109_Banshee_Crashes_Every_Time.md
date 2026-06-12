---
title: "Banshee Crashes Every Time"
date: 2011-01-11
forum: Multimedia Software
---

### Post by lanetherif on 2011-01-11
Hi,

every time I try to try to update my library, banshee keeps crashing. It started after I relocated where my mp3 files are and changed the path in banshee too. I tried deleting the banshee folder under my home folder and removing and reinstalling banshee, but the problem persisted.
This is the when it is run from terminal:
```
[Info  04:46:29.238] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, x86_64) @ 2010-11-26 14:10:54 UTC]
[Info  04:46:29.569] Starting collection of anonymous usage data
[Warn  04:46:30.139] Caught an exception - System.ApplicationException: Invalid frame dimensions (in `Hyena.Gui')
  at Hyena.Widgets.AnimatedImage.ExtractFrames () [0x00000] in <filename unknown>:0 
  at Hyena.Widgets.AnimatedImage.Load () [0x00000] in <filename unknown>:0 
  at Banshee.Gui.Widgets.TaskStatusIcon..ctor () [0x00000] in <filename unknown>:0 
[Info  04:46:30.273] Updating web proxy from GConf
[Info  04:46:30.317] All services are started 0.885947
[Info  04:46:31.218] nereid Client Started
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Hyena.Widgets.RoundedFrame.DrawFrame (Cairo.Context cr, Rectangle clip) [0x00000] in <filename unknown>:0 
  at Hyena.Widgets.RoundedFrame.OnExposeEvent (Gdk.EventExpose evnt) [0x00000] in <filename unknown>:0 
  at Gtk.Widget.exposeevent_cb (IntPtr widget, IntPtr evnt) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Widget.exposeevent_cb(IntPtr widget, IntPtr evnt)
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

```

I don't have any slightest idea about the problem, so any help will be appreciated...

---

### Post by jonesrussell42 on 2011-01-14
I was just having the same problem and I wiped out my ~/.gconf/apps/banshee-1 folder and just resetup banshee and it works fine.

I guess I would suggest trying:

mv ~/.gconf/apps/banshee-1 ~/banshee-1.bak

Start it up and see if you're happy with the results. Otherwise, you can put that backup back and go hunt for whatever specific file is causing the issue.

---

### Post by SorinN on 2011-02-11
Banshee work nicely for a while but now ..crash all time.
The dump : 

sorin@sorin:~$ banshee
[Info  08:56:07.316] Running Banshee 1.9.3: [Ubuntu 10.10 1677da1 (linux-gnu, i686) @ 2011-02-10 16:15:29 UTC]
[Info  08:56:12.074] [Streamrecorder.Gst.Marshaller] gstreamer version found: GStreamer 0.10.30
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
[Info  08:56:15.399] Updating web proxy from GConf
[Info  08:56:15.542] All services are started 7.587378

Native stacktrace:

	banshee-1() [0x80d4d0b]
	banshee-1() [0x805b81f]
	[0xd8c40c]
	/usr/lib/fglrx/dri/fglrx_dri.so(+0x17cedb3) [0xab2a9db3]
	/lib/libpthread.so.0(+0x5cc9) [0x4adcc9]
	/lib/libc.so.6(clone+0x5e) [0xf2469e]

Debug info from gdb:

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
sorin@sorin:~$ 


as a root Banshee can work - but still seems to have some problems :

sorin@sorin:~$ sudo banshee
[sudo] password for sorin: 
[Info  09:00:24.103] Running Banshee 1.9.3: [Ubuntu 10.10 1677da1 (linux-gnu, i686) @ 2011-02-10 16:15:29 UTC]
[Warn  09:00:26.547] DBus support could not be started. Disabling for this session.
[Info  09:00:26.846] Migrating album-art cache directory
[Info  09:00:26.851] Migrated 0 files in 0.002336s
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
[Warn  09:00:28.949] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  09:00:28.950] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  09:00:28.969] Updating web proxy from GConf
[Warn  09:00:29.092] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  09:00:29.092] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  09:00:29.093] All services are started 2.545101
[Warn  09:00:29.367] Migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/root/.config/banshee-1/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
[Info  09:00:29.923] nereid Client Started
[Info  09:00:30.844] AppleDeviceSource is ignoring unmounted volume System
[Warn  09:00:30.845] Caught an exception - System.InvalidOperationException: Operation is not valid due to the current state of the object (in `Banshee.Dap.AppleDevice')
  at Banshee.Dap.AppleDevice.AppleDeviceSource.DeviceInitialize (IDevice device) [0x00000] in <filename unknown>:0 
  at Banshee.Dap.DapService.FindDeviceSource (IDevice device) [0x00000] in <filename unknown>:0 
[Warn  09:01:52.350] IScreensaverManager extension failed to load - System.ArgumentNullException: Argument cannot be null.
Parameter name: address (in `NDesk.DBus')
  at NDesk.DBus.Bus.Open (System.String address) [0x00000] in <filename unknown>:0 
  at NDesk.DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
System.Exception: Unable to open the session message bus. (in `NDesk.DBus')
  at NDesk.DBus.Bus.get_Session () [0x00000] in <filename unknown>:0 
  at Banshee.GnomeBackend.GnomeScreensaverManager.get_Manager () [0x00000] in <filename unknown>:0 
  at Banshee.GnomeBackend.GnomeScreensaverManager..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. (in `mscorlib')
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] in <filename unknown>:0 
  at Mono.Addins.InstanceExtensionNode.CreateInstance (System.Type expectedType) [0x00000] in <filename unknown>:0 
  at Banshee.PlatformServices.ScreensaverManager..ctor () [0x00000] in <filename unknown>:0 
^C
sorin@sorin:~$

---

