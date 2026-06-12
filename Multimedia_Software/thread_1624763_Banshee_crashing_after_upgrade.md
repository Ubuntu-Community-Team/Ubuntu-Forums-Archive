---
title: "Banshee crashing after upgrade"
date: 2010-11-18
forum: Multimedia Software
---

### Post by Techrogue on 2010-11-18
Hi all

Last night I updated my system from Lucid to Maverick using update manager. I'm using KDE by way of Kubuntu.

In the process, Banshee got updated to 1.8, and now it crashes seconds after launch. I ran it from a terminal and got this:

```
[Info  08:48:16.428] Running Banshee 1.8.0: [Ubuntu 10.10 (linux-gnu, i686) @ 2010-10-26 18:21:18 UTC]
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
[Warn  08:48:19.223] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  08:48:19.224] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  08:48:19.257] Updating web proxy from GConf
[Info  08:48:19.272] Netbook extension initialized with hidden panel
[Warn  08:48:19.403] Add-in could not be loaded: The required addin 'Banshee.Mpris,1.0' is disabled. - Mono.Addins.MissingDependencyException: The required addin 'Banshee.Mpris,1.0' is disabled. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
[Warn  08:48:19.403] Caught an exception - Mono.Addins.MissingDependencyException: The required addin 'Banshee.Mpris,1.0' is disabled. (in `Mono.Addins')
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
  at Mono.Addins.AddinSessionService.ResolveLoadDependencies (System.Collections.ArrayList addins, System.Collections.Stack depCheck, System.String id, Boolean optional) [0x00000] in <filename unknown>:0 
[Warn  08:48:19.403] Extension `/Banshee/ServiceManager/Service/__nid_15' not started: The required addin 'Banshee.Mpris,1.0' is disabled.
[Warn  08:48:19.424] Caught an exception - System.ApplicationException: No support GNOME Settings Daemon could be reached. (in `Banshee.MultimediaKeys')
  at Banshee.MultimediaKeys.MultimediaKeysService.Banshee.ServiceStack.IExtensionService.Initialize () [0x00000] in <filename unknown>:0 
  at Banshee.ServiceStack.ServiceManager.StartExtension (Mono.Addins.TypeExtensionNode node) [0x00000] in <filename unknown>:0 
[Warn  08:48:19.424] Extension `Banshee.MultimediaKeys.MultimediaKeysService' not started: No support GNOME Settings Daemon could be reached.
[Info  08:48:19.425] All services are started 1.538885
The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 3164 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I've tried everything I could think of (removing extensions, downgrading to a lucid package) but no luck, and Google seems to have nothing.

Any help will be appreciated...alternately if you have a recommendation for a music player that supports iPod touch sync I'll check it out.

---

### Post by Decorian on 2010-12-05
The  same is happening for me too, I hope someone has some idea about what to do.

Thanks.

---

### Post by cipherboy_loc on 2010-12-05
Try this:

```
sudo apt-get install gnome-session
```


It looks like it is looking for gnome-session, but could not find it; hence the crash. 



Cipherboy

---

