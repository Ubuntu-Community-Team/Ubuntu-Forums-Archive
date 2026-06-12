---
title: "Banshee crashing on start since upgrade"
date: 2011-05-06
forum: Multimedia Software
---

### Post by lolwhites on 2011-05-06
Since upgrading to 11.04, Banshee crashes as soon as it's launched. When run in terminal, I get the following:

> [Info  12:37:35.878] Running Banshee 2.0.0: [Ubuntu Natty (development branch) (linux-gnu, i686) @ 2011-04-18 16:21:33 UTC]
[Warn  12:37:36.571] Could not migrate album artwork cache directory - System.IO.DirectoryNotFoundException: Directory 'file:/home/laurie/.cache/album-art/32' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetDirectories (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetDirectories (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.RecursiveDelete (System.String path) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.Delete (System.String path, Boolean recursive) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Delete (System.String directory, File dir, Boolean recursive) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Delete (System.String directory, Boolean recursive) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Directory.Delete (System.String directory, Boolean recursive) [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Gui.ArtworkManager.MigrateCacheDir () [0x00000] in <filename unknown>:0 
  at Banshee.Collection.Gui.ArtworkManager..ctor () [0x00000] in <filename unknown>:0 
[Info  12:37:37.554] Updating web proxy from GConf
[Info  12:37:37.642] All services are started 1.481466
** (Banshee:500): DEBUG: SyncDaemon already running, initializing SyncdaemonDaemon object

(Banshee:500): libsoup-WARNING **: No feature manager for feature of type 'U1RequestChrome'

** (Banshee:500): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 992, in get_info
    return self.syncdaemon_folders.get_info(path)
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 634, in get_info
    mdobj = self.fs.get_by_path(path.encode('utf-8'))
  File "/usr/lib/pymodules/python2.7/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 773, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/laurie/.ubuntuone/Purchased from Ubuntu One'


** (Banshee:500): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

** (Banshee:500): WARNING **: Error rescanning Purchased Music: No such file or directory
[Warn  12:37:39.319] Forcefully breaking out of RCS loop b/c change in total_width less than 1.0
** (Banshee:500): DEBUG: Loading the real store page
[Info  12:37:39.834] nereid Client Started
[Info  12:37:39.940] Converted legacy XML equalizer presets to new JSON format
[Info  12:37:39.965] GStreamer version 0.10.32.0, gapless: True, replaygain: False
[Info  12:37:40.020] AppleDeviceSource is ignoring unmounted volume Ubuntu 11.04 i386

Native stacktrace:

	banshee() [0x80dbc5b]
	banshee() [0x805e92f]
	[0xcc140c]
	/lib/libnss_wins.so.2(_nss_wins_gethostbyname2_r+0x3f) [0xaff9191f]
	/lib/i386-linux-gnu/libc.so.6(gethostbyname2_r+0x162) [0x1f85b2]
	/lib/i386-linux-gnu/libc.so.6(+0xa9079) [0x1b9079]
	/lib/i386-linux-gnu/libc.so.6(getaddrinfo+0x15b) [0x1b984b]
	/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x6e451) [0x18ca451]
	/usr/lib/i386-linux-gnu/libgio-2.0.so.0(+0x6dd86) [0x18c9d86]
	/lib/i386-linux-gnu/libglib-2.0.so.0(+0x6ca39) [0x518a39]
	/lib/i386-linux-gnu/libglib-2.0.so.0(+0x6a2df) [0x5162df]
	/lib/i386-linux-gnu/libpthread.so.0(+0x5e99) [0x45ae99]
	/lib/i386-linux-gnu/libc.so.6(clone+0x5e) [0x1e073e]

Debug info from gdb:

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

---

### Post by nickyspag on 2011-05-06
I was getting a similar problem.

Oddly when I set my gnome proxy setting to direct (no proxy) instead of using a proxy.pac, then banshee no longer crashes after opening.

---

### Post by Mphill102 on 2011-05-13
I too found that Banshee would crash as soon as it started. If I started banshee with sudo it would run. I remembered that a week ago I was trying to network my windows 7 HTPC with my Ubuntu 11.04 machine using Samba and winbind. When I removed winbind Banshee started to work again.

---

### Post by Mphill102 on 2011-05-14
> **Mphill102 said:**
> I too found that Banshee would crash as soon as it started. If I started banshee with sudo it would run. I remembered that a week ago I was trying to network my windows 7 HTPC with my Ubuntu 11.04 machine using Samba and winbind. When I removed winbind Banshee started to work again.


I have found a bug in Samba [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/529714](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/529714) I was able to get Samba with winbind and Banshee working  when I removed the banshee-extenision-ubuntuonemusicstore package from Synaptic Package Manager.

---

### Post by lidex on 2011-05-14
> **Mphill102 said:**
> I have found a bug in Samba [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/529714](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/529714) I was able to get Samba with winbind and Banshee working  when I removed the banshee-extenision-ubuntuonemusicstore package from Synaptic Package Manager.

Yes that seems to be the issue - not that there aren't more, mind you. Seems purging your banshee configuration then allows you to re-install it - gotta kill the cruft!

---

### Post by osfight.de on 2011-08-03
Does'nt work for me. I deinstalled winbind and the ubuntuone music store plugin, removed the .config/banshee-1 and .cache/banshee-1 dirs. 
Running Banshee as sudo works  but not without and ends up in a graphical mess (see attachment) and kills the window decorations once in a while. Any idea what is going?

---

### Post by URoRRuRRR on 2011-08-16
> **osfight.de said:**
> Does'nt work for me. I deinstalled winbind and the ubuntuone music store plugin, removed the .config/banshee-1 and .cache/banshee-1 dirs. 
Running Banshee as sudo works  but not without and ends up in a graphical mess (see attachment) and kills the window decorations once in a while. Any idea what is going?

I had this issue on 11.04 and found that the only way I could get Banshee working again was to also remove the .gconf/app/banshee-1 directory and then reinstall banshee.  You loose all yours settings and have to reimport the library again but it fixed the problem for me :)

---

### Post by dave2001 on 2011-10-10
> **URoRRuRRR said:**
> I had this issue on 11.04 and found that the only way I could get Banshee working again was to also remove the .gconf/app/banshee-1 directory and then reinstall banshee.  You loose all yours settings and have to reimport the library again but it fixed the problem for me :)

I think it's pretty ridiculous that the default audio player is still behaving like this months after release. I have tried everything listed in this thread.. all to no avail. Banshee still crashes about 3 seconds after opening. This is the log file created upon startup in /home/username/.config/banshee-1

```
exec -a banshee mono  /usr/lib/banshee/Banshee.exe    --redirect-log --play-enqueued

[Info  10:32:16.206] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[Info  10:32:19.113] Updating web proxy from GConf
[Info  10:32:19.366] All services are started 1.4268
[Warn  10:32:19.814] Migrating Internet Radio Stations - System.IO.DirectoryNotFoundException: Directory '/home/ubuntu/.config/banshee/plugins/stations/user' not found. (in `mscorlib')
  at System.IO.Directory.GetFileSystemEntries (System.String path, System.String searchPattern, FileAttributes mask, FileAttributes attrs) [0x00000] in <filename unknown>:0 
  at System.IO.Directory.GetFiles (System.String path, System.String searchPattern) [0x00000] in <filename unknown>:0 
  at Banshee.InternetRadio.XspfMigrator.Migrate () [0x00000] in <filename unknown>:0 
[Info  10:32:20.146] nereid Client Started
[Info  10:32:20.247] GStreamer version 0.10.32.0, gapless: True, replaygain: False

Unhandled Exception: GLib.GException: Can't recursively copy directory
  at GLib.FileAdapter.Move (File destination, FileCopyFlags flags, GLib.Cancellable cancellable, GLib.FileProgressCallback progress_callback) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Gio.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.IO.Directory.Move (Hyena.SafeUri from, Hyena.SafeUri to) [0x00000] in <filename unknown>:0 
  at Banshee.Podcasting.PodcastService.<DelayedInitialize>m__11 () [0x00000] in <filename unknown>:0 
```

---

### Post by lidex on 2011-10-10
Maybe 2.2 will work for you.
[http://banshee.fm/download/](http://banshee.fm/download/)

---

### Post by dave2001 on 2011-10-11
a solution in the following thread worked for me. the podcasting extension was causing the crash.[ http://ubuntuforums.org/showthread.php?t=1554252&page=3]("http://ubuntuforums.org/showthread.php?t=1554252&page=3")

---

### Post by mail.prabal on 2011-10-20
this solved my problem 

goto ubuntu software center
type banshee-extension-ubuntuonemusicstore
remove this package

and banshee runs fine

---

