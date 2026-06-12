---
title: "Banshee is not opening up"
date: 2011-03-30
forum: Multimedia Software
---

### Post by mteaphysicsbob on 2011-03-30
Hello i  have the newest version of Banshee and it has been working fine until today, when it did not open i unistalled and reinstalled it hoping this would fix the problem, the same problem occurred(i can click it but it did not open.) So i then chose to open it through the terminal using the sudo command and it open but cant read files, and in the terminal it said this:

Info  23:45:25.324] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-11-26 13:53:04 UTC]
[Warn  23:45:26.713] DBus support could not be started. Disabling for this session.
[Info  23:45:27.040] Migrating album-art cache directory
[Info  23:45:27.045] Migrated 0 files in 0.002523s
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
[Warn  23:45:30.307] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  23:45:30.307] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Warn  23:45:30.332] Add-in could not be loaded: The required addin 'Banshee.Mpris,1.0' is disabled. - Mono.Addins.MissingDependencyException: The required addin 'Banshee.Mpris,1.0' is disabled. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
[Warn  23:45:30.332] Caught an exception - Mono.Addins.MissingDependencyException: The required addin 'Banshee.Mpris,1.0' is disabled. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
[Warn  23:45:30.332] Extension `/Banshee/ServiceManager/Service/__nid_9' not started: The required addin 'Banshee.Mpris,1.0' is disabled.
[Info  23:45:30.338] Updating web proxy from GConf
[Warn  23:45:30.521] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  23:45:30.521] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  23:45:30.522] All services are started 3.808034
[Warn  23:45:30.934] Migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/root/.config/banshee-1/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
[Info  23:45:31.189] nereid Client Started
[Warn  23:46:09.569] IScreensaverManager extension failed to load - System.ArgumentNullException: Argument cannot be null.
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

---

### Post by mteaphysicsbob on 2011-03-30
So now i got the music uploaded it and it plays music but the only way i can open it is with terminal and nothing else....

---

### Post by directhex on 2011-03-30
sudo rm -r ~/.config/banshee-1 ~/.cache/banshee-1

Then DON'T use sudo to run banshee, ever.

---

