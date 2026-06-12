---
title: "Banshee Crashing"
date: 2011-10-10
forum: Multimedia Software
---

### Post by DaimyoKirby on 2011-10-10
First things first, I have to disclose that this error doesn't *always* happen, but it does every once in a while.

Sometimes, when I open banshee, it'll open, then close again.
I ran it in terminal, and this is what happened:
```
alden@Laptop:~$ banshee
[Info  14:26:28.785] Running Banshee 2.2.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-09-27 10:02:56 UTC]
[Warn  14:26:30.200] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  14:26:30.200] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  14:26:30.216] Updating web proxy from GConf
[Warn  14:26:30.440] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  14:26:30.440] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  14:26:30.445] All services are started 1.403867
[Info  14:26:31.507] AmazonMP3 store redirect URL: http://integrated-services.banshee.fm/amz/redirect.do/
** (Banshee:1877): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:1877): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:1877): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/alden/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:1877): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:1877): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:1877): DEBUG: Loading the real store page

** (Banshee:1877): WARNING **: Got less number of items in credentials hash table than expected!
[Info  14:26:32.322] nereid Client Started
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
[Info  14:26:32.516] GStreamer version 0.10.32.0, gapless: True, replaygain: True

(Banshee:1877): GLib-CRITICAL **: g_str_has_prefix: assertion `str != NULL' failed
Marshaling url-loaded signal
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.UbuntuOneMusicStore.UbuntuOneMusicStoreSource.OnDefaultStoreUrlLoaded (System.Object o, UbuntuOne.UrlLoadedArgs args) [0x00000] in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.MulticastDelegate.DynamicInvokeImpl (System.Object[] args) [0x00000] in <filename unknown>:0 
  at System.Delegate.DynamicInvoke (System.Object[] args) [0x00000] in <filename unknown>:0 
  at GLib.Signal.ClosureInvokedCB (System.Object o, GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.Invoke (GLib.ClosureInvokedArgs args) [0x00000] in <filename unknown>:0 
  at GLib.SignalClosure.MarshalCallback (IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data) [0x00000] in <filename unknown>:0 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.SignalClosure.MarshalCallback(IntPtr raw_closure, IntPtr return_val, UInt32 n_param_vals, IntPtr param_values, IntPtr invocation_hint, IntPtr marshal_data)
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

Anyone know what's wrong?

---

### Post by jherrero on 2011-10-23
I had a similar problem. Banshee was starting normally, but would use all the CPU and become unresponsive fairly quickly. Running banshee on the command line would output the same warning and error messages.

I manage to resolve my problem by disabling the UbuntuOne music store extension. I simply moved /usr/lib/banshee/Extensions/Banshee.UbuntuOneMusicStore.dll somewhere else and banshee is stable now. I haven't removed the  banshee-extension-ubuntuonemusicstore package in case future versions work better for me.

I hope this helps

---

### Post by sakthi on 2011-10-24
Thanks Jherrero! That solved the issue.

---

### Post by DaimyoKirby on 2011-10-25
I've actually (for now) tried using some other music players (exaile, clementine), just to try out some other popular options, so I haven't tried your fix - but if someone says it worked, than I'll count that as solved.

Thanks!

---

