---
title: "[SOLVED] Banshee won't start"
date: 2008-12-16
forum: Multimedia Software
---

### Post by civillian on 2008-12-16
Basically, the problem that I have is that every time I try to start banshee, it appears for a second or two, then vanishes.

When I run it from the command line I get this output

```
[Info  17:54:38.472] Running Banshee 1.2.1
Add-in could not be loaded: The required addin 'Banshee.Core,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Banshee.Core,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Warn  17:54:39.922] Caught an exception - The required addin 'Banshee.Core,1.0' is not installed. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Warn  17:54:39.923] Extension `/Banshee/ServiceManager/Service/__nid_7' not started: The required addin 'Banshee.Core,1.0' is not installed.
Add-in could not be loaded: The required addin 'Banshee.Core,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Banshee.Core,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Warn  17:54:40.284] Caught an exception - The required addin 'Banshee.Core,1.0' is not installed. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Warn  17:54:40.284] Extension `/Banshee/ServiceManager/Service/__nid_7' not started: The required addin 'Banshee.Core,1.0' is not installed.
[Info  17:54:40.285] All services are started 1.436816s
Add-in could not be loaded: The required addin 'Banshee.Core,1.0' is not installed.
Mono.Addins.MissingDependencyException: The required addin 'Banshee.Core,1.0' is not installed.
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Warn  17:54:40.607] IScreensaverManager extension failed to load - The required addin 'Banshee.Core,1.0' is not installed. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] 
[Info  17:54:41.005] nereid Client Started

** (Nereid:13860): WARNING **: The following assembly referenced from /usr/lib/banshee-1/Extensions/Banshee.Podcasting.dll could not be loaded:
     Assembly:   taglib-sharp    (assemblyref_index=7)
     Version:    2.0.3.0
     Public Key: db62eba44689b5b0
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/banshee-1/Extensions).


** (Nereid:13860): WARNING **: Could not load file or assembly 'taglib-sharp, Version=2.0.3.0, Culture=neutral, PublicKeyToken=db62eba44689b5b0' or one of its dependencies.
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.IO.FileNotFoundException: Could not load file or assembly 'taglib-sharp, Version=2.0.3.0, Culture=neutral, PublicKeyToken=db62eba44689b5b0' or one of its dependencies.
File name: 'taglib-sharp, Version=2.0.3.0, Culture=neutral, PublicKeyToken=db62eba44689b5b0'
  at Banshee.Podcasting.PodcastService.MigrateLegacyIfNeeded () [0x00000] 
  at Banshee.Podcasting.PodcastService.DelayedInitialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.DelayedInitialize (IService service) [0x00000] 
  at Banshee.ServiceStack.ServiceManager.DelayedInitialize () [0x00000] 
  at Banshee.ServiceStack.ServiceManager.OnClientStarted (Banshee.ServiceStack.Client client) [0x00000] 
  at Banshee.ServiceStack.Application.OnClientStarted (Banshee.ServiceStack.Client client) [0x00000] 
  at Banshee.ServiceStack.Client.OnStarted () [0x00000] 
  at Banshee.Gui.GtkBaseClient+<>c__CompilerGenerated15.<Run>c__67 () [0x00000] 
  at Banshee.Gui.GtkBaseClient+<>c__CompilerGenerated18.<RunIdle>c__70 () [0x00000] 
  at GLib.Idle+IdleProxy.Handler () [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Idle+IdleProxy.Handler()
   at GLib.Idle+IdleProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Banshee.Gui.GtkBaseClient.Run()
   at Banshee.Gui.GtkBaseClient.Startup()
   at Hyena.Gui.CleanRoomStartup.Startup(Hyena.Gui.StartupInvocationHandler startup)
   at Banshee.Gui.GtkBaseClient.Entry()
   at Nereid.Client.Main(System.String[] args)

```

has this happened to anyone? can anyone suggest a fix? 
Thanks, 
Civ.

---

### Post by civillian on 2008-12-16
I updated via the banshee repos and still get the same errors. Any help?

---

### Post by civillian on 2008-12-16
after updating **all** the packages that had newer versions in the banshee repos it works now, consider this problem fixed.

---

