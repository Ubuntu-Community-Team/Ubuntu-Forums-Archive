---
title: "Banshee Error Output Help"
date: 2011-06-19
forum: Multimedia Software
---

### Post by akira7799 on 2011-06-19
Hey All, 

Banshee was responding slowly, but now won't play music at all.

This is a code copy from the terminal from the "banshee" command:

```
[Info  16:11:40.455] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, x86_64) @ 2011-04-18 16:18:52 UTC]
[Info  16:11:41.665] Updating web proxy from GConf
[Info  16:11:41.716] All services are started 1.054423
** (Banshee:3389): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:3389): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:3389): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/dave/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:3389): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:3389): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:3389): DEBUG: Loading the real store page
[Info  16:11:43.407] nereid Client Started
[Info  16:11:43.595] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Info  16:11:43.754] AppleDeviceSource is ignoring unmounted volume System Reserved
[Info  16:11:43.765] AppleDeviceSource is ignoring unmounted volume Local Disk
[Info  16:11:43.767] AppleDeviceSource is ignoring unmounted volume 128 GB Filesystem
[Error 16:12:20.901] GStreamer resource error: NotFound
[Error 16:12:21.188] GStreamer resource error: NotFound
[Error 16:12:21.467] GStreamer resource error: NotFound
[Error 16:12:21.747] GStreamer resource error: NotFound
[Error 16:12:22.027] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:56.688] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:56.709] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:12:56.710] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:56.962] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:56.994] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:12:56.995] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:57.248] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:57.276] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:12:57.277] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:57.529] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:57.556] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:12:57.557] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:57.810] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:12:57.836] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:12:57.837] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:13:16.737] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:13:16.765] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:13:16.773] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:13:33.993] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:13:34.024] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:13:34.025] GStreamer resource error: NotFound

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:13:38.201] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 

(Banshee:3389): Gtk-CRITICAL **: IA__gtk_action_group_get_action: assertion `GTK_IS_ACTION_GROUP (action_group)' failed
[Warn  16:13:38.226] Error running PlayerEngine handler for StateChange - System.NullReferenceException: Object reference not set to an instance of an object (in `Banshee.PlayQueue')
  at Banshee.PlayQueue.PlayQueueActions.OnPlayerEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
  at Banshee.MediaEngine.PlayerEngineService.RaiseEvent (Banshee.MediaEngine.PlayerEventArgs args) [0x00000] in <filename unknown>:0 
[Error 16:13:38.228] GStreamer resource error: NotFound

```

Any suggestions?

Thanks, 
Dave

---

