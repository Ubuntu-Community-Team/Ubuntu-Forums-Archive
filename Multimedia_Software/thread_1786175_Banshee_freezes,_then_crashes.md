---
title: "Banshee freezes, then crashes"
date: 2011-06-19
forum: Multimedia Software
---

### Post by insanekat on 2011-06-19
I'm running Ubuntu 11.04 and dual booting with Windows 7. As soon as I open Banshee it freezes (and my computer becomes very slow and "skippy"), then it crashes. Banshee version is 2.1.0 (with +git20110613.r1.661e087-0ubuntu1+natty after it, if this makes a difference). For other information let me know and I'd be happy to give it. 

Any help would be appreciated, I miss my Banshee!

---

### Post by Yellow Pasque on 2011-06-19
Run it from a terminal. 
```
mono --debug /usr/lib/banshee/Banshee.exe
```

---

### Post by insanekat on 2011-06-19
```
[Info  09:39:35.778] Running Banshee 2.1.1: [Ubuntu 11.04 661e087 (linux-gnu, i686) @ 2011-06-13 19:04:48 UTC]
[Info  09:39:42.478] Updating web proxy from GConf
[Info  09:39:43.100] All services are started 5.705863
** (Banshee:4158): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:4158): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:4158): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/kat/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:4158): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:4158): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:4158): DEBUG: Loading the real store page

** (Banshee:4158): WARNING **: Got less number of items in credentials hash table than expected!
[Info  09:39:50.466] nereid Client Started
[Info  09:39:50.670] GStreamer version 0.10.32.0, gapless: False, replaygain: False
[Info  09:39:50.856] AppleDeviceSource is ignoring unmounted volume SYSTEM
[Info  09:39:50.858] AppleDeviceSource is ignoring unmounted volume 51 GB Filesystem
Stacktrace:

  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at Gtk.Application.Run () <IL 0x00000, 0x0000a>
  at Banshee.Gui.GtkBaseClient.Run () <IL 0x00013, 0x00054>
  at Banshee.Gui.GtkBaseClient.Startup () <IL 0x0000f, 0x0003f>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <IL 0x00045, 0x00089>
  at Banshee.Gui.GtkBaseClient.Startup<object> () <IL 0x00030, 0x0005c>
  at Banshee.Gui.GtkBaseClient.Startup<object> (string[]) <IL 0x0004d, 0x000d8>
  at Nereid.Client.Main (string[]) <IL 0x00001, 0x00015>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <IL 0x0001d, 0x00043>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <IL 0x00029, 0x0002e>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <IL 0x0000b, 0x00025>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <IL 0x00035, 0x00067>
  at System.AppDomain.ExecuteAssembly (string) <IL 0x00004, 0x00019>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <IL 0x00033, 0x00057>
  at Booter.Booter.BootClient (string) <IL 0x00024, 0x00069>
  at Booter.Booter.Main () <IL 0x000f6, 0x001a0>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <IL 0x0001b, 0x0003a>

Native stacktrace:

Inconsistency detected by ld.so: dl-open.c: 222: dl_open_worker: Assertion `_dl_debug_initialize (0, args->nsid)->r_state == RT_CONSISTENT' failed!

```

---

### Post by dino99 on 2011-06-19
if you run the git version, you might know and understand you are using the bleeding hedge development package, so no bug free guaranty

uninstall banshee* then uncheck the related ppa, update and install the genuine banshee package back

---

### Post by Yellow Pasque on 2011-06-19
Ah, thanks for pointing that out, dino. Indeed, the error given:
> Inconsistency detected by ld.so
..points to problems with different versions of shared libs.

---

### Post by insanekat on 2011-06-19
Tried that, the version I have now is: 2.0.0-2ubuntu1

However, still having the same problem.

```
[Info  10:54:41.554] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, i686) @ 2011-04-18 16:21:33 UTC]
[Info  10:54:44.219] Updating web proxy from GConf
[Info  10:54:44.295] All services are started 2.310366
** (Banshee:4470): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:4470): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:4470): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/kat/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:4470): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:4470): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:4470): DEBUG: Loading the real store page

** (Banshee:4470): WARNING **: Got less number of items in credentials hash table than expected!
[Info  10:54:48.498] nereid Client Started
[Info  10:54:48.637] GStreamer version 0.10.32.0, gapless: False, replaygain: False
[Info  10:54:48.731] AppleDeviceSource is ignoring unmounted volume SYSTEM
[Info  10:54:48.733] AppleDeviceSource is ignoring unmounted volume 51 GB Filesystem
Stacktrace:

  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at Gtk.Application.Run () <IL 0x00000, 0x0000a>
  at Banshee.Gui.GtkBaseClient.Run () <IL 0x00013, 0x00054>
  at Banshee.Gui.GtkBaseClient.Startup () <IL 0x0000f, 0x0003f>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <IL 0x00045, 0x00089>
  at Banshee.Gui.GtkBaseClient.Startup<object> () <IL 0x00030, 0x0005c>
  at Banshee.Gui.GtkBaseClient.Startup<object> (string[]) <IL 0x0004d, 0x000d8>
  at Nereid.Client.Main (string[]) <IL 0x00001, 0x00015>
  at (wrapper runtime-invoke) <Module>.runtime_invoke_void_object (object,intptr,intptr,intptr) <IL 0x0001d, 0x00043>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <IL 0x00029, 0x0002e>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <IL 0x0000b, 0x00025>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <IL 0x00035, 0x00067>
  at System.AppDomain.ExecuteAssembly (string) <IL 0x00004, 0x00019>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <IL 0x00033, 0x00057>
  at Booter.Booter.BootClient (string) <IL 0x00024, 0x00069>
  at Booter.Booter.Main () <IL 0x000f6, 0x001a0>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <IL 0x0001b, 0x0003a>

Native stacktrace:

Inconsistency detected by ld.so: dl-open.c: 222: dl_open_worker: Assertion `_dl_debug_initialize (0, args->nsid)->r_state == RT_CONSISTENT' failed!

```

---

### Post by insanekat on 2011-06-19
It's possibly an overarching problem, as all of my installed media programs (Movie Player, xine, VLC) are freezing and crashing as well.

Trying to get some debugging info but failing at it...

---

### Post by insanekat on 2011-06-19
Well it's fixed somehow... I guess that trick must've done it, it just took several restarts?

---

