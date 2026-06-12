---
title: "Banshee will not open"
date: 2011-08-15
forum: Multimedia Software
---

### Post by lalilulelo on 2011-08-15
Banshee will not run when I click its icon in the launcher. The little arrow appears next to it, and then nothing happens. I'm running Ubuntu 11.04. I ran it in the terminal and got this (x's inserted for username):

```
[Info  06:10:11.264] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, x86_64) @ 2011-06-28 05:39:10 UTC]
[Info  06:10:12.004] Updating web proxy from GConf
[Info  06:10:12.034] All services are started 0.637278
** (Banshee:3180): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:3180): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:3180): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/xxxxx/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:3180): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:3180): WARNING **: Error rescanning Purchased Music: No such file or directory
** (Banshee:3180): DEBUG: Loading the real store page

** (Banshee:3180): WARNING **: Got less number of items in credentials hash table than expected!
[Info  06:10:13.013] nereid Client Started
[Info  06:10:13.069] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Info  06:10:13.093] AppleDeviceSource is ignoring unmounted volume 320 GB Filesystem
[Info  06:10:13.140] AppleDeviceSource is ignoring unmounted volume System Reserved
```

The 320GB Filesystem is my other drive which has Windows 7 installed on it. I haven't purchased any music from Ubuntu One, so I don't know why it's looking for that. I also don't have any Apple devices connected to my computer, although I did earlier. I've tried uninstalling and reinstalling Banshee, but it did nothing. This really sucks.

Another piece of information that may be relevant: this started happening immediately after I installed a GStreamer plugin, specifically the one for aac, xvid, mpeg2, and faad. I've since uninstalled this package, but Banshee still will not load.

---

### Post by lalilulelo on 2011-08-15
Well, thanks for all the helpful suggestions. I figured it out myself. For some reason, the window was opening on another screen that was connected but powered down. Not sure why it's doing that, but at least I know Banshee isn't the problem.

---

